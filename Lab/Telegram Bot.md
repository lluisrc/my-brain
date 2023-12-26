# Overview
Esta documentación te mostrará como montar un bot de telegram.

Un bot de telegram es como crear un usuario que te manda mensajes automaticos.

Cuando creamos un bot, por ejemplo stuard, le ponemos un nombre al bot "Stuard" y su username "un identificador unico"
Con este paso hemos creado a la "persona"

Ahora debemos crear un canal y hacer admin a stuard para que pueda enviar mensajes. Al ser un bot, para meterlo dentro hay que hacerle admin.

Una vez tenemos el canal podemos crear mensajes automaticos con el token del bot y con el id del canal

# Realizar los pasos
1. Abrimos telegram y buscamos @father_bot.
2. Clicamos en /start
3. Clicamos en /newbot
4. Indicamos el nombre del bot + su username
5. Copiamos el BOT_TOKEN
6. Creamos un canal (no es lo mismo que grupo)
7. Vamos a administrar canal y en la pestaña administradores, añadimos el bot creado (buscamos por username)
8. Una vez añadido escribimos texto en el grupo
9. Abrimos un navegador y accedemos a la siguiente URL --> `https://api.telegram.org/bot<BOT_TOKEN>/getUpdates`, si no aparece nada, hay que volver a repetir el paso enterior
10. Copiamos el campo que pone id (es el id del canal, debería ser algo como -1081670307614)
11. Ahora ya podemos lanzar mensajes automaticos con el comando CURL:  `curl "https://api.telegram.org/bot<BOT_TOKEN>/sendMessage?chat_id=<CANAL_ID>&text=sometext..."`