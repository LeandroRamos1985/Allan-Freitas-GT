# Allan Freitas — pacote final de implementação

**Vídeo substituído e retestado:** cena costeira de Cape Cod, com versões desktop/mobile. Pesquisa de reutilização, comparação e licença em `SELECAO-DE-MIDIA.md`; regra para próximos projetos em `ATUALIZACAO-BRIEFING.md`.

Site estático em inglês, português brasileiro e espanhol. Abra `site/index.html` ou sirva a pasta `site/` por HTTP. Vídeo, retrato fornecido, fontes e imagem de compartilhamento estão locais. Não exige instalação para publicar os arquivos estáticos.

## Publicação

O pacote é uma prévia local, com indexação bloqueada para não atribuir um domínio sem confirmação. Depois de confirmar domínio e caminho de hospedagem, execute `python tools/configure-domain.py https://DOMINIO-CONFIRMADO` em uma cópia. O script gera canonical, hreflang, Schema RealEstateAgent, Open Graph absoluto, robots e sitemap. Para GitHub Pages de projeto, inclua `/nome-do-repositorio` na URL. Publique somente o conteúdo de `site/`. Configure 404 conforme o provedor.

## Atendimento e LeadPilot

`site/assets/config.js` contém `leadEndpoint`, `analyticsId` e `siteUrl`. Sem endpoint, o visitante vê a situação real e um botão para ligar. O formulário não finge envio. O e-mail e o Instagram vêm do material fornecido pelo usuário. WhatsApp não foi anunciado porque sua disponibilidade não foi comprovada.

O endpoint deve ser um gateway próprio HTTPS, autorizado pela imobiliária. Não coloque tokens CRM no navegador. Recebe POST JSON com `name`, `email`, `phone`, `goal` (buy/sell/invest), `region`, `message`, `consent`, `language`, `source`, `campaign` e `consentVersion`. Deve responder `{"success":true}` apenas após aceitar a solicitação para entrega. Erros HTTP, JSON ambíguo, redirecionamentos e timeout não geram obrigado nem evento de conversão. Server-side: validar tamanho/dados, honeypot, rate limit e origem/CORS; encaminhar ao LeadPilot com credenciais privadas e registrar resultado. Documentação/credenciais do LeadPilot não foram fornecidas; não se afirma integração ativa.

Depois de definir o gateway, adicione sua origem a `connect-src` em `_headers` e ao provedor efetivo. `_headers` funciona nos provedores compatíveis; GitHub Pages não aplica esse arquivo. Em produção, configure CSP e demais headers no provedor. JSON-LD é um bloco de dados, não código executável. HTTPS, certificado, redirecionamentos e headers reais exigem teste na hospedagem escolhida.

## Analytics e privacidade

GA4 só carrega se houver ID válido e consentimento. Eventos locais de CTA, telefone, links, controle de vídeo, sucesso e erro podem ser inspecionados em `window.dataLayer`. Não levam nome, e-mail, telefone, endereço ou mensagem. UTMs/gclid/fbclid são limitados a 200 caracteres e acompanham o lead da navegação atual; não há persistência de identificadores de campanha entre sessões. Preferência de analytics fica no armazenamento local; revogação recarrega o site. O titular deve definir provedores, retenção e política jurídica final antes de publicação.

## Conteúdo e aprovação profissional

Telefone principal: (401) 639-5163. Escritório: 670 Depot Street, Suite 1, North Easton, MA 02356. Licença reproduzida conforme perfil Realtor.com, sem presumir jurisdição ou verificação governamental. Horários e prazo de resposta não foram inventados. Transações são identificadas como anteriores, sem atribuir exclusivamente a Allan todos os resultados. Imóvel em Freetown requer reconfirmação de disponibilidade. Não há IDX/MLS instalado nem promessa de busca em tempo real.

Consulte `AUDITORIA-72.md`, `FONTES-E-LICENCAS.md` e `evidence/`. O pacote não recebe READY FOR PRODUCTION enquanto atendimento real, domínio e divulgações profissionais estiverem pendentes.

## Repetir QA (opcional)

O site não depende de npm. Para repetir os testes, instale os devDependencies de `package.json` com npm/pnpm e o Chromium do Playwright se não houver Edge no Windows. Execute `npm test`, depois `npm run preview` e, em outro terminal, `npm run audit`, `npm run tracking` e `npm run lighthouse`. Os testes de entrega usam dados sintéticos no servidor local, sem enviar mensagens a Allan ou ao CRM. O QA sobrescreve os relatórios em `evidence/`. Antes de repetir, preserve as evidências desta entrega. `tools/optimize-image.cjs` faz compressão WebP proporcional.
