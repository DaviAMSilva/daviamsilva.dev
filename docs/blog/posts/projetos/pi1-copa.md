---
title: Simulador de Copa
description: Um simulador de copa do mundo desenvolvido em C para o projeto integrador 1
date:
  created: 2020-07-01
categories:
  - Projetos
  - Faculdade
tags:
  - c
  - make
  - windows
  - faculdade
  - projeto integrador
  - copa do mundo
---

[![GitHub DaviAMSilva/PI-Copa](https://img.shields.io/badge/github-DaviAMSilva/PI--Copa-dddddd?logo=github)](https://github.com/DaviAMSilva/PI-Copa){ target="_blank" rel="noopener noreferrer" }
{ .badges }

Foi o meu primeiro grande projeto em grupo no primeiro semestre da minha graduação na Doctum. O objetivo geral do projeto foi:

> Desenvolver um programa capaz de simular a realização de um torneio (copa). Pode-se utilizar o modelo atual utilizado pela FIFA para organizar a copa do mundo de futebol.

O contexto era de um organizador de eventos que desejasse inserir os resultados de um tornamento, conforme ele ia acontecendo, de tal maneira que o sistema calculasse e gerasse automaticamente o resultado de cada jogo, fase e do campeonato inteiro.

A minha versão suportava a quantidade de gols e cartões amarelos e vermelhos recebidos por cada time e para cada jogo. Também conseguia calcular todas as fases do torneio, desde a fase de grupos até a final, conforme as regras básicas da Copa do Mundo da FIFA. O usuário tinha também a opção de aleatorizar os resultados dos jogos, principalmente útil para testar o programa.

O projeto foi desenvolvido em C e compilado usando a ferramenta make para facilitar a compilação e execução do programa. Essa experiência foi uma das razões que motivaram a minha ideia para o projeto integrador 2, que foi o [Arcade Mania](pi2-arcade-mania/pi2-arcade-mania.md).

Esse programa foi, principalmente na segunda fase, construído utilizando-se o sistema operacional Microsoft Windows 10 e a biblioteca `windows.h` para manipular o console do Windows. Por causa disso eu nem consigo mais testar o programa no meu sistema operacional atual, o [Pop!_OS](https://pop.system76.com/). Mesmo ferramentas como o [wine](https://www.winehq.org/) não conseguem exibir corretamente o console do Windows, apesar de conseguirem rodar o programa e gerar o resultado correto.

Um resultado típico do programa, ao selecionar todas as opções aleatórias, é o seguinte:

<style>
    .simulador-de-copa code {
        /* Por algum motivo colocar "Fira Code" causa os símbolos de caixa a terem espaçamento incorreto  */
        font-family: monospace !important;
    }
</style>

<div class="simulador-de-copa">
    ```text title="Saída do Terminal"
                ___________
           .---'::'        `---.
          (::::::'              )
        __|`-----._______.-----'|__
       /  |              :::::::|  \
      |   |               ::::::|   |
      |   |                :::::|   |
       \  |               ::::::|  /
        \ |    Copa do Mundo   :| /
         \|       da FIFA   ::::|/
          |               ::::::|
          |              .::::::|
          \             :::::::|
           \            ::::::/
            `.        .:::::::'
              `-._  .::::::-'
                  |  """|"
                  |  :::|
                  |   ::|
                 /     ::\
            __.-'      :::`-.__
           (_           ::::::_)
             `"""---------"""'

          GANHADOR:      
          Brasil
    ```
    
    ```text title="Arquivo de Resultado"
    O campeão da Copa do Mundo da FIFA foi o time:
    > Brasil <
    
    ┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━━━━┓
    ┃            COPA DO MUNDO DA FIFA             ┃             Gols            ┃        Cartões       ┃
    ┣━━━━┳━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┯━━━━━━━━╋━━━━━━━━━━┯━━━━━━━━━━┯━━━━━━━╋━━━━━━━━━━┯━━━━━━━━━━━┫
    ┃ Nº ┃          Nome do Time          │ Pontos ┃ Marcados │ Sofridos │ Saldo ┃ Amarelos │ Vermelhos ┃
    ┣━━━━╋━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┿━━━━━━━━╋━━━━━━━━━━┿━━━━━━━━━━┿━━━━━━━╋━━━━━━━━━━┿━━━━━━━━━━━┫
    ┃ 01 ┃ Brasil                         │ 18     ┃ 34       │ 21       │ +13   ┃ 37       │ 2         ┃
    ┃ 02 ┃ Croácia                        │ 15     ┃ 23       │ 25       │ -2    ┃ 35       │ 4         ┃
    ┃ 03 ┃ Japão                          │ 15     ┃ 35       │ 29       │ +6    ┃ 41       │ 2         ┃
    ┃ 04 ┃ Egito                          │ 13     ┃ 29       │ 17       │ +12   ┃ 37       │ 4         ┃
    ┃ 05 ┃ Marrocos                       │ 9      ┃ 20       │ 12       │ +8    ┃ 16       │ 2         ┃
    ┃ 06 ┃ Senegal                        │ 9      ┃ 23       │ 18       │ +5    ┃ 28       │ 2         ┃
    ┃ 07 ┃ Alemanha                       │ 9      ┃ 20       │ 19       │ +1    ┃ 26       │ 4         ┃
    ┃ 08 ┃ Islândia                       │ 7      ┃ 17       │ 15       │ +2    ┃ 25       │ 3         ┃
    ┃ 09 ┃ Rússia                         │ 7      ┃ 11       │ 6        │ +5    ┃ 20       │ 3         ┃
    ┃ 10 ┃ Austrália                      │ 6      ┃ 18       │ 14       │ +4    ┃ 18       │ 1         ┃
    ┃ 11 ┃ Costa Rica                     │ 6      ┃ 10       │ 8        │ +2    ┃ 16       │ 2         ┃
    ┃ 12 ┃ Portugal                       │ 6      ┃ 14       │ 14       │ +0    ┃ 19       │ 2         ┃
    ┃ 13 ┃ Sérvia                         │ 6      ┃ 7        │ 8        │ -1    ┃ 16       │ 3         ┃
    ┃ 14 ┃ Bélgica                        │ 6      ┃ 14       │ 20       │ -6    ┃ 21       │ 1         ┃
    ┃ 15 ┃ Panamá                         │ 6      ┃ 21       │ 28       │ -7    ┃ 23       │ 4         ┃
    ┃ 16 ┃ Dinamarca                      │ 6      ┃ 8        │ 16       │ -8    ┃ 31       │ 3         ┃
    ┃ 17 ┃ México                         │ 6      ┃ 14       │ 14       │ +0    ┃ 21       │ 3         ┃
    ┃ 18 ┃ Nigéria                        │ 4      ┃ 11       │ 10       │ +1    ┃ 15       │ 1         ┃
    ┃ 19 ┃ Irã                            │ 4      ┃ 10       │ 14       │ -4    ┃ 12       │ 0         ┃
    ┃ 20 ┃ Colômbia                       │ 3      ┃ 7        │ 2        │ +5    ┃ 5        │ 0         ┃
    ┃ 21 ┃ Inglaterra                     │ 3      ┃ 6        │ 3        │ +3    ┃ 3        │ 0         ┃
    ┃ 22 ┃ Peru                           │ 3      ┃ 12       │ 10       │ +2    ┃ 12       │ 1         ┃
    ┃ 23 ┃ Tunísia                        │ 3      ┃ 19       │ 19       │ +0    ┃ 20       │ 3         ┃
    ┃ 24 ┃ França                         │ 3      ┃ 11       │ 11       │ +0    ┃ 8        │ 2         ┃
    ┃ 25 ┃ Suécia                         │ 3      ┃ 8        │ 9        │ -1    ┃ 9        │ 1         ┃
    ┃ 26 ┃ Polônia                        │ 3      ┃ 14       │ 17       │ -3    ┃ 21       │ 2         ┃
    ┃ 27 ┃ Coreia do Sul                  │ 3      ┃ 13       │ 17       │ -4    ┃ 25       │ 3         ┃
    ┃ 28 ┃ Arábia Saudita                 │ 3      ┃ 2        │ 6        │ -4    ┃ 19       │ 2         ┃
    ┃ 29 ┃ Argentina                      │ 2      ┃ 9        │ 10       │ -1    ┃ 14       │ 3         ┃
    ┃ 30 ┃ Espanha                        │ 1      ┃ 6        │ 12       │ -6    ┃ 14       │ 3         ┃
    ┃ 31 ┃ Suíça                          │ 0      ┃ 6        │ 15       │ -9    ┃ 18       │ 2         ┃
    ┃ 32 ┃ Uruguai                        │ 0      ┃ 0        │ 13       │ -13   ┃ 14       │ 0         ┃
    ┗━━━━┻━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┷━━━━━━━━┻━━━━━━━━━━┷━━━━━━━━━━┷━━━━━━━┻━━━━━━━━━━┷━━━━━━━━━━━┛
    ```
</div>
