# CLAUDE.md — forster-propostas
Leitura obrigatória antes de qualquer tarefa neste repositório.

## O que é esse repositório
Páginas de proposta comercial da Forster, publicadas em `propostas.forsterfilmes.com`.
Cada pasta é uma proposta independente. O padrão completo está em `PROPOSTA.md`.

---

## Regras que se aplicam sempre, sem precisar pedir

### Assets — nunca subir arquivos pesados sem otimizar

Antes de qualquer commit com imagens ou vídeo:

| Tipo | Formato obrigatório | Tamanho máximo | Comando |
|---|---|---|---|
| Foto / hero | JPG | 600 KB | `ffmpeg -i foto.png -q:v 4 foto.jpg` |
| Vídeo autoplay | MP4 H.264, sem áudio, faststart | 15 MB | `ffmpeg -i v.mov -c:v libx264 -crf 26 -preset medium -an -movflags +faststart v.mp4` |
| Thumbnail de reel | JPG local (não microlink em produção) | 100 KB | `curl -sL "https://api.microlink.io/?url=URL_ENCODED&embed=image.url" -o thumb.jpg` |

- Nunca commitar `.mov`, `.png` de hero ou qualquer vídeo acima de 15 MB.
- Sempre converter PNG de fundo para JPG antes do primeiro commit.
- Thumbnails de portfólio: baixar localmente via microlink, salvar em `assets/img/`, nunca usar a URL da API como `src` em produção.

### Referências de assets entre propostas

- Assets compartilhados ficam em `conteudo-recorrente/assets/img/`.
- Novas propostas referenciam via path relativo: `../conteudo-recorrente/assets/img/`.
- Não duplicar `tela-inicial.jpg`, `video-reel.mp4` ou `forster-equipe.jpg`.

### Deploy

- Repositório: sempre `oiforster/forster-propostas`. Nunca em conta pessoal.
- Após push com novos assets pesados (vídeo, imagens), avisar o Samuel para raspar no Facebook Sharing Debugger se a proposta já tiver sido compartilhada.
- URL pública: `propostas.forsterfilmes.com/[nome-pasta]/`

### Copy — regras inegociáveis

- Sem travessões (— ou –). Usar vírgula, ponto ou reescrever.
- Sem a palavra "presença". Substituir por: constância, ritmo, posicionamento, visibilidade.
- Voz: "você" (nunca "tu").
- Tom: direto, pessoal, sem jargão de marketing.

### Ano

- Verificar se o ano no badge e no `<title>` está atualizado antes de qualquer deploy.
- Atualmente: **2026**.

---

## Onde está o padrão completo

- Estrutura de seções, CSS, meta tags, checklist pré-deploy: `PROPOSTA.md`
- Padrão de sessão avulsa: `PROPOSTA.md` seção 9
- Padrão de performance: `PROPOSTA.md` seção 10
