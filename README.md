# projeto-ciencia-de-dados-unoesc

Projeto de ciência de dados do curso de Ciência de Dados e IA da Universidade do Oeste de Santa Catarina (UNOESC).

## Tecnologias
- Python 3.11+
- Pandas
- Git/Github
- SQLite
- DBeaver
- Matplotlib
- Plotly
- Scikit-learn

## Como executar o projeto
1. Crie o ambiente virtual python e instale as dependências do projeto:
```bash
python -m venv .venv
# Windows
.venv\Scripts\activate
# Linux ou MacOS
source .venv/bin/activate
pip install -r requirements.txt
2. Execute o script `etl.py` (caso queira processar os dados)
3. Para análise gráfica, execute o script `analyze.py`
4. Para análise estatística (com regressão linear simples), execute o script `predict.py`
```

## Problema de Negócio
O governo do Brasil está investindo recursos para reduzir o número de queimadas nas florestas do país. O objetivo é entender quais os locais que mais sofrem com queimadas, realizando uma análise mensal, para entender quais os meses que mais ocorrem queimadas e quais os locais que mais sofrem com isso, a fim de destinar de uma forma mais correta os recursos disponíveis. O projeto consiste em analisar dados de queimadas no Brasil, utilizando técnicas de ciência de dados para identificar padrões e tendências.

## Requisitos de negócio
* Coletar dados de queimadas no Brasil, incluindo informações sobre localização, data e quantidade de focos de queimadas.
* Analisar os dados de queimadas no Brasil, identificando os meses com maior número de queimadas e os locais mais afetados.
* Criar um modelo preditivo para prever o número de queimadas nos próximos anos, utilizando técnicas de análise estatística.

## Explicação do Projeto
Com base no objetivo do projeto, foi localizado um dataset no Kaggle com dados de queimadas no Brasil. O dataset contém informações sobre a localização, data e quantidade de focos de queimadas. O projeto consiste em realizar uma análise exploratória dos dados, identificando os meses com maior número de queimadas e os locais mais afetados. Além disso, será criado um modelo preditivo para prever o número de queimadas nos próximos meses.

Como primeira etapa, optou-se pela criação de um banco de dados SQLite para armazenamento dos dados do dataset, como uma área de staging, onde os dados serão armazenados antes de serem processados. Essa etapa é importante para garantir a integridade dos dados e facilitar o acesso aos dados para análise. Também visa a persistência dos dados para evitar dependência do dataset original, que pode ser alterado ou removido. Nessa primeira etapa, também foi realizada uma análise exploratória dos dados, identificando quais colunas e tipos de dados deveriam ser armazenados no banco de dados. A partir dessa análise, foram criadas as tabelas no banco de dados SQLite. Todos esses itens estão no script `extract.py`.

Na segunda etapa, foi realizada outra análise exploratória, visando entender quais transformações seriam necessárias para que os dados ficassem íntegros para utilização no projeto. Essa etapa é importante para garantir que os dados estejam prontos para serem utilizados na análise e no modelo preditivo. Nessa etapa, foram identificados os tipos de dados que deveriam ser utilizados, as colunas que deveriam ser removidas e as colunas que deveriam ser transformadas. Essas transformações foram realizadas no script `transform.py`.

Posteriormente, para finalizar o processo de ETL, foi criado um datawarehouse, onde os dados transformados foram armazenados. Essa etapa é importante para garantir que os dados estejam prontos para serem utilizados na análise e no modelo preditivo. O datawarehouse foi criado no script `load.py`.

Com os dados processados e armazenados no datawarehouse, foi realizada uma análise gráfica dos dados, utilizando a biblioteca Plotly Express. Essa etapa é importante para visualizar os dados e identificar padrões e tendências. A análise gráfica foi realizada no script `analyze.py`.

Na última etapa, foi criado um modelo estatístico, com a técnica de regressão linear simples, para prever o número de queimadas nos próximos anos, no script `predict.py`.

## Resultados
Com a análise gráfica foi possível observar que o mês de setembro é o mês com maior número de queimadas, seguido por agosto e outubro. Além disso, foi possível identificar que os estados mais afetados por queimadas são Pará, Maranhão e Bahia. O ano que mais teve queimadas foi 2017, seguido por 2015 e 2005.

Através de um modelo de regressão linear simples, foi possível prever que o número de queimadas deve continuar aumentando nos próximos anos, com uma tendência de crescimento de 2837 queimadas por ano. Essa informação é importante para o governo do Brasil, pois pode ajudar a direcionar os recursos para as áreas mais afetadas e a desenvolver políticas públicas para reduzir o número de queimadas.

## Referências
- [Dataset](https://www.kaggle.com/datasets/gustavomodelli/forest-fires-in-brazil/data)