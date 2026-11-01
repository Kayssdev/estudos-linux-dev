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

## Aviso

> ⚠️ A VM é um ambiente descartável — fique à vontade para testar comandos destrutivos como `rm -rf` e `kill` sem medo de afetar sua máquina real.
