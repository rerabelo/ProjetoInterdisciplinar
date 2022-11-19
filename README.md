# Projeto Interdisciplinar - Risco de Inadimplência de Crédito Residencial
O projeto descrito nesse repositório é requisito parcial para conclusão de atividades do segundo semestre do curso de Especialização em Ciência de Dados do IFSP Campinas. 

**Tema do projeto:** Risco de Inadimplência de Crédito Residencial

**Alunos:** Renata Santos Rabelo
        Gabriel Trindade dos Santos

# Sumário

# Introdução

Muitas pessoas lutam para obter empréstimos devido a históricos de crédito insuficientes ou inexistentes, e a fim de garantir que essa população carente tenha uma experiência de empréstimo positiva, o Home Credit faz uso de uma variedade de dados alternativos - incluindo informações de telecomunicações e transacionais - para prever as habilidades de reembolso de seus clientes. 
Nesse cenário, a empresa também desafia cientistas e programadores a ajudá-los a desbloquear todo o potencial de seus dados, e garantir que seus clientes capazes de reembolso não sejam rejeitados.
Pensando nisso, e com base nos dados disponibilizados pela Home Credit na plataforma do Kaggle (https://www.kaggle.com/c/home-credit-default-risk#description), buscamos implementar em núvem, algums modelos de ML (Machine Learning) com o objetivo de prever os clientes que conseguiriam ou não reembolsar o empréstimo.


# Descrição dos dados

A lista abaixo descreve cada um dos arquivos fornecidos no desafio:

**1. application_{train|test}.csv:** Esta é a tabela principal do banco de dados, e está dividida em dois arquivos, um para Train (com TARGET) e um para Test (sem TARGET). Cada linha da tabela representa um empréstimo. A tabela complementar **Home_credit_columns descriptions.csv** traz a descrição de cada uma das colunas presentes na tabela principal

**2. bureau.csv:** Todos os créditos anteriores do cliente fornecidos por outras instituições financeiras que foram reportados ao Credit Bureau (para clientes que possuem empréstimo na amostra). Para cada empréstimo na amostra, há tantas linhas quanto o número de créditos que o cliente tinha no Credit Bureau antes da data da solicitação.

**3. bureau_balance.csv:** Saldos mensais de créditos anteriores no Credit Bureau. Esta tabela tem uma linha para cada mês de histórico de cada crédito anterior relatado ao Credit Bureau, ou seja, a tabela tem linhas (#empréstimos na amostra # de créditos anteriores relativos # de meses em que há algum histórico observável para os créditos anteriores).

**4. POS_CASH_balance.csv:** Instantâneos do saldo mensal do POS anterior (ponto de venda) e empréstimos em dinheiro que o requerente tinha com Crédito Habitação. Esta tabela tem uma linha para cada mês de histórico de todos os créditos anteriores em Crédito à Habitação (crédito ao consumo e empréstimos em dinheiro) relacionados com empréstimos na amostra – ou seja, a tabela tem (#empréstimos na amostra # de créditos anteriores relativos # de meses em que há algum histórico observável para as linhas de créditos anteriores.

**5. credit_card_balance.csv:** instantâneos do saldo mensal dos cartões de crédito anteriores que o requerente tem com Crédito Habitação. Esta tabela tem uma linha para cada mês de histórico de todos os créditos anteriores em Crédito à Habitação (crédito ao consumidor e empréstimos em dinheiro) relacionados a empréstimos na amostra – ou seja, a tabela tem (#empréstimos na amostra # de cartões de crédito anteriores relativos # de meses em que há algum histórico observável para as linhas de cartão de crédito anteriores.

**6. previous_application.csv:** Todos os pedidos anteriores de crédito à habitação de clientes que têm empréstimos na amostra. Há uma linha para cada solicitação anterior relacionada a empréstimos no banco de dados.

**7. installments_payments.csv:** Histórico de reembolso dos créditos anteriormente desembolsados em Crédito Habitação relacionados com os empréstimos da amostra. Há a) uma linha para cada pagamento que foi feito mais b) uma linha para cada pagamento perdido. Uma linha equivale a um pagamento de uma prestação OU a uma prestação correspondente a um pagamento de um crédito de Crédito Habitação anterior relacionado com empréstimos da amostra.

As tabelas suplementares (previous_application, bureau_balance, installments_payments, etc) não podem ser mescladas diretamente à tabela principal, porque os requerentes têm vários números de empréstimos anteriores e diferentes comprimentos de histórico de crédito. Assim, novos parâmetros só poderiam ser obtidos agrupando as tabelas pelo ID e calculando novas métricas sobre contas diferentes e registros de meses diferentes. O problema que encontramos ao tentar explorar essa possibilidade é que algumas contas e registros podem ter um peso maior que outros, e é difícil definir uma regra que possa aplicar pesos a cada registro, por exemplo.

# Workflow

# Infraestrutura
