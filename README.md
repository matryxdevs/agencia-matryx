# MATRIX — Landing page de serviços

Site institucional de conversão, em HTML, CSS e JavaScript puros, pronto para abrir no Visual Studio Code e publicar em hospedagem estática.

## Arquivos

- `index.html`: conteúdo, serviços, formulário, links e SEO.
- `styles.css`: layout responsivo, visual estilo terminal/hacker e animações.
- `script.js`: validação do formulário, montagem de mensagem para WhatsApp e efeito Matrix.
- `assets/foto-perfil.svg`: imagem provisória para ser substituída por sua foto.
- `assets/favicon.svg`: ícone da marca.
- `_headers`: cabeçalhos de segurança para Netlify e Cloudflare Pages (compatível com hosts que usam esse formato).
- `.htaccess`: cabeçalhos de segurança e bloqueio de listagem para servidores Apache, como alguns planos da Hostinger.
- `404.html`: página para URL não encontrada.
- `robots.txt`: instruções de indexação.

## Como abrir no VS Code

1. Extraia o ZIP e abra **a pasta inteira** no VS Code.
2. Instale a extensão **Live Server** (opcional) e abra o `index.html` com o Live Server, ou abra o `index.html` diretamente no navegador.
3. Para publicar, envie os arquivos **mantendo a estrutura de pastas** para `public_html` (Hostinger/Apache) ou publique a pasta em Netlify/Cloudflare Pages.
4. Configure o domínio e **HTTPS válido** na hospedagem; idealmente habilite redirecionamento HTTP → HTTPS pelo painel do provedor.

## Onde colocar sua foto

Quando tiver a foto, salve a imagem como `assets/foto-hiago.webp` (recomendado: 560 x 640 px, WebP otimizado; 300 KB ou menos, se possível). No `index.html`, procure por:

```html
<img src="./assets/foto-perfil.svg"
```

Troque por:

```html
<img src="./assets/foto-hiago.webp"
```

Mantenha os outros atributos e atualize o texto alternativo (`alt`) para identificar corretamente a foto. Se você enviar a imagem no chat, a integração pode ser feita diretamente no projeto.

## Contatos configurados

- WhatsApp: `+55 94 98405-6659` (código de destino `5594984056659`).
- Instagram: `https://www.instagram.com/hiagonelvilli/`.
- E-mail: `hiagooslv4@gmail.com`.

## Como funciona o formulário

Solicita nome, telefone e serviço. Após validar e obter a confirmação do visitante, prepara uma mensagem endereçada ao WhatsApp da MATRIX. **Não há backend ou armazenamento de dados**, e o visitante ainda precisa confirmar o envio no WhatsApp.

A página NÃO salva automaticamente contatos em CRM, banco de dados ou planilha; isso exige uma integração posterior com backend/API segura. Não cole chaves privadas, senhas, tokens de WhatsApp ou credenciais de CRM no código da página.

## Segurança: o que já foi implementado

- Código estático, sem formulários enviados ao servidor e sem dependências de terceiros.
- Validação de entradas antes de gerar o link; uso de `encodeURIComponent` e destino de WhatsApp fixo.
- Nenhum uso de `innerHTML`, `eval` ou execução dinâmica de entrada fornecida pelo visitante.
- Política de Segurança de Conteúdo (CSP), proteção contra *clickjacking*, `nosniff`, política de referenciador, restrições de permissões e HSTS via configurações de servidor.
- Links externos com `rel="noopener noreferrer"`.
- Limitação de movimento para visitantes com preferência por reduzir animações.

**Importante:** nenhum website é invulnerável. Os cabeçalhos em `_headers` e `.htaccess` só têm efeito se o servidor de hospedagem os aplicar. O HSTS deve ser usado somente com HTTPS em funcionamento. Use senhas fortes e MFA no painel, atualizações do servidor, backups, WAF e permissões de arquivos apropriadas. A segurança do domínio e da hospedagem precisa ser configurada fora do código.

## Privacidade e boas práticas

O formulário inclui autorização explícita para encaminhar dados pelo WhatsApp, e a página tem um aviso de privacidade. Para campanhas de mensagens em massa, é necessário usar contatos com base legal adequada, respeitar a LGPD, oferecer opt-out quando pertinente e seguir as políticas da plataforma utilizada. Não compre bases de contatos e não envie mensagens não autorizadas.

## O que personalizar antes de publicar

- Substituir foto provisória.
- Conferir textos comerciais (promessas, condições e escopo dos serviços).
- Se incluir rastreamento, instalar somente scripts confiáveis, ajustar CSP e providenciar as informações e controles de privacidade adequados.
- Adicionar política de privacidade completa se a operação passar a usar coleta, pixels, cookies ou backend.
- Confirmar se o servidor está entregando os cabeçalhos de segurança (por exemplo, no DevTools > Network > Response Headers).
