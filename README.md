# 📊 Databricks Análises - Estudos Avançados em Data Analytics

Um repositório abrangente de estudos, experimentos e aplicações práticas em análise de dados com foco em processamento em escala, exploração de informações e interpretação de cenários complexos em ambiente **Databricks**.

## 📋 Descrição do Projeto

Este repositório reúne análises práticas e teóricas que cobrem:

- **Estudos de Caso Reais e Fictícios**: Cenários que simulam desafios analíticos do mundo empresarial
- **Processamento em Escala**: Manipulação eficiente de grandes volumes de dados
- **Comparação de Abordagens**: PySpark vs SQL - qual usar em cada situação
- **Integração com IA**: Conectar dados com inteligência artificial para auditoria e insights
- **Exploração de Dados**: Técnicas de EDA, transformação e enriquecimento
- **Otimização de Consultas**: Performance tuning em ambiente Spark

## 🎯 Caso de Uso

Ideal para:
- 📈 **Analistas de Dados**: Aprimorar skills em Databricks e Spark
- 🔬 **Cientistas de Dados**: Explorar técnicas de processamento em escala
- 💼 **Engenheiros de Dados**: Estudar padrões de otimização e design
- 🎓 **Aprendizado**: Referência prática para análise de dados em produção
- 🏢 **Empresas**: Modelos de caso de uso aplicáveis a cenários reais

## 🏗️ Arquitetura e Fluxo

```
┌──────────────────────────────────────────────────────────────┐
│                    Dados Brutos (RAW)                        │
│           (CSV, JSON, Parquet, Delta Tables)                 │
└────────────────┬─────────────────────────────────────────────┘
                 │
         ┌───────▼──────────┐
         │  Exploração (EDA)│
         │  Perfilamento    │
         │  Limpeza         │
         └───────┬──────────┘
                 │
         ┌───────▼──────────────────────┐
         │  Transformação & Enriquecimento
         │  ├─ PySpark APIs             │
         │  ├─ SQL via Spark            │
         │  └─ Otimização               │
         └───────┬──────────────────────┘
                 │
         ┌───────▼──────────────────────┐
         │  Análises Temáticas          │
         │  ├─ Auditoria                │
         │  ├─ BI/BI                    │
         │  ├─ Modelos Preditivos       │
         │  └─ Insights com IA          │
         └───────┬──────────────────────┘
                 │
         ┌───────▼──────────────────────┐
         │  Visualizações e Relatórios  │
         │  (Dashboards, Exports)       │
         └──────────────────────────────┘
```

## 📁 Estrutura do Projeto

```
databricks_analises/
├── (Public) Case_Ficticio_Auditoria_Assistente_IA.ipynb
│   ├── Cenário: Auditoria de dados com assistência IA
│   ├── Conceitos: RAG, Busca semântica, LLM
│   ├── Técnicas: Validação de dados, anomalias
│   └── Saída: Relatório estruturado com recomendações
│
├── (Public) Pyspark vs SQL via Spark - Manipulação de Dados.ipynb
│   ├── Comparação prática entre APIs
│   ├── Performance benchmarks
│   ├── Quando usar cada uma
│   └── Exemplos lado a lado
│
├── README.md  # Este arquivo
└── [Novos notebooks podem ser adicionados]
```

## 📓 Projetos Inclusos

### 1️⃣ Case Fictício: Auditoria com Assistente IA

**Arquivo**: `(Public) Case_Ficticio_Auditoria_Assistente_IA.ipynb`

**Objetivo**: Demonstrar como usar IA generativa para auxiliar auditoria e validação de dados.

**Tópicos Cobertos:**
- 🔍 Carregamento e exploração de dados
- 📊 Perfilamento de qualidade
- 🤖 Integração com modelos de linguagem (LLM)
- ✅ Geração automática de checklist de auditoria
- 📋 Identificação de anomalias e padrões suspeitos
- 🎯 Relatório estruturado com recomendações

**Tecnologias:**
- PySpark para processamento
- SQL para consultas analíticas
- Groq/LLaMA para análise com IA
- Delta Lake para persistência

**Casos de Uso:**
- Auditoria de qualidade de dados
- Validação de integridade referencial
- Detecção de fraudes e anomalias
- Geração de relatórios com insights automatizados

---

