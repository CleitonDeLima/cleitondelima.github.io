---
layout: post
title: Pyenv - Instalação no Ubuntu 14.04
---

Em todas as distribuições linux, o Python já vem instalado por padrão. Mas nem todos possuem a mesma versão, uns usam o Python 2.7 e outros a 3.4 como python global do sistema.

Instalando o pyenv, é possível ter um maior controle entre as versões do Python.
#### Segue abaixo a instalação do pyenv para Ubuntu 14.04:

Primeiro é necessário instalar algumas dependências no sistema operacional:

```sh
sudo apt-get install -y make build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev
```

Depois de instalar as dependências, vamos instalar o pyenv através de um script:

```sh
curl -L https://raw.githubusercontent.com/yyuu/pyenv-installer/master/bin/pyenv-installer | bash
```

[pyenv-installer] - pyenv-installer

Logo após terminar a instalação, precisamos copiar as seguintes linhas no final do arquivo .bashrc da home (Se você usa o zsh, é só copiar para o arquivo .zshrc que fica localizado na home):

```sh
export PATH="/home/cleiton/.pyenv/bin:$PATH"
eval "$(pyenv init -)"
eval "$(pyenv virtualenv-init -)"
```

Agora salve o arquivo o recarregue as informações do .bashrc (ou .zsh) com o comando:

```sh
source ~/.bashrc
```

Executando o comando *```pyenv versions```* no terminal, é listado todas as versões do Python que eu tenho instalado no sistema operacional.

Usando o comando *```pyenv install -l```*, é listado todas as versões do python que podem ser instaladas, nesse exemplo vamos instalar a versão 3.5.1.

Com o comando *```pyenv install 3.5.1```* , é feito o download do python 3.5.1 e a sua compilação.

Novamente executando o comando *```pyenv versions```*, veja que temos uma nova versão instalada.

Para definirmos essa nova versão como padrão no sistema, use o comando *```pyenv global 3.5.1```*.

[//]: #
[pyenv-installer]: <https://github.com/yyuu/pyenv-installer>
