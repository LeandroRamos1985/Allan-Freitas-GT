# Auditoria real — Allan Freitas

**Reteste após substituição:** vídeo anterior e posters removidos; nova cena costeira instalada nos três idiomas. Seleção e limites de pesquisa em `SELECAO-DE-MIDIA.md`. Resultados de navegador e Lighthouse atualizados após a troca.

Data: 15/09/2026. **42 Aprovados · 28 Atenção · 0 Falhou · 2 Não aplicáveis.**

Score estrito: 60.0% dos critérios aplicáveis aprovados. Cobertura de classificação: 72/72. Atenção não equivale a aprovação; o score não é a nota Lighthouse.

**Estado: implementação local entregue; NÃO READY FOR PRODUCTION.** Bloqueadores: gateway de atendimento e LeadPilot reais, domínio/SSL confirmado, aplicação de headers no provedor e revisão de licença/disclosures/política pela imobiliária. Analytics não está conectado. Nenhum envio ao corretor ou CRM foi realizado.

## Evidências

- `evidence/browser-audit.json`: 9 cenários principais, 34 páginas renderizadas (a entrada restante é redirecionamento), zero links internos quebrados e zero erros JavaScript. Quatro mensagens HTTP esperadas: três erros 500 provocados e uma rota 404 deliberada.
- `evidence/responsive-final.json`: 21 verificações, sete larguras × três idiomas, zero overflow; controle mobile não encoberto.
- `evidence/tracking-final.json`: validação de espaços, consentimento, honeypot, UTMs e eventos reais de UI contra servidor de teste. Não certifica serviços externos.
- `evidence/lighthouse-desktop.html/json` e `lighthouse-mobile.html/json`: performance 100/94, acessibilidade 100/100, boas práticas 100/100. SEO da prévia 66/66 em razão do noindex deliberado e ausência de domínio definitivo. LCP desktop ~0,52 s, mobile ~2,93 s; CLS <0,001; TBT 0. INP não medido em campo.
- `evidence/seo-audit.json`: 30 títulos e descrições únicos, canonical/hreflang idempotentes, Schema validado e 27 URLs de sitemap em cópia com domínio fictício de teste. Isso não configura domínio real.
- `evidence/external-links.json` e `reference-rendering.json`: alcance HTTP e renderização das seis referências individuais no Edge. Realtor.com limitou checagem direta com 429; fonte factual consultada pela ferramenta web.
- Capturas de hero/contato nos idiomas e larguras; `portrait-final.png` e `pt-br-390-hero-final.png` mostram os últimos ajustes. Mobile usa viewport emulado, não aparelhos físicos.

- `evidence/video-replacement.json`: seis cenários idioma/dispositivo; arquivo e poster adequados, avanço real de reprodução e pausa/retomada confirmados.

## Correções realizadas

Contraste do monograma decorativo, nomes acessíveis do logo/idiomas, área de toque dos links legais, controle de pausa acima do CTA fixo mobile, envio sem falso sucesso, nome composto apenas por espaços, preservação de UTMs sem dados pessoais em analytics. As falhas encontradas foram corrigidas e retestadas.

## Os 72 itens

