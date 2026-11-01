# Cheatsheet — Comandos Linux

Referência rápida de todos os comandos documentados neste repositório.

---

## Navegação

| Comando | O que faz |
|---|---|
| `pwd` | Mostra o caminho da pasta atual |
| `ls -la` | Lista arquivos com detalhes, incluindo ocultos |
| `cd pasta` | Entra em uma pasta |
| `cd ..` | Sobe um nível para a pasta pai |
| `cd ~` | Vai para a pasta pessoal (home) |
| `cd -` | Volta para a pasta anterior |
| `cd /` | Vai para a raiz do sistema |
| `mkdir nome` | Cria um diretório |
| `cp origem destino` | Copia um arquivo |
| `cp -r origem destino` | Copia um diretório inteiro |
| `mv origem destino` | Move ou renomeia arquivo/diretório |
| `rm arquivo` | Remove um arquivo |
| `rmdir diretorio` | Remove um diretório vazio |
| `rm arquivo*` | Remove todos os arquivos com o mesmo prefixo |
| `cat arquivo` | Exibe o conteúdo de um arquivo |
| `cat arquivo{1..4}.txt` | Concatena e exibe múltiplos arquivos |
| `whoami` | Exibe o nome do usuário atual |
| `hostname` | Exibe o nome da máquina |
| `touch arquivo` | Cria um arquivo vazio |
| `file arquivo` | Identifica o tipo real de um arquivo |

---

## Permissões e Admin

| Comando | O que faz |
|---|---|
| `sudo comando` | Executa um comando com privilégios administrativos |
| `chmod u+x arquivo` | Dá permissão de execução ao dono (notação simbólica) |
| `chmod 755 arquivo` | Define permissões via notação numérica |
| `ls -l` | Exibe permissões dos arquivos |
| `chown dono arquivo` | Altera o dono de um arquivo |
| `chown dono:grupo arquivo` | Altera o dono e o grupo de um arquivo |
| `chown :grupo arquivo` | Altera apenas o grupo de um arquivo |

**Referência rápida — notação numérica:**

| Valor | Permissão |
|---|---|
| `4` | leitura (r) |
| `2` | escrita (w) |
| `1` | execução (x) |
| `7` | todas (r+w+x) |

**Permissões mais comuns:**

| Valor | Representação | Uso típico |
|---|---|---|
| `777` | `rwxrwxrwx` | Todos podem tudo — evite, é inseguro |
| `755` | `rwxr-xr-x` | Padrão para pastas e scripts |
| `644` | `rw-r--r--` | Padrão para arquivos comuns |
| `600` | `rw-------` | Obrigatório para chaves SSH privadas |
| `700` | `rwx------` | Usado para a pasta `~/.ssh` |

**Dica — `sudo` com redirecionador `>`:**

```bash
sudo echo "texto" > /etc/arquivo   # ❌ Permission denied
sudo sh -c "echo 'texto' > /etc/arquivo"  # ✅
```

---

## Processos

| Comando | O que faz |
|---|---|
| `ps aux` | Lista todos os processos em execução |
| `ps aux \| grep nome` | Filtra processos por nome |
| `htop` | Gerenciador de processos interativo |
| `kill PID` | Encerra um processo pelo PID |
| `sleep 300 &` | Cria um processo em segundo plano (útil para praticar `kill`) |
| `systemctl status serviço` | Verifica o estado de um serviço |
| `systemctl start serviço` | Inicia um serviço |
| `systemctl stop serviço` | Para um serviço |
| `systemctl restart serviço` | Reinicia um serviço (derruba conexões) |
| `systemctl reload serviço` | Recarrega um serviço (sem derrubar conexões) |
| `systemctl enable serviço` | Ativa o serviço no boot |
| `systemctl disable serviço` | Desativa o serviço no boot |
| `systemctl is-active serviço` | Verifica se o serviço está ativo |
| `systemctl is-enabled serviço` | Verifica se o serviço está habilitado no boot |
| `systemctl list-units --type=service` | Lista todos os serviços |
| `systemctl --failed` | Lista serviços com falha |

---

## Redes

| Comando | O que faz |
|---|---|
| `ping -c 4 host` | Testa conectividade com um host (4 pacotes) |
| `curl url` | Faz uma requisição HTTP/HTTPS |
| `wget url` | Baixa um arquivo via HTTP/HTTPS/FTP |
| `ip a` | Exibe interfaces de rede e endereços IP |
| `telnet dominio porta` | Testa se uma porta está aberta em um servidor |
| `whois dominio` | Consulta o dono de um domínio ou bloco de IP |
| `dig dominio` | Consulta registros DNS de um domínio |
| `dig +short dominio` | Retorna apenas o IP do domínio |
| `dig dominio MX` | Retorna os servidores de e-mail |
| `dig dominio NS` | Retorna os servidores de nome |
| `dig -x ip` | DNS reverso: retorna o nome associado ao IP |

---

## SSH e Acessos Linux

| Comando | O que faz |
|---|---|
| `ssh usuario@ip` | Conecta em uma máquina remota |
| `ssh -p 2222 usuario@ip` | Conecta em uma porta diferente da padrão (22) |
| `ssh-keygen -t ed25519 -C "email"` | Gera um par de chaves SSH |
| `ssh-copy-id usuario@ip` | Copia a chave pública para o servidor |
| `scp arquivo.txt host:~` | Envia um arquivo para o servidor |
| `scp host:arquivo.txt .` | Baixa um arquivo do servidor para a pasta atual |
| `ssh -L 8080:localhost:8000 host -N` | Cria um túnel SSH (port forwarding) |
| `sudo sshd -t` | Testa a sintaxe do `sshd_config` antes de reiniciar |
| `sudo systemctl restart ssh` | Reinicia o serviço SSH |
| `ssh -o PubkeyAuthentication=no usuario@ip` | Testa login forçando senha (validar hardening) |

**Permissões obrigatórias para o SSH funcionar:**

| Caminho | Permissão |
|---|---|
| `~/.ssh/` | `700` |
| `~/.ssh/authorized_keys` | `600` |
| `~/.ssh/id_ed25519` (chave privada) | `600` |

**Exemplo de `~/.ssh/config`:**

```
Host labvm
    HostName 192.168.33.10
    User vagrant
```
