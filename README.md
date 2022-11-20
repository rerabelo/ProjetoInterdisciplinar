# Projeto Interdisciplinar
O projeto descrito nesse repositório é requisito parcial para conclusão de atividades do segundo semestre do curso de Especialização em Ciência de Dados do IFSP Campinas. A atividade proposta no semestre prevê o desenvolvimento de uma solução de aprendizado de máquina cujo treinamento e processamento deverão ser realizados em ambiente de nuvem, com processamento distribuído, explorando o uso de paralelismo.

**Tema do projeto:** Risco de Inadimplência de Crédito Residencial

**Alunos:** Gabriel Trindade dos Santos (CP3016749) e Renata Santos Rabelo (CP301634X)

**Banco de dados de origem:** Kaggle (https://www.kaggle.com/c/home-credit-default-risk#description)

**Requisitos do projeto:** [*Descrição dos requisitos*](./Requisitos%20do%20projeto)

# Sumário

* [Introdução](#intro)
* [Descrição dos dados](#descri)
* [Workflow](#work)
* [Infraestrutura](#infra)
* [Descrição dos notebooks](#note)
* [EDA](##EDA)
* [Machine Leaning](##ML)


# Introdução <a id='intro'></a> 

Muitas pessoas lutam para obter empréstimos devido a históricos de crédito insuficientes ou inexistentes. A fim de garantir que essa população carente tenha uma experiência de empréstimo positiva, o Home Credit faz uso de uma variedade de dados para prever as habilidades de reembolso de seus clientes. Nesse cenário, a empresa desafia Kagglers a ajudá-los a desbloquear todo o potencial de seus dados, e garantir que clientes capazes de reembolso não sejam rejeitados em uma análise de crédito. Pensando nisso, implementamos em ambiente de nuvem uma solução de aprendizado de máquina com foco na resolução do desafio que pudesse também atender aos requisitos do projeto interdisciplinar proposto no segundo semestre do curso de Especialização em Ciência de Dados do IFSP Campinas. Os requisitos do projeto, bem como detalhes relacionadas ao desenvolvimento da atividade são disponibilizados nesse repositório, e serão apresentados no formato de uma apresentação de 15 mim como requisito parcial para conclusão do semestre.

# Descrição dos dados <a id='descri'></a> 

A lista abaixo descreve cada um dos arquivos do desafio:

**1. application_{train|test}.csv:** Esta é a tabela principal do banco de dados, e está dividida em dois arquivos, um para Train (com TARGET) e um para Test (sem TARGET). Cada linha da tabela representa um empréstimo. A tabela complementar **Home_credit_columns descriptions.csv** traz a descrição de cada uma das colunas presentes na tabela principal. ***Nota:** TARGET = 0 => o empréstimo foi reembolsado, TARGET = 1 => o empréstimo não foi reembolsado*.

**2. bureau.csv:** Todos os créditos anteriores do cliente fornecidos por outras instituições financeiras que foram reportados ao Credit Bureau (para clientes que possuem empréstimo na amostra). Para cada empréstimo na amostra, há tantas linhas quanto o número de créditos que o cliente tinha no Credit Bureau antes da data da solicitação.

**3. bureau_balance.csv:** Saldos mensais de créditos anteriores no Credit Bureau. Esta tabela tem uma linha para cada mês de histórico de cada crédito anterior relatado ao Credit Bureau, ou seja, a tabela tem linhas (#empréstimos na amostra # de créditos anteriores relativos # de meses em que há algum histórico observável para os créditos anteriores).

**4. POS_CASH_balance.csv:** Instantâneos do saldo mensal do POS anterior (ponto de venda) e empréstimos em dinheiro que o requerente tinha com Crédito Habitação. Esta tabela tem uma linha para cada mês de histórico de todos os créditos anteriores em Crédito à Habitação (crédito ao consumo e empréstimos em dinheiro) relacionados com empréstimos na amostra – ou seja, a tabela tem (#empréstimos na amostra # de créditos anteriores relativos # de meses em que há algum histórico observável para as linhas de créditos anteriores.

**5. credit_card_balance.csv:** instantâneos do saldo mensal dos cartões de crédito anteriores que o requerente tem com Crédito Habitação. Esta tabela tem uma linha para cada mês de histórico de todos os créditos anteriores em Crédito à Habitação (crédito ao consumidor e empréstimos em dinheiro) relacionados a empréstimos na amostra – ou seja, a tabela tem (#empréstimos na amostra # de cartões de crédito anteriores relativos # de meses em que há algum histórico observável para as linhas de cartão de crédito anteriores.

**6. previous_application.csv:** Todos os pedidos anteriores de crédito à habitação de clientes que têm empréstimos na amostra. Há uma linha para cada solicitação anterior relacionada a empréstimos no banco de dados.

**7. installments_payments.csv:** Histórico de reembolso dos créditos anteriormente desembolsados em Crédito Habitação relacionados com os empréstimos da amostra. Há a) uma linha para cada pagamento que foi feito mais b) uma linha para cada pagamento perdido. Uma linha equivale a um pagamento de uma prestação OU a uma prestação correspondente a um pagamento de um crédito de Crédito Habitação anterior relacionado com empréstimos da amostra.

As tabelas suplementares (previous_application, bureau_balance, installments_payments, etc) não poduram ser mescladas diretamente à tabela principal, porque os requerentes têm vários números de empréstimos anteriores e diferentes comprimentos de histórico de crédito. Assim, novos parâmetros só poderiam ser obtidos agrupando as tabelas pelas IDs (SK_ID_CURR, SK_ID_PREV e SK_ID_BUREAU) e calculando novas métricas sobre contas diferentes e registros de meses diferentes. O problema que encontramos ao tentar explorar essa possibilidade é que algumas contas e registros podem ter um peso maior que outros, e é difícil definir uma regra que possa aplicar pesos a cada registro, por exemplo. Abaixo descrevemos as IDs que conectam os dataframes fornecidos pela Home Credit.

**SK_ID_CURR** está conectando os dataframes application_train|test com bureau, previous_application e também com dataframes POS_CASH_balance, installments_payments e credit_card_balance. 

**SK_ID_PREV** conecta os dataframes previous_application com POS_CASH_balance, installments_payments e credit_card_balance. 

**SK_ID_BUREAU** conecta o dataframe bureau com o dataframe bureau_balance.


# Workflow <a id='work'></a>

# Infraestrutura <a id='infra'></a>

# Descrição dos notebboks <a id='note'></a>

## EDA <a id='EDA'></a>

## Machine learning <a id='ML'></a>
