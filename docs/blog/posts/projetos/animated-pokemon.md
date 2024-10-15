---
title: Animated Pokémon
date: 2022-10-11
categories:
  - Projetos
tags:
  - python
  - pokémon
  - steam
  - wallpaper engine
  - jogo
  - html
  - javascript
  - css
---

[![GitHub DaviAMSilva/AnimatedPokemon](https://img.shields.io/badge/github-DaviAMSilva/AnimatedPokemon-dddddd?logo=github)](https://github.com/DaviAMSilva/AnimatedPokemon){ target="_blank" rel="noopener noreferrer" }
[![YouTube](https://img.shields.io/badge/youtube-Animated Pokémon -- Wallpaper Engine-ff0000?logo=youtube)](https://youtu.be/1iHMsn2k8DU?si=1RjxHRUrVUfHyOVT){ target="_blank" rel="noopener noreferrer" }
[![Steam Downloads](https://img.shields.io/steam/downloads/2870660754?logo=steam&label=downloads)](https://steamcommunity.com/sharedfiles/filedetails/?id=2870660754){ target="_blank" rel="noopener noreferrer" }
[![Steam Inscrições](https://img.shields.io/steam/subscriptions/2870660754?logo=steam&label=inscrições)](https://steamcommunity.com/sharedfiles/filedetails/?id=2870660754){ target="_blank" rel="noopener noreferrer" }
[![Steam Favoritos](https://img.shields.io/steam/favorites/2870660754?logo=steam&label=favoritos)](https://steamcommunity.com/sharedfiles/filedetails/?id=2870660754){ target="_blank" rel="noopener noreferrer" }

<style>
iframe {
    width: 560px;
    aspect-ratio: 16 / 9;
    margin: auto;
    display: block;
}
</style>

Um sou um fã dos jogos de Pokémon, especialmente os clássicos que ainda tinham toda a apresentação em pixel art (1). Um dia enquanto eu estava jogando Pokémon Black eu imaginei quão interessante seria ter um papel de parede animado de um Pokémon utilizando as animações de pixel art presentes especificamente nesse jogo e no jogo seguinte.
{ .annotate }

1. O meu jogo favorito é o Pokémon Emerald, que eu tive oportunidade de jogar em cartucho pela primeira vez após comprar o equipamento para o meu projeto de faculdade [Arcade Mania](./../projetos/pi2-arcade-mania/pi2-arcade-mania.md).

A partir disso eu me perguntei se não seria possível criar de maneira automática um papel de parede animado para cada Pokémon existente. Na época existiam um pouco menos de mil Pokémon distintos, mas com o lançamento de Pokémon Scarlet e Pokémon Violet em 2022 esse número já foi superado.

<iframe src="https://www.youtube-nocookie.com/embed/1iHMsn2k8DU?si=R9OhnztgAj0-dz18" title="YouTube: Animated Pokémon - Wallpaper Engine" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

Nesse mesma época eu tinha começado a utilizar a ferramenta [Wallpaper Engine](https://www.wallpaperengine.io) em meu computador pois eu gostava dos planos de fundos animados que ele conseguia produzir e não estava muito preocupado com o efeito dela na performance do sistema. Um dos modos de funcionamento dessa *engine* é baseado em HTML e JavaScript o que era perfeito para um projeto desse tipo.

O projeto envolve duas partes, a primeira delas sendo um script escrito em Python responsável por encontrar, baixar e organizar as informações dos Pokémon desejados utilizando a API [PokéAPI](https://pokeapi.co) construída e mantida por fãs da franquia. O script inclusive salva tais informações em um cache local. Isso foi preciso pois as informações necessárias precisam ser obtidas utilizando quase mil buscas distintas isso era absolutamente necessário. O resultando desse script era um arquivo JavaScript contendo todos os Pokémon em uma lista para ser importada no papel de parede em si.

A segunda parte é composta de uma simples página HTML contendo um local para inserir alguns dados do Pokémon, um local para inserir a sua imagem animada e um plano de fundo colorido de acordo com os tipos do Pokémon. A verdadeira complexidade estava no JavaScript da página devido ao fato que ele precisava interagir com o framework disponibilizado pela Wallpaper Engine para fornecer diversas opções de customização para o usuário final do wallpaper, como tempo para a troca de Pokémon, opções de cores, entre outras.

![Animated Pokémon - Ícone contendo Pikachu](https://github.com/DaviAMSilva/AnimatedPokemon/blob/master/preview.gif?raw=true "Animated Pokémon - Ícone"){ align=left }

Dessa forma eu fui capaz de publicar meu papel de parede no Steam Workshop onde ele teve um sucesso moderado e foi bem recebido. Eu o utilizei como meu papel de parede principal por todo o tempo restante em que eu estive utilizando o Microsoft Windows. Entretanto, atualmente o sistema operacional que estou utilizando exclusivamente é o Linux [Pop_OS!](https://pop.system76.com), sendo que não tenho mais a vontade de ter um papel de parede animado, ambos motivos porque eu não tenho mais vontade de atualizar e melhorar esse projeto.
