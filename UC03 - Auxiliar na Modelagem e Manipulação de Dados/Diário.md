# Diário de Estudos — UC03

## 📅 15 de maio de 2025

### Tópico: Modelagem Conceitual do Banco de Dados

**Início do estudo em:**
- Modelagem Conceitual do Banco de Dados

**Conteúdo a ser aprendido:**
- Levantamento de dados  
- Levantamento e especificação de requisitos
- Dicionário de dados
- Arquitetura de arquivos de dados
- Integridade referencial

---

### 📘 Lição 1: Levantamento de dados

- O levantamento de dados é a etapa em que se coleta todas as informações relevantes sobre o ambiente que será modelado.
- Envolve observar processos, conversar com usuários e levantar documentos.
- É uma etapa investigativa e aberta, sem ainda criar diagramas ou restrições técnicas.

---

**🧠 Resumo do aprendizado:**
O **levantamento de dados** tem como objetivo entender as principais e reais necessidades do cliente.  
Para isso, são utilizadas diversas técnicas, como:

**🔍 Observação ativa ou pessoal:**
> Consiste em observar diretamente as atividades do usuário em seu ambiente de trabalho, fazendo anotações.  
> O objetivo é compreender o que está envolvido nas tarefas, como elas são realizadas e com qual finalidade.

**📋 Questionário**  
> Método de coleta de informações por meio de perguntas.  
> Pode ser:
> - **Fechado**: com alternativas de múltipla escolha.  
> - **Aberto**: permitindo respostas livres.  
> É basicamente como uma prova.

**🗣️ Entrevista**  
> Semelhante ao questionário, porém realizada oralmente.  
> Isso permite adaptar as perguntas conforme a conversa evolui, tornando a coleta mais rica e dinâmica.

**📄 Análise da documentação**  
> Consiste em analisar documentos já existentes na empresa relacionados ao projeto, como planilhas, formulários e registros.

> Exemplo: uma empresa que ainda utiliza papel e caneta para cadastrar clientes (sim, isso ainda existe!). Agora, com o aumento da demanda, precisa informatizar esse processo.  
> O analista irá examinar os formulários impressos que a empresa já utiliza para entender como esse cadastro é feito atualmente.

> Como exatamente ele vai fazer isso? Problema dele! 😄  
> (Brincadeiras à parte... um dia pode ser o seu trabalho ou o meu, então é bom entender desde já!)
#

## 📅 19 de maio de 2025

### 📘 Lição 2: Levantamento e especificação de requisitos

- Essa etapa define o que o sistema precisa fazer.
- Consiste em documentar de forma clara e organizada como o sistema pode alcançar esses objetivos.
- Os requisitos levantados são compartilhados com a equipe e os clientes para garantir o alinhamento entre todos os envolvidos.

**🧠 Resumo do aprendizado:**

Sabe quando alguém te pede um favor, mas não explica direito o que quer? Quais são as chances disso dar errado? 
Para evitar que isso aconteça no seu projeto, é realizado o **levantamento e especificação de requisitos** que consiste basicamente em *entender — o que o sistema — precisa fazer*

É para isso que utilizamos as **técnicas de levantamento de dados** que estudamos no dia 17/05, como observação, entrevista e questionário.

Depois de coletado as informações, é hora de **especificar os requisitos**. Ou seja, colocar tudo no papel de forma clara e organizada sobre o que será feito, e **compartilhar com os membros da equipe** para garantir que todos (isso inclui o cliente, tá?) compreendam e concordem com o que será desenvolvido.

Isso ajuda todo mundo a falar a mesma língua, evitar confusão e tudo acabar no casos de familía.

<div align="center">
  <img src="./Recursos/UC03 - exemplo_de_dicionario_de_dados.png" alt="casos_de_familia" width="300px">
</div>
---

### 📘 Lição 3: Dicionário de dados

- Descrever o que cada dado significa.
- Garantir que todo mundo entenda os dados da mesma forma.

**🧠 Resumo do aprendizado:**

Pense em um diacioário de verdade, como o Aurélio. Ele explica o que cada palavra significa, certo?  
O **dicionário de dados** é parecido: ele explica os *componentes do sistema* — o que são, como são usados e qual seu significado.

É nele que a gente organiza e descreve cada informação que o sistema vai usar.

**📌 Importância:**

A qualidade da informação depende de como os dados são coletados, organizados e contextualizados. Um dicionário de dados bem elaborado garante que *os dados serão compreendidos corretamente por todos os envolvidos no projeto*.

**⚠️ Quando não há dicionarização:**

Sem um dicionário de dados, se as informações forem entregues apenas em uma planilha ou relatório, podem surgir **interpretações equivocadas**. Isso porque não ficará claro o que cada coluna ou campo representa. A falta de contexto abre espaço para confusão.

**Exemplo de Dicionário de dados:**
Imagine uma entidade “consumidor”, com seus atributos. Em um dicionário de dados ficaria assim:

![Exemplo dicionário de dados](./Recursos/UC03%20-%20exemplo_de_dicionario_de_dados.png)

#

## 📅 17 de maio de 2025

### Tópico: Modelo de Entidade e Relacionamento

**Início do estudo em:**
- Modelo de entidade e relacionamento

**Conteúdo a ser aprendido:**
- Entidades  
- Atributos  
- Chave primária e estrangeira  
- Relacionamentos  

**Impressão inicial:**  
Banco de dados me parece ser uma coisa bem bacana. Gosto da ideia de manipular, organizar e facilitar o acesso a vários dados.

**Vamos que vamos!**

---

### 📘 Lição 1: Relacionamentos Ternários

- No início, me assustei um pouco 😅
- Pesquisando por fora, percebi que é mais simples do que parecia.
- **Dica pessoal:** Sempre façam pesquisas complementares!  
- Um vídeo curto no YouTube pode esclarecer algo que não ficou claro no material principal.

**Resumo do aprendizado:**
> 
