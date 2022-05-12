# ciencia de Dados no E-Commerce
 Análise de vendas e previsão de demanda de uma empresa de e-commerce

# Introdução
Projeto desenvolvido para uma empresa de e-commerce. 
Após realizar um levantamento de resultados de 2021 para a empresa, os gestores e eu pensamos em maneiras para facilitar a análise de vendas e identificar erros de precificação que geram prejuízos para a empresa.
Na época em que o projeto foi realizado a empresa vendia 631 produtos em 19 diferentes canais de venda online.
A partir deste ponto, desenvolvi dois modelos de análise:
- Modelo de análise de desemprenho da semana anterior
	- Toda segunda-feira o modelo gera um relatório de análise da semana anterior.
- Modelo de análise da segunda-feira e previsão de demanda da semana
	- Segunda-feira é um dia preditivo nas vendas da empresa. 
	- Analisar a segunda-feira permite realizar correções em curto prazo
	- Desenvolver um modelo de Machine Learnig para prever as vendas na semana a partir dos resultados da segunda-feira.

# Dados
Os dados foram coletados diretamente do servidor SQL Server da empresa. Para tal, foram realizadas as seguintes etapas:
- Configurar um VPN na minha máquina
- Acessar o servidor SQL Server da empresa com o da minha máquina
- Integração Python/SQL com a biblioteca PYODB
- Montar uma Query para extração dos dados.
Foram extraídos dados da empresa com mais de 500 mil pedidos com 84 colunas de informações sobre cada pedido.

# Tecnologia
- OpenVPN
- SQL Server
- Python 3

# Bibliotecas Python utilizadas:
- Pandas
- Numpy
- Matplotlib
- Statsmodel
- Datetime
- Pyodbc
- Sklearn
- Catboost

# Projeto 1: Relatório de Vendas da semana passada
Para o projeto 1, são gerados dois relatórios para os gestores da empresa:
	- Agrupado por código de produto: realiza uma análise de desempenho das vendas do produto na semana
	- Agrupado por código e por canal: gera as mesmas análises, mas separadas por canal de vendas, permitindo uma análise mais granular da situação do produto.

## Limpeza de dados:
	Primeiro foram tirados do DF as devoluções de pedidos
## Tratamento de dados
- Para desenvolver esse projeto, foram selecionadas seis colunas de interesse para desenvolver o DataFrame (DF) final. São elas:
	- Data Emissão
	- Código do Produto
	- Canal de Venda
	- Quantidade de itens do pedido
	- Preço unitário
	- Margem de Contribuição
A partir da data foi criada a coluna com a semana do ano para agrupar as vendas por semana.
 
O período utilizado para realizar os dados comparativos do relatório foi o histórico dos últimos 90 dias agrupados por semana.
Para a média de vendas esperada foi utilizado a média de vendas nos últimos 90 dias até um desvio padrão a mais.
Foi criado um DF da semana anterior com as mesmas informações.
	- Preço
	- Volume de Vendas
	- Margem de Contribuição
Para avaliar o desempenho das vendas em períodos mais curtos, são gerados resultados médios dos últimos 30 e 60 dias. É levantado tanto o preço médio quanto a média de vendas por semana e inseridos na tabela final.
É calculado o % da Margem de Contribuição de cada produto e inserido na tabela final.
Colunas comparativas e de resultados foram inseridas na tabela de acordo com os resultados da semana quando comparados com o período.
## Conclusão Projeto1
	Projeto em vigor atualmente na empresa. Auxilia a área comercial em identificar de forma rápida e precisa a necessidade de ações comerciais específicas para cada produto em cada canal de venda.

# Projeto 2
	Para o projeto 2, é gerado um relatório de análise de desempenho da segunda-feira dos produtos em cada canal de venda com uma previsão de demanda da semana a partir desse desempenho.
	- 28% do volume de vendas da empresa ocorre na segunda-feira
## Limpeza de dados:
	Primeiro foram tirados do DF as devoluções de pedidos
## Tratamento de dados
- Para desenvolver esse projeto, foram selecionadas seis colunas de interesse para desenvolver o DataFrame (DF) final. São elas:
	- Data Emissão
	- Código do Produto
	- Canal de Venda
	- Quantidade de itens do pedido
	- Preço unitário
	- Margem de Contribuição
A partir da data foi criada a coluna com a semana do ano para agrupar as vendas por semana.
## Modelo de Análise
	Os dados da segunda-feira foram com comparados com os resultados de uma, duas e três segundas-feiras anteriores. Foram analisadas:
	- Vendas
	- Preço médio
	- Margem de Contribuição
## Modelo de Previsão de Demanda
	Para desenvolver o modelo foi realizado um trabalho de feature engineering a fim de montar um DF com informações que impactam as vendas do produto. O DF final utilizado para o modelo de análise continha as seguintes variáveis:
	- Canal de Vendas
	- Código do produto
	- Preço unitário
	- Volume de vendas na segunda-feira
	- Mês
	- Semana do mês
	- Se a segunda ou a terça-feira da semana é um feriado ou não

	Essa informação gerou um valor com a participação das vendas na segunda-feira em relação ao resto da semana.
	Para o modelo de previsão foi divida a venda na segunda-feira pela participação de vendas, dando um valor previsto com o total de vendas até à sexta-feira.
	O modelo de train/test performou com um RMSE de 0,25.
	Ao comparar o modelo de previsão com as vendas reais com os produtos que mais vendem na empresa, o modelo mostrou uma boa performance.
	Em sua primeira semana rodando oficialmente na empresa, o modelo de previsão apresentou os seguintes resultados:
- Foram realizadas 339 previsões de demanda por canal de venda
- 288 análises tiveram um erro menor ou igual do que 5 unidades entre vendas previstas e vendas reais
- 51 previsões erraram por mais de 5 unidades quando comparado ao real.
      		 - Dessas 51 análises, 20 erraram por mais de 10 unidades de venda 

## Conclusões: Projeto 2
	O projeto opera atualmente na empresa e já ajudou a identificar de forma rápida erros de precificação gerando impacto financeiro direto.
	O modelo de previsão auxilia além de prever a demanda para o setor comercial, estimar o impacto de ações comerciais ou de marketing realizados.

# Autor: 
Gustavo Ururahy Corrêa
guocorrea@gmail.com
https://www.linkedin.com/in/gustavo-corrêa
