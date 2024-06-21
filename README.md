# Java: persistência de dados e consultas com Spring Data JPA

Projeto desenvolvido no segundo curso da formação Avançando com Java da Alura


## 🔨 Objetivos do projeto

- Modelar as abstrações da aplicação através de classes, enums, atributos e métodos;
- Consumir a API do ChatGPT;
- Utilizar o Spring Data JPA para persistir dados no banco;
- Conhecer vários tipos de banco de dados e utilizar o PostgreSQL;
- Trabalhar com vários tipos de consultas ao banco de dados;
- Aprofundar na interface JPARepository

## Aprendizados

### Aula 01

Buscar várias séries na API. Criamos um loop que encerra somente quando o usuário escolhe sair do menu, sendo capaz de buscar várias séries na API sem parar.

Métodos privados. Vimos que, se apenas uma classe irá acessar um método, não precisamos deixá-lo público, podemos declará-lo como privado. Isso é essencial para o encapsulamento das nossas classes.

Adicionar mais informações aos dados buscados. Revisamos como realizar o mapeamento entre atributos da API e atributos da nossa record.

Converter os dados que vêm da API para a sua própria classe. Criamos nossa própria classe `Serie` para representar melhor nossos dados. Para isso, foi necessário utilizar vários métodos de conversão.

Utilizar um “`if` reduzido”. Utilizamos a classe OptionalDouble para lidar com valores decimais e seus possíveis erros, utilizando os métodos `of` e `orElse`, que lembram muito o código de um if reduzido, e são muito úteis para evitar que ocorram Exceptions.

Criar um Enum. Percebemos que seria excelente poder categorizar nossas séries por gênero. Criamos um enum para isso, e vimos como criar métodos personalizados em enums.

Consumir a API do ChatGPT. Utilizamos a API do ChatGPT para traduzir nossos dados, adicionamos todas as dependências necessárias e configuramos a classe de consumo.

### Aula 02

Configurar seu ambiente Postgres. Fizemos a instalação desse banco de dados relacional e vimos a diferença entre bancos relacionais e outros tipos de bancos de dados, além de criar nosso banco de séries no Postgres.

Preparar sua aplicação para trabalhar com banco de dados. Adicionamos a dependência da JPA ao `pom.xml` e as configurações do banco de dados no `application.properties`.

Utilizar anotações do Hibernate para mapear suas entidades. Usamos anotações como @Entity, @Transient e @Column na classe `Serie`, indicando como seriam as configurações da tabela correspondente no banco de dados.

Manipular interfaces do tipo Repository. Para fazer operações básicas no banco de dados, como um CRUD, precisamos de uma interface do tipo Repository com o nosso tipo de dados. No nosso caso, criamos a SerieRepository.

Injetar dependências. Vimos que não podemos instanciar uma interface do tipo Repository em qualquer lugar. Elas precisam ser declaradas em classes gerenciadas pelo Spring, precedidas de um `@Autowired`, indicando que está sendo realizada uma injeção de dependências.

Trabalhar com variáveis de ambiente. Utilizamos variáveis de ambiente para proteger dados sensíveis da conexão com o banco de dados e com a API.

### Aula 03

Mapear relacionamentos entre entidades da JPA. Conhecemos o uso das anotações @OneToMany e @ManyToOne para identificar o relacionamento ”um para muitos” de séries e episódios.

Conhecer diversos tipos de relacionamento: Identificamos qual era o relacionamento presente na nossa aplicação, além de ter conhecimento dos vários tipos de relacionamento em banco de dados.

Associar chaves estrangeiras. Entendemos o conceito de chave estrangeira, que é como o banco de dados identifica e configura relacionamentos.

Trabalhar com os tipos de Cascade. Como o nosso fluxo de salvamento de dados era salvar séries e depois episódios, foi preciso configurar isso utilizando o atributo Cascade.

Identificar como os dados são carregados. Trabalhamos também com o atributo fetch, que fala sobre carregar os dados de forma “preguiçosa” (lazy) ou “ansiosa” (eager).

Configurar relacionamentos bidirecionais. Vimos a importância de relacionamentos bidirecionais e deixamos as modificações aparecendo dos dois lados da relação, fazendo tanto setEpisodios() na Série quanto setSerie() nos Episodios.

### Aula 04

Criar queries derivadas com a JPA. Conhecemos o recurso padrão da JPA para fazer buscas utilizando palavras-chave em métodos na classe Repository.

Comparar streams e buscas no banco de dados. Percebemos as mudanças em utilizar streams e as derived queries na nossa aplicação.

Conhecer diversas palavras-chave para criar seus métodos. Aprofundamos nas palavras-chave e em como utilizá-las, reforçando a prática.

Discutir os vários tipos de retorno ao realizar as buscas. Conversamos sobre as diferenças entre retornar uma série, uma lista de séries ou um Optional de séries.

Ler dados dinamicamente e armazenar em um Enum. Vimos como fazer a correspondência entre o que está sendo digitado e um campo no enum.

### Aula 05 

Diferenciar os tipos de consulta da JPA. Vimos que podemos trabalhar com derived queries, com queries nativas usando o nativequery e a JPQL, que é a linguagem de buscas da JPA.

Criar métodos totalmente personalizados e mais legíveis. Vimos que utilizar a JPQL pode auxiliar na escrita de métodos mais legíveis. Para isso, basta escrever o nome do método e anotá-lo com @Query.

Aprofundar em linguagem SQL. Conhecemos várias expressões utilizadas em SQL, como LIKE, ORDER e LIMIT.

Recuperar informações secundárias. Conseguimos buscar informações relacionadas a episódios a partir da série, utilizando o recurso das junções (JOIN).

Comparar recursos SQL e Java. Percebemos que, assim como o Java tem uma API de datas, o SQL também tem sua forma de lidar com datas. No nosso caso, utilizamos a função YEAR do SQL.