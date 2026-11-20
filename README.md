# Framework Consent Mode v2 & Diretrizes CNPD / RGPD | TAVARDT Portugal

[![Validador de Consentimento](https://img.shields.io/badge/TAVARDT-Diagn%C3%B3stico%20T%C3%A9cnico-5b3cf5.svg)](https://tools.tavardt.com/pt/validador-consent-mode-v2-rgpd/)
[![Conformidade](https://img.shields.io/badge/Jurisdi%C3%A7%C3%A3o-Portugal-00C853.svg)](https://ag.tavardt.com/pt/ciberseguranca/)

Implementação técnica do Google Consent Mode v2, bloqueio prévio de rastreadores e conformidade com as diretrizes da CNPD e do RGPD em Portugal.

Desenvolvido e mantido pela divisão de privacidade digital e engenharia de dados da **[TAVARDT Portugal](https://ag.tavardt.com/pt/)**.

---

## 1. Arquitetura e Ordem de Carregamento

Para cumprimento integral do RGPD, este ficheiro deve ser incorporado no <head> da página antes de qualquer chamada ao Google Tag Manager ou ferramentas analíticas:

```html
<script src="consent-mode-v2.js"></script>
<!-- O contentor do Google Tag Manager ou scripts de medição seguem aqui -->
```

---

## 2. Capacidades Técnicas do Framework

* **Bloqueio Prévio 'Denied':** Nenhum identificador é gravado no terminal do utilizador antes de consentimento inequívoco.
* **Método de Atualização Assíncrono:** Função window.tavardtUpdateConsent() estruturada para emitir o evento tavardt_consent_updated no dataLayer.
* **Redação de Identificadores de Anúncios:** Limpeza automática de parâmetros de clique caso o consentimento de marketing seja recusado.
* **Ligação Segura entre Domínios:** Suporte a url_passthrough sem violação de diretivas de privacidade.

---

## 3. Documentação e Requisitos Regulamentares

Consulte a lista detalhada de requisitos técnicos para este país:

* [Checklist Técnico de Conformidade](checklist.md)

---

## 4. Ferramentas Técnicas Online (Portugal)

Audite a conformidade das suas etiquetas e proteja o seu domínio com ferramentas online verificadas:

* [Validador de Consent Mode v2 e RGPD](https://tools.tavardt.com/pt/validador-consent-mode-v2-rgpd/)
* [Auditoria de Cabeçalhos de Segurança](https://tools.tavardt.com/pt/analise-cabecalhos-seguranca/)
* [Verificador DMARC e Segurança de E-mail](https://tools.tavardt.com/pt/verificador-dmarc-email/)
* [Deteção de Ficheiros Sensíveis Expostos](https://tools.tavardt.com/pt/verificador-ficheiros-expostos/)
* [Portal de Diagnóstico Técnico Portugal](https://tools.tavardt.com/pt/)

---

## 5. Consultoria e Governação de Etiquetas

Para auditorias de privacidade, testes de conformidade com o RGPD e implementação de consentimento em Portugal, contacte a **[TAVARDT Portugal](https://ag.tavardt.com/pt/contato/)**.
