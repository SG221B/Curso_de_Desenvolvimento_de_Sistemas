
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

Manipulação de dados: inclusão, atualização e exclusão de dados.  
Comandos abordados: `INSERT`, `UPDATE`, `DELETE`.

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
Existem várias formas de utilizá-la.

### Sintaxe básica

```sql
INSERT INTO nome_da_tabela VALUES (valores);
```

- Os valores devem seguir a ordem e o tipo de dados das colunas da tabela.

#### Exemplos

```sql
INSERT INTO tabela VALUES (1, 2, 3);
INSERT INTO tabela VALUES ('Valor 1', 'Valor 2', 'Valor 3');
INSERT INTO tabela VALUES (null, null, null);
```

### Inserção sem colunas (não recomendado)

```sql
INSERT INTO curso VALUES (
    1,
    'Técnico em Desenvolvimento de Sistemas',
    'Prepara o aluno para exercer funções técnicas...'
);
SELECT * FROM curso;
```

> ⚠️ O `AUTO_INCREMENT` pode não funcionar corretamente.

### Inserção com colunas (recomendado)

```sql
INSERT INTO curso(nome) VALUES ('Técnico em Informática para Internet');
SELECT * FROM curso;
```

### Inserção múltipla

```sql
INSERT INTO curso(nome) VALUES
('Técnico em Administração'),
('Técnico em Contabilidade'),
('Técnico em Design de Interiores');
SELECT * FROM curso;
```

### Inserção de datas

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

### Sintaxe

```sql
UPDATE nome_da_tabela
SET coluna1 = valor1, coluna2 = valor2, ...
WHERE condição;
```

### Exemplos

```sql
UPDATE aluno SET curso_id = 2 WHERE id = 2;

UPDATE aluno
SET curso_id = 2
WHERE nome LIKE 'A%';

UPDATE aluno
SET curso_id = 2
WHERE data_nascimento >= '1998-01-01';

UPDATE aluno SET
sobrenome = 'Ferreira',
data_nascimento = '1983-09-15'
WHERE id = 4;

UPDATE aluno SET curso_id = 2;
```

> ⚠️ A ausência da cláusula `WHERE` atualiza todos os registros da tabela.

---

## Lição 3 – Exclusão de dados: `DELETE`

### Sintaxe

```sql
DELETE FROM nome_da_tabela WHERE condição;
```

- A cláusula `WHERE` é essencial para evitar exclusão total.
- Para excluir todos os registros, omita o `WHERE`, mas com muito cuidado.

#### Exemplos

```sql
DELETE FROM curso WHERE id = 5;
DELETE FROM aluno WHERE nome = 'Alice' AND id = 1;
DELETE FROM aluno WHERE nome = 'Alice' OR id = 1;
```

### Problemas com chaves estrangeiras

```sql
DELETE FROM curso WHERE id = 1;
-- Erro: chave estrangeira impede exclusão
```

### Soluções:

#### 1. Quebrar a referência antes

```sql
UPDATE aluno SET curso_id = NULL WHERE curso_id = 1;
DELETE FROM curso WHERE id = 1;
```

#### 2. Exclusão em cascata

```sql
CREATE TABLE aluno2 (
    id INT AUTO_INCREMENT,
    nome VARCHAR(30),
    sobrenome VARCHAR(30),
    data_nascimento DATE,
    curso_id INT,
    PRIMARY KEY (id),
    FOREIGN KEY (curso_id) REFERENCES curso(id) ON DELETE CASCADE
);

INSERT INTO curso (id, nome) VALUES (12, 'Técnico em Informática');
INSERT INTO aluno2 (nome, curso_id) VALUES ('Daltron', 12), ('Wilson', 12);

DELETE FROM curso WHERE id = 12;
SELECT * FROM curso;
SELECT * FROM aluno2;
```

> ⚠️ A exclusão em cascata pode apagar muitos dados acidentalmente.

### Preservação de registros

- Evite exclusão de dados com `DELETE`.
- Use uma coluna `status` com valores como `'A'` (ativo) ou `'I'` (inativo).

```sql
ALTER TABLE aluno ADD status CHAR(1);
UPDATE aluno SET status = 'I' WHERE id = 3;
SELECT * FROM aluno;
```
