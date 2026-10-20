# CP2 — Site pessoal responsivo (HTML semântico + CSS + Flexbox/Grid)

**Autor:** Guilherme Arcanjo Barra
**Curso:** Análise e Desenvolvimento de Sistemas (ADS) — Centro Universitário Braz Cubas

## Sobre o projeto

Evolução do site do CP1: as mesmas 5 páginas agora são responsivas, construídas com abordagem
**mobile-first**, usando **Flexbox** no cabeçalho/menu e em outras seções, **Grid** para layouts em
colunas e **media queries com `min-width`** para adaptar o layout a telas maiores.

## Estrutura de arquivos

```
CP2_Guilherme_Barra_Turma/
├── index.html          → página inicial: quem sou eu, avatar e interesses (Grid de cartões)
├── curriculo.html       → formação, sobre mim, habilidades e tabela (Grid de 2 colunas em telas largas)
├── formulario.html      → formulário de contato (campos em linha com Flexbox em telas largas)
├── multimidia.html      → vídeo, áudio e mapa incorporado por iframe (mídia responsiva)
├── graficos.html        → desenho em canvas (JavaScript) e gráfico em SVG estilizado com CSS
├── css/
│   └── estilos.css     → folha de estilo única, mobile-first, usada por todas as páginas
├── img/
│   └── foto-guilherme.jpg → foto usada no cabeçalho de todas as páginas
└── README.md
```

## O que mudou do CP1 para o CP2 (responsividade)

- **Mobile-first com `min-width`:** o CSS parte do layout de celular e usa `@media (min-width: 600px)`
  (tablet) e `@media (min-width: 900px)` (desktop) para acrescentar colunas e reorganizar o layout —
  em vez do antigo `max-width` (desktop-first) do CP1.
- **Flexbox no cabeçalho/menu:** `.cabecalho-site .wrapper` é `display: flex`, empilhado
  (`column`) no celular e em linha (`row`) a partir de 900px; `nav.menu-principal ul` e `.identidade`
  também usam Flexbox. Outras seções com Flexbox: `.opcoes-linha` (rádios/checkboxes do formulário) e
  `.linha-campos` (campos do formulário lado a lado a partir de 600px).
- **Grid em pelo menos uma página:**
  - `index.html`: `.grade-cartoes` — 1 coluna no celular, 2 colunas a partir de 600px, 3 colunas a
    partir de 900px.
  - `curriculo.html`: `.layout-curriculo` — conteúdo empilhado no celular e, a partir de 900px,
    duas colunas (`2fr 1fr`) com o conteúdo principal e a nota lateral lado a lado.
- **Imagens e mídias responsivas:** regra global `img, video, iframe, svg, canvas { max-width: 100%;
  height: auto; }`, além de `audio { width: 100%; }` e tabela dentro de um contêiner com
  `overflow-x: auto` para não quebrar o layout em telas pequenas.
- **`<meta name="viewport">`** mantido em todas as páginas (já vinha do CP1).
- **Mesmo cabeçalho/menu** reaproveitado e adaptado em todas as páginas.

## Onde cada requisito foi atendido

- **HTML semântico:** `header`, `nav`, `main`, `section`, `article`, `aside` e `footer` em todas as
  páginas, com papéis distintos (nenhum `div` genérico substituindo esses elementos).
- **Menu igual em todas as páginas:** o mesmo `<nav class="menu-principal">` com links relativos
  (`index.html`, `curriculo.html`, `formulario.html`, `multimidia.html`, `graficos.html`) aparece em
  todas as páginas, com `aria-current="page"` indicando a página atual.
- **Formulário (`formulario.html`):** campos `text`, `email`, `tel`, `date`, `select`, `radio`,
  `checkbox` e `textarea` — todos com `<label>` associado e atributos de validação nativa
  (`required`, `type="email"`, `minlength`, `pattern`).
- **Multimídia (`multimidia.html`):** `<video controls>`, `<audio controls>` e um `<iframe>` com um
  vídeo do YouTube incorporado.
- **Gráficos (`graficos.html`):** um `<canvas>` desenhado via JavaScript (script inline no fim da
  página) e um `<svg>` estilizado inteiramente por classes definidas em `css/estilos.css`.
- **CSS externo:** todo o estilo está em `css/estilos.css`, vinculado por `<link>` nas 5 páginas.
  Não há `style="..."` nem `<style>` em nenhuma página.

## Paleta e tipografia

- Cores: `#16202B` (tinta), `#101A24` (faixa escura do cabeçalho), `#F5F6F3` (fundo), `#FFFFFF`
  (cartões), `#2F6F5E` (destaque principal) e `#E2A33D` (destaque secundário).
- Tipografia: **Space Grotesk** para títulos, **IBM Plex Sans** para o corpo do texto e
  **IBM Plex Mono** para rótulos e itens de navegação (referência ao universo de programação),
  carregadas via Google Fonts.

## Como visualizar

1. Extraia o `.zip` em uma pasta.
2. Abra `index.html` diretamente no navegador.
3. Navegue pelas 5 páginas usando o menu do cabeçalho.

## Observações

- O vídeo e o áudio da página `multimidia.html` usam arquivos de exemplo de domínio público
  hospedados pela MDN, incorporados com `<video>`/`<audio>` e não apenas como link.
- A foto usada no cabeçalho (`img/foto-guilherme.jpg`) é uma foto real, redimensionada em CSS para
  um formato circular pequeno (`object-fit: cover`).
