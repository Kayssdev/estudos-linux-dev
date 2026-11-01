# Estudos de Linux

Repositório onde documento meus estudos de Linux: comandos explicados, exemplos testados no terminal e prints reais.

> Comandos testados em **Fedora** e **Ubuntu 24.04**. Os comandos de instalação variam conforme a distro (`dnf` no Fedora, `apt` no Ubuntu).

## Conteúdo

| Arquivo | Comandos abordados |
|---|---|
| [01 — Navegação](docs/01-navegacao.md) | `pwd`, `ls -la`, `cd`, `mkdir`, `cp`, `mv`, `rm`, `cat` |
| [02 — Permissões e Admin](docs/02-permissoes.md) | `sudo`, `chmod`, `chown` |
| [03 — Processos](docs/03-processos.md) | `ps aux`, `htop`, `kill`, `systemctl` |
| [04 — Redes](docs/04-redes.md) | `ping`, `curl`, `wget`, `ip a`, `telnet`, `whois`, `dig` |
| [05 — SSH e Acessos Linux](docs/05-ssh.md) | `ssh`, `ssh-keygen`, `ssh-copy-id`, `scp`, `~/.ssh/config` |

## Ambiente de laboratório

A pasta `labs/` contém uma VM Ubuntu 24.04 provisionada com Vagrant, reservada para os exercícios práticos que serão adicionados futuramente.

**Pré-requisitos:**
- [VirtualBox](https://www.virtualbox.org/)
- [Vagrant](https://www.vagrantup.com/)

**Subir a VM:**

```bash
cd labs
vagrant up
vagrant ssh
```

## Estrutura do repositório

```
estudos-linux-dev/
├── assets/img/        # prints dos exemplos por tema
├── docs/              # documentação dos comandos
├── labs/              # ambiente Vagrant e exercícios práticos
└── README.md
```

## Aviso

> ⚠️ Teste comandos como `rm`, `kill` e `chown` apenas em arquivos e processos seus, nunca em arquivos do sistema.
