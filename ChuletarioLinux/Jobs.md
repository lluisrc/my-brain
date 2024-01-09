### Usano '&'
**Command:**
```terminal
nano &
```
**Output:**
```terminal
[1] 2781
```

Verifying the running of Background Processes
```terminal
jobs -l
```

Bringing a backgruound process to the foreground
```terminal
fg 1%
```
```terminal
fg 2781
```
Terminating the background process
```terminal
kill -9 2781
```

### Usando 'nohup'
Previene las señales hangup asegurando que el proceso siga corriendo (evento de desconexión, salir del sistema, cerrar la sesión del teminal)

**Command:**
```terminal
nohup command &
```

**Output:**
```terminal
nohup: ignoring input and appending output to 'nohup.out'
```

To verify execution
```terminal
jobs
```
```terminal
cat nohup.out
```

### Usando 'bg'
Para pasar un proceso parado a segundo plano

Para parar un proceso \^Z
Una vez parado lo podemos enviar al segundo plano con bg y se convierte en un job
**Command:**
```terminal
sleep 20
```
**Output:**
```terminal
^Z
[1]+  Stopped                 sleep 20
```

**Command:**
```terminal
bg
```
**Output:**
```terminal
[1]+ sleep 20 &
```

### Usando 'disown'
Para que el proceso en seguno plano no dependa de la tabla de procesos background de la terminal actual

```terminal
nano & disown
```
Si hay más de un proceso en los jobs 
```terminal
disown %1
```
Ver la tabla de jobs de la shell actual
```terminal
jobs -l
```
Para confirmar la ejecución del proceso
```terminal
ps aux | grep [process ID]
```

### Usando 'systemd'
**Command**
```terminal
sudo vim /etc/systemd/system/my-background-service.service
```
**Input:**
```vim
Specify the service unit in the file as follows:
[Unit]
Description=My Background Service

[Service]
Type=simple
ExecStart=/path/to/your/command
Restart=always
User=your_username
Group=your_groupname

[Install]
WantedBy=multi-user.target
```

**Command**
```terminal
sudo systemctl deamond-reload
sudo systemctl enable my-background-service
sudo systemctl start my-background-service
sudo systemctl status my-background-service
```