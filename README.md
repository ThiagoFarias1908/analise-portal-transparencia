# ✈️ EDA: Análise de Despesas de Viagens Governamentais

<p align="left">
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white" alt="Pandas">
  <img src="https://img.shields.io/badge/Matplotlib-11557C?style=for-the-badge&logo=matplotlib&logoColor=white" alt="Matplotlib">
  <img src="https://img.shields.io/badge/Jupyter-F37626.svg?&style=for-the-badge&logo=Jupyter&logoColor=white" alt="Jupyter">
</p>

> **Objetivo:** Auditar e extrair inteligência de dados a partir do histórico de viagens abertas do Governo Federal (Portal da Transparência), mapeando a correlação entre cargos públicos e a média de despesas geradas.

## 📈 Visualização de Alto Impacto

![Despesa média em viagens por cargo público (2025)](output/grafico_2025.png)

## ⚙️ Desafios Técnicos e Metodologia (ETL e Análise)

O trabalho com bases de dados abertas governamentais exige rigorosas etapas de limpeza (ETL) e engenharia de *features*. Este projeto (desenvolvido em Jupyter Notebook) seguiu a seguinte arquitetura de dados:

1.  **Tratamento de Dados Regionais:** Resolução de inconsistências de importação do `pd.read_csv`, especificando *encoding* (`Windows-1252`), separadores e o padrão brasileiro de decimais (vírgula) para evitar a quebra de tipos numéricos.
2.  **Feature Engineering (Criação de Variáveis):**
    *   Criação da métrica financeira unificada `Despesas` (somando diárias, passagens e outros gastos).
    *   Derivação de dimensões temporais (`Mês da viagem` e `Dias de viagem`), processando a diferença absoluta de dias entre datas de ida e volta (`pd.to_datetime`).
3.  **Agregações Lógicas:** Uso intensivo do método `.agg()` no Pandas para gerar uma tabela consolidada simultânea, cruzando média de dias, despesa total, destino modal (mais frequente) e volume de viagens, tudo agrupado por `Cargo`.
4.  **Filtros Estatísticos de Relevância:** Aplicação de um filtro na base (isolando cargos que representam **>1% do volume total de viagens**) para eliminar *outliers* ruidosos e focar a visualização nos dados mais representativos para a administração pública.
5.  **Dataviz (Exportação):** Criação de um gráfico de barras horizontais utilizando `matplotlib`, estilizado sob uma paleta *dark* personalizada para leitura facilitada e exportado para compor painéis gerenciais.

## 📁 Estrutura de Diretórios

O *pipeline* de dados exige uma estrutura de pastas organizada para a correta entrada e saída de arquivos gerados (Tabelas Excel e PNGs).

```text
analise-portal-transparencia/
│
├── data/
│   └── amostra_viagens.csv        # Amostra reduzida (5 mil linhas) para testes
├── output/
│   ├── tabela_2025.xlsx           # Tabela filtrada agregada gerada pelo script
│   └── grafico_2025.png           # Visualização final gerada pelo matplotlib
│
├── EDA_Gastos_Governo.ipynb       # Notebook principal com o código de limpeza e EDA
├── requirements.txt               # Dependências do projeto (pandas, matplotlib, openpyxl)
└── README.md

```

## 🚀 Como Executar o Projeto

Para garantir a reprodutibilidade rápida por recrutadores e gestores, o repositório já acompanha uma amostra tratada de 5.000 linhas (`amostra_viagens.csv`).

1. Clone este repositório e instale as dependências em seu ambiente virtual:
```bash
git clone [https://github.com/ThiagoFarias1908/analise-portal-transparencia.git](https://github.com/ThiagoFarias1908/analise-portal-transparencia.git)
cd analise-portal-transparencia
pip install -r requirements.txt

```


2. Abra o `EDA_Gastos_Governo.ipynb` no Jupyter Notebook ou em sua IDE (como VS Code).
3. Execute todas as células. O script lerá a amostra local e gerará as tabelas e gráficos na pasta `output/`.

> **⚠️ Atenção:** Os gráficos exibidos neste README foram gerados utilizando a base oficial completa (que excede o limite de tamanho do GitHub). Se desejar replicar os resultados exatos do ano, faça o download do histórico completo no [Portal da Transparência](https://portaldatransparencia.gov.br/), coloque o arquivo na pasta `data/` e altere o caminho de leitura na primeira célula do notebook.

## 💡 Roadmap de Evolução

* [ ] Incorporar análise geoespacial (mapa de calor) dos destinos mais caros.
* [ ] Implementar modelo preditivo de série temporal para prever gastos no próximo trimestre.
* [ ] Migrar as visualizações estáticas para um Dashboard interativo em Streamlit.

---

**Autor:** [Thiago Farias Lourenço](https://www.linkedin.com/in/thiagofarias1908/)
