# Giulia Palinka Tattoo

Landing page da tatuadora Giulia Palinka: estilos de trabalho, portfólio, avaliações do Google, "Quem sou" e formulário de orçamento que abre o WhatsApp com a mensagem pronta.

É um site estático: um `index.html` e a pasta `assets/` com as fotos. Não precisa de build nem de instalação. As fontes vêm do Google Fonts.

## Testar no computador

Abra o `index.html` no navegador (dois cliques no arquivo).

## Publicar

Funciona em qualquer hospedagem de site estático. Envie o `index.html`, o `favicon.png` e a pasta `assets/` juntos, mantendo a estrutura.

- **GitHub Pages:** suba os arquivos num repositório e ative em Settings → Pages → *Deploy from a branch* → `main` / `(root)`.
- **Netlify:** arraste a pasta inteira em app.netlify.com/drop.
- **Hostinger, Locaweb e similares:** envie os arquivos para a pasta `public_html`.

## Onde editar

No fim do `index.html`, dentro do `<script>`, o objeto `site` guarda o conteúdo que muda com frequência:

- `estilos`: os 4 cards do carrossel "Estilos de trabalho" (título, texto e foto).
- `portfolio`: as fotos de "Trabalhos recentes", na ordem em que aparecem. Para trocar ou acrescentar, coloque a foto em `assets/` e adicione `{ src: "assets/nome.webp", alt: "descrição" }`.
- `avaliacoes`: avaliações do Google (nome, tempo, texto), da mais recente para a mais antiga.
- `whatsappBase` e `mensagemWhatsApp`: número e mensagem inicial do formulário.
- `webhook`: endereço do webhook do Make que recebe os orçamentos.
- `locais`, `tamanhos`, `estilosForm`, `investimentos`: opções das caixas de seleção do formulário.

Ficam direto no HTML: textos do banner e do "Quem sou", a nota do Google (5,0 e 29 avaliações) e os links do Instagram e do perfil no Google.

## Formulário de orçamento

Todos os campos são obrigatórios. Ao enviar, o formulário:

1. Manda os dados para o webhook do Make (`webhook` no objeto `site`), cada informação num campo separado: `nome`, `whatsapp`, `whatsapp_numero` (com 55), `local_do_corpo`, `tamanho`, `estilo`, `orcamento`, `ideia`, `data_envio` (padrão brasileiro, horário de Brasília: `22/10/2026 16:54:12`) e `pagina`.
2. Em seguida, leva a pessoa direto para o WhatsApp da Giulia com a mensagem do orçamento já escrita.

No Make, use "Redetermine data structure" no módulo do webhook e envie um orçamento de teste pelo site publicado para o Make reconhecer os campos. O envio só funciona com o site publicado numa hospedagem; abrindo o arquivo direto do computador, alguns navegadores podem bloquear.

## Fotos

- `favicon.png` e `apple-touch-icon.png`: ícone do site com a foto da Giulia
- `assets/banner.webp`: foto do banner
- `assets/quem-sou.webp`: foto do "Quem sou"
- `assets/estilo-*.webp`: fotos do carrossel de estilos
- `assets/portfolio-01.webp` a `portfolio-14.webp`: fotos do portfólio

Cada foto do portfólio e dos estilos tem uma versão menor com `-480` no nome (por exemplo `portfolio-01-480.webp`), e o banner e o "Quem sou" têm `banner-800.webp` e `quem-sou-720.webp`. O celular carrega a versão menor e o computador a maior. Ao trocar uma foto, troque as duas versões.

## Desempenho

- As fontes do Google carregam sem bloquear a abertura da página.
- `_headers` (Netlify e Cloudflare Pages) e `vercel.json` (Vercel) mandam o navegador guardar as fotos em cache por 1 ano. Por isso, ao trocar uma foto, use um nome de arquivo novo (por exemplo `portfolio-15.webp`) em vez de substituir o arquivo com o mesmo nome. No GitHub Pages esses arquivos não têm efeito.
