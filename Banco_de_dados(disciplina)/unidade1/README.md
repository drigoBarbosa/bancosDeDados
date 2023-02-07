#### Unidade 1: Organização de Dados.
 
Para termos um tabela bem organizada faz-se necéssario o uso de algumas regras (regras de nomeação e tipos de Dados)

- Regras de Nomeação: 
    - Os nomes das tabelas e colunas devem conter de 1 a 30 caracteres, sendo o primeiro
    - caractere alfabético.
    - Os nomes devem conter apenas caracteres de a-z, A-Z, 0-9, _, S e #.
    - Os nomes não podem ser iguais às palavras reservadas do Oracle.

- Tipo de Dados: Ao se criar a estrutura de uma tabela, é necessário que o usuário forneça, para cada coluna, as seguintes informações:
    - Tipo de Dado
    - Tamanho
    - Restrições

Todo estrutura que criarmos na nossa tabela, podemos colocar regras/limitações que mantém os dados do usuário restritos, e assim evitam que dados inválidos sejam inseridos no banco.

**Constraint**(Limitação/regra/restrições):  São regras básicas estabelecidas para o preenchimento de uma ou mais colunas da tabela e são definidas ao final da especificação de cada coluna ou ao final do comando.

- Not Null: Impede que valores nulos sejam inseridos em uma coluna.
- Unique: Impede que valores duplicados sejam inseridos na coluna.
- Primary key(Chave primária): É um índice da sua tabela no qual o valor de seu conteúdo é: único, estático (não deve ser alterado) e JAMAIS será nulo.
- Foreign Key(Chave estrangeira): É o campo que estabelece o relacionamento entre duas tabelas. Assim, uma coluna corresponde à mesma coluna que é a chave primária de outra tabela.
- Check: Especifica uma condição que deve ser verdadeira, obedecendo a uma regra
do negócio. A Constraint CHECK é usada para limitar o intervalo de valores que pode ser colocado em uma coluna. Se você definir uma Constraint CHECK em uma coluna, ela permitirá apenas determinados valores para está coluna.

#### A SQL apresenta uma série de comandos que permitem a definição dos dados, chamada de DDL(Data Definition Language), composta, entre outros, pelos comandos Create, Alter e Drop.

- Criação de Tabela: 

**CREATE TABLE** nome_tabela
( nome_coluna tipo de dado | constraint_tabela ),
( nome_coluna tipo de dado | constraint_tabela )

- Alteração de Tabela: 

Após a criação da estrutura de uma tabela, pode-se incluir (ADD), excluir (DROP) ou modificar (MODIFY) colunas ou constraints e desabilitar contraints dessa tabela. Utilizaremos o comando ALTER.

**Acrescentar campos em uma tabela**

ALTER TABLE CLIENTE
ADD( IE_FISICA_JURIDICA CHAR(1))

**Alterando obrigatoriedade de atributos em uma tabela.**

ALTER TABLE CLIENTE
MODIFY (nm_cliente not null);

**Modificando o tipo de atributos em uma tabela.**

ALTER TABLE CLIENTE
 MODIFY (DS_ENDERECO NUMBER(3));

**Modificando o tamanho dos atributos em uma tabela.**

ALTER TABLE CLIENTE
MODIFY (NR_CEP VARCHAR2(12));

**Acrescentar restrições a uma tabela.**

ALTER TABLE CLIENTE
 ADD(CONSTRAINT CLIENTE_IE_FISICA_JURIDICA_CK
 CHECK(IE_FISICA_JURIDICA IN(‘F’,’J’)));

**Desabilitar uma restrição de uma tabela.**

ALTER TABLE CLIENTE
DISABLE CONSTRAINT CLIENTE_IE_FISICA_JURIDICA_CK;

**Excluir uma restrição de uma tabela.**

ALTER TABLE CLIENTE
DROP CONSTRAINT CLIENTE_IE_FISICA_JURIDICA_CK
13

**Exclusão de Tabela**

Após a criação da estrutura de uma tabela ou alteração da sua estrutura, podemos excluí-la
através do comando DROP.
Ao excluir uma tabela, todas as constraints e os dados inseridos são deletados fisicamente.
DROP TABLE CLIENTE
