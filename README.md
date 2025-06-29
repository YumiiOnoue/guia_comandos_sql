# Guia de Comandos SQL
Este guia reúne os principais comandos SQL para consultas, manipulação e definição de dados.

## Para criar tabela

```sql
CREATE TABLE nome_da_tabela (
    coluna1 TIPO_DADO restricoes_coluna,
    coluna2 TIPO_DADO restricoes_coluna,
    coluna3 TIPO_DADO restricoes_coluna,
    restricoes_tabela -- como chaves primárias e estrangeiras
);

-- Como inserir dados
INSERT INTO nome_da_tabela
VALUES (valor1, valor2, valor3, ...);
```

## Comandos básicos

```sql 
-- Para retornar todas as colunas 
SELECT *
FROM nome_da_tabela

-- Para retornar coluna 1 e coluna 2
SELECT coluna1, coluna2
FROM nome_da_tabela
WHERE condicao;

-- Para retornar valores únicos
SELECT DISTINCT coluna
FROM nome_da_tabela;

-- Para alterar o nome da coluna
SELECT coluna1 AS "Nome da Coluna", coluna2 AS "Outra Coluna"
FROM nome_da_tabela;

-- Para filtrar
SELECT *
FROM nome_da_tabela
WHERE idade > 30;
```

Operadores de Comparação: =, != (ou <>), >, <, >=, <=.

Operadores Lógicos: AND, OR, NOT.

```sql
-- Usado quando não lembramos a palavra completa
SELECT *
FROM clientes
WHERE nome LIKE 'A%'; -- Nomes que começam com 'A'

-- Especifica múltiplos valores possíveis para uma condição WHERE
SELECT *
FROM produtos
WHERE categoria IN ('Eletrônicos', 'Roupas');

-- Seleciona valores dentro de um determinado intervalo
SELECT *
FROM vendas
WHERE data_venda BETWEEN '2023-01-01' AND '2023-12-31'

-- Verifica se um valor é nulo ou não
SELECT *
FROM usuarios
WHERE email IS NULL;

-- Agrupa linhas que têm os mesmos valores em colunas especificadas em um conjunto de linhas de resumo.
-- Geralmente usado com funções de agregação.
SELECT categoria, 
	COUNT(*) AS total_produtos
FROM produtos
GROUP BY categoria;

-- Filtra grupos criados pelo GROUP BY.
SELECT categoria, 
	AVG(preco) AS preco_medio
FROM produtos
GROUP BY categoria
HAVING AVG(preco) > 50;

-- ASC e DESC classifica os resultados em ordem crescente ou decrescente
SELECT *
FROM vendas
ORDER BY data_venda DESC
``` 

LIMIT / TOP: Limita o número de registros retornados. LIMIT é comum em MySQL, PostgreSQL, SQLite; TOP é comum em SQL Server.

```sql
-- MySQL/PostgreSQL
SELECT *
FROM clientes
LIMIT 10;

-- SQL Server
SELECT TOP 10 *
FROM clientes;
```

## Unindo Tabelas

Uma JOIN é uma cláusula SQL usada para combinar linhas de duas ou mais tabelas com base em uma coluna relacionada

* INNER JOIN (retorna registros com valores correspondentes em ambas as tabelas)

```sql
SELECT
  tab_A.name AS tab_A_name,
  tab_B.name AS tab_B_name
FROM
  tabela_A AS tab_A
INNER JOIN
  tabela_B AS tab_B
  ON tab_A.id = tab_B.id
```

* LEFT JOIN (retorna todos os registros da tabela da esquerda e somente os registros correspondentes da tabela da direita)

```sql
SELECT
  tab_A.name AS tab_A_name,
  tab_B.name AS tab_B_name
FROM
  tabela_A AS tab_A
LEFT JOIN
  tabela_B AS tab_B
  ON tab_A.id = tab_B.id
```

* RIGHT JOIN (retorna todos os registros da tabela da direita e apenas os registros correspondentes da tabela da esquerda)

```sql
SELECT
  tab_A.name AS tab_A_name,
  tab_B.name AS tab_B_name
FROM
  tabela_A AS tab_A
RIGHT JOIN
  tabela_B AS tab_B
  ON tab_A.id = tab_B.id
```

## Subconsultas

Subconsulta é uma consulta dentro de outra consulta, geralmente utilizada para filtrar ou manipular dados de forma mais complexa. Ela pode aparecer em várias partes de uma instrução SQL, como dentro da cláusula WHERE, FROM, SELECT, ou HAVING

```sql
-- em desenvolvimento
```

---
Qualquer dúvida ou sugestão será muito bem-vinda! 😊
