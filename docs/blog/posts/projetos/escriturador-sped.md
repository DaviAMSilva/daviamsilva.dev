---
title: Escriturador SPED
description: Biblioteca Python para auxiliar a criação e edição de arquivos de escrituração do SPED brasileiro.
date:
  created: 2026-10-21
categories:
  - Projetos
  - Destaques
tags:
  - biblioteca
  - docstrings
  - documentação
  - material for mkdocs
  - mkdocs
  - pylint
  - pypi
  - pytest
  - python
  - semver
  - sped
  - website
links:
  - Documentação: https://escriturador-sped.daviamsilva.dev
  - Repositório: https://github.com/DaviAMSilva/escriturador-sped
  - Pacote: https://pypi.org/project/escriturador-sped
  - curriculo.md#kepi-supermercado
---

<style>
img#logo {
    float: left;
    width: 220px;
    max-width: 100%;
    height: auto;
    margin: 0 1.5rem 1rem 0;
}

@media (max-width: 721px) {
    .logo-paragrafo {
        text-align: center !important;
    }

    img#logo {
        float: unset;
        width: 160px;
        margin: 0 auto 0.75rem;
    }
}
</style>

[![Static Badge](https://img.shields.io/badge/github-DaviAMSilva%2Fescriturador--sped-dddddd?logo=github)](https://github.com/DaviAMSilva/escriturador-sped)
[![Static Badge](https://img.shields.io/badge/website-Escriturador%20SPED-326eff)](https://escriturador-sped.daviamsilva.dev)
[![Static Badge](https://img.shields.io/pypi/v/escriturador-sped?logo=pypi&logoColor=white)](https://pypi.org/project/escriturador-sped)
{ .badges }

> A biblioteca Escriturador SPED tem como objetivo fornecer uma API de acesso, criação e manipulação de arquivos de escrituração pertencentes ao projeto SPED do governo brasileiro. A biblioteca escrita em Python é destinada a programadores, ou usuários avançados, que trabalham com módulos do projeto SPED que envolvam a criação ou edição de escriturações.

**Para informações de uso da biblioteca em si acesse o site da documentação: [Escriturador SPED](https://escriturador-sped.daviamsilva.dev/).**

<img id="logo" src="https://raw.githubusercontent.com/DaviAMSilva/escriturador-sped/main/docs/imagens/logo-transparente.webp" alt="Logo do Escriturador SPED" markdown />
{ .logo-paragrafo }

Atualmente eu trabalho como assistente administrativo no [Kepi Supermercado], em que algumas das minhas funções principais são a entrada e emissão de notas fiscais por intermédio do sistema ERP contratado pela empresa. Uma responsabilidade adicional é a geração, análise, correção e validação prévia dos arquivos de escrituração da [EFD ICMS IPI](https://www.gov.br/sped/pt-br/assuntos/escrituracoes-digitais/efd-icms-ipi) e [EFD Contribuições](https://www.gov.br/sped/pt-br/assuntos/escrituracoes-digitais/efd-contribuicoes).

Quando eu comecei meu trabalho na empresa os arquivos de escrituração eram feitos de forma completamente manual, visto que o gerador do sistema ERP gerava um único arquivo *pronto* e quaisquer alterações posteriores precisavam ser realizadas manualmente por intermédio dos programas validadores disponibilizados pelo governo federal.

Entretanto desde o meu primeiro dia no escritório eu adotei uma filosofia em que eu deveria utilizar as habilidades que apenas eu possuísse para me destacar no meu trabalho, especificamente o meu conhecimento em ciência da computação. Após adquirir alguns anos de experiência eu fiquei mais familiarizado com o programa SPED, seus módulos e principalmente os formatos dos arquivos de escrituração.

Originalmente eu editava os arquivos manualmente para corrigir os pequenos detalhes e correções que o gerador dos arquivos não suportava configurar ou que ele gerava de maneira incorreta. Mas após vários períodos fiscais realizando as mesmas alterações repetidamente eu decidi aprender um pouco mais sobre a parte técnica do formato dos arquivos de escrituração e tentar automatizar o processo.

---

O formato utilizado pelo SPED é baseado em texto, similar a um arquivo CSV, mas usando barras verticais (`|`), inclusive no início e fim da linha. Cada linha representa um registro e entre cada par de barras verticais o texto representa um campo desse registro. Cada registro tem um nome composto de um caractere que representa o bloco organizacional a que o registro pertence em adição de três algarismos.

Em uma linha de um registro o primeiro campo sempre contém o nome do registro em si. A partir da informação do nome do registro atual é necessário consultar o manual relevante para descobrir a quantidade de campos esperado para a linha, os nomes e tipos dos campos, além da explicação de como cada campo deve ser interpretado.

Apesar do fato de os registros serem listados linearmente na forma de texto, cada registro tem um nível a que ele pertence. Registros são considerados *filhos* do primeiro registro anterior em um nível acima, sendo esse o registro *pai*. Esse método de gerar uma árvore é idêntico à maneira como o python interpreta indentação, apenas nesse caso a indentação é substituída por um nível implícito baseado no registro.

Além disso as escriturações contém alguns funcionalidades adicionais em sua estrutura, como registros de abertura e fechamento da escrituração e dos vários blocos presentes. Finalmente o bloco 9 é dedicado exclusivamente para totalizar a quantidade de vezes que cada registro aparece na escrituração, servindo como uma validação básica de que a estrutura da escrituração está valida.

??? abstract "Exemplo de um arquivo de escrituração do módulo EFD Contribuições"

    Contida no exemplo abaixo linha `|0140|1|EMPRESA XXX|99999999000191|MG||3106200|||` representa o registro 0140, pertencente ao bloco 0. O registro tem nove campos no total, cujos os nomes são `|REG|COD_EST|NOME|CNPJ|UF|IE|COD_MUN|IM|SUFRAMA|` e o resto dos detalhes podem ser consultados na seguinte [tabela](https://escriturador-sped.daviamsilva.dev/modulos/?tabela=efd_contribuicoes-006-1.35#0140) ou no seguinte [manual](https://www.gov.br/sped/pt-br/assuntos/escrituracoes-digitais/efd-contribuicoes/manuais/guia_pratico_efd_contribuicoes_versao_1_35-18_06_2021.pdf/@@display-file/file).

    ```text
    |0000|002|0|||01042011|30042011|EMPRESA XXX|99999999000191|MG|3106200||00|0|
    |0001|0|
    |0110|1|2|1|
    |0111|1|0|0|0|1|
    |0140|1|EMPRESA XXX|99999999000191|MG||3106200|||
    |0990|6|
    |A001|1|
    |A990|2|
    |C001|1|
    |C990|2|
    |D001|1|
    |D990|2|
    |F001|1|
    |F990|2|
    |M001|0|
    |M200|0|0|0|0|0|0|0|0|0|0|0|0|
    |M600|0|0|0|0|0|0|0|0|0|0|0|0|
    |M990|4|
    |1001|1|
    |1990|2|
    |9001|0|
    |9900|0000|1|
    |9900|0001|1|
    |9900|0110|1|
    |9900|0111|1|
    |9900|0140|1|
    |9900|0990|1|
    |9900|1001|1|
    |9900|1990|1|
    |9900|9001|1|
    |9900|9990|1|
    |9900|9999|1|
    |9900|A001|1|
    |9900|A990|1|
    |9900|C001|1|
    |9900|C990|1|
    |9900|D001|1|
    |9900|D990|1|
    |9900|F001|1|
    |9900|F990|1|
    |9900|M001|1|
    |9900|M200|1|
    |9900|M600|1|
    |9900|M990|1|
    |9900|9900|24|
    |9990|27|
    |9999|47|
    ```

O fato que existem centenas de registros e milhares de campos para cada módulo e que a única fonte para essa informação são manuais publicados em formato PDF é o que dificulta o trabalho de conversão desses dados para um formato próprio para automatização.

---

A primeira versão da ferramenta interna que utiliza a biblioteca foi desenvolvida há mais de dois anos. Desde então a biblioteca foi atualizada incrementalmente baseado nas necessidades e limitações encontradas durante o uso dentro do escritório. O uso dessa ferramenta como um passo adicional após a geração inicial das escriturações transformou um processo que demorava uma tarde inteira para um que pode ser realizado em menos de dez minutos. Isso, além do fato que várias inconsistências anteriormente despercebidas agora podem ser detectadas e corrigidas automaticamente.

Essa foi a minha primeira experiência desenvolvendo e [publicando](https://pypi.org/project/escriturador-sped/) um pacote python. Um dos novos paradigmas de programação que eu aprendi durante o processo foi a utilização do sistema [semver](https://semver.org/lang/pt-BR/) para versionamento das mudanças. Adicionalmente foi a minha primeira experiência com uma utilização mais avançada de Git e GitHub. Especificamente a prática de criar ramos para funcionalidades específicas, que são unidas no ramo *dev* e eventualmente no ramo *main* para a publicação de uma nova versão.
