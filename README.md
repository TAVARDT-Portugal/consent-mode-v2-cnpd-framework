# Framework Consent Mode v2 & Conformidade RGPD | TAVARDT Portugal

[![Diagn%C3%B3stico%20T%C3%A9cnico](https://img.shields.io/badge/TAVARDT-Diagn%C3%B3stico%20T%C3%A9cnico-5b3cf5.svg)](https://tools.tavardt.com/pt/validador-consent-mode-v2-rgpd/)
Implementação técnica do Google Consent Mode v2, bloqueio prévio de cookies analíticos e conformidade regulamentar com o RGPD e a CNPD em Portugal.

Desenvolvido e mantido pela área de ciberdefesa e privacidade técnica da **TAVARDT Portugal**.

***

## 1. Arquitetura e Ordem de Carregamento

Para cumprimento integral do RGPD, incorpore este ficheiro no <head> da página antes de qualquer chamada ao Google Tag Manager:

```html
<script src="consent-mode-v2.js"></script>
<!- Google Tag Manager / measurement scripts execute here ->
```

***

## 2. Capacidades Técnicas do Framework

* **Estado Predefinido Recusado:** Bloqueio preventivo obrigatório de todas as finalidades até consentimento expresso.
* **API de Atualização Síncrona:** Interface window.tavardtConsent.update() perfeitamente acoplada ao dataLayer.
* **Ocultação de Identificadores (ads_data_redaction):** Supressão estrita de dados de navegação quando o consentimento for recusado.
* **Transmissão Segura de Parâmetros:** Suporte a url_passthrough para preservar medições sem criar cookies.

***

## 3. Documentação e Requisitos Regulamentares

Consulte a lista detalhada de requisitos técnicos para Portugal:

* Checklist

***

## 4. Ferramentas Técnicas Online (Portugal)

Audite a infraestrutura pública das suas aplicações utilizando a suíte de diagnósticos da TAVARDT:

* Validador de Consent Mode v2 e RGPD
* [Auditoria de Cabeçalhos de Segurança](https://tools.tavardt.com/pt/analise-cabecalhos-seguranca/)
* [Verificador DMARC e Autenticação](https://tools.tavardt.com/pt/verificador-dmarc-email/)
* [Deteção de Ficheiros Expostos](https://tools.tavardt.com/pt/verificador-ficheiros-expostos/)
* [Portal de Diagnóstico Técnico Portugal](https://tools.tavardt.com/pt/)

***

## 5. Consultoria e Remediação Técnica

Para auditorias a contentores de tags, blindagem de privacidade e consultoria de conformidade em Portugal, contacte a **TAVARDT Portugal**.
