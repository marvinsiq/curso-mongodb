# curso-mongodb

Notas sobre o curso de MongoDB

## Instalando e Configurando o MongoDB

Para fazer o download do MongoDB, basta clicar em https://www.mongodb.com/download-center/community , realizar o download e seguir os passos para o seu sistema operacional nos links abaixo:

Mac
https://docs.mongodb.org/manual/tutorial/install-mongodb-on-os-x/

Linux (ubuntu)
https://docs.mongodb.org/manual/tutorial/install-mongodb-on-ubuntu/

Windows
https://docs.mongodb.org/manual/tutorial/install-mongodb-on-windows/



## Criando uma coleção

```db.createCollection("alunos")```


## Inserindo dados

```
db.alunos.insert(
   {
      "nome":"Felipe",
      "data_nascimento":new Date(1994,02,26),
      "notas":[
         10,
         9,
         4.5
      ],
      "curso":{
         "nome":"Sistemas de informação"
      },
      "habilidades":[
         {
            "nome":"Inglês",
            "nivel":"Avançado"
         }
      ]
   }
)

db.alunos.insert({
    "nome": "Paulo",
    "data_nascimento": new Date(1979, 12, 31),
    "notas": [10, 9, 7],
    "curso": {
        "nome": "Ciências da computação"
    },
    "habilidades": [
        {
            "nome": "Inglês",
            "nível": "Avançado"
        },
        {
            "nome": "Francês",
            "nível": "Avançado"
        }
    ] 
})

db.alunos.insert({
    "nome": "Daniela",
    "data_nascimento": new Date(1995, 07, 17),
    "notas": [10, 9, 7],
    "curso": {
        "nome": "Moda"
    },
    "habilidades": [
        {
            "nome": "Alemão",
            "nível": "Básico"
        }
    ] 
})

```

## Listando dados

```
db.alunos.find()

```

## Removendo dados

```
db.alunos.remove( {
    "_id": ObjectId("id_do_objeto")
})
```

## Busca de dados

https://docs.mongodb.com/manual/reference/method/db.collection.find/


```
db.alunos.find(
    {
        nome : "Felipe"
    }
).pretty()


db.alunos.find({
    "nome" : "Felipe",
    "habilidades.nome" : "inglês"
})


db.alunos.find({
    $or : [
        {"curso.nome" : "Sistemas de informação"},
        {"curso.nome" : "Engenharia Química"}    
    ]
})


 db.alunos.find({
     $or : [
        {"curso.nome" : "Sistemas de informação"},
        {"curso.nome" : "Engenharia Química"},
        {"curso.nome" : "Moda"}
    ],
    "nome" : "Daniela"
 })


 db.alunos.find({
    "curso.nome" : {
        $in : ["Sistema de informação", "Engenharia Química"]
        }
})


db.alunos.find({
    "nome" : "Felipe",
    "data_de_nascimento" : new Date(1994, 02, 26)
})
```
## Atualização completa e parcial de documentos