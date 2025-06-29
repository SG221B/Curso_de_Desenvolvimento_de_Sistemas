# 📦 Módulo 01 — Banco de Dados

## 📅 Informações
- **UC:** UC03 — Auxiliar na Modelagem e Manipulação de Dados
- **Data de início:** 13/05/2025  
- **Data de conclusão:** 26/06/2025  
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

**📅 Data do Registro:** 26/06/2025
**📚 Tema:** Funções principais dos bancos de dados

### 📝 Conteúdo

Antes de entender tecnicamente como um banco de dados funciona, é útil imaginar seu funcionamento de forma intuitiva. Pense nele como um depósico com várias caixas organizadas. O depósito representa o banco de dados, e cada caixa é uma tabela. Cada uma tem um nome (como "roupas", "brinquedos" etc.) e um formato específico, usado para guardar diferentes tipos de objetos — ou registros.

Nos bancos de dados relacionais, os dados são organizados em **tabelas** formadas por **colunas** (tipos de informação) e **linha**s (os dados em si). É como uma planilha do Excel onde o banco é a planilha, e cada aba é uma tabela com suas colunas e linhas.

Ex.: 
| **id** | **nome**            | **idade** | **país** |
|--------|---------------------|-----------|----------|
| 1      | Henrique Marques    | 28        | Brasil   |
| 2      | Terry Crews         | 65        | USA      |

Cada tabela em um banco de dados representa um assunto específico. Por exemplo, em uma loja, pode haver uma tabela Cliente, com dados como nome, endereço e idade, e outra tabela Venda, com informações como data e valor da compra.

Essas tabelas geralmente estão relacionadas. No caso da loja, uma venda está ligada a um cliente, indicando que aquele cliente realizou aquela compra. Por isso, chamamos de banco de dados relacional.

Ex.:
|                   **Cliente**                   |
| **id** | **nome**  | **endereço**   | **idade** |
|--------|-----------|----------------|-----------|
| 1      | João      | Rua A, 10      | 35        |
| 2      | Maria     | Rua B, 50      | 70        |
| 3      | Joaquim   | Rua C, 5       | 20        |


|                          **Venda**                         |
| **id** | **data_venda** | **valor_total** | **id_cliente** |
|--------|----------------|-----------------|----------------|
| 1      | 10/10/21       | 1000.00         | 2              |
| 2      | 11/10/21       | 150.00          | 1              |
| 3      | 11/10/21       | 79.90           | 2              |


As tabelas Cliente e Venda estão preenchidas com dados de exemplo. Na tabela Venda, a coluna id_cliente se refere ao id da tabela Cliente, formando um relacionamento entre elas. Isso permite que uma tabela complemente a outra.

Por exemplo, a venda 1, feita em 10/10/21 no valor de R$ 1000,00, foi realizada por Maria (cliente 2). Maria também fez a venda 3. João (cliente 1) fez a venda 2. Já Joaquim (cliente 3) ainda não realizou nenhuma compra.

Esse relacionamento evita repetir informações. Não é preciso registrar os dados de Maria toda vez que ela faz uma compra — basta referenciar seu id.

Bancos de dados não vêm prontos. Eles devem ser planejados e estruturados para atender às necessidades da empresa e se tornam um de seus bens mais valiosos.

Após construído, o banco de dados permite:
- **Incluir novas informações**
- **Atualizar ou remover dados**
- **Consultar uma ou mais tabelas**
- **Controlar o acesso por meio de regras de segurança**

Tudo isso é feito de forma rápida e eficiente pelos sistemas de banco de dados, mesmo com grandes volumes de informação.

---

## 📘 Lição 4 — Modelo Relacional x Não Relacional

**📅 Data do Registro:** 26/06/2025
**📚 Tema:** Comparação entre modelos de banco de dados

### 📝 Conteúdo

Nem todo banco de dados usa o modelo relacional. Existem também os bancos não relacionais, como os do tipo NoSQL, que podem ser mais adequados dependendo das necessidades do projeto.

**Modelo Relacional**
Criado em 1970, o modelo relacional organiza os dados em tabelas com colunas e linhas, usando chaves primárias para identificar registros e chaves estrangeiras para relacionar tabelas. Ele é ideal para dados estruturados e usa a linguagem SQL para consulta e manipulação.

Esse modelo resolveu problemas antigos em que cada aplicação criava sua própria estrutura de dados, dificultando o acesso e manutenção. Com tabelas padronizadas, o banco relacional se tornou eficiente, intuitivo e flexível.

Exemplos de bancos relacionais:
- **MySQL**
- **PostgreSQL**
- **Oracle**
- **SQL Server**
- **MariaDB**

**Modelo Não Relacional (NoSQL)**
O NoSQL surgiu no final dos anos 2000 para lidar com grandes volumes de dados e estruturas mais flexíveis. Ele não usa tabelas tradicionais, mas armazena informações em formatos como documentos, objetos ou grafos.

Apesar do nome, bancos NoSQL podem ter relacionamentos entre dados — mas de forma diferente do modelo relacional. São usados, por exemplo, por plataformas como o Twitter, que lidam com muitos dados em tempo real.

Exemplo de documento JSON:

```json
{
"cep": "01001-000",
"logradouro": "Praça da Sé",
"complemento": "lado ímpar",
"bairro": "Sé",
"localidade": "São Paulo",
"uf": "SP",
"ibge": "3550308",
"gia": "1004"
}
```

Principais tipos de bancos NoSQL:

- **Documentos** (ex: MongoDB, CouchDB)
- **Chave-valor (ex: Redis)**
- **Grafos (para dados interconectados)**
- **Orientados a objetos**
- **Distribuídos (dados espalhados em várias máquinas)**
---

## 📘 Lição 5 — SGBD e Implantação de Banco de Dados

**📅 Data do Registro:** DD/MM/AAAA  
**📚 Tema:** Sistema Gerenciador de Banco de Dados e instalação Workbanch

### 📝 Conteúdo

(incluir conteúdo sobre a instalação do Workbanch)

---

### ✅ Observações Finais do Módulo

- Dificuldades encontradas  
- Estratégias que funcionaram  
- Pontos para revisar mais tarde  
- Dicas futuras
