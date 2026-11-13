# Kefi Burguer — Site institucional

Landing page estática (HTML + CSS puro, sem build, sem framework) para a hamburgueria **Kefi Burguer**. Objetivo: atrair novos clientes e direcionar para o pedido online.

## Estrutura

```
kefi/
├── index.html        # página única, com um <script> inline no final
├── style.css         # todo o visual; variáveis de cor em :root
├── img/
│   ├── logo.png          # logo oficial (fundo laranja, quadrada)
│   └── burger-banner.png # post do Instagram; o hambúrguer fica à esquerda
└── CLAUDE.md
```

Para ver: abrir `index.html` direto no navegador (`start index.html` no Windows). Não precisa de servidor.

## Dados reais do negócio (fonte: Instagram @kefi_burguer)

| Item | Valor |
|---|---|
| Nome | Kefi Burguer |
| Slogan | "Sabor que conquista em cada mordida." |
| Endereço | Rua Cornélio Procópio, 20 - Nova Vista |
| Cidade | **não confirmada** (posts marcados por @alosabaraeregiao sugerem região de Sabará/BH — confirmar com o dono) |
| Horário | Segunda a Domingo, 19h às 01h |
| Pedido online | https://pedido.anota.ai/loja/kefi-burguer-1 |
| Instagram | https://www.instagram.com/kefi_burguer/ (~2.247 seguidores, nov/2026) |
| Diferenciais | Molho verde à vontade; reinauguração recente com espaço renovado |
| WhatsApp | desconhecido |

Não invente dados novos (telefone, preços, CNPJ etc.). Se faltar, pergunte ao usuário.

## Pendências conhecidas

- **Cardápio é fictício.** Os 4 itens em `#cardapio` (Kefi Clássico, Kefi Duplo, Kefi Crispy, Batata Suprema) são exemplos sem preço. Há um comentário `<!-- ATENÇÃO: itens de exemplo -->` no HTML. Substituir quando o usuário passar o cardápio real.
- **Cidade do mapa** — o iframe do Google Maps e o link "Abrir no Google Maps" usam só rua + bairro; adicionar a cidade quando confirmada.
- **Fotos** — os cards do cardápio usam emojis como ícone; trocar por fotos reais quando disponíveis em `img/`.
- Botão de WhatsApp — adicionar se o número for fornecido.

## Identidade visual

Cores tiradas da logo e dos posts (definidas em `:root` no `style.css`):

| Variável | Cor | Uso |
|---|---|---|
| `--orange` | `#ff6a00` | cor principal, botões, destaques |
| `--red` | `#e5261f` | gradientes com o laranja |
| `--yellow` | `#ffc21a` | detalhes, bordas, selos |
| `--dark` / `--dark-2` / `--dark-3` | `#0f0f10` / `#18181b` / `#232327` | fundos (site é dark) |

Fontes (Google Fonts):
- **Bebas Neue** — títulos (`h1–h3`), estilo dos cartazes do Instagram
- **Poppins** — texto corrido
- **Pacifico** — toques manuscritos (nome da marca, "kickers" das seções), remetendo ao lettering da logo

Padrões visuais: botões em pílula com gradiente laranja→vermelho, cards com cantos de 20px, faixa animada (`.marquee`) inclinada.

## Seções da página (ordem)

1. `.header` — fixo; fica com fundo ao rolar (`.header--scrolled`); vira menu lateral abaixo de 860px
2. `.hero` — título, CTAs, info rápida e imagem do burger (crop circular via `object-position: 0% 50%`)
3. `.marquee` — faixa rolando (conteúdo duplicado de propósito para o loop infinito)
4. `#cardapio` — cards (`.card`, destaque com `.card--featured`)
5. `#diferenciais` — 4 `.feature`
6. `.cta` — chamada para pedido
7. `#local` — endereço, horário e mapa
8. `.footer` + `.float-order` (botão flutuante de pedido)

## Convenções

- Textos do site em **português (pt-BR)**.
- Nomes de classe em estilo BEM simplificado (`bloco__elemento`, `bloco--modificador`).
- Todo link de pedido aponta para o anota.ai e abre em nova aba (`target="_blank" rel="noopener"`). Se o link mudar, há várias ocorrências no `index.html` — trocar todas.
- Animação de entrada: o JS adiciona `.reveal` aos elementos e `.visible` quando aparecem na tela. Para animar algo novo, inclua o seletor na lista do `querySelectorAll` no script.
- Respeitar `prefers-reduced-motion` (já existe regra no fim do CSS).
- Breakpoints: 1024px (grids em 2 colunas), 860px (layout mobile), 560px (1 coluna).
- Manter sem dependências/build; não adicionar frameworks sem o usuário pedir.
