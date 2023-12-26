Trap ejecuta una funcion dependiendo de la señal con la que ha finalizado el proceso, en este caso interrupción (ctrl+c)<br>
Para ver el listado de señales con los que puede finalizar un proceso: INT, EXIT, TERM...
```terminal
[user@serverlinux ~]$ kill -l
```
INT es cuando se interrumpe un proceso (equivalente al típico ctrl+C)
```bash
trap control_c INT

control_c () {
        echo -e "\nAdioooos!!"
        exit 1
}

# La función control_c se ejecuta cuando el script como proceso se detiene con señal INTerrumpida.
```