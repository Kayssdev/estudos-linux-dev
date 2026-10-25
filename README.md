# Estudos de Linux

## Comandos de Navegação

### `pwd`
- **O comando pwd pode ser utilizado para mostrar o caminho da pasta atual**

Exemplo -> `$pwd` -> resultado -> `/home/user/downloads`

O comando pwd é útil para confirmar em qual pasta o usuário está antes de executar outros comandos.

### `ls -la`
- **Este é uma extensão detalhada do comando padrão 'ls'**

O comando ls -la traz essas informações -> `/permissões/links/usuário/grupos/tamanho do arquivo/data e hora/nome do arquivo`

O "l" logo antes do "a" lista os arquivos ou pasta com detalhes mostrando suas permissões, links, usuários, grupos, tamanho e data do arquivo. E a utilidade do "a" é mostrar até mesmo os diretórios ou arquivos quais estão ocultos no sistema. Após juntar as siglas o terminal entrega uma saída detalhada como essa no exemplo a seguir:

`drwxr-xr-x. 1 user user 38 oct 24 10:33 Desktop` <- Arquivo não-oculto

`drwxr-xr-1. 1 user user 442 oct 24 14:39 .config` <- Arquivo oculto definidos geralmente por "."

### `cd`
-**cd é um comando básico de navegação entre pastas**

Pode ser utilizado da seguinte forma conforme o exemplo a seguir:

O usuário quer ir até a pasta downloads pode-se usar o comando ls para listar os diretórios disponíveis -> `Desktop, Downloads, Documents... etc` e decide querer ir até a pasta downloads, utiliza-se então o seguinte comando -> `cd Downloads` -> e logo após utilizar o comando pwd para confirmar que entrou no diretório `pwd` saída do terminal prevista -> `/home/user/Downloads`

### ´mkdir´
-**"make directory" ou como propriamente é sua abreviatura "mkdir" é um comando utilizado para a criação de diretórios ou pasta como preferir!**

Exemplos de usos:

Pode-se criar pastas atráves de um caminho específico -> `mkdir /home/user/Documents/estudos-linux` ou até mesmo dentro já dentro de uma pasta em específico -> `mkdir estudos-linux`(Dentro da pasta desejada)

O resultado será criação da pasta desejada, liste ela com o comando "ls" no terminal dentro da pasta ou diretório atual -> `ls` -> `estudos-linux`

### `cp`
-**"Copy" ou cp, é o comando utilizado para copiar pastas e arquivos**

Dado pelo seguinte formato

`cp origem destino`

Exemplo:

-> `cp arquivo.txt /home/user/Downloads/` ou pode criar a cópia na pasta atual com um nome diferente `cp arquivo.txt notas.txt`

Para copiar diretórios completos utiliza-se de uma incrementação no comando que seria o `-r` significando "recursivo" faz o cp entrar na pasta e copiar tudo que está dentro dela incluindo suas subpastas, exemplo:

-> `cp -r home/user/Documents home/user/Downloads` 

ou até mesmo de forma mais simples, estando no caminho da pasta desejada pode escrever o seguinte comando para copiar para o caminho desejado:

-> `cp -r Documents ../Downloads`