# Estudos de Linux

## Comandos de Navegação

### `pwd`
- **O comando pwd pode ser utilizado para mostrar o caminho da pasta atual**

Exemplo -> `$pwd` -> resultado -> `/home/user/downloads`

O comando pwd é útil para confirmar em qual pasta o usuário está antes de executar outros comandos.

### `ls -la`
- **Este é uma extensão detalhada do comando padrão 'ls'**

O "l" logo antes do "a" lista os arquivos ou pasta com detalhes mostrando suas permissões, links, usuários, grupos, tamanho e data do arquivo. E a utilidade do "a" é mostrar até mesmo os arquivos quais estão ocultos no sistema. Após juntar as siglas o terminal entrega uma saída detalhada como essa no exemplo a seguir:

`drwxr-xr-x. 1 user user 38 oct 24 10:33 Desktop` <- Arquivo não-oculto

O comando ls traz essas informações -> `/permissões/links/usuário/grupos/tamanho do arquivo/data e hora/nome do arquivo`

`drwxr-xr-1. 1 user user 442 oct 24 14:39 .config` <- Arquivo oculto definidos geralmente por "."