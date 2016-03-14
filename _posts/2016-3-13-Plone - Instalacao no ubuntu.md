---
layout: post
title: Plone - Instalação no Ubuntu
---

#####Segue abaixo a instalação do Plone 5:

O Plone funciona com o python 2.7, verifique se existe essa versão com o comando:

```sh
python -V
```

#####Abaixo tem um passo a passo da instalação. Mas se preferir, no final da pagina possui um script para instalação rápida.

Como o Plone necessita de várias dependências, é recomendável que seja usado o virtualenv para isolar o projeto do sistema, 
basicamente é criado um pasta com o python isolado, assim, o Plone vai utilizar esse novo python da pasta, e não a versão do 
sistema, segue abaixo o comando de instalação do virtualenv:

Para instalar o virtualenv:

```sh
sudo apt-get install python-pip
sudo pip install virtualenv
```

Para criar um projeto isolado utilizando o virtualenv:

```sh
mkdir ProjetoPlone
cd ProjetoPlone
virtualenv -p python2 --no-site-packages .ProjetoPlone
```

O plone requer que algumas dependências sejam instaladas em seu sistema operacional:

```sh
sudo apt-get install build-essential libxslt1-dev wget libxml2-dev libxml2-utils zlib1g-dev libjpeg-dev libfreetype6-dev poppler-utils wv python2.7-dev python-setuptools
```

Agora vamos fazer o nosso projeto reconhecer o python dentro do virtualenv, detro da pasta criada 
(no nosso exemplo foi ProjetoPlone) execute o comando abaixo:

```sh
.ProjetoPlone/bin/activate
```

Nosso cursor do terminal vai ter as iniciais da pasta criada pelo virtualenv (.PloneTeste)… 
Isso quer dizer que o python que está sendo utilizado não é mais o do sistema, e sim do virtualenv.

Com o virtualenv ativado, vamos instalar duas bibliotecas que o Plone depende:

```sh
pip install Pillow
pip install zc.buildou
```

Agora vamos criar um arquivo simples de configuração do Plone, dentro da pasta do projeto. Execute o seguinte comando:

```sh
echo """
[buildout]
extends =
    http://dist.plone.org/release/5-latest/versions.cfg

parts =
    instance

[instance]
recipe = plone.recipe.zope2instance
user = admin:admin
http-address = 8080
eggs =
    Plone
    Pillow

""" > buildout.cfg
```

Com isso, vai ser criado um arquivo _buildout.cfg_ dentro da pasta ProjetoPlone.

Para executar a instalação do Plone, execute o comando:

```sh
./ProjetoPlone/bin/buildout
```

A Instalação pode levar alguns minutos.

Por ultimo, pode rodar o comando:

```sh
bin/instance fg
```

Com isso, vai ser instanciado um servidor local do plone, para cancelar, só executar ctrl + C.


Agora é só acessar o navegador e conhecer o Plone (:

