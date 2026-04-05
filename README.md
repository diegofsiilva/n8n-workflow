# 🤖 Inteli Academy – AI News Aggregator

> Sistema automatizado de curadoria e análise de notícias de Inteligência Artificial, desenvolvido com n8n + GPT-4o.

---

## 📌 Sobre o Projeto

O **AI News Aggregator** é um workflow no n8n que roda automaticamente toda segunda-feira às 8h, coletando, filtrando e analisando as principais notícias de IA da semana. O sistema usa GPT-4o para gerar um relatório completo em português, com destaques, tendências, oportunidades de startups e análises de lacunas — enviando tudo por **e-mail** e **Slack**.

---

## 🔁 Fluxo do Workflow

```
[Schedule Trigger - Toda Segunda 8h]
        ↓
[RSS Feeds: TechCrunch + VentureBeat + MIT Tech Review + O'Reilly]
        ↓
[Merge All Feeds]
        ↓
[Filter & Categorize AI News - JavaScript]
   • Filtra por palavras-chave de IA
   • Filtra notícias dos últimos 7 dias
   • Categoriza em 8 categorias
        ↓
[Aggregate & Count by Category]
   • Conta notícias por categoria
   • Gera estatísticas percentuais
        ↓
[GPT-4o Analysis & Report]
   • Destaques da semana
   • Notícias por categoria
   • Tendências emergentes
   • Oportunidades para startups
   • Tópicos sub-representados
        ↓
[Format HTML Newsletter]
        ↓
[📧 Email] + [💬 Slack]
```

---

## ✨ Funcionalidades

| Funcionalidade | Descrição |
|---|---|
| 📡 4 fontes RSS | TechCrunch, VentureBeat AI, MIT Tech Review, O'Reilly Radar |
| 🔍 Filtro inteligente | 30+ palavras-chave de IA, filtragem dos últimos 7 dias |
| 🏷️ 8 categorias | IA Generativa, ML, Visão Computacional, Ética, Saúde, Finanças, Infraestrutura, Startups |
| 📊 Contagem automática | Estatísticas por categoria com percentual |
| 🤖 Análise GPT-4o | Relatório completo em português com insights reais |
| 💡 Oportunidades | Identificação de gaps para startups e projetos |
| ⚠️ Sub-representados | Detecta tópicos importantes ausentes na cobertura |
| 📧 Email automático | Newsletter HTML enviada para a lista da comunidade |
| 💬 Slack | Resumo enviado ao canal `#ai-news` automaticamente |
| ⏰ Schedule | Trigger automática toda segunda-feira às 8h |

---

## 🗂️ Categorias Monitoradas

1. **🧠 Generative AI** – GPT, LLMs, difusão, multimodal
2. **📈 Machine Learning** – Deep learning, redes neurais, fine-tuning
3. **👁️ Computer Vision** – Reconhecimento de imagem, vídeo
4. **⚖️ AI Ethics & Regulation** – Segurança, governança, políticas
5. **🏥 AI in Healthcare** – Diagnóstico, descoberta de drogas
6. **💰 AI in Finance** – Detecção de fraudes, trading, fintechs
7. **🖥️ AI Infrastructure** – Chips, GPUs, edge computing
8. **🚀 AI Startups & Business** – Funding, aquisições, valuações

---

## 🚀 Como Usar

### 1. Importar o Workflow
1. Acesse sua instância do n8n
2. Clique em **"+"** > **"Import from file"**
3. Selecione o arquivo `ai_news_workflow.json`

### 2. Configurar Credenciais
No n8n, configure:
- **OpenAI API Key** → para o nó GPT-4o
- **SMTP / Email** → para envio da newsletter
- **Slack OAuth2** → para notificações no Slack

### 3. Ativar o Workflow
- Clique no toggle **"Active"** no canto superior direito
- O workflow rodará automaticamente toda segunda às 8h

---

## 📦 Estrutura do Repositório

```
/
├── ai_news_workflow.json   # Workflow exportado do n8n
└── README.md               # Este arquivo
```

---

## 🛠️ Tecnologias

- **n8n** – Automação de workflow
- **RSS Feed** – Coleta de notícias (TechCrunch, VentureBeat, MIT, O'Reilly)
- **JavaScript (Code node)** – Filtragem, categorização e formatação
- **GPT-4o (OpenAI)** – Análise e geração do relatório
- **SMTP** – Envio de e-mail
- **Slack API** – Notificação no canal da comunidade

---

## 📊 Exemplo de Saída

```
🔥 Destaques da Semana
• OpenAI lança GPT-4.1 com capacidade de raciocínio estendida...
• Meta open-sources Llama 3.2 Vision para aplicações multimodais...

📈 Tendências Identificadas
1. Crescimento de modelos multimodais open-source
2. Regulamentação de IA ganha força na Europa e EUA
3. Edge AI avança em dispositivos móveis e IoT

💡 Oportunidades para Startups
• Ferramentas de compliance para regulamentação de IA
• Plataformas de fine-tuning para modelos open-source

📊 Resumo: 38 notícias | IA Generativa: 12 (32%) | ML: 8 (21%) | Ética: 6 (16%) | ...
```

---

## 👤 Autor

Desenvolvido para o processo seletivo do **Inteli Academy** – Clube de IA do Inteli.

---

## 📄 Licença

MIT License
