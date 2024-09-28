# Gerencia-de-BD
# Teoria
## O que são Bancos de Dados Não Relacionais?

Tradicionalmente, os bancos de dados relacionais, como MySQL e PostgreSQL, organizam dados em tabelas com linhas e colunas rígidas. Essa estrutura é ideal para muitos cenários, mas pode se tornar inflexível para lidar com a diversidade e o volume de dados que as aplicações modernas exigem.

Bancos de dados não relacionais **(NoSQL)** oferecem uma alternativa mais flexível, armazenando dados em formatos diferentes, como documentos JSON, chave-valor ou grafos. Essa flexibilidade permite que você modele dados de maneira mais próxima à sua estrutura natural, sem as restrições impostas pelos esquemas rígidos dos bancos relacionais.

## Por que usar MongoDB?

- **Flexibilidade:** O MongoDB armazena dados em documentos JSON, permitindo que você adicione ou remova campos sem a necessidade de alterar o esquema do banco de dados.
- **Escalabilidade:** O MongoDB é projetado para escalar horizontalmente, distribuindo dados em vários servidores para lidar com grandes volumes de dados e altas cargas de trabalho.
- **Alta Performance:** O MongoDB oferece um desempenho excepcional para operações de leitura e escrita, tornando-o ideal para aplicações que exigem respostas rápidas.
- **Grande Comunidade:** O MongoDB possui uma comunidade ativa e em constante crescimento, o que significa que você encontrará muitos recursos, tutoriais e suporte.

## Conceitos Fundamentais do MongoDB

- **Coleções:** Equivalentes às tabelas em bancos de dados relacionais, as coleções armazenam documentos.
- **Documentos:** Unidades básicas de dados no MongoDB, semelhantes a linhas em uma tabela, mas com uma estrutura mais flexível.
- **Campos:** Os documentos são compostos por campos, que podem armazenar diferentes tipos de dados, como strings, números, arrays e objetos.
- **Chave Primária:** Cada documento possui um campo único chamado "_id", que serve como chave primária para identificar o documento de forma exclusiva.

---

# Usando o MongoDB.

Aqui o foco será em utilizar o banco utilizando o MongoShell. Mas todas as operações podem ser feitas usando a interface gráfica do mongoDB: *MongoDB Compass*;

## Observações:
- Eu estou executando o mongoDB através de uma imagem docker que pode ser obtida através do repositório: [https://hub.docker.com/_/mongo](https://hub.docker.com/_/mongo)
- Para facilitar o processo de instalação eu criei esse shell script: [docker-install-mongoDB.sh]( https://github.com/ArthurViniciusL?tab=repositories)
- O shell script está configurado para batizar a imagem do mongoDB de "mymongo". Caso queira alterar basta editar o shell script.
- Para iniciar o container:
	```
	sudo docker start mymongo
	```
- Para rodar o MongoShell dentro da imagem docker basta executar o comando:
  ```
  docker exec -it mymongo mongosh
	```

--- 
# Banco de dados
## Criando um banco de dados

```
use meu_banco_de_dados
```

- Quando o seu banco de dados for criado ele automaticamente entra no banco de dados criado.
- Um fato interessante é que o comando **use** é usado para criar o banco de dados, mas caso esse banco já exista ele apenas irá acessar o banco existente.

## Listando as bases de dados:
```
show dbs
```

# Coleção

## Criando uma coleção.
```
db.createCollection('nome_da_coleção');
```

## Listando as coleções.
```
show collections
```

ou também:
```
db.getCollectionNames()
```

A diferença é que *show collections* retorna o nome das coleções, enquanto *db.getCollectionNames()* retorna um array com as coleções.

## Listando o conteúdo de uma coleção.
```
db.nome_da_coleção.find
```

## Deletando a coleção.
```
db.nome_da_coleção.drop()
```

# Documentos

A sintaxe do mongoDB é a mesma do JSON.
## Criando um documento:
```
db.nome_da_coleção.insertOne({ atributos:"valores" });
```

**Exemplo:**
```
db.usuarios.insertOne({
    nome: "João",
    idade: 30,
    cidade: "São Paulo"
});
```
## Criando vários documentos:
```
db.usuarios.insertMany([ { atributos: valores }, ... ]);
```

**Exemplo:**
```
db.usuarios.insertMany([
	{ nome: "Maria", idade: 25, cidade: "Rio de Janeiro" },
	{ nome: "Pedro", idade: 32, cidade: "Belo Horizonte" }
]);
```

## Listando o conteúdo de um documento:
```
db.receitas.find(atributo: conteúdo)
```

---
# Operadores lógicos