| Nº | Critério | Status | Evidência / limite |
|---|---|---|---|
| 1 | CTA principal na primeira dobra | Aprovado | CTAs de compra e avaliação renderizados na primeira dobra; capturas dos três idiomas. |
| 2 | CTAs claros e consistentes | Aprovado | Compra, venda e investimento encaminham ao contato com objetivo selecionado; testes de interação. |
| 3 | CTA fixo no mobile, quando adequado | Aprovado | CTA de contato fixo no mobile; controle de vídeo reposicionado para não ficar encoberto. |
| 4 | Promessa/expectativa de tempo de resposta, quando aplicável | Não aplicável | Nenhum prazo de resposta foi inventado; compromisso não informado pelo titular. |
| 5 | Página de obrigado após conversão | Atenção | Página de obrigado nos três idiomas; fluxo passou com confirmação do servidor local. Entrega real depende do gateway. |
| 6 | Formulários com validação e estados de erro/sucesso | Atenção | Nome vazio, espaços, e-mail inválido, consentimento ausente e HTTP 500 testados. Atendimento online ainda sem endpoint. |
| 7 | Links e URLs amigáveis/personalizados | Aprovado | Rotas estáticas por idioma e comunidades, com caminhos relativos compatíveis com subdiretórios. |
| 8 | Seção de cases/resultados quando houver material autorizado | Aprovado | Três transações anteriores com preços, datas e atribuição à fonte pública; não apresentadas como listings disponíveis. |
| 9 | Avaliações reais e verificáveis | Aprovado | Avaliação verificada de Angela Oliveira identificada por fonte, data e nota, sem texto fabricado. |
| 10 | Mapas, endereço e rotas | Aprovado | Endereço do escritório na fonte Realtor.com; mapa e rotas externos HTTP 200. Sem embed antecipado. |
| 11 | Responsividade completa para celular, tablet e desktop | Aprovado | 21 verificações finais, 320/360/375/390/768/1024/1440 px × três idiomas, sem overflow. |
| 12 | Meta title único por página | Aprovado | 30 títulos únicos nas páginas de conteúdo e utilidade; teste SEO na cópia de configuração. |
| 13 | Meta description única por página | Aprovado | 30 descrições únicas; confirmação automática na auditoria SEO. |
| 14 | H1 único e hierarquia correta de H2/H3 | Aprovado | Um H1 por página de conteúdo; estrutura H2/H3 e zero violações Axe nos cenários principais. |
| 15 | Títulos e conteúdo sem duplicações desnecessárias | Aprovado | Conteúdo específico por idioma, jornada e comunidade; não foram adicionados artigos artificiais. |
| 16 | Alt text contextual nas imagens | Aprovado | Retrato com nome e brokerage no alt; mídia de fundo descrita e elemento decorativo oculto de tecnologia assistiva. |
| 17 | Breadcrumbs quando fizerem sentido | Aprovado | Breadcrumbs nas 18 páginas de comunidades, com links de retorno conferidos. |
| 18 | FAQ + dados estruturados de FAQ somente quando aplicáveis | Aprovado | FAQ visível e respostas específicas nos três idiomas; abertura testada. Nenhum FAQ Schema artificial. |
| 19 | URLs amigáveis | Aprovado | Slugs legíveis e consistentes para idiomas, comunidades e páginas legais. |
| 20 | Canonical tags | Atenção | Canonical correto e idempotente na cópia de teste. Domínio real ainda não confirmado; não aplicado à prévia. |
| 21 | robots.txt | Aprovado | robots da prévia bloqueia rastreamento; script gera regras de produção e sitemap após domínio confirmado. |
| 22 | sitemap.xml | Atenção | Sitemap de 27 URLs validado na cópia de teste. Arquivo de produção exige domínio confirmado. |
| 23 | Página 404 personalizada | Aprovado | 404 personalizada, versões por idioma e retorno útil; rota inexistente respondeu HTTP 404 no teste. |
| 24 | Favicon | Aprovado | Favicon AF em SVG local; referência nos heads e resposta de recurso confirmada. |
| 25 | Open Graph | Atenção | Títulos/descrições OG existentes; URL e imagem absolutas são geradas após domínio. Compartilhamento real pendente. |
| 26 | Imagem adequada para compartilhamento social | Aprovado | Imagem social original 1200×630 JPEG, local, cerca de 34 KB; coerente com marca. |
| 27 | Dados estruturados LocalBusiness ou tipo mais específico aplicável | Atenção | RealEstateAgent JSON válido na cópia de domínio; dados profissionais precisam de revisão e aplicação no domínio final. |
| 28 | Google Search Console configurável após domínio/verificação | Atenção | Projeto preparado para verificação e sitemap; Search Console não configurado, sem acesso à conta/domínio. |
| 29 | Verificação automática de links quebrados | Atenção | Zero links internos quebrados. Maps e Instagram HTTP 200; Realtor.com retornou 429 na checagem direta, embora consulta web factual tenha funcionado. |
| 30 | Indexabilidade das páginas verificada | Atenção | Prévia intencionalmente noindex. Cópia de teste habilita 27 páginas de conteúdo, mantendo obrigado e 404 fora da indexação. Produção pendente. |
| 31 | Compressão e otimização automática de imagens | Aprovado | Retrato convertido de PNG ~1 MB para WebP ~93 KB; ferramenta proporcional de otimização incluída. |
| 32 | Formatos modernos de imagem quando adequados | Aprovado | Retrato e posters WebP, favicon SVG e compartilhamento JPEG conforme função. |
| 33 | Lazy loading | Aprovado | Retrato abaixo da dobra usa lazy loading; vídeo possui preload controlado e arquivo mobile específico. |
| 34 | Teste de PageSpeed/Lighthouse | Aprovado | Lighthouse 13.4.1 real, desktop e mobile: HTML e JSON preservados; resultados locais. |
| 35 | Core Web Vitals | Atenção | CLS ~0,00002 mobile e TBT 0; LCP mobile ~2,78 s no cenário simulado. INP e CWV reais requerem tráfego e domínio publicado. |
| 36 | Otimização de carregamento de fontes, CSS e JavaScript | Aprovado | CSS ~18 KB, JS de interação ~5,5 KB, módulo de envio ~1,1 KB, fontes locais com font-display:swap; sem framework de runtime. |
| 37 | HTTPS/SSL | Atenção | Links externos HTTPS; site não publicado. Certificado e transporte efetivo ainda não verificados. |
| 38 | Headers e configurações básicas de segurança | Atenção | Headers/CSP preparados e revisados. Aplicação real depende do provedor; GitHub Pages não aplica _headers. |
| 39 | Proteção anti-spam/bot nos formulários | Atenção | Honeypot bloqueou submissão no teste. Rate limit, validação server-side e defesa contra bots dependem do gateway. |
| 40 | Tratamento seguro dos dados enviados | Atenção | Sem tokens no front-end, dados não entram em analytics/storage, gateway HTTPS obrigatório para host remoto. Tratamento CRM server-side ainda pendente. |
| 41 | Política de Privacidade | Atenção | Política nos três idiomas; revisão jurídica, fornecedores e retenção reais ainda necessários. |
| 42 | Cookies/consentimento quando juridicamente necessário | Aprovado | Analytics opcionais condicionados ao consentimento, preferências de privacidade e recusa testadas; sem pixels ativos na prévia. |
| 43 | Dados empresariais/profissionais no rodapé | Atenção | Nome, brokerage, endereço e número de licença da fonte exibidos. Jurisdição, vigência e disclosures dependem da imobiliária. |
| 44 | Google Analytics ou solução equivalente | Atenção | Campo GA4 configurável; não há ID ou conta de recebimento fornecidos. Não se afirma mensuração ativa. |
| 45 | Eventos de conversão configurados | Atenção | Eventos locais de CTA, telefone, e-mail, link externo e formulário definidos. Recepção em GA4 pendente. |
| 46 | Cliques em WhatsApp monitoráveis | Não aplicável | WhatsApp não anunciado: disponibilidade desse canal não comprovada. |
| 47 | Envios de formulário monitoráveis | Atenção | Evento de sucesso capturado após aceite explícito do servidor local; nenhuma entrega real ao CRM validada. |
| 48 | Origem/campanha do lead preservada quando possível | Aprovado | UTMs whitelisted preservadas no payload real do teste; parâmetros pessoais ignorados. Sem persistência entre sessões. |
| 49 | Integração com CRM do LeadPilot | Atenção | Payload e gateway preparados. Credenciais, documentação e endpoint do LeadPilot ausentes; integração ativa não validada. |
| 50 | Teste real dos eventos antes da publicação | Atenção | Eventos e payloads exercitados em navegador; GA4/LeadPilot end-to-end ainda não testados. |
| 51 | Logo e identidade visual | Aprovado | Wordmark Allan Freitas / Real Estate, monograma AF e paleta grafite, marfim e vinho consistentes. |
| 52 | Informações reais do negócio | Aprovado | Identidade, canais e especialidades cruzados com fonte pública e capturas enviadas; números agregados divergentes omitidos. |
| 53 | Telefone/WhatsApp conferidos | Aprovado | Telefone +14016395163 coincide com capturas e Realtor.com; links tel corretos. WhatsApp omitido. |
| 54 | Endereço e horários conferidos | Atenção | Endereço conferido na fonte pública; horários não fornecidos e não inventados. Confirmação operacional com titular pendente. |
| 55 | Serviços/especialidades conferidos | Aprovado | Compra, venda, investimento, residencial e multifamiliar alinhados às especialidades publicadas. |
| 56 | Fotos reais autorizadas | Aprovado | Vídeo Pexels licenciado; retrato fornecido preservado e comprimido. Licenças documentadas; divulgação final pelo titular indicada. |
| 57 | Informações da equipe/profissionais conferidas | Aprovado | Nome, retrato e brokerage conferidos em material enviado e fonte profissional; sem equipe fictícia. |
| 58 | Avaliações reais sem fabricação por IA | Aprovado | Nenhum depoimento fabricado; referência à avaliação original verificada, sem Review Schema. |
| 59 | Conteúdo adaptado ao segmento e localização | Aprovado | Conteúdo sobre South Coast, MA/RI, compradores, vendedores e investidores, com três versões editoriais. |
| 60 | Revisão de informações sensíveis ou regulamentadas | Atenção | Licença reproduzida da fonte; sem consulta regulatória de vigência. Disclosures e documentos legais precisam de revisão profissional. |
| 61 | Teste desktop | Aprovado | Edge real renderizou as páginas; cenário 1440 px, capturas e testes funcionais preservados. |
| 62 | Teste mobile | Aprovado | Edge real com viewport mobile 390 px e verificações adicionais 320–375; não é teste em aparelho físico. |
| 63 | Teste de todos os formulários | Atenção | Cada versão do formulário: validação, erros, confirmação local, obrigado, UTMs e honeypot testados. Entrega ao titular/CRM ainda pendente. |
| 64 | Teste de todos os CTAs | Aprovado | Links de navegação, jornadas, avaliação, comunidade, idioma e contato validados; zero links internos quebrados. |
| 65 | Teste dos links externos | Atenção | HTTP externo executado; Maps e Instagram 200, Realtor.com com rate limit 429 na checagem direta. Acesso protegido não certificado. |
| 66 | Teste de WhatsApp, telefone e e-mail | Atenção | tel e mailto corretos conforme material enviado; evento de clique em e-mail testado. Sem ligação ou e-mail enviados; recebimento não certificado. |
| 67 | Auditoria SEO | Aprovado | 30 páginas com metadados únicos; canonical/hreflang/schema/sitemap validados em fixture. Noindex da prévia documentado. |
| 68 | Auditoria de acessibilidade básica | Aprovado | Zero violações Axe nas nove combinações principais; reteste mobile inclui WCAG 2.2. Lighthouse acessibilidade 100/100. Foco, menu, labels e controle de movimento testados. |
| 69 | Auditoria de performance | Aprovado | Lighthouse real: performance 100 desktop / 94 mobile, boas práticas 100 em ambos. Relatórios e peso registrados; resultados locais, sem pontuação de campo. |
| 70 | Auditoria de segurança | Atenção | Código e configuração revisados: sem segredos/eval/HTML dinâmico de lead; gateway restrito e CSP preparado. Backend e headers publicados não auditados. |
| 71 | Verificação de domínio/SSL | Atenção | Domínio, propriedade, redirects e SSL não fornecidos/verificados. Nenhum domínio sugerido foi assumido. |
| 72 | Site Quality Score final | Aprovado | Todos os 72 itens classificados com evidências, correções e bloqueadores; pacote não recebe READY FOR PRODUCTION. |
