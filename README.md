# Style guide generator

Um _style guide_ **standalone** (um único `index.html`, sem dependências) que funciona como **gerador de tokens**: umas poucas variáveis de topo governam todos os componentes, e um painel interativo permite editá-las ao vivo e exportar o CSS resultante para usar em qualquer contexto.

## Como usar

Abra o `index.html` no navegador (duplo-clique ou arraste pra uma aba). Clique no **botão flutuante** no canto inferior direito para abrir o painel de controles.

> O JavaScript precisa rodar, então abra o arquivo direto no navegador — previews estáticos (que não executam JS) mostram o layout mas não a interação.

## Modelo de tokens

Os valores vivem no `:root` em duas camadas:

- **Primitivas** — as variáveis que o humano controla (cores base, `--space-unit`, `--radius`, `--fs-base`, `--lh`, fontes).
- **Derivadas** — calculadas a partir das primitivas via `calc()` (as 7 `--space-*`, `--radius-lg`, as 7 `--fs-*`). Mexer numa primitiva repercute em toda a escala.

Cada componente referencia **apenas tokens**, nunca valores fixos — é isso que permite o controle central.

## Painel de controles

- **Tema escuro** — alterna a paleta clara/escura; os _color pickers_ passam a editar o tema ativo.
- **Cores** — 10 _color pickers_ (bg, surface, text, muted, border, accent, info, ok, wip, danger).
- **Escala** — sliders de espaço base, raio base, tamanho de tipo base e entrelinha.
- **Fontes por papel** — Títulos, Corpo e Mono, cada um recebendo qualquer família do [Google Fonts](https://fonts.google.com) (carregada sob demanda; basta colar o nome exato).
- **Botões** — controles granulares só dos botões: fonte própria, cantos, altura, padding, espaçamento entre letras, peso e caixa alta.

## Exportar

O botão **Exportar CSS** monta um bloco `:root { … }` com os valores atuais (cores, escalas, fontes e botões) e o copia para a área de transferência. Fontes do Google entram como `@import` no topo, então a saída é autossuficiente.

## Componentes cobertos

Tokens, tipografia (incl. texto corrido), botões, form controls, badges/chips, avatares, alerts, context-box, cards, tabelas, accordion, listas, item expansível, navegação (tabs/breadcrumb/paginação), feedback (progress/spinner/skeleton/tooltip), dialog, toast e empty state.
