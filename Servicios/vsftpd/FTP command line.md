## Common FTP Commands
-   `help` or `?` - list all available FTP commands.
-   `cd` - change directory on the remote machine.
-   `lcd` - change directory on the local machine.
-   `ls` - list the names of the files and directories in the current remote directory.
-   `mkdir` - create a new directory within the current remote directory.
-   `pwd` - print the current working directory on the remote machine.
-   `delete` - remove a file in the current remote directory.
-   `rmdir`- remove a directory in the current remote directory.
-   `get` - copy one file from the remote to the local machine.
-   `mget` - copy multiple files from the remote to the local machine.
-   `put` - copy one file from the local to the remote machine.
-   `mput` - copy multiple files from the local to the remote machine.

```
[lluis@linuxserver ~]$ ftp 192.168.42.77
```
Debes acceder con usuario y contraseña.
Puede ser que en algunos servidores ftp permita el acceso como anonimo. En este caso, lograremos entrar con usuario anonymous y contraseña vacía.