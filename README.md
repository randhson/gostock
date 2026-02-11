# GoStock (Microserviço de Inventário)

🏗️ Projeto: GoStock (Microserviço de Inventário)

## Sprint 1: O Motor e a Estrutura (CLI Inicial)

Nesta fase, você vai sair do zero e entender como o Go organiza dados sem usar classes.

O que construir: Uma ferramenta de linha de comando que permite cadastrar produtos (ID, Nome, Preço, Quantidade) em uma lista em memória.

O que você vai aprender na prática:

* Iniciar o projeto com "***go mod init***"
* Definir a entidade Product usando Structs.
* Manipular listas usando Slices.
* Implementar uma função de busca que retorna o produto ou um erro customizado.

**Desafio Mão na Massa:** Crie uma função que recebe um Slice de produtos e retorna apenas os que estão com estoque abaixo de 5 unidades.

## Sprint 2: Flexibilidade com Interfaces e Performance

Aqui você vai refatorar o código para que ele suporte diferentes tipos de armazenamento, preparando o terreno para o Banco de Dados.

O que construir: Criar um contrato (Interface) de "Repositório". O seu código principal não deve saber se o estoque está num Array ou num Banco de Dados.

O que você vai aprender na prática:

* Ponteiros: Usar *Product para atualizar a quantidade de estoque de forma eficiente, alterando o valor original e não uma cópia
* Interfaces Implícitas: Criar uma interface StockStorage e fazer sua struct de memória satisfazê-la sem usar palavras-chave como "**implements**".

**Desafio Mão na Massa:** Implementar o método UpdateStock(id int, qty int) que usa ponteiros para refletir a mudança imediatamente.

## Sprint 3: O "Pulo do Gato" - Concorrência e Resiliência

Este é o diferencial do Go. Vamos simular um cenário de checkout onde milhares de pessoas tentam baixar o estoque ao mesmo tempo.

O que construir: Um "Processador de Lote". Imagine que você recebeu um arquivo CSV com 10.000 atualizações de estoque e precisa processar isso o mais rápido possível.

O que você vai aprender na prática:

* Goroutines: Disparar o processamento de cada linha em paralelo com "*go func()*".
* Channels: Usar canais para coletar os resultados das atualizações e evitar "Race Conditions" (condições de corrida).
* WaitGroups: Garantir que o programa só feche quando todos os processamentos terminarem.

**Desafio Mão na Massa:** Criar um "Worker Pool" simples: apenas 5 funções rodando simultaneamente processando uma fila de 100 itens.

## Sprint 4: Produção - API REST e Persistência
Agora vamos colocar o GoStock no mundo real, expondo endpoints e salvando no Postgres (que você já domina).

O que construir: Uma API que recebe um JSON de venda e abate o estoque no banco de dados.

O que você vai aprender na prática:

* Net/Http: Criar rotas sem frameworks pesados.
* JSON Tags: Aprender como o Go mapeia json:"product_id" para as variáveis da sua struct.
* Conexão com Postgres: Usar a biblioteca "**pgx**" para executar SQL puro (muito comum em Go pela performance).

**Desafio Mão na Massa:** Criar um endpoint GET /inventory que retorna o estado atual do estoque em formato JSON.

