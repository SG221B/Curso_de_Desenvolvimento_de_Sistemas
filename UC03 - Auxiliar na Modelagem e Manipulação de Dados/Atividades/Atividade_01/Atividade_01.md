# 📘 UC03 – Auxiliar na Modelagem e Manipulação de Dados

## 📝 Atividade 1 – Diagrama ER de um sistema de streaming

### 🎯 Objetivo
Desenvolver, utilizando a interface do **MySQL Workbench**, um **Diagrama Entidade-Relacionamento (DER)** que represente as principais entidades e relacionamentos de um sistema de streaming de filmes.

---

## 📚 Dica de Leitura

- [Banco de Dados]
- [Modelagem conceitual de banco de dados](#)
- [Modelo de entidade e relacionamento](#)

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

## 🖥️ Desenvolvimento

📍 *Descreva aqui as decisões que você tomou para montar o diagrama, justificativas de modelagem e observações importantes.*

---

## 🧩 Resultado

📷 *Adicione uma imagem do seu diagrama exportado do MySQL Workbench (DER).*

---

## 📈 Indicadores da Atividade

> Elabora, sob supervisão, modelagem de dados de acordo com projeto de software.
