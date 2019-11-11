---
layout: post
title:  "Inserindo dados no MongoDB com Python em menos de 5 minutos"
category: Tecnologia
---

Neste rápido tutorial, descrevo como criar um usuário/coleção no MongoDB e como inserir diversos JSONs nessa nova base de dados para consultas futuras. 

Aqui, assumo que você já possui uma instância de MongoDB rodando na sua máquina.

### Criando uma nova coleção no mongodb

Primeiramente, é necessário logar na sua instancia do MongoDB e criar um novo usuario para ficar responsável pela coleção. Para isso, entre com o usuario admin do MongoDB pelo _shell_.

``` shell
mongo -u seu_admin -p sua_senha_de_admin --authenticationDatabase admin
``` 

Crie o usuário que sera o administrador da sua coleção:

``` mongo
use novo_db 
db.createUser(
    {
    user: "admin_da_colecao",
    pwd: "senha_do_usuario",
    roles: [ { role: "readWrite", db: "novo_db" } ]
    }
)
```

Entre no MongoDB com suas novas credenciais:

``` shell
mongo -u admin_da_colecao -p senha_do_usuario --authenticationDatabase novo_db
```

Crie a coleção que voce deseja:

``` mongo
use novo_db
db.createCollection("nova_colecao") 
```

### Inserindo os dados

Para esse exemplo, carregamos alguns dicionários de Python em uma lista e iteramos para inserir todos os dados no banco de dados recém criado. Note que se você carregasse de um arquivo JSON múltiplas instâncias de algum tipo de dado, o processo seria ańalogo. O código é o seguinte:

``` python

# Carregando os dados para serem importados
lista_de_dados = [{"nome": "David Berman", "idade": 52},
                  {"nome": "Frank Ocean", "idade": 32},
                  {"nome": "Jeff Tweedy", "idade": 52}]

# Inserindo os dados
from pymongo import MongoClient
client = MongoClient('137.117.43.115', 
                     username='admin_da_colecao',
                     password='senha_do_usuario',
                     authSource='novo_db',
                    authMechanism='SCRAM-SHA-256'
    )
db = client['novo_db']
collection = db.nova_colecao

for dado in lista_de_dados:
    collection.insert_one(dado)
```

### Verificando no shell do mongo que todos os documentos foram inseridos

Você pode verificar por Python ou pelo próprio _shell_ do mongo a inserção correta dos documentos com o comando: 

``` mongo
db.carf_html.find().sort({_id:1}).limit(10);
```

É isso, em menos de 5 minutos você configurou uma coleção no MongoDB e guardou dados para consultas futuras.