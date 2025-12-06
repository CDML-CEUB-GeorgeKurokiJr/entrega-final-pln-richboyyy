# RAG-Demo: Assistente para Concursos de Ciência de Dados (Cebraspe)

**Projeto Final de PLN** | Adaptação da plataforma RAG-Demo para o contexto de **Concursos Públicos**.

Este repositório contém a implementação final com foco na banca **CEBRASPE**, cobrindo o histórico de provas de **2020 a 2025** para cargos de Ciência de Dados e TI.

---

## 🎯 Detalhes da Implementação

### 1. Curadoria de Dados (Data Curation)
Para resolver problemas de ingestão de gráficos e tabelas (comuns em questões de estatística como Curva ROC), foi realizado um **pré-processamento manual (ETL)**:
- Conversão das provas de PDF para **TXT limpo**.
- Resultado: O sistema recupera e explica corretamente questões que falhavam na extração padrão.

### 2. Clusters Semânticos
Foi realizada a ingestão de **múltiplos anos de provas** (2020-2025) na mesma collection.
- Isso gerou densidade vetorial suficiente para a formação de **clusters visuais no Qdrant**, agrupando questões por tema (ex: agrupamento de questões sobre Python, SQL, Estatística).

### 3. Arquitetura Multi-Agente (n8n)
Implementação de um **Agente Proxy** que atua como roteador semântico:
- **Rota A (Especialista):** Direciona perguntas técnicas para a base de *Ciência de Dados*.
- **Rota B (Generalista):** Direciona perguntas de interpretação/gramática para a base de *Conhecimentos Básicos*.

---

## 📂 Organização dos Dados

As collections no Qdrant já estão populadas (pasta `/volumes` inclusa no commit):

| Collection | Conteúdo |
| :--- | :--- |
| **`cebraspe_ciencia_dados_historico`** | Questões técnicas e gabaritos (Machine Learning, BD, Estatística) de 2020 a 2025. |
| **`cebraspe_conhecimentos_basicos_historico`** | Questões e gabaritos de Português e Inglês das mesmas provas. |

---

## 🚀 Como Rodar

1. **Configuração:**
   Certifique-se de adicionar sua `OPENAI_API_KEY` no arquivo `.env`.

2. **Execução:**
   ```bash
   docker-compose up -d --build

Aluno: Riam Renella Martinelli
RA: 22205569
