-- Criação do Database
CREATE DATABASE controle_estoque_avioes;
USE controle_estoque_avioes;
-- Criação do Usuário
CREATE USER 'galmanus'@'localhost' IDENTIFIED BY 'galmanus2357';

-- Concessão de Permissões
GRANT ALL PRIVILEGES ON controle_estoque_avioes.* TO 'galmanus'@'localhost';
FLUSH PRIVILEGES;
-- Criação de Tabelas

-- Tabela: AVIOES
CREATE TABLE AVIOES (
    id_aviao INT PRIMARY KEY,
    fabricante VARCHAR(50),
    modelo VARCHAR(50),
    preco_unitario DECIMAL(10,2)
);
-- Tabela: ENTRADAS_ESTOQUE_AVIOES
CREATE TABLE ENTRADAS_ESTOQUE_AVIOES (
    id_entrada INT PRIMARY KEY,
    id_aviao INT,
    quantidade INT,
    data_entrada DATE,
    FOREIGN KEY (id_aviao) REFERENCES AVIOES(id_aviao)
);

-- Tabela: SAIDAS_ESTOQUE_AVIOES
CREATE TABLE SAIDAS_ESTOQUE_AVIOES (
    id_saida INT PRIMARY KEY,
    id_aviao INT,
    quantidade INT,
    data_saida DATE,
    FOREIGN KEY (id_aviao) REFERENCES AVIOES(id_aviao)
);

-- Inserção de Dados

-- Inserção de dados na tabela AVIOES
INSERT INTO AVIOES (id_aviao, fabricante, modelo, preco_unitario)
VALUES
    (1, 'Boeing', '747', 150000000.00),
    (2, 'Airbus', 'A320', 90000000.00),
    (3, 'Embraer', 'E190', 50000000.00);
    
    -- Inserção de dados na tabela ENTRADAS_ESTOQUE_AVIOES
INSERT INTO ENTRADAS_ESTOQUE_AVIOES (id_entrada, id_aviao, quantidade, data_entrada)
VALUES
    (1, 1, 5, '2023-11-01'),
    (2, 2, 8, '2023-11-05'),
    (3, 3, 3, '2023-11-10');
    
    -- Inserção de dados na tabela SAIDAS_ESTOQUE_AVIOES
INSERT INTO SAIDAS_ESTOQUE_AVIOES (id_saida, id_aviao, quantidade, data_saida)
VALUES
    (1, 1, 2, '2023-11-02'),
    (2, 2, 4, '2023-11-08'),
    (3, 3, 1, '2023-11-15');
-- Comandos do CRUD

-- UPDATE para modificar a quantidade em estoque de um avião
UPDATE AVIOES SET preco_unitario = 160000000.00 WHERE id_aviao = 1;

-- DELETE para remover registros (estornar uma entrada)
DELETE FROM ENTRADAS_ESTOQUE_AVIOES WHERE id_entrada = 3;
-- SELECT para listar todos os aviões em estoque
SELECT * FROM AVIOES;
-- SELECT para mostrar as operações de entrada em um determinado período

-- SELECT para calcular o saldo atual de cada avião
SELECT
    a.id_aviao,
    a.modelo,
    (COALESCE(SUM(ee.quantidade), 0) - COALESCE(SUM(se.quantidade), 0)) AS saldo_atual
FROM
    AVIOES a
LEFT JOIN ENTRADAS_ESTOQUE_AVIOES ee ON a.id_aviao = ee.id_aviao
LEFT JOIN SAIDAS_ESTOQUE_AVIOES se ON a.id_aviao = se.id_aviao
GROUP BY a.id_aviao, a.modelo;
-- SELECT para identificar aviões com estoque abaixo de um nível mínimo
SELECT * FROM AVIOES
WHERE
    (SELECT COALESCE(SUM(quantidade), 0) FROM ENTRADAS_ESTOQUE_AVIOES WHERE id_aviao = AVIOES.id_aviao)
    - (SELECT COALESCE(SUM(quantidade), 0) FROM SAIDAS_ESTOQUE_AVIOES WHERE id_aviao = AVIOES.id_aviao) < 5;
    
    -- SELECT para agrupar e contar as operações de estorno realizadas
SELECT
    id_aviao,
    COUNT(*) AS total_estornos
FROM
    (
        SELECT id_aviao FROM ENTRADAS_ESTOQUE_AVIOES WHERE id_entrada NOT IN (SELECT id_entrada FROM SAIDAS_ESTOQUE_AVIOES)
        UNION ALL
        SELECT id_aviao FROM SAIDAS_ESTOQUE_AVIOES WHERE id_saida NOT IN (SELECT id_saida FROM ENTRADAS_ESTOQUE_AVIOES)
    ) AS estornos
GROUP BY id_aviao;

