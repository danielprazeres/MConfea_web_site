# Landing de campanha: `ar-condicionado.html`

Página de destino dos anúncios Google Ads de instalação de ar condicionado (agência Saltypuzzle).
URL: `https://mconfea.com/ar-condicionado.html`. É uma página à parte: o site principal mantém-se.

## Checklist antes de ativar os anúncios

1. **Prova social.** A secção de testemunhos foi removida por não haver testemunhos reais. Quando existirem
   avaliações (idealmente no Perfil de Empresa do Google), inserir uma secção entre "Porquê nós" e o FAQ,
   com nome e localidade reais.
2. **Fotografias.** A página não usa fotos de pessoas. Se o cliente enviar fotos de instalações suas,
   a secção "Quem somos" ganha uma coluna de imagem ao lado do cartão de credenciais.
3. **Formulários.** O envio usa o FormSubmit sem backend. Está pendente a ativação: foi enviado um email
   para `geral@mconfea.com` com o link "Activate Form"; enquanto não for clicado, o formulário mostra erro
   e oferece WhatsApp e telefone. Depois de ativado, trocar o email pelo alias que o FormSubmit atribui,
   no `action` dos dois formulários e na constante `ENDPOINT` do JavaScript.
4. **Medição.** A agência cola o snippet do GTM (ou gtag.js) no sítio marcado no `<head>`, a seguir ao bloco
   de Consent Mode, e passa `CONSENT_BANNER` a `true` no JavaScript.
5. **Pré-visualização.** Passar `PREVIEW` a `false` no JavaScript (remove a etiqueta de pré-visualização).
6. **Dados legais.** Falta a entidade de resolução alternativa de litígios (RAL) da zona e, para cumprir o
   artigo 171.º do Código das Sociedades Comerciais, a conservatória do registo comercial, o número de
   matrícula e o capital social. O rodapé já tem firma, NIPC e sede.
7. **Certificação.** O selo usado é o CERTIF que o cliente forneceu; a arte indica "serviço certificado"
   ao abrigo do Dec.-Lei 145/2017 e do Reg. (UE) 2015/2067. O texto visível diz "Empresa certificada ·
   Certificação CERTIF", como o cliente pediu. Confirmar o âmbito exato e o número do certificado se se
   quiser exibi-lo.
8. **Indexação.** A página está em `noindex`. Para a indexar organicamente, trocar para `index, follow`
   e acrescentá-la ao `sitemap.xml`.

## Preço confirmado pelo cliente (2026-09-17)

Visita técnica com orçamento **a partir de 30 €, IVA incluído**, valor **descontado na instalação** se o
cliente avançar. Está escrito assim em todas as menções, incluindo meta tags.

## Eventos publicados no dataLayer

Todos incluem `zona` (`geral` ou o nome do concelho).

| Evento | Quando | Campos |
| --- | --- | --- |
| `generate_lead` | envio do formulário confirmado pelo servidor | `form_id` (`hero`/`completo`), `localidade`, `divisoes` |
| `whatsapp_click` | clique em qualquer botão WhatsApp | `location` |
| `phone_click` | clique em qualquer botão de chamada | `location` |
| `quote_scroll_click` | clique num CTA que leva ao formulário | `location` |
| `lead_form_error` | falha no envio | `form_id`, `message` |
| `faq_open` | abertura de uma pergunta | `question` |

Recomendação: usar `generate_lead` como acionador de conversão, não o URL. O email do lead inclui
`gclid`/`gbraid`/`wbraid`, parâmetros `utm_*`, `zona`, `form_id`, página e data.

## Message match por concelho

`?zona=<slug>` troca a localidade no H1, no título e no pré-preenchimento do formulário. Os slugs aceites
são os 19 concelhos do distrito de Aveiro, em minúsculas e sem acentos (por exemplo
`?zona=oliveira-de-azemeis`). Um slug desconhecido é ignorado e a página fica na versão genérica.
