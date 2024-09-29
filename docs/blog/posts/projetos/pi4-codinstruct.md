---
title: codinStruct
date:
  created: 2021-11-27
  updated: 2023-09-29
categories:
  - Projetos
  - Faculdade
tags:
  - javascript
  - html
  - scss
  - faculdade
  - projeto integrador
  - site
  - markdown
  - github actions
  - webpack
  - node
  - npm
  - express
---

---

[![GitHub codinStruct/codinStruct](https://img.shields.io/badge/github-codinStruct/codinStruct-dddddd?logo=github)](https://github.com/codinStruct/codinStruct){ target="_blank" rel="noopener noreferrer" }
[![Website codinStruct](https://img.shields.io/badge/website-codinStruct-326eff)](https://codinstruct.github.io/codinStruct-content){ target="_blank" rel="noopener noreferrer" }
[![Website codinStruct Next](https://img.shields.io/badge/website-codinStruct Next-326eff)](https://codinstruct.luizf.dev){ target="_blank" rel="noopener noreferrer" }

É o projeto mais moderno que eu já desenvolvi durante o quarto semestre da minha graduação na Doctum. Foi parte de um trabalho em grupo com tema livre em que nossa motivação foi:

> O trabalho é uma plataforma que oferece um repertório de informação sobre linguagens de programação, apresentadas de diferentes formas tal que facilite o aprendizado dos usuários através de um portal que agrupa esses conhecimentos em um só lugar.
>
> Quase todo brasileiro que busca aprender programação percebe a escassez de conteúdo nacional de qualidade sobre a área, e quando existe costuma estar em um lugar obscuro.
>
> Conhecemos bastante as dificuldades e necessidades do possível usuário, pois passamos pelas mesmas. Isso é uma fonte de inspiração e motivação que nos mostra a utilidade de nosso projeto e transcende retorno financeiro, mas não descartamos a possibilidade de monetização.

No fim o projeto incorporou uma documentação das linguagens C, JavaScript e Python.

O projeto contêm três partes principais: O [site em si](https://github.com/codinStruct/codinStruct), para apresentar o conteúdo; o [conteúdo](https://github.com/codinStruct/codinStruct-content) escrito em markdown; e um conversor de markdown para o html que seria importado pelo site.

Em retrospectiva é claro como esse trabalho é similar a projetos como [MkDocs](https://www.mkdocs.org/), [GitBook](https://www.gitbook.com/) e [Jekyll](https://jekyllrb.com/), mas na época nós queríamos desenvolver tudo nós mesmos.

Quando o site foi desenvolvido nos o hosteamos na plataforma Heroku, no plano grátis, mas depois de alguns anos a plataforma essencialmente [anunciou o fim do plano grátis](https://help.heroku.com/RSBRUH58/removal-of-heroku-free-product-plans-faq), e como esse era apenas um projeto escolar simples não tomamos ação para manter o site funcionando pelo Heroku.

Felizmente um dos meus colegas nesse trabalho, [Luiz](https://github.com/luizffgv), pessoalmente criou uma versão do conteúdo para estar acessível por meio do GitHub Pages utilizando a ferramenta [mdBook](https://github.com/rust-lang/mdBook), disponível em [codinStruct](https://codinstruct.github.io/codinStruct-content/). Adicionalmente ele também criou uma versão utilizando a ferramenta [Next.js](https://nextjs.org/), disponível em [codinStruct Next](https://codinstruct.luizf.dev/).
