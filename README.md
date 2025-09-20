### Análise de Varejo com PostgreSQL

Este é um projeto de exemplo para análise de dados de varejo, utilizando o PostgreSQL como banco de dados e o Python para consultas analíticas e visualização. O objetivo é demonstrar o fluxo de trabalho de um cientista de dados ou analista de BI, desde a criação do esquema até a extração de insights.

---

### Tecnologias Utilizadas

* **PostgreSQL**: Sistema de gerenciamento de banco de dados relacional.
* **Python**: Usado com a biblioteca Pandas para manipulação de dados, Matplotlib para visualização e psycopg2 para conexão com o banco de dados.
* **Jupyter Notebook**: Onde as consultas analíticas e a visualização são executadas.
* **Docker**: Para a execução do banco de dados em um ambiente isolado.

---

### Estrutura do Projeto

* **`docker-compose.yml`**: Configuração do ambiente Docker para o banco de dados PostgreSQL.
* **`sql/`**: Diretório contendo os scripts SQL para a configuração do banco de dados e as consultas.
    * `01_create_schema.sql`: Cria as tabelas do projeto, incluindo `customers`, `products`, `stores`, `orders` e `order_items`.
    * `02_generate_sample_data.sql`: Script para popular o banco de dados com dados sintéticos.
    * `03_indexes_and_views.sql`: Contém a criação de índices para otimizar o desempenho e vistas (`vw_customer_orders`, `vw_sku_sales`) para análises recorrentes.
    * `04_analysis_queries.sql`: Arquivo para armazenar consultas analíticas principais, incluindo KPIs, RFM, Análise de Coorte, ABC, Churn e CLTV.
    * `05_etl_examples.sql`: Exemplos de scripts de ETL simples.
* **`retail_analysis.ipynb`**: Notebook Jupyter com o código Python para se conectar ao banco de dados, extrair dados, realizar análises e gerar gráficos como o de vendas mensais.

---

### Como Rodar o Projeto

1.  **Inicie o banco de dados com Docker:**
    `docker-compose up -d`
2.  **Execute os scripts SQL:**
    * Crie o esquema: `psql -h localhost -p 5432 -U postgres -d retail -f sql/01_create_schema.sql`
    * Gere dados de exemplo: `psql -h localhost -p 5432 -U postgres -d retail -f sql/02_generate_sample_data.sql`
    * Crie índices e vistas: `psql -h localhost -p 5432 -U postgres -d retail -f sql/03_indexes_and_views.sql`
3.  **Execute a análise:**
    Abra e execute o notebook `retail_analysis.ipynb` para visualizar os dados e gerar os gráficos.
