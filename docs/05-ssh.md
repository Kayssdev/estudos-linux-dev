# SSH e Acessos Linux

## O que é SSH?

O SSH (Secure Shell) é um protocolo que permite acessar o terminal de uma máquina remota de forma criptografada. Não é uma interface gráfica — é acesso direto à linha de comando de outro sistema.

A porta padrão é a **22**.

## Conectar em uma máquina remota

### `ssh`

Formato básico:

`ssh usuario@ip`

Para conectar em uma porta diferente da padrão:

`ssh -p 2222 usuario@ip`

## Gerar e usar chaves SSH

A autenticação por senha é vulnerável a ataques de força bruta. O método recomendado é usar um par de chaves criptográficas:

- **Chave privada:** fica na sua máquina. Nunca compartilhe.
- **Chave pública:** é copiada para o servidor. Fica em `~/.ssh/authorized_keys`.

### `ssh-keygen`

Gera o par de chaves:

```bash
ssh-keygen -t ed25519 -C "seu-email@exemplo.com"
```

As chaves são salvas em `~/.ssh/`:
- `id_ed25519` → chave privada (`chmod 600` obrigatório)
- `id_ed25519.pub` → chave pública

No Windows, use `type` para ver o conteúdo da chave pública antes de copiá-la para o servidor:

```powershell
type .\id_ed25519.pub
```

![chaves-ssh](/assets/img/ssh/exemplo-chaves-ssh.png)

### Instalar a chave pública no servidor

Dentro do servidor, prepare a pasta e cole o conteúdo da chave pública:

```bash
mkdir -p ~/.ssh
chmod 700 ~/.ssh
nano ~/.ssh/authorized_keys   # cola o conteúdo de id_ed25519.pub aqui
chmod 600 ~/.ssh/authorized_keys
```

### `ssh-copy-id`

Alternativa automática ao processo manual acima:

```bash
ssh-copy-id usuario@ip
```

Após instalar a chave, o `ssh` conecta direto sem pedir senha:

![ssh-conectando](/assets/img/ssh/exemplo-ssh-conectando.png)

## Hardening — desativar login por senha

Após configurar as chaves, desative o login por senha para fechar a porta para ataques de força bruta.

Edite o arquivo `/etc/ssh/sshd_config`:

```bash
sudo nano /etc/ssh/sshd_config
```

Altere a linha:

```
PasswordAuthentication no
```

> ⚠️ **Atenção no Ubuntu:** o arquivo `/etc/ssh/sshd_config.d/50-cloud-init.conf` pode sobrescrever essa configuração. Verifique e altere esse arquivo também se necessário.

Teste a sintaxe antes de reiniciar:

```bash
sudo sshd -t
```

Reinicie o serviço:

```bash
sudo systemctl restart ssh
```

Para confirmar que o login por senha foi bloqueado:

```bash
ssh -o PubkeyAuthentication=no usuario@ip
# Resultado esperado: Permission denied (publickey)
```

![hardening](/assets/img/ssh/exemplo-hardening.png)

## Configurar atalhos de conexão

### `~/.ssh/config`

Crie uma "agenda" de servidores para não precisar digitar IP e usuário toda vez.

Arquivo: `~/.ssh/config` (no Linux/macOS) ou `C:\Users\SeuUsuario\.ssh\config` (no Windows)

```
Host labvm
    HostName 192.168.33.10
    User vagrant
```

Com isso, basta digitar:

```bash
ssh labvm
```

> ⚠️ **No Windows:** o Bloco de Notas salva como `config.txt` por padrão. Renomeie para `config` sem extensão usando `mv .\config.txt config` no PowerShell.

![config-txt](/assets/img/ssh/exemplo-config-txt.png)

Após renomear corretamente, o `ssh labvm` conecta direto:

![ssh-config](/assets/img/ssh/exemplo-ssh-config.png)

## Copiar arquivos via SSH

### `scp`

O `scp` (Secure Copy) copia arquivos usando o túnel seguro do SSH.

Enviar um arquivo do computador local para o servidor:

```bash
scp arquivo.txt labvm:~
```

Puxar um arquivo do servidor para a pasta atual:

```bash
scp labvm:arquivo.txt .
```

![scp](/assets/img/ssh/exemplo-scp.png)

## Túnel SSH (Port Forwarding)

Permite acessar serviços que estão rodando dentro do servidor diretamente na sua máquina local.

**Cenário:** servidor web rodando na porta `8000` dentro da VM, acessível na porta `8080` do computador local.

Dentro da VM, suba o serviço:

```bash
python3 -m http.server 8000
```

No computador local, crie o túnel:

```bash
ssh -L 8080:localhost:8000 labvm -N
```

- `-L`: encaminhamento local
- `8080`: porta no computador local
- `localhost:8000`: destino dentro da VM
- `-N`: não abre shell, apenas mantém o túnel

![tunel-terminal](/assets/img/ssh/exemplo-tunel-terminal.png)

Acesse `http://localhost:8080` no navegador para ver os arquivos da VM:

![tunel-navegador](/assets/img/ssh/exemplo-tunel-navegador.png)
