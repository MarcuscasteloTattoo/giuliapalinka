# Giulia Palinka Tattoo

Landing page da tatuadora Giulia Palinka. Tem banner, estilos de trabalho, portfólio, avaliações do Google, "Quem sou" e um formulário de orçamento que abre o WhatsApp com a mensagem já escrita.

O layout, as cores, as fontes e o funcionamento são os mesmos do site da Victoria Hatab. As fotos, as avaliações, os contatos e o Pixel eram da Victoria e foram retirados. Enquanto não houver fotos, aparecem desenhos em traço fino com a etiqueta "Foto a adicionar".

É um site estático: um `index.html`, os ícones e a pasta `assets/` (crie a pasta quando tiver as fotos). Não precisa de build. Para testar, abra o `index.html` no navegador.

## Antes de publicar: preencha o objeto `site`

O objeto `site` fica no fim do `index.html`, dentro do `<script>`.

| Campo | O que colocar |
|---|---|
| `whatsapp` | Número da Giulia só com dígitos: 55 + DDD + número. Exemplo: `"5511999999999"`. O formulário só funciona depois que este campo estiver preenchido. |
| `instagram` | Usuário sem o @. O link aparece no "Quem sou" e no rodapé. |
| `webhook` | Endereço do webhook do Make, se for registrar os orçamentos. Vazio = não envia. |
| `fotoQuemSou` | Exemplo: `"assets/quem-sou.webp"` |
| `estilos[].imagem` | Uma foto para cada card do carrossel. Exemplo: `"assets/estilo-pets.webp"` |
| `portfolio` | `{ src: "assets/portfolio-01.webp", alt: "descrição da tatuagem" }`. Inclua quantas fotos quiser. |
| `avaliacoes` | Avaliações reais do Google: `{ nome, tempo, texto }`. A seção só aparece quando esta lista tiver pelo menos uma avaliação. |
| `google` | `{ nota: "5,0", total: 12, link: "https://..." }`: nota, total e link do perfil no Google. |
| `locais`, `tamanhos`, `estilosForm`, `investimentos` | Opções das caixas de seleção do formulário. |

Os textos que ficam direto no HTML são o banner e os dois parágrafos do "Quem sou". O texto do "Quem sou" é genérico e deve ser trocado pela história da Giulia.

### Foto no banner

Hoje o banner tem um desenho no lugar da foto. Para usar uma foto, siga o comentário no topo do `<header class="hero">`: troque o `<svg class="hero-art">` por um `<img>` e tire a classe `no-photo`.

### Meta Pixel

Se for usar anúncios, cole o código do Pixel da Giulia no lugar do comentário "Meta Pixel" dentro do `<head>`. Com o Pixel instalado, o envio do formulário é registrado como Lead automaticamente.

## Publicar

Funciona em qualquer hospedagem de site estático: Netlify (arraste a pasta em app.netlify.com/drop), Vercel, GitHub Pages, Hostinger etc. Envie tudo mantendo a estrutura de pastas.

O `_headers` (Netlify/Cloudflare) e o `vercel.json` (Vercel) guardam as fotos em cache por 1 ano. Por isso, para trocar uma foto, use um nome de arquivo novo.

## Testar o formulário

Abra o site com `?teste` no fim do endereço. Cada etapa do envio aparece na tela e o site não redireciona sozinho para o WhatsApp.
