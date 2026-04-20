# Padrão de Propostas Web — Forster

Este documento define o padrão completo para criação de novas páginas de proposta da Forster,
baseado nas páginas implementadas em `conteudo-recorrente/`, `movimento/`, `olimoveis/` e `veadrigo/`.

---

## 1. ESTRUTURA DE SEÇÕES

Ordem obrigatória em toda proposta:

1. **Hero** — foto de fundo + título + subtítulo + eyebrow (ex: "Proposta comercial")
2. **Quem somos** — foto da equipe + texto padrão da Forster + créditos (Samuel e Silvana)
3. **O projeto ou contexto** — específico de cada proposta (o que o cliente faz, o que será produzido)
4. **Como trabalhamos** — etapas verticais numeradas (processo de produção)
5. **Como começamos** — linha do tempo horizontal (passos para fechar e iniciar)
6. **Seção visual** — making of, imagens do projeto ou mosaico de feeds
7. **Planos ou investimento** — cards com valores e o que está incluído
8. **Próximos passos** — CTA principal + contato + link direto para WhatsApp

---

## 2. REGRAS DE COPY

- **Nunca usar travessões** (— ou –). Substituir por vírgula, ponto ou reescrita da frase.
- **Nunca usar a palavra "presença"**. Substituir por: constância, ritmo, posicionamento, visibilidade ou similar.
- **Voz padrão:** "você" (nunca "tu").
- **Tom:** direto, pessoal, como se Samuel e Silvana estivessem explicando pessoalmente.
- Sem jargões de marketing. Sem superlativos desnecessários.
- Frases curtas. Parágrafos de no máximo 3 linhas.
- Evitar palavras como: storytelling, branding, insights, awareness, engagement, target, deadline.
  Ver vocabulário completo em `SynologyDrive-Agencia/CLAUDE.md` (seção Rebranding FORSTER).

---

## 3. PADRÃO VISUAL

Seguir o CSS de `conteudo-recorrente/assets/style.css` como referência canônica.

| Elemento | Valor |
|---|---|
| Fundo escuro | `#1a1a1a` |
| Fundo claro | `#f5f0e8` |
| Cor de destaque | `#f0a500` (dourado Forster) |
| Tipografia títulos | Sora |
| Tipografia corpo | Inter |
| Scroll | livre (sem scroll snap) |
| Altura de seção | `height: 100svh` |

- Seções com conteúdo longo: usar duas colunas ou reduzir fonte para caber em `100svh` sem overflow.
- Fundo escuro e fundo claro devem alternar ao longo da página para criar ritmo visual.
- Fotos de fundo no Hero: sempre com overlay escuro para garantir legibilidade do texto.

---

## 4. ESTRUTURA DE ARQUIVOS

Nova proposta sempre em pasta própria dentro de `forster-propostas/`:

```
forster-propostas/
└── nome-cliente/
    ├── index.html
    └── assets/
        ├── style.css    → copiar de conteudo-recorrente/assets/style.css
        └── img/         → imagens da proposta (hero, making of, equipe, etc.)
```

- O nome da pasta deve ser o slug do cliente: minúsculo, sem acentos, hífens no lugar de espaços.
- Não criar subpastas adicionais dentro de `assets/img/`.
- O `style.css` pode ter ajustes pontuais de cor ou fonte, mas a estrutura base não muda.

---

## 5. META TAGS OBRIGATÓRIAS

Incluir sempre no `<head>` de todo `index.html`:

```html
<meta property="og:title" content="[Título da proposta] — Forster">
<meta property="og:description" content="[Descrição em 1 frase, sem travessão]">
<meta property="og:image" content="https://propostas.forsterfilmes.com/[nome-cliente]/assets/img/[foto].jpg">
<meta property="og:url" content="https://propostas.forsterfilmes.com/[nome-cliente]/">
<meta property="og:type" content="website">
```

- `og:image` deve ser uma foto relevante da proposta ou do cliente.
- Imagem com pelo menos 1200x630px para garantir boa exibição no WhatsApp e Facebook.
- O `og:title` nunca deve usar travessão: usar ponto ou vírgula como separador.

---

## 6. DEPLOY

1. Repositório: sempre dentro de `oiforster` no GitHub (nunca em `silvanasforster` ou `samuelforster`).
2. GitHub Pages ativado na branch `main`, raiz `/`.
3. O CNAME do repositório aponta para `propostas.forsterfilmes.com`.
4. Após o push, raspar a URL no Facebook Sharing Debugger para atualizar o cache:
   `https://developers.facebook.com/tools/debug/`
5. URL pública padrão: `propostas.forsterfilmes.com/nome-cliente/`

---

## 7. CHECKLIST PRÉ-DEPLOY

- [ ] Nenhum travessão (— ou –) em nenhum texto da página
- [ ] A palavra "presença" não aparece em nenhum lugar
- [ ] Meta tags Open Graph completas (`og:title`, `og:description`, `og:image`, `og:url`)
- [ ] `og:image` com pelo menos 1200x630px
- [ ] Scroll snap funcionando em Safari e Chrome
- [ ] Versão mobile revisada (testar em 390px e 430px de largura)
- [ ] Links do WhatsApp funcionando com número correto
- [ ] Commit com mensagem descritiva no padrão `feat: adiciona proposta [nome-cliente]`
- [ ] Push feito para `oiforster/forster-propostas`
- [ ] URL raspada no Facebook Sharing Debugger após o deploy

---

## 8. REFERÊNCIAS INTERNAS

| Recurso | Caminho |
|---|---|
| CSS canônico | `conteudo-recorrente/assets/style.css` |
| Exemplo completo (recorrente) | `conteudo-recorrente/index.html` |
| Exemplo com making of | `movimento/index.html` |
| Exemplo com imóveis | `olimoveis/index.html` |
| Exemplo com feed | `veadrigo/index.html` |
| Vocabulário de marca | `SynologyDrive-Agencia/CLAUDE.md` (seção Rebranding FORSTER) |
