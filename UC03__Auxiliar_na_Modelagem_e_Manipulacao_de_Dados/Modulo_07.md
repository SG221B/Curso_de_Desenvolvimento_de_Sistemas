## 📅 11/06/2025

### 🧠 Tópicos estudados
- Conceitos básicos da teoria dos conjuntos
- Operações com conjuntos: união, interseção e diferença.

### ✍️ Conteúdo
*(você preenche)*

### 📌 Resumo pessoal
*(você preenche)*

### 📚 Lições
1. ...
2. ...

### 💡 Dica ou observação
*(opcional)*


CREATE DATABASE super;

USE super;
CREATE TABLE Produtos (
	idProduto INT NOT NULL AUTO_INCREMENT,
    NomeProduto VARCHAR(200),
    CategoriaProduto VARCHAR(200),
    ValorVendaProduto DOUBLE(9,2),
    QuantidadeProduto INT,
    PRIMARY KEY(idProduto)
);

INSERT INTO Produtos
(NomeProduto, CategoriaProduto, ValorVendaProduto, QuantidadeProduto)
VALUES
('Refrigerante','Bebidas','5.50',300),
('Arroz 5kg','Mercearia','8.50',100),
('Feijão','Mercearia','6.50',800),
('Detergente','Limpeza','2.10',100),
('Leite','Laticínios','2.70',600),
('Bolacha recheada',NULL,'1.50',200),
('Leite condensado','Mercearia','4.50',500);

			-- CONSULTA DE DADOS --
            
-- Seleciona todas as colunas da tabela Produto:
SELECT * FROM Produtos;


-- Seleciona especificaente apanas as colunas NomeProduto e ValorVedaProduto:
SELECT NomeProduto, ValorVendaProduto FROM Produtos;


-- Condição WHERE:
-- Seleciona dentre todas as colunas, a linha cujo NomeProduto seja 'Leite':
SELECT * FROM Produtos WHERE NomeProduto = 'Leite';


-- Seleciona entre as colunas NomeProduto e ValorVendaProduto a linha cujo NomeProduto seja 'Leite':
SELECT NomeProduto, ValorVendaProduto FROM Produtos WHERE NomeProduto = 'Leite';


-- Seleciona entre as colunas NomeProduto e ValorVendaProduto a linha cujo NomeProduto seja 'Leite':
SELECT NomeProduto, CategoriaProduto, ValorVendaProduto FROM Produtos WHERE CategoriaProduto <> 'Mercearia';


		-- Operadores lógicos AND, OR, NOT --

-- Seleciona todas as colunas de Produtos onde ValorVendaProduto é igual a 1.50 e (támbem) QuantidadeProduto igual a 200;:
SELECT * FROM Produtos WHERE ValorVendaProduto = 1.50 AND QuantidadeProduto = 200;


SELECT * FROM Produtos WHERE Categoriaproduto = 'Limpeza' OR ValorVendaProduto = 5.50;


-- Busca por produtos das categorias "limpeza" ou "mercearia" com valor de venda igual a 6.50:
SELECT * FROM Produtos WHERE (CategoriaProduto = 'Limpeza' OR CategoriaProduto = 'Mercearia') AND ValorVendaProduto = 6.50;


-- Lista todos os produtos, exceto os da categoria “mercearia”:
SELECT * FROM Produtos WHERE NOT CategoriaProduto = 'Mercearia';

		-- Operadores de comparação --

SELECT * FROM Produtos WHERE QuantidadeProduto >= 300;

SELECT * FROM Produtos WHERE ValorVendaProduto <= 5;

		-- Operador BETWEEN --

SELECT * FROM Produtos WHERE ValorVendaProduto BETWEEN 5 AND 10;

		-- Operadores de existência IN, NOT IN --

SELECT * FROM Produtos WHERE CategoriaProduto IN ('Limpeza','Bebidas','Laticínios');

SELECT * FROM Produtos WHERE CategoriaProduto NOT IN ('Limpeza','Bebidas','Laticínios');

		-- Operador LIKE --

SELECT NomeProduto, ValorVendaProduto FROM Produtos WHERE NomeProduto LIKE '%leite%';

		-- Operador IS NULL e IS NOT NULL --

SELECT * FROM Produtos WHERE CategoriaProduto IS NULL;

SELECT * FROM Produtos WHERE CategoriaProduto IS NOT NULL;

