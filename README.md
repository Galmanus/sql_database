 BANCO DE DADOS CONTROLE DE ESTOQUE DE AVIÕES



![1](https://github.com/Galmanus/sql_database/assets/60741154/1e876fdc-67e5-4ffc-bf85-c43392d53929)

![2](https://github.com/Galmanus/sql_database/assets/60741154/4dd77e12-eee9-44b2-b883-6f3147903072)

![3](https://github.com/Galmanus/sql_database/assets/60741154/add1c143-5346-447f-91c8-e1c9163bd7ae)

![4](https://github.com/Galmanus/sql_database/assets/60741154/f59341ad-4677-494a-8f59-08ed6e619712)

![5](https://github.com/Galmanus/sql_database/assets/60741154/5afa9c2a-193e-4595-9e6f-08a899a04870)

![6](https://github.com/Galmanus/sql_database/assets/60741154/c0fa202f-e375-45e1-bf5d-e80c59424877)

![7](https://github.com/Galmanus/sql_database/assets/60741154/c3778147-b0f7-4a42-a726-9c330e366609)

![8](https://github.com/Galmanus/sql_database/assets/60741154/2fec6285-2c1d-4b73-ab50-a1cdab797a1f)

![9](https://github.com/Galmanus/sql_database/assets/60741154/7480f062-9797-4c09-84b0-fd2e347afb8d)

![10](https://github.com/Galmanus/sql_database/assets/60741154/2cc2e9d7-9c83-420c-a117-ee336e95bb19)

![11](https://github.com/Galmanus/sql_database/assets/60741154/7b3c7561-2aeb-4ad3-b1cf-0e6da09b08b0)

Estrutura do Banco de Dados:

Tabela AVIOES: Armazena informações sobre os aviões, com atributos como id_aviao, fabricante, modelo e preco_unitario.

Tabela ENTRADAS_ESTOQUE_AVIOES: Registra operações de entrada de aviões no estoque, com atributos como id_entrada, id_aviao, quantidade e data_entrada.

Tabela SAIDAS_ESTOQUE_AVIOES: Registra operações de saída de aviões do estoque, com atributos como id_saida, id_aviao, quantidade e data_saida.


Relatório:

Listagem de todos os aviões em estoque.

Operações de entrada em um determinado período.

Operações de saída de um avião específico.

Saldo atual de cada avião.

Identificação de aviões com estoque abaixo do nível mínimo.

Agrupamento e contagem de operações de estorno realizadas.

