# Comandos basicos y CRUD mongosh
## Comandos basicos
Ver si el porceso está en ejecución
`$ ps -ef | grep mongod`

Ver la verisón de mongodb
`$ mongo -version`

Entrar en mongosh
`$ mongosh -u <usr> -p <pass>`

Ver las bases de datos que hay en mongo desde mongosh
`test> show databases`

Entrar o crear una base de datos
`use <database>`

## CRUD mongosh
Insertar un documento, varios "insertMany"
````terminal
inventory> db.inventory.insertOne({ item: "canvas", qty: 100, tags: ["cotton"], size: { h: 28, w: 35.5, uom: "cm" } })
````

Queries
````terminal
inventory> db.inventory.find( {} )
inventory> db.inventory.find( { status: "D" } )
````

Update un documento, varios "updateMany"
````terminal
inventory> db.inventory.updateOne({ item: "paper" },{$set: { status: "P" }})
````

Delete un documento, varios "deleteMany"
````terminal
inventory> db.inventory.deleteOne( { status: "D" } )
inventory> db.inventory.deleteMany({})
````