### 2️⃣ PySpark vs SQL - Manipulação de Dados

**Arquivo**: `(Public) Pyspark vs SQL via Spark - Manipulação de Dados.ipynb`

**Objetivo**: Comparação prática e objetiva entre PySpark e SQL para as mesmas operações.

**Tópicos Cobertos:**
- 📌 Leitura e escrita de dados
- 🔄 Transformações básicas (select, filter, groupby)
- 📊 Agregações e janelas (window functions)
- 🔗 Joins e left joins
- 🎯 Ordenação e ranking
- ⚡ Performance benchmarks
- 💡 Quando usar cada uma

**Comparação de Abordagens:**

| Operação | PySpark | SQL via Spark | Melhor Para |
|----------|---------|---|---|
| **SELECT simples** | `df.select(cols)` | `SELECT col FROM table` | SQL - mais legível |
| **FILTER** | `df.filter(condition)` | `WHERE condition` | SQL - intuitivo |
| **GROUPBY** | `df.groupBy().agg()` | `GROUP BY ... HAVING` | SQL - performance |
| **JOIN** | `df.join(df2, on)` | `JOIN ... ON` | SQL - otimização |
| **Window Functions** | `df.over(Window.partitionBy())` | `OVER (PARTITION BY)` | SQL - nativo |
| **Lógica Customizada** | Python UDF | SQL UDF | PySpark - flexibilidade |

**Código de Exemplo:**

```python
# PySpark
df_pyspark = spark.read.csv("dados.csv", header=True)
resultado = (df_pyspark
    .filter(df_pyspark.idade > 30)
    .groupBy("departamento")
    .agg(F.avg("salario").alias("media_salario"))
    .orderBy(F.desc("media_salario")))

# SQL
spark.sql("""
    SELECT 
        departamento,
        AVG(salario) as media_salario
    FROM dados
    WHERE idade > 30
    GROUP BY departamento
    ORDER BY media_salario DESC
""")
```

**Performance:**
- SQL geralmente é mais otimizado pelo Catalyst
- PySpark oferece mais controle e flexibilidade
- Ambos compilam para Spark Plan idêntico em muitos casos

---

## 🚀 Como Usar Este Repositório

### 1️⃣ Pré-requisitos

- Conta Databricks (Community Edition ou Pro)
- Python 3.8+
- Conhecimento básico de SQL e Spark

### 2️⃣ Importar Notebooks

**Opção 1: Via Interface Databricks**
1. Acesse seu workspace Databricks
2. Clique em "Import" → "URL"
3. Cole a URL do notebook do GitHub
4. Clique em "Import"

**Opção 2: Download Local**
1. Baixe o arquivo `.ipynb`
2. Faça upload no Databricks
3. Defina um cluster para executar

### 3️⃣ Configurar Ambiente

```python
# No primeiro cell do notebook, execute:
from pyspark.sql import functions as F
from pyspark.sql.window import Window
import pandas as pd

# Confirme que Spark está disponível
print(spark.version)
```

### 4️⃣ Executar Notebooks

- Selecione um cluster Databricks ativo
- Execute célula por célula (Shift + Enter)
- Modifique parâmetros e dados conforme necessário

## 🔧 Componentes Principais

### Dependências e Bibliotecas

| Biblioteca | Versão | Uso |
|-----------|--------|-----|
| PySpark | 3.0+ | Processamento distribuído |
| SQL (Databricks) | Native | Queries analíticas |
| Pandas | 1.0+ | Manipulação local de dados |
| Numpy | 1.19+ | Operações numéricas |
| Matplotlib/Plotly | Latest | Visualizações |

### Técnicas de Análise

- **EDA (Exploratory Data Analysis)**: Perfil de dados, distribuições, correlações
- **Data Profiling**: Qualidade, completude, validade
- **Anomaly Detection**: Detecção de outliers e padrões
- **Windowing**: Análises temporais e rankingização
- **Delta Lake**: Versionamento e ACID em Data Lakes

## 📊 Exemplos de Análises

### Exemplo 1: Agregação Temporal

```python
# Analisar tendências por período
resultado = spark.sql("""
    SELECT 
        DATE_TRUNC('month', data_transacao) as mes,
        categoria,
        COUNT(*) as total_transacoes,
        SUM(valor) as total_vendas,
        AVG(valor) as ticket_medio
    FROM transacoes
    WHERE ano = 2024
    GROUP BY DATE_TRUNC('month', data_transacao), categoria
    ORDER BY mes DESC, total_vendas DESC
""")
```

