---
title: Witch Hat Atelier Spell Maker
description: Um criador de magias digital para fãs da série Witch Hat Atelier criada por Kamome Shirahama. Crie, personalize e compartilhe magias baseadas no sistema de magia da série.
date:
  created: 2026-04-05
  updated: 2026-07-29
slug: wha-spell-maker
categories:
  - Projetos
  - Destaques
tags:
  - anime
  - bootstrap
  - cloudflare
  - css
  - font awesome
  - html
  - javascript
  - json
  - jsx
  - mangá
  - node
  - npm
  - p5.js
  - python
  - sass
  - site
  - typescript
  - vite
---

<style>
  .width30 {
    margin:auto;
    text-align: center !important;
    width: min(max(30%, 350px), 90%) !important;
    max-width: 100% !important;
  }
  .width50 {
    margin:auto;
    text-align: center !important;
    width: max(50%, 400px) !important;
    max-width: 100% !important;
  }
  .width75 {
    margin:auto;
    text-align: center !important;
    width: max(75%, 600px) !important;
    max-width: 100% !important;
  }
  .md-typeset details p {
    font-size: 0.8rem;
  }
</style>

[![Static Badge](https://img.shields.io/badge/github-DaviAMSilva%2Fwha--spell--maker-dddddd?logo=github)](https://github.com/DaviAMSilva/wha-spell-maker)
[![Static Badge](https://img.shields.io/badge/website-Witch Hat Atelier Spell Maker-326eff)](https://wha-spell-maker.daviamsilva.dev)
{ .badges }

Witch Hat Atelier Spell Maker é um editor de magias digital para fãs da série Witch Hat Atelier que permite criar, editar e compartilhar magias baseadas no sistema de magia dessa série. Esse projeto é um site estático desenvolvido com Typescript e Node.js, hospedado na Cloudflare Workers & Pages.

[![Witch Hat Atelier Spell Maker Preview](/blog/projetos/wha-spell-maker/whasm-preview.png)](https://wha-spell-maker.daviamsilva.dev/)
{ .width75 }

Criada por Kamome Shirohama, a série de fantasia Witch Hat Atelier, em forma de mangá e anime, é uma das minhas favoritas. Não apenas a *mangaká* demonstra habilidades artísticas e de composição incríveis, a ponto de ser sua própria mágica, mas ela também cria personagens interessantes e enredos cativantes que forçam o leitor a ponderar os temas apresentados.

<!-- more -->

<figure markdown="span" align=right style="float: right; margin: 1rem" class="width30">
![Sapatos Sylph](/blog/projetos/wha-spell-maker/spell-sylph-shoes-dark.png#only-dark)
![Sapatos Sylph](/blog/projetos/wha-spell-maker/spell-sylph-shoes-light.png#only-light)
<figcaption style="clear: both" class="width30" markdown>**Magia Sapatos Sylph**:<br/>Contendo um brasão de vento e flechas de levitação e convergência</figcaption>
</figure>

Uma das fundações da série é o sistema de magia baseado em desenhos que os bruxos usam. De maneira simplificada um brasão no centro do selo define o elemento que a magia irá incorporar. Flechas em volta do brasão definem a forma em que a magia irá se manifestar. E, por último, ao fechar um círculo em volta, a magia é ativada. (1)
{ .annotate }

1. Em inglês: círculo = *ring*, brasão = *sigil* e flecha = *sign*

Esse sistema de magia contém outros conceitos mais avançados que o torna mais surpreendentemente profundo e complexo, de forma que um leitor criativo pode aprender o sistema, pegar magias e símbolos apresentados na série e desenvolver novas magias originais. Para leitores interessados o melhor lugar para começar é na página sobre magia da [Independent Witch Hat Atelier Wiki](https://witchhatatelier.telepedia.net/wiki/Magic).

A série cria uma analogia entre a magia e a arte, convidando o leitor a desenhar as magias ele mesmo. Foi a partir daí que eu percebi a oportunidade de desenvolver um aplicativo para acelerar a criação de novas magias. A capacidade de criar, mover, copiar e apagar os símbolos como quiser e a natureza simétrica das magias que necessita o uso de símbolos repetidos são as principais vantagens que o editor digital providencia.

Entretanto é importante enfatizar: **O editor não é um substituto para a criatividade, habilidade artística e conhecimento do sistema necessários para criar magias**. Eu recomendo que qualquer fã interessado tente desenhar pelo menos uma vez uma magia complexa em papel para compreender a habilidade demonstrada pelos personagens na série.

## Apresentação

A interface de usuário é dividida em duas partes, na esquerda há o elemento canvas em que ocorre o desenha das magias. Já na direita há o painel que permite editar as diversas partes da magia. O site também suporta a orientação vertical; nesse modo o canvas move para o topo da página, enquanto o editor move para a parte de baixo.

![Visualização do website](/blog/projetos/wha-spell-maker/whasm-website.png)
{ .width75 }

Com o editor o usuário pode adicionar a quantidade que quiser dos diversos tipos de elementos que compõem uma magia: Círculos, brasões e flechas. O editor permite posicionar, rotacionar e alterar o tamanho e cores dos diversos símbolos já estabelecidos na série. Imagens customizadas fornecidas pelo próprio usuário também são suportadas para símbolos não-oficiais e outras variações.

As diferentes partes do editor foram especificamente projetadas para facilitar a criação do tipo mais comum de magia: contendo um círculo, um brasão central e várias flechas distribuídas uniformemente em volta do brasão. Magias mais complexas que usam múltiplos círculos, e símbolos não uniformes ou com posição arbitrária são suportadas, mas requerem mais trabalho para serem criadas.

O editor exporta as magias criadas na forma de imagem (1000×1000px) ou como JSON usando a representação interna da magia. A disponibilidade desse formato permite que usuários salvem magias para serem importadas posteriormente, ou ainda, editem diretamente no editor secundário no formato JSON. O editor também é capaz de criar um link compartilhável da magia atual, permitindo que outros usuários possam rapidamente abrir a mesma magia.

## Desenvolvimento

Esse projeto utiliza duas bibliotecais centrais para a criação do site: [p5.js], para o desenho das magias, e [JSONEditor](https://github.com/json-editor/json-editor), para a edição da magia. Para a build do site usa-se a ferramenta [Vite](https://vite.dev/) em Node.js, sendo o meu primeiro grande projeto a usar Typescript (suportado em Node 23+).

Curiosamente eu tenho maior experiência com JavaScript e Python, duas linguagens famosas por terem tipagens fracas, entretanto em ambas eu geralmente acabou usando a tipagem opcional. De certa maneira esse modo de desenvolver junta as duas vantagens de cada tipo de linguagem: Liberdade de manipulação de dados, mas com dicas de tipagem providenciadas automaticamente por editores como o Visual Studio Code.

### Editor de Magias <small>(JSONEditor)</small>

O JSONEditor usa como base um arquivo [JSON Schema](https://json-schema.org/) para gerar um componente HTML em que os vários elementos presentes seguirão as regras de exibição e validação definidas. O resultado é um editor visual e dinâmico que é equivalente a uma estrutura JSON, garantindo uma boa experiência de usuário, mas ainda tirando proveito da flexibilidade do formato JSON e da organização do schema.

A partir daí a biblioteca oferece métodos de conseguir o valor atual do editor no formato JSON definido no schema e, opcionalmente, o resultado da validação dos dados inseridos pelo usuário. Entretanto, nesse projeto, tanto o schema quanto o código de desenho utilizam valores padrões para todos os campos, portanto a funcionalidade de validação não foi necessária.

Abaixo está uma versão simplificado do schema (o real tem cerca de 600 linhas) que demonstra que uma magia contem uma estrutura em hierarquia. A raiz da estrutura deve conter um ou mais selos (1) e que cada selo pode ter qualquer quantidade de círculos, brasões, flechas e linhas. No schema real a propriedade `format` pode ser utilizada para mudar o tipo de dado que aquele elemento representa: textual, numérico, cor e vários outros tipos.
{ .annotate }

1. Selo, ou *seal* em inglês, se refere ao desenho de círculo com símbolos dentro

```json hl_lines="6 63 65 66"
{
    "$schema": "https://json-schema.org/draft-07/schema#",
    "type": "object",
    "title": "Witch Hat Atelier Spell Maker",
    "properties": {
        // Mensagem inicial exibida no topo do editor
        "firstTimeInfo": { /* ... */ }
        /* ... */
        "seals": {
            "type": "array",
            "format": "tabs-top",
            "title": "Spell Seals",
                "format": "categories",
                "title": "Seal",
                "properties": {
                    /* ... */
                    "rings": {
                        "type": "array",
                        "format": "tabs-top",
                        "title": "Seal Rings",
                        "items": {
                            "type": "object",
                            "title": "Ring",
                            "properties": { /* ... */ }
                        }
                    },
                    "sigils": {
                        "type": "array",
                        "format": "tabs-top",
                        "title": "Seal Sigils",
                        "items": {
                            "type": "object",
                            "title": "Sigil",
                            "properties": { /* ... */ }
                        }
                    },
                    "signs": {
                        "type": "array",
                        "format": "tabs-top",
                        "title": "Seal Signs",
                        "options": {
                            "disable_collapse": true,
                            "enable_array_copy": true
                        },
                        "items": {
                            "type": "object",
                            "title": "Sign",
                            "properties": { /* ... */ }
                        }
                    },
                    "lines": {
                        "type": "array",
                        "format": "tabs-top",
                        "title": "Seal Lines",
                        "items": {
                            "title": "Line",
                            "properties": { /* ... */ }
                        }
                    }
                }
            }
        }
        // Usado para armazenar as imagens customizadas
        "custom": { /* ... */ }
        // Ambas as seções de Importar/Exportar e Sobre precisam estar presentes no schema para que
        // as abas sejam geradas pelo JSONEditor e eventualmente populadas por código Javascript
        "io": { /* ... */ }
        "about": { /* ... */ }
    }
}
```

Infelizmente, devido ao fato dessa biblioteca ser tão focada em criar um editor com base em um schema fixo, foram encontradas as seguintes limitações que tiveram de ser resolvidas durante o desenvolvimento do projeto:

Um usuário avançado tem a opção de adicionar novos símbolos com imagens e nomes customizáveis para serem usadas dentro das magias e permitir o uso de brasões e flechas que não estão presentes no editor ou na série. Uma consequência dessa funcionalidade é a necessidade da adição ou remoção de itens da lista de imagens nas caixas de seleção de símbolos. Entretanto o JSONEditor não suporta a alteração do schema dinamicamente após a criação do editor.

Para isso a função `createJsonEditor` é a responsável por criar ou recriar o editor e invocar todas as correções e adições secundárias a serem aplicadas. Uma das correções é realizada pela função `rebuildAvailableSymbols` cuja a responsabilidade é juntar os símbolos embutidos com os símbolos carregados pelo usuário em uma única lista que é injetada dentro do schema JSON importado toda vez que o editor é criado ou recriado.

Duas adições realizadas no editor são a população das abas "Importar / Exportar" e "Sobre" (1), em que a estrutura é criada no arquivo `src/tabs.tsx` e injetada por JavaScript logo após a árvore HTML do editor ser gerada. Os elementos dessas abas são formatadas usando o mesmo estilos de Bootstrap usados no tema do editor.
{.annotate}

1. "Import / Export" e "About" em inglês

Por fim, uma das funcionalidades adicionadas após a publicação do site foi uma opção de destacar temporariamente o símbolo atualmente em edição, ou seja, o símbolo atualmente visível no editor. Mas, ao meu entendimento, o JSONEditor não tem um modo nativo de informar em qual parte da schema o usuário está atualmente acessando. A solução adotada é uma que eu não estou muito satisfeito, mas que funciona:

Ela envolve o uso de `#!javascript MutationObserver` para detectar alterações em um dos elementos no HTML do editor quando o usuário troca o símbolo atualmente sendo editado. Quando isso ocorre o código encontra o índice do selo, o tipo do símbolo e o índice do símbolo atualmente visível e armazena em uma variável global. Então o p5.js utiliza essas informações durante o desenho da magia para determinar se algum símbolo precisa ser pintado com a cor de destaque.

```javascript
// Variável global em src/sketch.ts, importada e alterada em src/form.ts
export const highlightInfo: {
    seal: number | null,
    type: string | null,
    index: number | null
} = {
    seal: null,
    type: null,
    index: null
};

/* ... */

// Ao desenhar os símbolos e, de maneira similar, outros elementos da magia
const symbolHighlighted =
    spell.highlight &&
    highlightInfo.seal  === sealIndex &&
    highlightInfo.type  === symbolDrawType &&
    highlightInfo.index === localIndex;
```

### Canvas de Magias <small>(p5.js)</small>

A responsabilidade de desenhar as magias em si é da biblioteca p5.js, que eu já estou [familiarizado há algum tempo](../../../../tags.md#tag:p5js). O código que recebe e interpreta a magia em forma de JSON foi desenvolvido com o foco em evitar erros fatais. Todos as partes do código de desenho contém valores padrões, além do fato que o schema em si já vir configurado com padrões preenchidos pelo JSONEditor. Dessa forma mesmo que a magia fornecida esteja incompleta, inválida ou qualquer outro erro exceto de sintaxe JSON, o canvas ainda será preenchido com *alguma coisa*.

As várias partes da estrutura de uma magia são processadas em vários *loops*, um por um. O ponto interessante foi lidar com o posicionamento relativo dos símbolos em diferentes níveis da hierarquia, considerando que cada elemento contém uma translação e rotação relativas ao elemento um nível acima na estrutura. A maneira inteligente de conseguir esse efeito é usando as funções de [transformação](https://p5js.org/reference/#Transform) do p5.js.

O modo como elas funcionam é usando as funções `#!javascript push()` para adicionar um grupo à pilha de transformação, executando todas as transformações necessárias àquele grupo, e finalmente usando `#!javascript pop()` para finalizar o grupo. Dessa forma todos os grupos na pilha são afetados pelos grupos abaixo de forma automática. A melhor demonstração desse método é na parte responsável pelo posicionamento e desenho dos brasões e flechas:

```javascript hl_lines="9 10"
/* [Comentários originais traduzidos] */
// Desenhando cada um dos brasões/flechas no círculo
for (let i = 0; i < symbolAmountDraw; i++) {
    p.push(); // BRASÕES & FLECHAS

    // Transladar o centro do brasão/círculo de flechas
    p.translate(symbolOffsetX, symbolOffsetY);

    // A melhor maneira de imaginar essas transformações é imaginar que
    // elas acontecem na ordem opostas a que elas estão definidas no código
    if (symbolDrawType === "sign") {
        // Girar em volta do centro do círculo de flechas com
        // uma distância baseada no índice da flecha atual
        p.rotate(
            (symbol.rotation ?? symbolDefaults.rotation) +
            i * 360 / symbolAmount
        );

        // Transladar para a parte superior do círculo de flechas
        p.translate(0, - (symbol.radius ?? symbolDefaults.radius));

        // Transladar o brasão/flecha horizontalmente relativo
        // à posição individual da flecha no círculo de flechas
        p.translate(symbolOffsetStrafe, 0);
    }

    // Girar em volta do centro do brasão/flecha
    p.rotate(symbolAngle);

    if (tintedImage) {
        p.image(tintedImage, 0, 0, symbolSize, symbolSize);
    } else {
        p.image(symbolImage, 0, 0, symbolSize, symbolSize);
    }

    // Desenhar bordas em volta dos símbolos
    if (spell.symbolBorder) {
        p.strokeWeight(2);
        p.noFill();
        p.strokeWeight(1 / sealScale);
        p.stroke(tintColor);
        p.rect(0, 0, symbolSize, symbolSize);
    }

    p.pop(); // BRASÕES & FLECHAS
}
```

### Links Compartilháveis

O editor permite que o usuário crie um link da magia em edição para salva-la ou compartilha-la. Esse link envolve o uso da url do site com o parâmetro `?spell=` preenchido com um valor compactado e codificado em base64.

Em testes foi verificado que simplesmente codificar o texto em formato JSON diretamente é extremamente ineficiente, de forma que, em magias complexas, o link seria muito grande, possivelmente atingindo limites de redes sociais e de navegadores. Por isso grande esforço foi tomado para diminuir o tamanho dos links gerados.

Para isso foi adicionado uma etapa de compressão usando o algoritmo `deflate-raw`, mas ainda mais significante foi a adição de uma etapa anterior responsável por remover informações redundantes, ou seja, campos que já continham o valor padrão e portanto podem ser apagados, com a ciência de que o JSONEditor irá preenche-los com o mesmo valor padrão.

Com isso é possível compartilhar magias usando apenas um link e [um clique :material-cursor-default-click:](https://wha-spell-maker.daviamsilva.dev/?spell=XVJBjtswDPwKoVMLGEmxwF58K3ppse3JLXJogoCRaYtYhTQkOka6yN8Lyem224shazjDITUvTvBMrnXdNU4BuqCUXeNwtqDJte4Jz3om6AInDHhG17iesk88Gau41n0PBLlyc-FCJozgVQxZMiB4EksYYWHpYZae0qBqkHnkCO8QLpgYxUAHsEBrWQXfQ55T0kLp4XQFFMBolASNZYQJrfwUnle5UBpJPAFKD5EubFj8FSXJG-gUBkwNsEHADCrxCicigVw-pe6fCYr5hHW-DEtgHwBj1KX6mzMlMIUhKhrgSS9U78fqtLYf4hWWQEKXUhoIbNG7NCYC09kH6sF0JAuUNlBXWNbGGU6cyRv1DagQBIxDsUfoA2SN1NQORb0qr6pV8VVvBdZXOE-RrPQt1rzxBY1ys45Tlvh2outmL3vpdE6eWvgiPU0kPYnBjs0H-IwGH40iU4IdP_NegtmU2-12KXhAwxXdGEWaqGfcCNl24Wfe1nwda76OHWF0jSsms2t_vrjEMq6nexq_IYu7HRpXo_AGqjfHXcnJjz9xKmL8i1z7-PjhzpL_SXL89Dcn7ta8xb6-ZsY1Lun92D483A63w-03){ target="_blank" rel="noopener noreferrer" }.

```javascript title="Código de codificação e decodificação do parâmetro spell:"
export async function base64urlDeflateRawEncode(input: string): Promise<string> {
    const stream = new Response(input).body!.pipeThrough(new CompressionStream("deflate-raw"));
    const buffer = await new Response(stream).arrayBuffer();
    const bytes = new Uint8Array(buffer);
    const binary = Array.from(bytes, byte => String.fromCharCode(byte)).join("");
    return btoa(binary).replace(/\+/g, "-").replace(/\//g, "_").replace(/=/g, "");
}

export async function base64urlDeflateRawDecode(input: string): Promise<string> {
    const base64 = input.replace(/-/g, "+").replace(/_/g, "/");
    const padded = base64.padEnd(base64.length + (4 - base64.length % 4) % 4, "=");
    const binary = atob(padded);
    const bytes = Uint8Array.from(binary, char => char.charCodeAt(0));
    const stream = new Response(bytes).body!.pipeThrough(new DecompressionStream("deflate-raw"));
    const decompressed = await new Response(stream).arrayBuffer();
    return new TextDecoder().decode(decompressed);
}
```

### Criação dos Símbolos

Para simplificar o processo de inserção de símbolos e evitar confusão com conceitos já definidos na comunidade a lista de símbolos (brasões e flechas) foi tirada diretamente da Independent Witch Hat Atelier Wiki, a fonte principal de informações sobre a série.

![Símbolos disponíveis no editor](/blog/projetos/wha-spell-maker/whasm-symbols.png){ .width50 align=right }

A maior parte dos símbolos foi desenhada se traçando por cima dos desenhos já presentes na wiki, ou usando referências diretas da série. Além dos símbolos oficialmente reconhecidos foram adicionados figuras geométricas úteis e os símbolos de magia vindos da série [A Casa Coruja](https://pt.wikipedia.org/wiki/The_Owl_House), outra série que eu sou fã e que contém diversas semelhanças com Witch Hat Atelier.

Para todos os símbolos a grossura da linha é fixa como sendo 10px, o mesmo valor padrão da grossura dos círculos e linhas disponíveis no editor. Entretanto símbolos diferentes geralmente tem proporções diferentes entre si (brasões são geralmente maiores que flechas, por exemplo), e para lidar com isso certos tipos diferentes de símbolos tem imagens de tamanho diferentes, variando de 200×200px até 800×800px.

Durante o processo de build do site um script python é responsável por converter e organizar todas as imagens nas pastas dentro de `symbols` para converter em um único arquivo `src/data/symbols.json` que é importado dentro do código e integrado diretamente no código gerado pelo sistema de build Vite. (1)
{ .annotate }

1. Ou manualmente para desenvolvimento, usando o comando `#!terminal npm run make`

### Cloudflare

Para esse projeto, hospedar o site na infraestrutura Workers & Pages da Cloudflare foi o ideal. Ela é gratuita, global, fácil de começar e que permite algumas opções avançadas para a configuração do backend. Mais especificamente foi possível resolver alguns problemas derivados pela forma como o site é carregado, que não seria possível em Github Pages, por exemplo.

Primeiramente, uma limitação de usar as bibliotecas p5.js, JSONEditor e código para gerar as abas extras é que nenhum desses códigos será executado quando um motor de busca tentar indexar a página. Ou seja, caso nada fosse feito, a única estrutura HTML disponível para análise seriam as tags `#!html <meta>` do cabeçalho, o título `#!html <h1>` e os contêineres que irão acomodar a estrutura do site que ainda não existe.

Para resolver isso, usa-se o plugin `plugin/prerender.ts` que é executado durante a build do site e que usa a biblioteca [Puppeteer](https://pptr.dev/), capaz de executar o site localmente, para exportar o código HTML gerado para um arquivo separado (chamo de `index-prerendered.html`). A única desvantagem desse método é que o ambiente de build automático da Cloudflare não suporta a Puppeteer, o que força que o lançamento de novas versões ocorram de maneira manual e local.

Usando um binding do tipo ASSETS, uma funcionalidade da Cloudflare Workers & Pages, declarado em `functions/index.ts` é possível detectar quando uma requisição está vindo de um *crawler*, de uma lista fixa dos *crawlers* mais importantes, e propositalmente enviar como resposta o arquivo pré-renderizado. Dessa forma todos os motores de pesquisa, indexação ou de redes sociais processam a mesma versão da página que um usuário final vê.

Nesse mesmo arquivo acima há uma segunda funcionalidade implementada: Quando uma requisição é recebida contendo o parâmetro `?spell=`, indicando que isso é um link de compartilhamento, um código é executado para decodificar as informações da magia. Se um título válido é encontrado o arquivo HTML será editado para incluir o nome da magia no título do site, como exemplo, "Sylph&nbsp;Shoes&nbsp;Spell | Witch&nbsp;Hat&nbsp;Atelier&nbsp;Spell&nbsp;Maker". Assim, ao compartilhar magias em sites que suportam algum tipo de pré-visualização, o usuário final visualizará o título da página contendo o nome da magia que está preste a carregar:

![Pré-visualização de uma magia no site X](/blog/projetos/wha-spell-maker/x-preview.webp)
{ .width75 }

## Impacto

### Comunidade

Eu inicialmente comecei a desenvolver esse projeto no final do ano passado, mas ele ficou em suspensão até que em março desse ano eu decidi focar integralmente nesse projeto, com a intenção de lança-lo publicamente perto do dia do início da primeira temporada do anime. A data da publicação ocorreu em 5 de abril de 2026, no domingo, um dia antes do primeiro episódio lançar.

Com o projeto finalizado e estável eu o postei nas comunidades do [Reddit](https://www.reddit.com/r/WitchHatAtelier/comments/1sd5z5n/presenting_the_witch_hat_atelier_spell_maker/) (200 upvotes), Discord e [X (antigo Twitter)](https://x.com/DaviAMSilva/status/2040848941470597165) (4000 likes e 800 reposts) com várias reações positivas, um influxo de acessos ao site e engajamento nas redes sociais devido a combinação da novidade para fãs já existentes e novos fãs chegando na comunidade.

Após algumas semanas a explosão inicial diminuiu e, naturalmente, após a conclusão da primeira temporada houve uma segunda diminuição de popularidade. Após essa final a taxa de acesso normalizou. Ainda assim, é surreal encontrar imagens de magias sendo compartilhadas por fãs, principalmente no Reddit e Discord, e notar a presença dos símbolos que eu desenhei para o projeto.

Uma fato curioso, que eu acredito ser indiretamente responsável devido a facilidade de uso do meu editor, foi a proliferação de postagens de magias de baixa qualidade por novos fãs da série. Esses usuários não tinham o conhecimento suficiente do sistema de magia para criar magias coerentes. Isso chegou ao ponto de os moderadores serem forçados a adotar medidas para limitar essas postagens. No subreddit posts sobre esses tipos de magias agora só podem ser postados nos sábados com a etiqueta "Spell-Post Saturday" e no servidor discord canais separados foram criados para magias gerais e magias sérias.

Finalmente em termos de suporte posterior ao lançamento houveram poucas mudanças. Algumas correções de bugs visuais, funcionalidades de qualidade de vida, mas principalmente a atualização dos símbolos conforme as novidades que o anime trouxe. O meu plano atual para suporte futuro é ocasionalmente visitar as páginas da wiki e atualizar a lista de símbolos conforme novas informações sobre a série se tornam disponíveis.

### Estatísticas

Infelizmente eu não me dei conta que a Cloudflare tinha um limite de cerca de 30 dias em que as estatísticas de um Worker estão disponíveis. Mas no que eu me recordo que a taxa de acesso logo após o início do anime foi pelo menos três vezes a taxa de uso atual, talvez mais, que é perto de 500 invocações por dia:

![Cloudflare](/blog/projetos/wha-spell-maker/stats-cloudflare.webp)
{ .width75 }

As estatísticas realmente interessantes são as dos motores de pesquisa. Mesmo com as minhas tentativas de melhorar o SEO do site, no Google a posição média em resultados ainda é apenas a quinta posição. Inclusive em certas condições o repositório no GitHub ou a postagem no Reddit sobre a publicação do projeto consegue aparecer acima do site em si. Enquanto isso, com o Bing, o site é geralmente melhor colocado nos resultados, entretanto o CTR (1) e o volume absoluto de cliques são menores.
{ .annotate }

1. *Click-Through Ratio*, ou a porcentagem de impressões que geram um clique

<figure markdown="span">
![Google](/blog/projetos/wha-spell-maker/stats-google.webp){ .width75 }
<figcaption>Google</figcaption>
</figure>

<figure markdown="span">
![Bing](/blog/projetos/wha-spell-maker/stats-bing.webp){ .width75 }
<figcaption>Bing</figcaption>
</figure>

Principalmente no gráfico do Google é possível visualizar vários picos de cliques e impressões elevados, do qual apenas um eu tenho uma explicação muito interessante: No início de junho começaram a ser compartilhados pela comunidade o projeto [Witch Hat Atelier Spell Simulator](https://github.com/ytnrvdf/wha-spell-simulator) e outras versões derivadas, originalmente criado por usuário do GitHub [ytnrvdf](https://github.com/ytnrvdf), descrito como *"Um simulador de desenho de magias direto no navegador inspirado por Witch Hat Atelier"* (1).
{ .annotate }

1. Tradução própria. Original: *"A fan-made browser-based spell drawing simulator inspired by Witch Hat Atelier."*

Esse projeto não é um competidor direto em termos de conceito, entretanto o fato dele ser genuinamente impressionante e ter um apelo visual e interativo faz ele chamar mais atenção que o meu projeto que é destinado a fãs mais dedicados à criação de novas magias. Infelizmente, devido ao fato das palavras "Maker" and "Simulator" serem relacionadas, após ele ser lançado o CTR caiu do meu site caiu drasticamente devido à competição nos resultados de pesquisa.

E uma última estatística: Segundo o Google os países com a maior porcentagem de pesquisa são, sem muita surpresa, os Estados Unidos com 33% e o Reino Unido com 7%, já em terceiro lugar vem o brasil com 6%. Isso reflete a minha experiência de ter descoberto uma quantidade surpreendente de fãs brasileiros dentro da comunidade de Witch Hat Atelier, substancialmente maior que outras comunidades de anime e mangá que eu já vi.

## Análise da Série <small>(spoilers marcados)</small>

Por fim, eu acredito que seja apropriado terminar falando um pouco da série em si e o que me fez amar ela. Eu pretendo falar principalmente da arte da série e da premissa, sem focar nos personagens em si.

O motivo mais óbvio  para gostar dessa série, sem nenhuma surpresa para os fãs, é a qualidade da arte produzida pela *mangaká*, Kamome Shirahama, tanto em questão da qualidade técnica quanto a visão artística. Os personagens e ambientes são incrivelmente detalhados e as expressões conseguem facilmente transmitir toda as emoções presentes em cada cena.

Uma das características mais únicas sobre a arte dela é o fato da Shirahama não ter medo de quebrar o fluxo tradicional dos painéis em cada página. Em várias páginas personagens e objetos excedem e interagem com as margens dos painéis, tornando a cena mais dinâmica e aumentando a profundidade da página e do ambiente em questão.

O melhor exemplo dessa expressão artística está presente em uma sequência presente no capítulo 47 <small>(sem spoilers)</small>. No capítulo, durante duas páginas, Qifrey (o professor) está educando as garotas sobre a origem mitológica de um festival para o qual eles estão viajando; a história é exibida em um livro (um simbolismo constante no mangá e anime), inicialmente fechado e depois aberto, desenhado na página como um objeto dentro do universo da série. Na página dupla imediatamente a seguir nos deparamos com a seguinte cena:

<figure markdown="span">
![Silver Eve Festival Arrival (Chapter 47)](/blog/projetos/wha-spell-maker/manga-silver-eve.png){ .width75 }
<figcaption>Os personagens figurativamente e literalmente chegam ao festival após virar a página do livro sobre a origem do festival</figcaption>
</figure>

???warning "SPOILERS do volume 1: A premissa da série"

    ![Manga Intro](/blog/projetos/wha-spell-maker/manga-intro.png){ .width50 align=right }

    A premissa da série é também muito interessante, pois no primeiro capítulo a magia é inicialmente apresentada como uma habilidade exclusiva a pessoas que nasceram com ela, os bruxos, algo muito comum em histórias de fantasia. Mas rapidamente é revelado que os únicos pré-requisitos para usufruir da magia são uma folha de papel, uma caneta, tinta mágica e o conhecimento e técnica necessários para desenha-la. Todos os bruxos, e especialmente o Conselho de Segurança Mágico, são obrigados a manter esse conhecimento da magia um segredo completo para todos os não-bruxos.

    Toda a progressão da série ocorre em volta do conflito entre duas facções: Os bruxos de Chapéu Pontudos, na forma dos personagens principais, junto do Conselho de Segurança Mágica que juram manter o segredo da magia a todo custo e os Chapéus de Aba que pretendem revelar o segredo da magia para que todas as pessoas tenham acesso a ela.

    Enquanto outras histórias mais simples declarariam um ou outro grupo como o inimigo definitivo, Witch Hat Atelier mostra uma nuance em oferecer personagens dos dois lados com convicções baseadas em argumentos morais que não podem ser imediatamente rejeitadas pelo leitor. Dessa forma após ponderar sobre os conflitos levantados durante a história é possível perceber que ambos os lados têm motivações complexas em que não há uma solução fácil e definitiva.

    Me parece bem claro que essa obra é um estudo sobre a interação, no mundo real, dos fenômenos sociológicos que são o privilégio de nascença e a meritocracia. Em minha interpretação a obra é uma crítica na incapacidade da implementação de um meritocracia real devido a oposição das seções privilegiadas da sociedade que desejam, direta ou indiretamente, não permitir que outros tenham a capacidade de chegar ao mesmo nível que eles.

    Entretanto a autora é inteligente por reconhecer que existem perigos associados com a remoção de todas as barreiras da sociedade. O exemplo principal disso no mundo real é a democratização do acesso a serviços de comunicação digital. A partir dele pessoas de todos os cantos do mundo têm acesso a comunicação instantânea, mas ele também permite a proliferação de campanhas de desinformação em uma escala global. Isso demonstra como algumas limitações sociais e legais se tornam necessárias para suportar a estabilidade frágil da sociedade moderna, exatamente a justifica pelas ações tomadas pelo Conselho de Segurança Mágica na série.

???warning "SPOILERS do capítulo 85: Minha arte favorita da série e o seu significado"

    ![Manga Chapter 85 Cover](/blog/projetos/wha-spell-maker/manga-cover-85.jpeg){ .width50 align=right }

    Eu amo a arte dessa página, que é a capa do capítulo 85, pois ela representa todos os pontos que fazem Witch Hat Atelier ser especial: Arte belíssima e detalhada, presença interativa da arte dentro da página, cheia de emoção e que sozinha conta uma história sobre o sujeito representado.

    Qifrey é um personagem com várias camadas de segredos e traumas reprimidos desde a sua infância, mas que ele é forçado a esconder na atualidade. Isso é representado pelos quadros, cada um uma parte mais interna e antiga de sua alma até que, no quadro mais profundo e bem difícil de perceber, está o Qifrey quando era criança.

    Os braços apertados parecem representar desespero e uma vontade de esconder quem ele realmente é, mas, em outra interpretação, também podem significar uma tentativa de confortar e preservar o que sobra da inocência que ele anteriormente possuía.
