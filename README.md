# Estudos de Linux

## Comandos de Navegação

### `pwd`
- **O comando pwd pode ser utilizado para mostrar o caminho da pasta atual**

Exemplo -> `pwd` -> resultado -> `/home/user/downloads`

O comando pwd é útil para confirmar em qual pasta o usuário está antes de executar outros comandos.

### `ls -la`
- **Este é uma extensão detalhada do comando padrão 'ls'**

O comando ls -la traz essas informações -> `/permissões/links/usuário/grupos/tamanho do arquivo/data e hora/nome do arquivo`

O "l" logo antes do "a" lista os arquivos ou pasta com detalhes mostrando suas permissões, links, usuários, grupos, tamanho e data do arquivo. E a utilidade do "a" é mostrar até mesmo os diretórios ou arquivos quais estão ocultos no sistema. Após juntar as siglas o terminal entrega uma saída detalhada como essa no exemplo a seguir:

`drwxr-xr-x. 1 user user 38 oct 24 10:33 Desktop` <- Arquivo não-oculto

`drwxr-xr-x. 1 user user 442 oct 24 14:39 .config` <- Arquivo oculto definidos geralmente por "."

### `cd`
-**cd é um comando básico de navegação entre pastas**

Pode ser utilizado da seguinte forma conforme o exemplo a seguir:

O usuário quer ir até a pasta downloads pode-se usar o comando ls para listar os diretórios disponíveis -> `Desktop, Downloads, Documents... etc` e decide querer ir até a pasta downloads, utiliza-se então o seguinte comando -> `cd Downloads` -> e logo após utilizar o comando pwd para confirmar que entrou no diretório `pwd` saída do terminal prevista -> `/home/user/Downloads`

### `mkdir`
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

-> `cp -r /home/user/Documents /home/user/Downloads` 

ou até mesmo de forma mais simples, estando no caminho da pasta desejada pode escrever o seguinte comando para copiar para o caminho desejado:

-> `cp -r Documents ../Downloads`

### `mv`
-**"mv" como propriamente o nome "move" diz, move arquivos e diretorios**

Seu formato é bem simples, da seguinte forma:

`mv origem destino`

Arquivo por exemplo se encontra em documents, com o comando abaixo pode-se movê-lo para downloads

`mv arquivo.txt ../Downloads`

o comando `mv` pode ser utilizado para renomear arquivos também!

Basta apenas colocar a origem(arquivo ou diretório) e logo na frente o nome desejado, segue exemplo:

`mv arquivo.txt aprendendo-linux.txt`

### `rm`
-**rm significando remove, pode ser utilizado para remover arquivos, há também sua variante rmdir, anteriormente falamos sobre "dir" significando directory. Logo "rmdir" atua na exclusão de diretórios vázios**

formatos padrões -> `rm arquivo.txt`-> `rmdir diretorio`

pode-se apagar também vários arquivos simultaneamente da seguinte forma:

-> `rm arquivo1.txt arquivo2.txt arquivo3.txt` ou acaso os arquivos iniciem com o mesmo nome é possível apagá-los utilizando "*", que corresponde a qualquer sequência de caracteres no nome de arquivos ou diretórios, segue exemplo:

-> arquivos desejados para apagar -> arquivo{1..3}.txt -> utiliza-se dessa forma -> `rm arquivo*` assim será apagado todos os arquivos que tenham o mesmo inicio.

### `cat`
-**cat é um comando que pode ser utilizado para juntar arquivos e exibir o seu resultado, ou apenas mostrar o que há dentro de um arquivo em específico.**

imagine que há um arquivo.txt, que em seu conteúdo está escrito "estudos-linux :D". E portanto deseja ver o que há dentro desse arquivo por meio do terminal. Então pode-se utilizar do comando cat para extrair o conteúdo dentro deste arquivo:

-> `cat arquivo.txt` saída esperada no terminal -> `estudos-linux :D`

![alt text](image.png)

Além disso é possível juntá-lo com diversos arquivos simultaneamente desta forma:

-> `cat arquivo{1..4}.txt` e assim a saída no terminal será todo o conteúdo em cada arquivo!

## Permissões e Admin

### `sudo`
-**sudo é um comando que pode ser utilizado para executar comandos com privilégios administrativos**

Útil para situações que exigem privilégios mais altos como para instalação de aplicativos ou até mesmo alterar arquivos do sistema.

Exemplo:

(Depende da distro que está utilizando, neste exemplo usei fedora)
-> `sudo dnf install nodejs`

### `chmod`
-**Com o chmod(Change Mode), você pode alterar e revogar permissões de arquivos e diretórios no Linux. As permissões em si controlam o que cada tipo de usuário(dono, grupo e outros) podem fazer com determinado arquivo ou diretório, sendo ler, escrever ou executá-lo**

No linux, cada arquivo ou diretório tem três tipos de permissões para as três categorias de usuário que são

1. Usuário(Owner): Proprietário do arquivo

2. Grupo(group): Grupo de usuários que aquele arquivo pertence

3. Outros(Others): Todos os outros usuários

- As permissões são representadas por três letras

r: Permissão para Ler(read)

w: Permissão para Escrever(Write)

x: Permissão para Executar(Execute)

