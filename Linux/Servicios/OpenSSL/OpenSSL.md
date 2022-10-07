## Cifrado simétrico
### Cifrar
````terminal
$ openssl enc -aes-256-cbc -base64 -in <input> -out <output>
````
### Descifrar
````terminal
$ openssl enc aes-256-cbc -d -base64 -in <input> -out <output>
````
## Cifrado asimétrico
### Generar par de llaves (privada + publica)
````terminal
$ openssl genrsa -out <output>.pem 2048
````
### Sacar la pública
````terminal
$ openssl rsa -in <input>.pem -pubout  -out <output>.pem
````
### Cifrar con la pública
````terminal
$ openssl rsutl -encrypt -in Dato -out DatoEnc -inkey public.pem -pubin
````
### Descifrar con la privada
````terminal
$ openssl rsautl -decrypt -in <input> -out <output> -inkey <par_de_llaves>.pem
````

También podemos cifrar con la privada y descifrar con la pública

Ver los tipos de cifrados
````terminal
$ openssl list -cipher-commands
````

El par de llaves esta en formato texto plano y ya no se usa, para obtener la private key actual con este comando:
````termianl
$ openssl rsa -in <input>.pem -des3 -out <output>.pem
````