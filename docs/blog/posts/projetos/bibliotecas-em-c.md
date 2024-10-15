---
title: Bibliotecas em C
description: Algumas bibliotecas de manipulação de dados em C
date:
  created: 2020-11-13
  updated: 2021-06-21
categories:
  - Projetos
  - Faculdade
tags:
  - c
  - faculdade
  - make
  - algoritmo
---

---

[![GitHub DaviAMSilva/Estruturas_de_Dados](https://img.shields.io/badge/github-DaviAMSilva/Estruturas__de__Dados-dddddd?logo=github)](https://github.com/DaviAMSilva/Estruturas_de_Dados){ target="\_blank" rel="noopener noreferrer" }
[![GitHub DaviAMSilva/Searches](https://img.shields.io/badge/github-DaviAMSilva/Searches-dddddd?logo=github)](https://github.com/DaviAMSilva/Searches){ target="\_blank" rel="noopener noreferrer" }
[![GitHub DaviAMSilva/Sorts](https://img.shields.io/badge/github-DaviAMSilva/Sorts-dddddd?logo=github)](https://github.com/DaviAMSilva/Sorts){ target="\_blank" rel="noopener noreferrer" }
{ .badges }

Essas bibliotecas se referem a três conjuntos de funções e tipos de dados que eu desenvolvi enquanto estava cursando o curso de Ciência da Computação na Doctum para acelerar o desenvolvimentos das atividades. Esses projetos são:

- [**Estruturas de Dados**](https://github.com/DaviAMSilva/Estruturas_de_Dados):

    Contém as estruturas de dados do tipo pilha, fila e lista e métodos para criar, acessar e modificar tais estruturas. O tipo de dado armazenado nessas estruturas é dinâmico e definido pelo usuário.

- [**Searches**](https://github.com/DaviAMSilva/Searches):

    Contém diversos algoritmos de pesquisa em tipos de dados quaisquer, definidos pelo usuário.

- [**Sorts**](https://github.com/DaviAMSilva/Sorts):

    Contém diversos algoritmos de ordenação em tipos de dados quaisquer, definidos pelo usuário.

Eu criei essas bibliotecas durante os semestres em que cada um desses tópicos foi apresentado na faculdade. Minha principal motivação é que bem no início eu percebi o quanto eu reutilizava código pois atividades diferentes requeriam as mesmas estruturas, apenas a situação da atividade eram alteradas. Por causa disso, apesar de essas bibliotecas não terem muito utilidade prática no mundo externo, para mim elas foram de uma ajuda enorme.

A maneira como elas funcionam em geral é que elas permitem o uso de qualquer tipo de dados por meio de alocação dinâmica e conversão de ponteiros. O usuário apenas precisa definir o tamanho do tipo de dados no início e definir as funções necessárias para interagir com as bibliotecas utilizando os mesmos tipos de dados definidos.

Além disso outra vantagem é que as bibliotecas foram feitas de tal forma que o código fonte podia ser copiado para cada atividade necessária e continha um makefile para compilar cada arquivo para um arquivo de biblioteca estática (extensão `.a`) que poderia ser importada para os arquivos próprios da atividade por meio de outro makefile.

<div class="grid cards" markdown>

=== "Biblioteca 'Estrutura_de_Dados'"

    ```makefile
    DIRS    := build/ lib/
    SOURCES := $(wildcard source/*.c)
    OBJECTS := $(patsubst source/%.c,build/%.o,$(SOURCES))
    LIBS    := $(patsubst source/%.c,lib/lib%.a,$(SOURCES))

    all: $(LIBS)
    dirs: $(DIRS)

    .PHONY: all dirs clean
    .SECONDARY: $(OBJECTS)

    build/%.o: source/%.c include/%.h | $(DIRS)
        gcc -c $< -Wall -O3 -o $@ -I include/

    lib/lib%.a: build/%.o | $(DIRS)
        ar cr $@ $<

    $(DIRS):
        mkdir -p $@

    clean:
        rm -fr build/ lib/
    ```

=== "Atividade que utiliza as as estruturas lista e pilha"

    ```makefile
    .PHONY: all clean eds
    all: $(patsubst %.c,bin/%,$(wildcard *.c))


    libs := lista pilha
    args := -Ieds/include -Leds/lib $(addprefix -l,$(libs))


    bin/%: %.c | bin eds
        gcc $^ $(args) -O3 -Wall -Wno-unused-result -Wno-discarded-qualifiers -o $@


    bin:
        mkdir -p bin/


    eds:
        $(MAKE) -C eds


    clean:
        rm -fr bin/
    ```

</div>
