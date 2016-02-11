---
layout: post
title: Django – Iniciando um Projeto
---


Comandos basicos para iniciar um projeto em Django

Adicionando alias no .bashrc:

```sh
alias actvenv="source ".${PWD##*/}"/bin/activate"
alias manage="python $VIRTUAL_ENV/../manage.py"
```

Criando projeto:

```sh
mkdir nome_projeto
cd nome_projeto
python -m venv .nome_projeto
actvenv
pip install django
django-admin startproject projeto .
cd projeto
manage startapp core
```
