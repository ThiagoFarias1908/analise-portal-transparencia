# ✈️ Análise de Gastos com Viagens - Portal da Transparência

## 📌 Sobre o Projeto

Este projeto tem como objetivo realizar uma Análise Exploratória de Dados (EDA) focada nas despesas de viagens governamentais, utilizando bases de dados abertas do **Portal da Transparência do Governo Federal Brasileiro**.

Através do processamento de dados e engenharia de recursos (feature engineering), o projeto extrai insights valiosos sobre o comportamento de gastos, duração de viagens e distribuição de recursos por cargos.

## 🛠️ Tecnologias Utilizadas

* **Python:** Linguagem principal para manipulação de dados.
* **Pandas:** Utilizado para importação (lidando com encoding `Windows-1252`, separadores e padrões de decimais brasileiros), limpeza e agregação de dados.
* **Matplotlib:** Utilizado para a criação de visualizações customizadas e de alto impacto visual (estilo *dashboard*).

## 📊 Principais Etapas e Análises

1. **Coleta e Tratamento:** Importação do arquivo CSV nativo do Portal da Transparência, adequando formatações regionais para evitar perda de integridade numérica e textual.
2. **Engenharia de Features:**
* Criação de novas métricas, como `Mês da viagem` e `Dias de viagem`, calculadas a partir das datas de início e término.
* Consolidação da coluna `Despesas`.


3. **Agrupamento e Estatísticas:** Geração de uma tabela consolidada utilizando `.agg()` para extrair múltiplas métricas simultâneas (média, soma, moda, contagem) por diferentes variáveis.
4. **Filtragem de Relevância:** Aplicação de filtros estatísticos (foco em cargos que representam mais de 1% do volume de viagens) para reduzir ruídos e focar nos dados mais expressivos.
5. **Visualização de Dados:** Construção de gráficos de barras horizontais altamente customizados (paleta dark com destaque em `#49deac`), facilitando a leitura e a tomada de decisão.

## 🚀 Como Executar o Projeto

1. Clone este repositório:
```bash
git clone https://github.com/ThiagoFarias1908/analise-portal-transparencia.git

```


2. Instale as dependências necessárias:
```bash
pip install pandas matplotlib

```


3. Baixe a base de dados do [Portal da Transparência](https://portaldatransparencia.gov.br/) e coloque-a na mesma pasta do script (ou altere o caminho no código).
4. Execute o Jupyter Notebook ou o script Python em sua IDE de preferência, lembrando de rodar as células na ordem correta (primeiro a importação e tratamento, seguido do agrupamento e visualização).

## 💡 Próximos Passos (To-Do)

* [ ] Analisar a sazonalidade dos gastos (meses com maior volume de despesas).
* [ ] Mapear os destinos mais frequentes e com maior custo.
* [ ] Criar funções automatizadas para gerar o relatório mensalmente.

---

*Desenvolvido com dedicação para aprimorar habilidades em Análise de Dados.*
