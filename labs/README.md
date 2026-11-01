# Laboratório — Estudos de Linux

Exercícios práticos dos comandos documentados em `docs/`, executados numa VM Ubuntu 24.04.

## Ambiente

| Item | Versão |
|---|---|
| Sistema | Ubuntu 24.04 |
| Provisionamento | Vagrant + VirtualBox |

**Subir a VM:**

```bash
vagrant up
vagrant ssh
```

**Desligar a VM:**

```bash
vagrant halt
```

**Destruir a VM (apaga tudo):**

```bash
vagrant destroy
```

## Estrutura dos exercícios

```
labs/
├── 01-navegacao/    # pwd, ls, cd, mkdir, cp, mv, rm, cat
├── 02-permissoes/   # sudo, chmod, chown
├── 03-processos/    # ps aux, htop, kill, systemctl
├── 04-redes/        # ping, curl, wget, ip a, telnet, whois, dig
└── Vagrantfile
```

## Como usar

Cada pasta de tema contém exercícios relacionados ao que foi documentado em `docs/`. A ideia é reproduzir os exemplos dentro da VM para praticar num ambiente isolado e seguro.

## Aviso

> ⚠️ A VM é um ambiente descartável — fique à vontade para testar comandos destrutivos como `rm -rf` e `kill` sem medo de afetar sua máquina real.
