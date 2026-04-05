# AI News Aggregator

Sistema automatizado de curadoria e analise de noticias de Inteligencia Artificial, desenvolvido com n8n.

## Sobre o Projeto

O **AI News Aggregator** e um workflow no n8n que coleta noticias de inteligencia artificial de 3 fontes RSS, filtra por relevancia, categoriza, remove duplicatas, gera um relatório analitico e envia por e-mail em formato HTML. O workflow pode ser executado manualmente ou agendado com trigger semanal toda segunda-feira as 8h.

## Fluxo do Workflow

```
[schedule trigger - toda segunda 8h / manual]
        |
        v
[3 RSS Feeds: TechCrunch + VentureBeat AI + MIT Tech Review]
        |
        v
[Merge -> Remove Duplicates]
        |
        v
[Filter & Categorize AI News]
   - Filtra por 40+ palavras-chave de IA
   - Filtra noticias dos ultimos 7 dias
   - Categoriza em 9 categorias
        |
        v
[Aggregate & Count by Category]
   - Conta noticias por categoria
   - Gera estatisticas percentuais
   - Constroi o prompt para o LLM
        |
        v
[Format HTML Newsletter]
   - Layout responsivo com inline styles
   - Tabela de distribuicao + secoes por categoria
   - Converte markdown do LLM para HTML
        |
        v
[Send Email Newsletter]
```

## Funcionalidades

| Funcionalidade | Descricao |
|---|---|
| 3 fontes RSS | TechCrunch, VentureBeat AI, MIT Tech Review |
| Filtro inteligente | 40+ palavras-chave de IA, noticias dos ultimos 7 dias |
| 9 categorias | Generative AI, ML, Computer Vision, Etica, Saude, Financas, Infraestrutura, Startups, General AI |
| Contagem automatica | Estatisticas por categoria com percentual |
| Relatorio analitico | Destaques, tendencias, oportunidades e topicos sub-representados |
| E-mail automatico | Newsletter HTML responsiva |
| Schedule | Trigger automatica toda segunda-feira as 8h |
| Deduplicacao | Evita noticias repetidas entre as fontes |

## Categorias Monitoradas

1. **Generative AI** - GPT, LLMs, difusao, multimodal
2. **Machine Learning** - Deep learning, redes neurais, fine-tuning
3. **Computer Vision** - Reconhecimento de imagem, video
4. **AI Ethics & Regulation** - Seguranca, governanca, politicas
5. **AI in Healthcare** - Diagnostico, descoberta de drogas
6. **AI in Finance** - Detecao de fraudes, trading, fintechs
7. **AI Infrastructure** - Chips, GPUs, edge computing
8. **AI Startups & Business** - Funding, aquisoes, valuacoes
9. **General AI** - Noticias de IA que nao se encaixam nas demais

## Como Executar

### 1. Importar o Workflow

1. Acesse sua instancia do n8n
2. Clique em **"+"** > **"Import from File"**
3. Selecione o arquivo `AI News Aggregator.json`

### 2. Configurar Credenciais

No n8n, configure a credencial de **SMTP** para envio da newsletter (credencial chamada "SMTP account").

### 3. Executar

- **Manualmente**: Abra o workflow e clique em **"Test Workflow"** ou **"Execute Workflow"**
- **Automaticamente**: Ative o toggle **"Active"** no canto superior direito. O workflow rodara automaticamente toda segunda-feira as 8h (cron `0 8 * * 1`)

### 4. Receber o Resultado

A newsletter HTML sera enviada por e-mail para o endereco configurado no no **Send Email Newsletter** (campo `toEmail`).

## Estrutura do Repositorio

```
/
+-- AI News Aggregator.json   # Workflow exportado do n8n
+-- README.md                 # Este arquivo
```

## Tecnologias

- **n8n** - Automacao de workflow
- **RSS Feed** - Coleta de noticias (TechCrunch, VentureBeat, MIT Tech Review)
- **JavaScript (Code node)** - Filtragem, categorizacao, deduplicacao e formatacao
- **SMTP** - Envio de e-mail

## Autor

Diego Figueiredo - desenvolvido para o processo seletivo do **Inteli Academy**.
