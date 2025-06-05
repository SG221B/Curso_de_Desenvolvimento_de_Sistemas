# 📘 UC03 – Auxiliar na Modelagem e Manipulação de Dados

## 📝 Atividade 1 – Diagrama ER de um sistema de streaming

### 🎯 Objetivo
Desenvolver, utilizando a interface do **MySQL Workbench**, um **Diagrama Entidade-Relacionamento (DER)** que represente as principais entidades e relacionamentos de um sistema de streaming de filmes.

---

## 📚 Dica de Leitura

- [Banco de Dados] (A desenvolver)
- [Modelagem conceitual de banco de dados](/UC03%20-%20Auxiliar%20na%20Modelagem%20e%20Manipulação%20de%20Dados/Modulo_02%20-%20Modelagem%20Conceitual%20do%20Banco%20de%20Dados/diario_02.md)
- [Modelo de entidade e relacionamento](/UC03%20-%20Auxiliar%20na%20Modelagem%20e%20Manipulação%20de%20Dados/(Revisando%20)Modulo_03%20-%20Modelo%20de%20Entidade%20e%20Relacionamento/diario_03.md)

---

## 📦 Contexto

Uma nova empresa deseja entrar no mercado de filmes sob demanda com um sistema de streaming. Para isso, precisa planejar e estruturar uma base de dados relacional que irá suportar suas operações.  
Você foi contratado como **analista de dados**, e sua primeira tarefa é desenvolver o Diagrama ER.

As informações fornecidas são:

### 📄 Entidades e atributos

**Usuário**
- ID;
- Nome;
- E-mail;
- CPF;
- Endereço (FK);

**Endereço**
- ID;
- Rua;
- Número;
- Cidade;
- Estado;
- CEP;

**Conteúdo**
- ID;
- Título;
- Gênero;
- Ano;
- Estúdio (FK);

**Estúdio**
- ID;
- Nome;

**Visualização** (relação N:N entre Usuário e Conteúdo)
- ID;
- Usuário (FK);
- Conteúdo (FK);
- Tempo de visualização (minutos)

---

## 📌 Regras de Negócio

- Cada usuário **deve ter um endereço** (1:1 obrigatório).  
- Cada conteúdo pertence a **um único estúdio**, mas um estúdio pode ter vários conteúdos (1:N).  
- A tabela **Visualização** será gerada automaticamente no relacionamento N:N entre Usuário e Conteúdo.  
- Todos os campos devem conter **tipos de dados apropriados**.

---

## 🧩 Meu trabalho

![Atividade_01](/UC03%20-%20Auxiliar%20na%20Modelagem%20e%20Manipulação%20de%20Dados/Atividades/Atividade_01/Atividade01_DER.png)

---

## 🖥️ Avaliação do Tutor

(Aguardando resposta)

---

## 📈 Indicadores da Atividade

> Elabora, sob supervisão, modelagem de dados de acordo com projeto de software.
