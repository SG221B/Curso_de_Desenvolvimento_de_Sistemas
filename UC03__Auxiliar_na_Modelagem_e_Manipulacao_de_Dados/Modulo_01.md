# 📦 Módulo 01 — Banco de Dados

## 📅 Informações
- **UC:** UC03 — Auxiliar na Modelagem e Manipulação de Dados
- **Data de início:** 13/05/2025  
- **Data de conclusão:** DD/MM/AAAA  
- **Última atualização:** 26/06/2026

---

## 📖 Índice de Lições

- [ ] [Lição 01 — Introdução](#-lição-1--introdução)
- [ ] [Lição 02 — Introdução a Banco de Dados Relacional](#-lição-2--introdução-a-banco-de-dados-relacional)
- [ ] [Lição 03 — Funcionalidade](#-lição-3--funcionalidade)
- [ ] [Lição 04 — Modelo Relacional x Não Relacional](#-lição-4--modelo-relacional-x-não-relacional)
- [ ] [Lição 05 — SGBD e Implantação de Banco de Dados](#-lição-5--sgbd-e-implantação-de-banco-de-dados)

---

## 📘 Lição 1 — Introdução

**📅 Data do Registro:** 26/06/2025  
**📚 Tema:** Conceito e importância

### 📝 Conteúdo

Um banco de dados é:
    - Uma coleção organizada de dados que permite armazenar, manipular e recuperar informações de forma eficiente.
    - É fundamental em sistemas que exigem integridade, consistência e acesso rápido aos dados.

Antigamente, usava-se arquivos físicos, o que dificultava o controle e a atualização das informações. Com a digitalização, ganhou-se segurança, organização e praticidade.

Além disso, bancos de dados se destacam pela eficiência, escalabilidade, confiabilidade, abstração e persistência — qualidades essenciais em praticamente qualquer sistema que lida com dados.

---

## 📘 Lição 2 — Introdução a Banco de Dados Relacional

**📅 Data do Registro:** 26/06/2025  
**📚 Tema:** Conceito e vantagens

### 📝 Conteúdo

O termo “banco de dados” vem do inglês databanks, mais tarde substituído por databases (base de dados), por ter um significado mais apropriado.

Um banco de dados é um local onde se armazenam dados importantes para o funcionamento de uma organização. Ele serve como fonte de informação tanto para os sistemas atuais quanto para os futuros.

Existem duas formas de armazenar dados em computadores: por meio de **bancos de dados** ou por **arquivos permanentes**. A segunda opção envolve cada programa criando seus próprios arquivos (como arquivos de texto), o que pode funcionar em casos simples. Porém, os bancos de dados oferecem vantagens mais robustas, como:

- **Controle centralizado de dados:**
    Os dados ficam reunidos em um só lugar, facilitando o gerenciamento. Já no modelo de arquivos, os dados ficam espalhados.

- **Redução da redundância e economia de espaço:**
    Informações são armazenadas apenas uma vez e podem ser usadas por vários usuários, evitando duplicações.

- **Eliminação de inconsistências e garantia de integridade:**
    A centralização evita que o mesmo dado esteja com valores diferentes em lugares distintos.

- **Padronização e facilidade de acesso:**
    A organização centralizada permite aplicar regras de nomenclatura e recuperar informações de forma mais eficiente.

- **Independência de dados:**
    A estrutura dos dados pode ser modificada sem impactar diretamente os programas, diferente do modelo baseado em arquivos.

---

## 📘 Lição 3 — Funcionalidade

**📅 Data do Registro:** DD/MM/AAAA
**📚 Tema:** Funções principais dos bancos de dados

### 📝 Conteúdo

Antes de entender tecnicamente como um banco de dados funciona, é útil imaginar seu funcionamento de forma intuitiva. Pense nele como um depósico com várias caixas organizadas. O depósito representa o banco de dados, e cada caixa é uma tabela. Cada uma tem um nome (como "roupas", "brinquedos" etc.) e um formato específico, usado para guardar diferentes tipos de objetos — ou registros.

Nos bancos de dados relacionais, os dados são organizados em **tabelas** formadas por **colunas** (tipos de informação) e **linha**s (os dados em si). É como uma planilha do Excel onde o banco é a planilha, e cada aba é uma tabela com suas colunas e linhas.

Ex.: 
 _______________________________________________
|**id** | **nome**              |  **idade**    |   **pais**     |
|1  | Henrique Marques  |  28       |   Brasil   |
|2  | Terry Crews       |  65       |    USA     |


---

## 📘 Lição 4 — Modelo Relacional x Não Relacional

**📅 Data do Registro:** DD/MM/AAAA
**📚 Tema:** Comparação entre modelos de banco de dados

### 📝 Conteúdo

O modelo relacional organiza dados em tabelas com relações entre si, ideal para estruturas bem definidas. É excelente para aplicações com regras rígidas de integridade.

Já os modelos não relacionais (NoSQL) não usam tabelas. Podem armazenar dados em documentos (MongoDB), grafos (Neo4j), colunas (Cassandra) ou chave-valor (Redis). São mais flexíveis e indicados para grandes volumes de dados não estruturados, como redes sociais e sistemas em nuvem.

A escolha entre os modelos depende das necessidades do sistema: estrutura rígida e integridade → relacional; escalabilidade e flexibilidade → não relacional.

---

## 📘 Lição 5 — SGBD e Implantação de Banco de Dados

**📅 Data do Registro:** DD/MM/AAAA  
**📚 Tema:** Sistema Gerenciador de Banco de Dados e seu uso

### 📝 Conteúdo

O SGBD (Sistema Gerenciador de Banco de Dados) é o software responsável por criar, gerenciar e operar um banco de dados. Ele oferece ferramentas para:

Criação de tabelas e relacionamentos
Execução de consultas
Controle de usuários
Garantia de integridade
Gerenciamento de transações

Exemplos de SGBDs: MySQL, PostgreSQL, Oracle, SQL Server.
A implantação de um banco envolve:
Definir requisitos do sistema
Projetar o modelo de dados
Implementar o banco no SGBD escolhido
Testar e validar
Iniciar o uso com segurança e monitoramento.

---

### ✅ Observações Finais do Módulo

- Dificuldades encontradas  
- Estratégias que funcionaram  
- Pontos para revisar mais tarde  
- Dicas futuras