### Exemplo 2: Análise com Window Functions

```python
# Ranking de clientes por recência
resultado = spark.sql("""
    SELECT 
        cliente_id,
        MAX(data_transacao) as ultima_compra,
        DAYS(CURRENT_DATE(), MAX(data_transacao)) as dias_desde_compra,
        RANK() OVER (ORDER BY MAX(data_transacao) DESC) as ranking_recencia
    FROM transacoes
    GROUP BY cliente_id
""")
```

### Exemplo 3: Detecção de Anomalias

```python
# Identificar transações atípicas por cliente
resultado = spark.sql("""
    WITH stats_cliente AS (
        SELECT 
            cliente_id,
            AVG(valor) as valor_medio,
            STDDEV_POP(valor) as desvio_padrao
        FROM transacoes
        GROUP BY cliente_id
    )
    SELECT 
        t.cliente_id,
        t.valor,
        s.valor_medio,
        ABS(t.valor - s.valor_medio) / NULLIF(s.desvio_padrao, 0) as z_score
    FROM transacoes t
    JOIN stats_cliente s ON t.cliente_id = s.cliente_id
    WHERE ABS(t.valor - s.valor_medio) / s.desvio_padrao > 3
""")
```

## 💡 Dicas e Boas Práticas

### Performance Otimization

- ✅ Use particionamento apropriado
- ✅ Prefira SQL nativo ao PySpark para queries complexas
- ✅ Utilize Delta Lake para melhor performance
- ✅ Broadcast pequenos DataFrames em joins
- ❌ Evite UDFs Python quando possível (lento)
- ❌ Não use collect() em DataFrames grandes

### Estrutura de Dados

```
Projeto analítico bem estruturado:
├── Bronze (Raw Data)
│   └── Dados brutos, sem transformação
├── Silver (Cleaned Data)
│   └── Dados limpos, validados, enriquecidos
└── Gold (Business Ready)
    └── Dados modelados para consumo
```

### Monitoramento e Logging

```python
# Logging básico em Databricks
print(f"[INFO] Processados {df.count()} registros")
print(f"[INFO] Schema: {df.printSchema()}")
print(f"[WARN] Possível duplicação detectada")
```

## 📈 Extensões Futuras

- [ ] Notebooks adicionais com casos de uso específicos
- [ ] Modelos de ML integrados (MLlib, scikit-learn)
- [ ] Pipelines de ETL com Databricks Workflows
- [ ] Integração com BI Tools (Tableau, Power BI)
- [ ] Exemplos com Apache Iceberg
- [ ] Testes unitários para lógica de transformação
- [ ] Benchmarks de performance em datasets maiores
- [ ] Integração com Databricks SQL (queries otimizadas)

## 🛡️ Segurança e Governança

- ✅ Dados sensíveis podem ser mascarados
- ✅ Controle de acesso por role
- ✅ Auditoria de operações no Workspace
- ✅ Lineage de dados com Delta Lake

## 🤝 Contribuindo

Contribuições são bem-vindas! Você pode:
1. Adicionar novos notebooks com casos de uso
2. Melhorar exemplos existentes
3. Adicionar testes e validações
4. Expandir documentação
5. Reportar bugs ou sugestões

## 📞 Suporte

Para dúvidas ou problemas:
- Abra uma issue no GitHub
- Consulte a documentação Databricks: https://docs.databricks.com
- Spark Documentation: https://spark.apache.org/docs/latest/
- Community: https://community.databricks.com

## 🎓 Recursos de Aprendizado

- [Databricks Academy](https://www.databricks.com/learn)
- [Spark SQL Documentation](https://spark.apache.org/docs/latest/sql-getting-started.html)
- [PySpark API](https://spark.apache.org/docs/latest/api/python/)
- [Delta Lake Guide](https://docs.delta.io/)
- [Databricks Best Practices](https://docs.databricks.com/best-practices/)

## 📝 Licença

Este projeto é fornecido como material educacional e de referência.

---

**Desenvolvido com ❤️ para a comunidade de Data Analytics e Databricks**
