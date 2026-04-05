# AI News Aggregator

Sistema automatizado de curadoria e analise de noticias de Inteligencia Artificial, desenvolvido com n8n + GPT-4o.

---

## Sobre o Projeto

O **AI News Aggregator** e um workflow no n8n que roda automaticamente toda segunda-feira as 8h, coletando, filtrando e analisando as principais noticias de IA da semana. O sistema usa GPT-4o para gerar um relatorio completo em portugues, com destaques, tendencias, oportunidades para startups e analises de lacunas -- enviando tudo por **e-mail** e **Slack**.

---

## Fluxo do Workflow

```
[Schedule Trigger - Toda Segunda 8h]
        |
        v
[4 RSS Feeds: TechCrunch + VentureBeat AI + MIT Tech Review + O'Reilly Media]
        |
        v
[Merge All Feeds]
        |
        v
[Remove Duplicates]
        |
        v
[Filter & Categorize AI News - JavaScript]
   - Filtra por 40+ palavras-chave de IA
   - Filtra noticias dos ultimos 7 dias
   - Categoriza em 8 categorias
        |
        v
[Aggregate & Count by Category]
   - Conta noticias por categoria
   - Gera estatisticas percentuais
   - Constroi o prompt para o GPT
        |
        v
[Call GPT-4o]
   - Analise das noticias
   - Destaques, tendencias, oportunidades, gaps
        |
        v
[Merge GPT Result]
   - Combina resposta do GPT com dados agregados
        |
        v
[Format HTML Newsletter]
   - Layout responsivo com inline styles
   - Escapamento correto de HTML
   - Tabela de distribuicao + secoes por categoria
        |
        v
[Email] + [Slack]
```

---

## Funcionalidades

| Funcionalidade | Descricao |
|---|---|
| 4 fontes RSS | TechCrunch, VentureBeat AI, MIT Tech Review, O'Reilly Media |
| Filtro inteligente | 40+ palavras-chave de IA, filtragem dos ultimos 7 dias |
| 8 categorias | IA Generativa, ML, Visao Computacional, Etica, Saude, Financas, Infraestrutura, Startups |
| Contagem automatica | Estatisticas por categoria com percentual |
| Análise GPT-4o | Relatorio completo em portugues com insights reais |
| Oportunidades | Identificacao de gaps para startups e projetos |
| Sub-representados | Detecta topicos importantes ausentes na cobertura |
| E-mail automatico | Newsletter HTML responsiva enviada para a lista da comunidade |
| Slack | Resumo enviado ao canal automaticamente |
| Schedule | Trigger automatica toda segunda-feira as 8h |
| HTML seguro | Escapamento de caracteres especiais em titulos e sumar ios |
| Deduplicacao | Evita noticias repetidas entre as fontes |

---

## Categorias Monitoradas

1. **Generative AI** - GPT, LLMs, difusao, multimodal
2. **Machine Learning** - Deep learning, redes neurais, fine-tuning
3. **Computer Vision** - Reconhecimento de imagem, video
4. **AI Ethics & Regulation** - Seguranca, governanca, politicas
5. **AI in Healthcare** - Diagnostico, descoberta de drogas
6. **AI in Finance** - Detecao de fraudes, trading, fintechs
7. **AI Infrastructure** - Chips, GPUs, edge computing
8. **AI Startups & Business** - Funding, aquisoes, valuacoes

---

## Como Usar

### 1. Importar o Workflow

1. Acesse sua instancia do n8n
2. Clique em **"+"** > **"Import from file"**
3. Selecione o arquivo `AI News Aggregator.json`

### 2. Configurar Credenciais

No n8n, configure:

- **OpenAI API Key** -> para o no GPT-4o (credencial chamada "OpenAI API")
- **SMTP** -> para envio da newsletter (credencial chamada "SMTP account")
- **Slack OAuth2** -> para notificacoes no canal (credencial chamada "Slack API")

### 3. Ativar o Workflow

- Clique no toggle **"Active"** no canto superior direito
- O workflow rodara automaticamente toda segunda as 8h

---

## Estrutura do Repositorio

```
/
+-- AI News Aggregator.json   # Workflow exportado do n8n
+-- README.md                 # Este arquivo
```

---

## Tecnologias

- **n8n** - Automacao de workflow
- **RSS Feed** - Coleta de noticias (TechCrunch, VentureBeat, MIT Tech Review, O'Reilly Media)
- **JavaScript (Code node)** - Filtragem, categorizacao, deduplicacao e formatacao
- **GPT-4o (OpenAI)** - Anali se e geracao do relatorio
- **SMTP** - Envio de e-mail
- **Slack API** - Notificacao no canal da comunidade

---

## Exemplo de Saida

```
Destques da Semana
- OpenAI lanca GPT-4.1 com capacidade de raciocinio estendida...
- Meta open-sources Llama 3.2 Vision para aplicacoes multimodais...

Tendencias Identificadas
1. Crescimento de modelos multimodais open-source
2. Regulamentacao de IA ganha forca na Europa e EUA
3. Edge AI avanca em dispositivos moveis e IoT

Oportunidades para Startups
- Ferramentas de compliance para regulamentacao de IA
- Plataformas de fine-tuning para modelos open-source

Resumo: 38 noticias | IA Generativa: 12 (32%) | ML: 8 (21%) | Etica: 6 (16%) | ...
```

---

## Autor

Diego Figueiredo - desenvolvido para o processo seletivo do **Inteli Academy**.