-- Operador de ihualdade e diferença ignoral valores NULL.
-- Para evitar isso pode se utilizar OR:
SELECT nomeProduto, categoriaProduto, valorVendaProduto FROM Produtos WHERE categoriaProduto <> 'Mercearia' OR categoriaProduto IS NULL;


		-- Alias --
-- A criação de um alias com AS é temporária e só existe enquanto durar a consulta para a qual foram criados

SELECT NomeProduto AS nome, ValorVendaProduto AS valor FROM Produtos;


		-- Operadores aritméticos --

-- Multiplicação:
SELECT (ValorVendaProduto*QuantidadeProduto) AS Valor_Total FROM Produtos;


-- Divisão:
SELECT (QuantidadeProduto/ValorVendaProduto) AS Valor_Divisao FROM Produtos;


-- Subtração:
SELECT (QuantidadeProduto - ValorVendaProduto) AS Valor_Subtracao FROM Produtos;


-- Adição:
SELECT (QuantidadeProduto + ValorVendaProduto) AS Valor_Soma FROM Produtos;

-- Porcentagem:
SELECT (ValorVendaProduto * 1.2) AS Valor_Reajustado FROM Produtos;

		--  ORDER BY --
-- ASC:
SELECT * FROM Produtos ORDER BY NomeProduto;

-- DESC:
SELECT * FROM Produtos ORDER BY NomeProduto DESC;

		-- Funções internas básicas --
 -- COUNT:
 -- Caso queira saber quantos de seus produtos tem o nome “leite”, você pode fazer esta consulta:
 SELECT COUNT(NomeProduto) FROM Produtos WHERE NomeProduto LIKE '%leite%';
 
 
-- AVG:
 -- É uma função que retorna o valor médio (média) de uma coluna
 SELECT AVG(ValorVendaProduto) FROM Produtos;
 
 
 -- SUM:
 -- É usado para encontrar a soma total de uma determinada coluna.
 -- Por exemplo, se você quiser ver a quantidade de produtos do supermercado, pode executar esta consulta:
 SELECT SUM(Quantidadeproduto) FROM Produtos;
 
SELECT MIN(nomeProduto) FROM Produtos;
  
  
 -- MIN:
 -- É usado para encontrar o menor valor em uma coluna especificada.
 -- Você pode usar essa consulta para ver qual é o valor do produto mais barato.
 SELECT MIN(ValorVendaProduto) FROM Produtos;
 
 -- MAX:
 -- É usado para encontrar o maior valor numérico em uma determinada coluna.
 -- Você pode usar essa consulta para obter o valor do produto mais caro.
 SELECT MAX(ValorVendaProduto) FROM Produtos;
 
 SELECT MAX(nomeProduto) FROM Produtos;
 
		-- Subconsulta em SQL (subquery) --
        
CREATE TABLE Vendas (
	idVenda INT AUTO_INCREMENT,
    idProduto INT,
    quantidadeVendida INT,
    valorVendido DOUBLE(9,2),
    dataVenda DATE,
    PRIMARY KEY(idVenda)
);

INSERT INTO Vendas
(idProduto, quantidadeVendida, valorVendido, dataVenda)
VALUES
(2,10,8.5,'2022-12-31'),
(2,15,8.5,'2022-01-01'),
(1,3,5.50,'2022-01-15');


-- Consulta simples

SELECT * FROM Vendas;

-- Subconsulta como filtro de uma consulta (IN)

SELECT MAX(valorVendaproduto) FROM Produtos; -- Irá retornar apenas o vlaor Maximo do produto (8.50), mas não os outros valores da linha.

-- Então:
SELECT * FROM Produtos WHERE valorVendaProduto = (SELECT MAX(valorVendaproduto) FROM Produtos); -- Irá retornar toda a linha do valor máximo.

SELECT * FROM Produtos WHERE valorVendaProduto <> (SELECT MAX(valorVendaproduto) FROM produtos);

SELECT nomeProduto FROM Produtos WHERE idProduto IN (SELECT idProduto FROM Vendas);


-- Subconsulta com uma nova coluna de consulta (SELECT (...) AS Novo_Campo)
USE super;

SELECT P.nomeProduto,
	(SELECT SUM(V.quantidadeVendida * V.valorVendido)
    FROM Vendas AS V
    WHERE V.idProduto = P.idProduto) AS Total_Vendido
FROM Produtos AS P;

 



