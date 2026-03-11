# 🛡️ Email Spoofing Check
**Ferramenta de validação automatizada de políticas de autenticação de e-mail (SPF e DMARC).**

[![Python Version](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](https://opensource.org/licenses/MIT)

Este script foi desenvolvido para auxiliar Pentesters e Analistas de Segurança na identificação de configurações falhas em registros DNS que permitem o forjamento de e-mails (**Email Spoofing**). A ferramenta realiza uma análise técnica passiva, sem o envio real de mensagens, tornando-a segura para ambientes de produção.

---

## 🚀 Funcionalidades

* **🔍 Scan de Registros DNS:** Identifica e extrai registros SPF (TXT) e DMARC (`_dmarc`).
* **⚖️ Análise de Qualificadores:** Avalia o impacto de políticas como `~all` (SoftFail), `-all` (Fail) e `+all` (Any).
* **🛡️ Verificação DMARC:** Checa a existência e o rigor das políticas de `none`, `quarantine` ou `reject`.
* **📊 Classificação de Risco:** Gera um veredito automático (Baixo, Médio ou Alto) baseado na postura de segurança do domínio.
* **📄 Output Estruturado:** Resultados formatados para fácil leitura e inclusão em relatórios técnicos de Pentest.

---

## 🛠️ O que a ferramenta analisa?

| Registro | Foco da Análise | Impacto se Falho |
| :--- | :--- | :--- |
| **SPF** | Qualificadores de autorização (`all`). | Permite que IPs não autorizados enviem e-mails pelo domínio. |
| **DMARC** | Instrução para o servidor receptor em caso de falha. | Sem DMARC, as falhas de SPF/DKIM podem ser ignoradas. |

> [!IMPORTANT]
> **Segurança e Ética:** A ferramenta utiliza exclusivamente consultas DNS. Ela **NÃO** realiza interação ativa com servidores SMTP e **NÃO** envia e-mails reais.

---

## 💻 Instalação e Uso

### Pré-requisitos
* Python 3.8 ou superior.
* Biblioteca `dnspython`.

### Instalação

```bash
# Clone o repositório
git clone https://github.com/nailtpax/email_spoofing_check.py.git
cd email_spoofing_check.py

# Instale as dependências
pip install dnspython
```

Script desenvolvido por nailtpax
