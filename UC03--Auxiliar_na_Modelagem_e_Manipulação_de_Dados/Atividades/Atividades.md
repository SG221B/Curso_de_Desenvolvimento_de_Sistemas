
## ✅ Atividades — UC03 Auxiliar na modelagem e Manipulação de Dados


### 📚 Índice de Atividades
- [Atividade 1](#-atividade-1---diagrama-er-para-sistema-de-streaming)
- [Atividade 2](#-atividade-2---sistema-para-associação-de-kart)
- [Atividade 3](#-atividade-3---filtros-avançados-em-mysql)

---

### 📝 Atividade 1 - Diagrama ER para Sistema de Streaming

**Descrição:**  
Nesta atividade, desenvolvi um Diagrama Entidade-Relacionamento (DER) no MySQL Workbench para representar as principais entidades e relações de um sistema de streaming de filmes.
O diagrama possui:

Entidades Modeladas
- *Usuário* (com vínculo obrigatório a um endereço)
- *Endereço*
- *Conteúdo* (associado a um estúdio)
- *Estúdio*
- *Visualização* (relacionamento N:N entre usuário e conteúdo)

Regras aplicadas
- Relacionamento 1:1 entre usuário e endereço  
- Relacionamento 1:N entre estúdio e conteúdo  
- Relacionamento N:N entre usuário e conteúdo (com atributos adicionais)

**Resposta:**  
![Diagrama ER](./Material/Atividade01_DER.png)


### 🖥️ Avaliação do Tutor

Resultado: **A**

---

### 📝 Atividade 2 - Sistema para Associação de Kart

**Descrição:**  
Sua empresa foi contratada para desenvolver o sistema de uma associação nacional de kart. A equipe de análise já elaborou o diagrama ER e forneceu um documento PDF com o guia da temporada. A partir desses materiais, você deverá:

1. Criar o **script de criação do banco de dados** com base no diagrama ER.
2. Criar um **script de inserção de dados** utilizando as informações contidas no guia da temporada.
3. Atualizar os registros da tabela `Etapa`:
   - Substituir **Campo Grande** por **Salvador**
   - Substituir **Londrina** por **Goiânia**
4. Remover o patrocinador da equipe **Corredores de Aço**, devido a uma rescisão contratual por questões éticas:
   - **Importante:** Execute `SET SQL_SAFE_UPDATES = 0;` para desativar a proteção contra atualizações inseguras.
5. Exibir os **dados dos pilotos**.

![Diagrama:](./Material/Atividade02.png)

[PDF:](./Material/atividade2_guia_da_temporada_de_kart.pdf)


**Resposta:**  

```sql
-- UC03 - Atividade 02
-- Aluno: Luis Fernando S. Gomes
-- Data: 18/06/2025


-- SCRIPT DE CRIAÇÃO DO BANCO DE DADOS CONFORME DIAGRAMA ER:
CREATE DATABASE KART_AT02;
USE KART_AT02;

-- TEMPORADA
CREATE TABLE Temporada (
	idTemporada INT NOT NULL AUTO_INCREMENT,
	Numero INT NOT NULL,
	PRIMARY KEY(idTemporada)
);

-- PATROCINIO
CREATE TABLE Patrocinio (
	idPatrocinio INT AUTO_INCREMENT,
 	nomePatrocinio VARCHAR(45) NOT NULL,
	PRIMARY KEY(idPatrocinio)
);

-- EQUIPE
CREATE TABLE Equipe (
	idEquipe INT NOT NULL AUTO_INCREMENT,
	Nome VARCHAR(45) NOT NULL,
	patrocinio_idPatrocinio INT UNIQUE,
	PRIMARY KEY(idEquipe),
	FOREIGN KEY(patrocinio_idPatrocinio) REFERENCES Patrocinio(idPatrocinio)
);

-- PILOTO
CREATE TABLE Piloto (
	idPiloto INT NOT NULL AUTO_INCREMENT,
	Nome VARCHAR(45) NOT NULL,
	Peso FLOAT NOT NULL,
	Capitao TINYINT NOT NULL,
	Equipe_idEquipe INT NOT NULL,
	Nacionalidade VARCHAR(45),
	PRIMARY KEY(idPiloto),
	FOREIGN KEY(Equipe_idEquipe) REFERENCES Equipe(idEquipe)
);

-- ETAPA
CREATE TABLE Etapa (
	idEtapa INT NOT NULL AUTO_INCREMENT,
	Local VARCHAR(45) NOT NULL,
	Data DATE NOT NULL,
	Hora VARCHAR(45)NOT NULL,
	Temporada_idTemporada INT NOT NULL,
	PRIMARY KEY(idEtapa),
	FOREIGN KEY(Temporada_idTemporada) REFERENCES Temporada(idTemporada)
);

-- Relacionamento N:N entre ETAPA e PILOTO
CREATE TABLE Etapa_has_Piloto (
	Etapa_idEtapa INT NOT NULL,
	Piloto_idPiloto INT NOT NULL,
	FOREIGN KEY(Etapa_idEtapa) REFERENCES Etapa(idEtapa),
	FOREIGN KEY(Piloto_idPiloto) REFERENCES Piloto(idPiloto)
);


-- SCRIPT DE INSERÇÃO DE DADOS DE ACORDO COM INFORMAÇÕES APARTIR DO PDF

-- TEMPORADA
INSERT INTO Temporada (Numero)
	VALUES (1);

-- PATROCINIO
INSERT INTO Patrocinio (nomePatrocinio)
	VALUES
	('MotorTech Brasil'),
	('Velocidade Extrema'),
	('Alta Performance'),
	('Turbo Racing'),
	('Pneus ProDrive');

-- EQUIPE
INSERT INTO Equipe (Nome, patrocinio_idPatrocinio)
	VALUES
	('Escuderia Veloz', 1),
	('Rápidos & Furiosos', 2),
	('Fênix Racing', 3),
	('Equipe Tempestade', 4),
	('Corredores de Aço', 5);

-- PILOTO
INSERT INTO Piloto (Nome, Peso, Capitao, Equipe_idEquipe, Nacionalidade)
VALUES
	('Lucas Andrade', 70.5, 1, 1, 'Brasil'),
	('Renato Figueiredo', 75.0, 0, 1, 'Brasil'),
	('Mateus Silva', 68.0, 0, 2, 'Brasil'),
	('Bruno Almeida', 78.3, 1, 2, 'Brasil'),
	('Carla Pereira', 60.0, 1, 3, 'Portugal'),
	('Gabriela Torres', 58.5, 0, 3, 'Brasil'),
	('João Costa', 80.5, 0, 4, 'Brasil'),
	('Thiago Santos', 72.5, 0, 4, 'Brasil'),
	('Mariana Gomes', 62.0, 1, 5, 'Portugal'),
	('Beatriz Lopes', 63.2, 1, 5, 'Portugal');

-- ETAPA
INSERT INTO Etapa (Local, Data, Hora, Temporada_idTemporada)
VALUES
	('São Paulo', '2024-01-15', '14:00', 1),
	('Rio de Janeiro', '2024-02-20', '16:00', 1),
	('Campo Grande', '2024-03-18', '15:00', 1),
	('Londrina', '2024-04-22', '13:00', 1),
	('Porto Alegre', '2024-05-10', '10:00', 1);


-- ALTERAR ETAPAS DE CAMPO GRANDE E LONDRINA PARA SALVADOR E GOIÂNIA
UPDATE Etapa SET Local = 'Salvador' WHERE Local = 'Campo Grande';
UPDATE Etapa SET Local = 'Goiânia' WHERE Local = 'Londrina';

-- É NECESSÁRIO EXCLUIR OS DADOS DO PATROCINADOR DA EQUIPE CORREDORES DE AÇO.
-- OBS: Desative o modo segurança para essa sessão:
SET SQL_SAFE_UPDATES = 0;
UPDATE Equipe SET patrocinio_idPatrocinio = NULL WHERE Nome = 'Corredores de Aço';

-- POR FIM, EXIBA OS DADOS DOS PILOTOS.
SELECT * FROM Piloto;

-- Entregue o arquivo da atividade em fromato compactado (rar, zip ou 7z) com o scripts
```

### 🖥️ Avaliação do Tutor

Resultado: **A**

---

### 📝 Atividade 3 - Filtros Avançados em MySQL

**Descrição:**  
Sua empresa foi contratada para desenvolver o banco de dados da TDS Cloud Gaming. O banco já foi criado e povoado, com as seguintes tabelas: Usuario, Desenvolvedora, Jogo, Categoria, JogoCategoria e Biblioteca. Agora, é necessário criar filtros de busca mais avançados utilizando as técnicas de MySQL aprendidas. As consultas devem selecionar e filtrar dados. A atividade requer o uso de comandos SELECT, com JOIN e subconsultas, conforme apropriado.


Atividade:

1 - Selecione todos os usuários cadastrados após 01 de março de 2023;
2 - Selecione todos os jogos com preço superior a 100.00;
3 - Encontre todas as desenvolvedoras que foram fundadas depois do ano 2000;
4 - Liste todos os jogos da desenvolvedora "Valve Corporation";
5 - Calcule o preço médio dos jogos na plataforma;
6 - Calcule o preço total dos jogos comprados pelo usuário "Carlos Silva";
7 - Encontre o jogo mais caro da desenvolvedora "Rockstar Games";
8 - Liste todos os jogos na categoria "RPG";
9 - Liste todos os usuários e os jogos que eles possuem na biblioteca;
10 -Encontre o número total de jogos na plataforma desenvolvidos por estúdios dos EUA.

**Resposta:**  
```sql
-- UC03 - Atividade 3
-- Aluno: Luis Fernando S. Gomes
-- Data: 23/06/25


-- PASSO 1 - DOWNLOAD E EXECUÇÃO DO SCRIPT: OK

-- SELECIONE TODOS OS USUÁRIOS CADASTRADOS APÓS 01 DE MARÇO DE 2023
SELECT * FROM Usuario WHERE data_cadastro > '2023-03-01';


-- SELECIONE TODOS OS JOGOS COM PREÇO SUPERIOR A 100.00
SELECT * FROM Jogo WHERE preco > 100.00;


-- ENCONTRE TODAS AS DESENVOLVEDORAS QUE FORAM FUNDADAS DEPOIS DO ANO 2000
SELECT * FROM Desenvolvedora WHERE ano_fundacao > '2000';


-- LISTE TODOS OS JOGOS DA DESENVOLVEDORA "VALVE CORPORATION"
-- 1º Código
SELECT J.* FROM Jogo AS J
JOIN Desenvolvedora AS D
ON J.id_desenvolvedora = D.id
WHERE D.nome = 'Valve Corporation';

-- 2º Código
SELECT * FROM Jogo
WHERE id_desenvolvedora = (
	SELECT id FROM Desenvolvedora WHERE nome = 'Valve Corporation'
    );


-- CALCULE O PREÇO MÉDIO DOS JOGOS NA PLATAFORMA
SELECT AVG(preco) AS preco_medio FROM Jogo;


-- CALCULE O PREÇO TOTAL DOS JOGOS COMPRADOS PELO USUÁRIO "CARLOS SILVA"
SELECT SUM(J.preco) AS total_gasto FROM Biblioteca AS B
JOIN Usuario AS U ON B.id_usuario = U.id
JOIN Jogo AS J ON B.id_jogo = J.id
WHERE U.nome = 'Carlos Silva';


-- ENCONTRE O JOGO MAIS CARO DA DESENVOLVEDORA "ROCKSTAR GAMES"
SELECT J.*  FROM Jogo AS J
JOIN Desenvolvedora AS D ON J.id_desenvolvedora = D.id
WHERE D.nome = 'Rockstar Games' ORDER BY J.preco DESC LIMIT 1;


-- LISTE TODOS OS JOGOS NA CATEGORIA "RPG"
SELECT J.* FROM Jogo AS J
JOIN JogoCategoria AS JC ON J.id = JC.id_jogo
JOIN Categoria AS C ON JC.id_categoria = C.id
WHERE C.nome = 'RPG';


-- LISTE TODOS OS USUÁRIOS E OS JOGOS QUE ELES POSSUEM NA BIBLIOTECA
SELECT U.nome AS usuario, J.titulo AS jogo FROM Biblioteca AS B
JOIN Usuario AS U ON B.id_usuario = U.id
JOIN Jogo AS J ON B.id_jogo = J.id ORDER BY U.nome;


-- ENCONTRE O NÚMERO TOTAL DE JOGOS NA PLATAFORMA DESENVOLVIDOS POR ESTÚDIOS DOS EUA
SELECT COUNT(*) AS total_jogos FROM Jogo AS J
JOIN Desenvolvedora AS D ON J.id_desenvolvedora = D.id
WHERE D.pais = 'EUA';

-- DICA: TODAS ESSAS QUERIES SÃO RESOLVIDAS COM SELECT, ALGUMAS SERÁ NECESSÁRIO O USO DE JOIN OU OUTRAS SUB CONSULTAS.
```

### 🖥️ Avaliação do Tutor

Resultado: ****

---
