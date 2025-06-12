# Módulo 06 - Manipulação de Dados com SQL

## Tópicos estudados

- Introdução à manipulação de dados
- Comandos SQL: `INSERT`, `UPDATE`, `DELETE`
- Criação de base de dados e tabelas
- Inserção de dados em tabelas com e sem especificação de colunas
- Inserção múltipla de registros
- Inserção de datas e chaves estrangeiras
- Atualização de registros com `UPDATE`

## Conteúdo

### Introdução

Manipulação de dados: inclusão, atualização e exclusão de dados  
Comandos abordados: `INSERT`, `UPDATE`, `DELETE` 

Para o aprendizado, vamos trabalhar com a seguinte base de dados:

```sql
DROP DATABASE IF EXISTS senac_ead;

-- Criar banco de dados: senac_ead
CREATE DATABASE senac_ead;
USE senac_ead;

-- Criar tabela curso
CREATE TABLE curso (
	id INT AUTO_INCREMENT,
	nome VARCHAR(150),
	descricao TEXT,
	PRIMARY KEY(id)
);

-- Criar tabela aluno
CREATE TABLE aluno (
	id INT AUTO_INCREMENT,
	nome VARCHAR(30),
	sobrenome VARCHAR(30),
	data_nascimento DATE,
	curso_id INT,
	PRIMARY KEY(id),
	FOREIGN KEY(curso_id) REFERENCES curso(id)
);
```

---

## Lição 1 – Inclusão de dados: `INSERT`

A instrução `INSERT` ou `INSERT INTO` é usada para inserir dados em uma tabela.
Existem várias formas de utilizá-la, com diferentes níveis de especificidade.

### Sintaxe básica

```sql
INSERT INTO nome_da_tabela VALUES (valores);
```

- Os valores devem seguir a ordem e o tipo de dados das colunas da tabela.

#### Exemplo com números

```sql
INSERT INTO tabela VALUES (1, 2, 3);
```

#### Exemplo com strings

```sql
INSERT INTO tabela VALUES ('Valor 1', 'Valor 2', 'Valor 3');
```

#### Exemplo com `NULL`

```sql
INSERT INTO tabela VALUES (null, null, null);
```

### Exemplos práticos

#### Inserção sem colunas (não recomendado)

```sql
INSERT INTO curso VALUES (
	1,
	'Técnico em Desenvolvimento de Sistemas',
	'Prepara o aluno para exercer funções técnicas, como: administração do sistema de banco de dados,
	desenvolver software, programar rotinas de sistema utilizando linguagens e técnicas de programação,
	programação de sistemas para desktop e para web, entre outras atividades.'
);

SELECT * FROM curso;
```

> ⚠️ Ao usar `INSERT` sem especificar colunas, o `AUTO_INCREMENT` não é utilizado corretamente.

### Inserção com colunas (recomendado)

```sql
INSERT INTO curso(nome) VALUES ('Técnico em Informática para Internet');
SELECT * FROM curso;
```

Veja que desta vez informamos a coluna a qual será atribuído o valor:

INSERT INTO curso **(nome)** VALUES ('Técnico em Informática para Internet');



### Inserção múltipla de registros

```sql
INSERT INTO curso(nome) VALUES
('Técnico em Administração'),
('Técnico em Contabilidade'),
('Técnico em Design de Interiores');

SELECT * FROM curso;
```

### Inserção de datas

Formato: `AAAA-MM-DD` ou `AA-MM-DD`

```sql
INSERT INTO aluno(nome, sobrenome, data_nascimento) VALUES ('Alice', 'Goçalves', '1998-10-18');
INSERT INTO aluno(nome, sobrenome, data_nascimento) VALUES ('Eduardo', 'Machado', '98-07-16');
INSERT INTO aluno(nome, sobrenome, data_nascimento) VALUES ('Vitória', 'Prestes', '1997-2-15');

SELECT * FROM aluno;
```

### Inserção com chave estrangeira

```sql
INSERT INTO aluno(nome, curso_id) VALUES ('Alex', 1);
SELECT * FROM aluno;
```

---

## Lição 2 – Atualização de Dados: `UPDATE`

O comando `UPDATE` é utilizado para modificar dados existentes na tabela.

### Sintaxe

```sql
UPDATE nome_da_tabela
SET coluna1 = valor1, coluna2 = valor2, ...
WHERE condição;
```

### Exemplos

#### Atualizar uma única coluna

```sql
UPDATE aluno SET curso_id = 2 WHERE id = 2;
```

#### Atualização com condições

```sql
UPDATE aluno
SET curso_id = 2
WHERE nome LIKE 'A%';

UPDATE aluno
SET curso_id = 2
WHERE data_nascimento >= '1998-01-01';
```

#### Atualizar várias colunas

```sql
UPDATE aluno SET
sobrenome = 'Ferreira',
data_nascimento = '1983-09-15'
WHERE id = 4;

SELECT * FROM aluno;
```

#### Atualizar todos os registros (com cuidado)

```sql
UPDATE aluno SET curso_id = 2;
```

> ⚠️ A ausência da cláusula `WHERE` atualiza **todos** os registros da tabela. Use com cautela!

