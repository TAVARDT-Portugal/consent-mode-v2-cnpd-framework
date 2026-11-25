# Framework Consent Mode v2 & Conformidade Técnica RGPD

[![Diagnóstico Técnico](https://img.shields.io/badge/TAVARDT-Diagn%C3%B3stico%20T%C3%A9cnico-5b3cf5.svg)](https://tools.tavardt.com/pt/validador-consent-mode-v2-rgpd/)
[![JavaScript](https://img.shields.io/badge/JavaScript-Node.js-yellow.svg)](https://nodejs.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

***

Implementação técnica do Google Consent Mode v2, bloqueio prévio de scripts de rastreamento e conformidade regulatória desenvolvida pela **TAVARDT**, em estrito alinhamento com as orientações da CNPD e o RGPD da União Europeia.

Para garantir a conformidade estrita com a legislação de privacidade, insira o script de inicialização no `<head>` do documento antes de carregar o Google Tag Manager. A execução precoce estabelece o estado padrão negado antes que qualquer pixel de medição grave cookies ou capture identificadores.

***

## Capacidades Centrais e Arquitetura Defensiva

* **Estado Padrão Negado (Default Denied)**: Define de imediato `ad_storage`, `ad_user_data`, `ad_personalization` e `analytics_storage` como negados antes da carga de scripts.
* **API de Atualização Orientada a Eventos**: Disponibiliza a função global `window.tavardtUpdateConsent` para sincronizar escolhas de qualquer CMP diretamente no `dataLayer`.
* **Redação Automática de Parâmetros de Anúncios**: Ativa `ads_data_redaction` para suprimir identificadores como GCLID das requisições quando não houver consentimento.
* **Preservação de Tráfego sem Cookies**: Habilita `url_passthrough` para garantir atribuição anônima de conversões entre páginas sem persistência local no dispositivo.
* **Zero Sobrecarga de Dependências**: Desenvolvido em JavaScript puro (`consent-mode-v2.js`), operando com execução inferior a 1 milissegundo.

***

## Vetores de Risco e Impacto Operacional

Publicar etiquetas de marketing e analytics sem bloqueio prévio de consentimento expõe empresas a multas regulatórias e falhas de mensuração. O framework mitiga quatro riscos críticos:

* **Disparo Indevido de Tags sem Consentimento**: Scripts de mídia gravando cookies antes da autorização do usuário, gerando infrações diretas à lei de privacidade.
* **Perda de Modelagem e Dados de Conversão**: Ausência dos sinais do Consent Mode v2, resultando em bloqueio de campanhas no Google Ads e GA4.
* **Vazamento de Identificadores de Clique**: Tráfego de parâmetros de rastreamento em requisições de rede sem respaldo de consentimento prévio.
* **Condições de Corrida no Sequenciamento de Tags**: Tags analíticas disparando antes que a CMP consiga registrar o estado do usuário.

***

## Guia de Implementação e Integração

Insira o script no ponto mais alto do `<head>` da aplicação antes do carregamento de qualquer container de tags:

```html
<script src="consent-mode-v2.js"></script>
```

### Script Execution Snippet

```javascript
// Programmatic consent update triggered by CMP callback
window.tavardtUpdateConsent({
    marketing: true,
    analytics: true,
    preferences: false
});
```

***

## Perguntas Técnicas Frequentes

### Quais parâmetros específicos de consentimento o Google Consent Mode v2 exige para conformidade?

O Consent Mode v2 adiciona os parâmetros ad_user_data e ad_personalization aos sinais existentes de ad_storage e analytics_storage. Esses parâmetros controlam se dados pessoais podem ser compartilhados com plataformas de mídia para modelagem preditiva, remarketing e atribuição de conversões.

### Por que o estado padrão negado deve ser declarado antes do carregamento do Google Tag Manager?

Declarar os estados como negados antes da inicialização do GTM impede que tags de mídia gravem cookies ou leiam identificadores logo no primeiro acesso. Qualquer tag disparada antecipadamente sem consentimento prévio constitui violação regulatória e corrompe os parâmetros de conformidade da sessão.

### De que forma a configuração ads_data_redaction protege a privacidade preservando a mensuração?

A ativação de ads_data_redaction remove identificadores de clique como GCLID e DCLID das requisições de rede sempre que ad_storage estiver negado. Em conjunto com url_passthrough, o mecanismo viabiliza a modelagem estatística de conversões entre páginas sem armazenar identificadores persistentes no dispositivo.

### Como o framework sincroniza as preferências do banner de cookies com as tags de marketing?

A função window.tavardtUpdateConsent recebe as seleções da CMP e aciona o comando gtag consent update para atualizar o dataLayer em tempo real. Os acionadores configurados no Google Tag Manager detectam a atualização e liberam dinamicamente apenas as tags autorizadas pelo visitante.

### Como os engenheiros podem auditar se o Consent Mode v2 está operando sem vazamento de dados?

As equipes podem analisar as requisições de rede no navegador para confirmar a presença dos parâmetros gcs e gcd nos pings de coleta do Google. Esteiras automatizadas de qualidade verificam se os pixels permanecem silenciados até que um sinal afirmativo de consentimento atualize o dataLayer.

***

## Links Úteis

* **Portal Corporativo:** https://ag.tavardt.com/pt/
* **Suíte de Diagnósticos:** https://tools.tavardt.com/pt/
* **Contacto Técnico:** https://ag.tavardt.com/pt/contacto/

***

### Licença
Distribuído sob a Licença MIT. Consulte [LICENSE](LICENSE) para obter detalhes completos.

***

© 2026 TAVARDT. Todos os direitos reservados.
