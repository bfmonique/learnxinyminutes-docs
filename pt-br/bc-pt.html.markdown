---
language: bc
contributors:
    - ["Btup"]
translators:
    - ["Monique Baptista", "https://github.com/bfmonique"]
lang: pt-br
filename: learnbc.bc
---
```c
/*Este é um comentário
de várias linhas*/
# Este é um comentário (de uma linha) (no bc GNU)

    /*1. Variáveis e estruturas de controle*/
num = 45 /*Todas as variáveis salvam doubles, e você não pode
           salvar strings constantes diretamente.*/
num = 45; /*Você pode colocar ponto e vírgula no final de uma
            expressão. Isto é opcional. */
/*Blocos são denotados por chaves:*/
while(num < 50) {
    num += 1 /*equivalente a num = num + 1
    a = a [operação] b é o mesmo que a [operação]= b*/
}
/*Existem operadores de incremento (++) e decremento (--)*/
/*Existem 3 variáveis especiais:
scale: define a escala dos números (procure sobre
representação em ponto flutuante)
ibase: define a base da entrada
obase: define a base da saída*/
/*Cláusulas condicionais*/
hour = read() /*Lê um número*/

if(hour < 12) { /*Exatamente igual a C.*/
    print "Good morning\n" /*"print" imprime strings ou 
    variáveis separadas por vírgulas*/
} else if(hour == 12) {
    print "Hello\n"
    /*Sequências de escape começam com barra invertida
    Exemplos de sequências que funcionam em bc:
    \b: backspace
    \c: retorno de carro
    \n: quebra de linha
    \t: tab
    \\: barra invertida*/
} else {
    /*Variáveis são globais por padrão*/
    thisIsGlobal = 5
    /*Uma variável pode ser local com a palavra-chave "auto"
    dentro de uma função*/
}

/*Toda variável é inicializada em 0*/
num = blankVariable /*num começa em 0*/

/*Tudo é verdadeiro, 0 é falso.*/
if(!num) {print "false\n"}

/*Não existe o if ternário em bc. O código abaixo não funciona:
a = (num) ? 1 : 0
Podemos simular um ternário da seguinte maneira:*/
a = (num) && (1) || (0) /*&& e || funcionam como em C: "e"
  e "ou" lógicos*/

/*Laços for*/
num = 0
for(i = 1; i <= 100; i++) {/*Similar a C.*/
    num += i
}

    /*2.Funções e vetores*/
define fac(n) { /*Defina uma função com define*/
    if(n == 1 || n == 0) {
        return 1 /*retorne um valor*/
    }
    return n * fac(n - 1) /*recursão é possível*/
}

/*Fechamentos e funções anônimas são impossíveis*/

num = fac(4) /*24*/

/*Exemplo de variáveis locais:*/
define x(n) {
    auto x
    x = 1
    return n + x
}
x(3) /*4*/
print x /*X não é acessível fora da função*/
/*Vetores funcionam como em C.*/
for(i = 0; i <= 3; i++) {
    a[i] = 1
}
/*São acessados assim:*/
print a[0], " ", a[1], " ", a[2], " ", a[3], "\n"
quit /*Isto garante que seu programa fecha, mas é opcional*/
```
Aproveite esta simples calculadora! Ou, para ser mais exato,
linguagem de programação.

Este programa foi escrito em GNU bc. Para executá-lo, use '''bc learnbc.bc'''
