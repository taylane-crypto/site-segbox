# Site Segbox

Site institucional da Segbox (tecnologia e white label para o mercado de seguros).

Prévia ao vivo: https://taylane-crypto.github.io/site-segbox/

O site é estático: só HTML, CSS, JavaScript e imagens. Não precisa instalar nada, não tem build e não tem dependências. Funciona em qualquer hospedagem de arquivos estáticos, como servidor próprio, Netlify, Vercel, Cloudflare Pages, S3 ou GitHub Pages.

## Como publicar

1. Baixe o repositório (Code → Download ZIP) ou clone com `git clone https://github.com/taylane-crypto/site-segbox.git`.
2. Suba **todo o conteúdo da pasta** para a raiz do domínio, mantendo a estrutura de pastas.
3. A home é o `index.html`. As outras páginas linkam umas às outras por caminho relativo (`sobre.html`, `produto-segzap.html` etc.), então tudo funciona em qualquer domínio ou subpasta.
4. O arquivo `.nojekyll` só serve para o GitHub Pages e pode ser ignorado em outra hospedagem.

Se quiser endereços sem `.html` (ex.: `/sobre`), configure isso na hospedagem. Na Netlify e na Vercel, a opção se chama "pretty URLs" ou "clean URLs".

## Estrutura

| Arquivo | Página |
|---|---|
| `index.html` | Home |
| `sobre.html` | Sobre a Segbox |
| `produto-segzap.html` | SegZap |
| `produto-segzap-whitelabel.html` | SegZap White Label |
| `produto-otimize.html` | Otimize |
| `produto-otimize-whitelabel.html` | Otimize White Label |
| `produto-corretorpro.html` | CorretorPRO |
| `produto-leadsgo.html` | LeadsGO! |
| `projetos-sob-medida.html` | Projetos sob medida |
| `case-mapfre.html` | Case MAPFRE +Digital |
| `case-suhai.html` | Case Venda+ Suhai |
| `case-suhai-academy-v2.html` | Case Consultor Suhai |
| `case-baeta.html` | Case BaetaPRO |
| `termos-de-uso.html`, `politica-de-privacidade.html`, `politica-anti-spam.html`, `politica-de-pagamento.html`, `seguranca-da-informacao.html` | Páginas legais (rodapé) |
| `design-system.html` | Design system do site (referência interna, não está no menu) |
| `assets/` | Imagens, cubos 3D, fotos, logos e favicons |
| `favicon.ico` | Ícone da aba |

Cada página traz o próprio CSS e JS dentro do HTML. Não há arquivos .css ou .js separados.

## Antes de colocar no ar (pendências)

### 1. Formulários: hoje NÃO enviam dados
Os formulários de contato validam os campos, mas não mandam os dados para lugar nenhum. Ao enviar, aparecem o texto "Enviando" e depois a mensagem "Prévia: o formulário não envia dados de verdade."

Onde estão:
- `index.html`, `case-mapfre.html`, `case-suhai.html`, `case-suhai-academy-v2.html`, `case-baeta.html`, `produto-segzap-whitelabel.html`: formulário `#leadForm`
- `produto-otimize.html`: `#leadForm` (agendar demonstração)
- `produto-otimize-whitelabel.html`: `#owForm`

O que fazer: em cada página, procure o `addEventListener('submit'` do formulário. Troque o `setTimeout` que mostra a mensagem de prévia por um envio real (`fetch` para o CRM, RD Station, HubSpot, Formspree ou o endpoint que a Segbox usar). Depois troque a mensagem final por uma confirmação de verdade.

Os campos são nome, sobrenome, e-mail e os demais do formulário. As páginas SegZap, CorretorPRO e LeadsGO! não têm formulário: os botões levam direto para o cadastro de cada plataforma.

### 2. Fonte GT Standard: arquivo ausente
As páginas carregam `fonts/GT-Standard-Medium.woff2`, mas esse arquivo não está no repositório porque é uma fonte licenciada. Sem ele, o navegador usa uma fonte de substituição e os títulos ficam diferentes do design.

O que fazer: se a Segbox tem a licença, crie a pasta `fonts/` na raiz e coloque o `GT-Standard-Medium.woff2` dentro.

### 3. Conteúdo a validar
- Os cases da Suhai, da MAPFRE e da Baeta têm números marcados como **"a confirmar"**. Valide com cada cliente antes de divulgar.
- Confirme se a Baeta aprovou aparecer como case.
- O botão "Falar com a gente" do plano Enterprise do SegZap ainda não aponta para nenhum canal de contato.
- `design-system.html` é uma referência interna. Se não deve ficar público, não suba esse arquivo.

## Links externos usados no site

- SegZap: https://app.segzap.com.br/register
- Otimize (teste): https://app.otimize.online/cadastro
- CorretorPRO: https://app.corretorpro.online/cadastro
- INSUMMIT: https://insummit.online/
- Redes: LinkedIn https://www.linkedin.com/company/segbox · Instagram https://www.instagram.com/segbox/ · YouTube https://www.youtube.com/@segbox-oficial

## Sobre este repositório

Este repositório guarda a **versão pronta para publicar**. Os arquivos-fonte ficam com a Taylane, e as atualizações dela chegam aqui substituindo as páginas e a pasta `assets/`.

Se a equipe for editar os arquivos direto aqui, combine com ela antes, para que uma atualização não sobrescreva a outra.
