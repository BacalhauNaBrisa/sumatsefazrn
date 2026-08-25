<p align="center">
  <img src="afrelefante.png" alt="Mascote AFRE Sefaz/RN" width="200"/>
</p>

<h1 align="center">sumatsefazrn</h1>

<p align="center">
  Visualizador não-oficial da escala de plantões dos novos<br/>
  <strong>Auditores Fiscais de Receitas Estaduais (AFRE)</strong> lotados na SUMAT (Subcoordenadoria de Fiscalização de Mercadorias em Trânsito) da Secretaria da Fazenda do Rio Grande do Norte (Sefaz/RN).
</p>

<p align="center">
  🔗 <strong><a href="https://bacalhaunabrisa.github.io/sumatsefazrn/">bacalhaunabrisa.github.io/sumatsefazrn</a></strong>
</p>

---

## Sobre o projeto

Este repositório contém uma única página HTML autocontida (`index.html`) que exibe, para os 47 novos Auditores Fiscais da SUMAT, a escala de plantões de 12 horas do mês de setembro/2026 — em formato de listagem/matriz, calendário mensal interativo e quadro de coincidências de plantão — sem necessidade de servidor, backend ou build: basta abrir o arquivo no navegador (ou acessá-lo via GitHub Pages).

O projeto é uma ferramenta de consulta pessoal, sem qualquer vínculo institucional com a Sefaz/RN. Os dados de escala foram inseridos manualmente a partir da planilha oficial recebida e podem ficar desatualizados em caso de trocas ou ajustes posteriores.

## Como usar

1. Na listagem superior, **clique no nome** de um auditor fiscal para selecioná-lo (apenas um por vez; clique novamente para desmarcar). Use o campo de busca para localizar um nome rapidamente.
2. Com um nome selecionado, o **calendário de setembro/2026** é colorido automaticamente: vermelho nos dias de plantão, verde nos dias de folga.
3. Logo abaixo do calendário, é possível **escolher um dia específico** do mês — pelo seletor "Quem está de plantão em um dia específico" ou clicando diretamente numa data do calendário — para ver, num só quadro, todos os auditores fiscais escalados naquele dia.
4. Mais abaixo, o **quadro de plantões do auditor selecionado** lista cada dia de trabalho do auditor escolhido na listagem e, para cada data, quais outros auditores da SUMAT também estarão de plantão naquele mesmo dia.
5. Sem nenhuma seleção, a listagem superior já mostra, para todos os 47 auditores, quais dias do mês são de plantão (vermelho) e quais são de folga (verde).
6. Com um auditor **base** selecionado, cada outro nome da listagem passa a ter uma caixa de marcação ao lado (na tabela desktop, dentro da própria célula do nome; nos cartões mobile, ao lado do nome). Marque quantos auditores quiser para comparar com a base: um novo quadro, **"Vínculos com outros auditores"**, mostra, para cada comparação, uma faixa visual dos 30 dias do mês e as listas de dias em que ambos trabalham juntos, dias exclusivos da base e dias exclusivos do comparado.

As formas de seleção — por auditor base, por dia específico e por comparação entre auditores — são complementares e podem ser usadas em conjunto.

## Dados exibidos

As únicas informações incorporadas ao código a partir da planilha de origem (`escala_setembro_2026_novatos.xlsx`) são:

- o **nome completo** de cada um dos 47 auditores fiscais; e
- os **dias do mês** em que cada um tem plantão de 12 horas.

Nenhum outro dado da planilha (CPF, matrícula, e-mail, contato, dados bancários) é utilizado ou exposto pela página.

## Preparado para expansão futura (turno e local)

Cada plantão já é modelado internamente como um objeto com três campos — `{ d: <dia>, turno: null, local: null }` — em vez de apenas um número de dia solto. Isso significa que a estrutura de dados e a interface já estão prontas para receber, em atualizações futuras:

- **Turno** (diurno ou noturno) de cada plantão individual, com filtro por turno na listagem;
- **Local** de trabalho de cada plantão individual (ex.: posto fiscal, aeroporto, correios, entre outros), com filtro por local na listagem.

Enquanto essas informações não forem cadastradas (`turno`/`local` permanecem `null`), a interface exibe esses atributos **acizentados** (badges tracejados "turno ?" / "local ?" nos cartões de plantão, e chips desabilitados "em breve" na barra de filtros), deixando claro que o dado existe na modelagem mas ainda não foi preenchido, sem permitir filtragem por ele.

## Tecnologias utilizadas

- **HTML5** — estrutura da página, em arquivo único (`index.html`).
- **CSS3** puro — sem framework; variáveis CSS (`:root`) para cores/tema, grid/flexbox para o layout responsivo (matriz com rolagem horizontal e calendário empilhável em telas estreitas) e fontes do Google Fonts (*Space Grotesk*, *Inter*, *JetBrains Mono* para dados numéricos), mantendo a mesma identidade visual do projeto irmão.
- **JavaScript (ES5/ES6)** — dados da escala embutidos no próprio script, montagem dinâmica da matriz, do calendário e do quadro de coincidências, e toda a lógica de seleção/busca.
- **jQuery 3.7** (via CDN) — manipulação do DOM e eventos (`click`/`input`) que disparam a atualização da interface.
- **GitHub Pages** — hospedagem estática, sem backend, sem build step, sem dependências instaladas: o repositório é publicado como está.

Não há framework de front-end (React, Vue etc.), bundler ou etapa de compilação — o projeto é intencionalmente simples para poder ser mantido e publicado direto pela interface do GitHub, do mesmo modo que os projetos irmãos [`remunerasefazrn`](https://github.com/BacalhauNaBrisa/remunerasefazrn) e [`cebraspe`](https://github.com/BacalhauNaBrisa/cebraspe).

## Estrutura do repositório

```
sumatsefazrn/
├── index.html        # página única: HTML + CSS + JS (e dados da escala) embutidos
├── afrelefante.png   # logotipo/mascote do projeto
└── README.md         # este arquivo
```

## Aviso legal

Ferramenta independente e não-oficial, sem qualquer vínculo com a Sefaz/RN. Os dados de escala aqui reproduzidos têm caráter meramente informativo e refletem a planilha de origem no momento em que foi incorporada ao código; eventuais trocas, permutas ou ajustes posteriores na escala oficial não são refletidos automaticamente. Consulte sempre a escala oficial junto à chefia competente para fins oficiais.
