---
layout: post
title: Python – Referência a Objetos
---
Em Python tudo é objeto. Muitos programadores que vem de outras linguagens como Java e C++, podem achar isso muito estranho, mas na verdade é um conceito muito fácil de entender.

Um pequeno exemplo:

```python
>> class Teste(object):
>>    pass
```
Oque acontece acima. É criado uma classe chamada Teste, que herda da classe object . Heranças de object podem ser omitidas, ficando assim: 

```python 
>> class Teste:
>>    pass
``` 

```python
>> x = Teste()
>> x.var1 = 200
>> x.var2 = 'Python é legal'
```

Aqui acontece a magica. É criado os atributos var1 e var2 dentro da instancia x, onde x referencia o objeto Teste que herda de object.
Muito show, né!? ;)

```python
>> a = 'texto qualquer'
>> b = a
>> print(id(a), id(b))
140530441103320 140530441103320
```
Nesse outro exemplo, criamos um objeto str em memória e a variável **a** aponta para este objeto. Logo mais temos a variável **b** que referencia o objeto **a**, nesse caso, ambos referenciam a um objeto *str*. O print(**id**(a), **id**(b)) mostra que o identificador das duas variáveis são iguais, ou seja, as duas variáveis referenciam a um único objeto em memória.

Outro exemplo para ficar mais claro:

```python
class Teste: 
    x = 11
    
t1 = Teste()
t2 = t1
 
t1.x = 22
print(t2)
22
print(Teste.x)
11
 
Teste.x = 33
del t2.x
print(t2.x)
33
```
Definimos uma classe Teste. Criamos dois atributos, **t1** e **t2**, os dois referenciam a classe Teste. Modificamos o atributo x da instancia **t1** para 22, mostrando o resultado de **t2**.x, notamos que o valor também foi modificado, mas Teste.x continua com o valor 11.
Agora mudando Teste.x para 33, deletamos o atributo x da instancia **t2**, agora o valor de **t2**.x é 33.

##### Concluindo

No Python é possível manipular objetos em tempo de execução. Quando criamos um atributo para uma instancia de classe, o atributo pertence somente a instancia e não a classe pai. No ultimo exemplo do *print*(**t2**.x) sendo 33, o interpretador do Python primeiro procura pelo atributo x na instancia, se ele não encontra, ele procura na classe pai, se existe algum atributo x. Se existir, **t2**.x utiliza o atributo x de Teste, nesse caso, modificamos o atributo x da classe Teste. Se o atributo não existir na classe e nem na instancia, ocorre um AttributeError.

Tudo isso pode ser feito com métodos, pois os métodos em Python são objetos também!

##### Leia mais:

* [https://docs.python.org/3/library/stdtypes.html] [linkDoc]
* [http://pythonclub.com.br/introducao-classes-metodos-python-basico.html] [linkPyClub]
* [http://python-history.blogspot.com.br/2010/06/method-resolution-order.html] [linkBlog]


[//]: #

   [linkDoc]: <https://docs.python.org/3/library/stdtypes.htmlr>
   [linkPyClub]: <http://pythonclub.com.br/introducao-classes-metodos-python-basico.html>
   [linkBlog]: <http://python-history.blogspot.com.br/2010/06/method-resolution-order.html>



