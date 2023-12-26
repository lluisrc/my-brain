Imprime las lineas que contenga el argumento
| Argument | Description |
|:--------:| ----------- |
| -r | Busca recursivamente. |
| -i | Ignore case sensetive. |
| -v | Invert match. |
| -c | Output count of matching lines only. |
| -l | Output matching files only. |
| -n | Precede each matching line with a line number. |
| -b | A historical curiosity: precede each matching line with a block number. |
| -h | Output matching lines without preceding them by file names. |
| -s | Suppress error messages about nonexistent or unreadable files. |
| -f | file: Take regexes from a file. |
| -o | Output the matched parts of a matching line. |
| --help | Get help. |
| -V, --version | Show version. |
| --regexp\=pattern | in addition to -e pattern. |
| --word-regexp | in addition to -w. |
| --line-regexp | in addition to -x. |
| -A num | num lines to show After grep line. |
| -B num | num lines to show Before grep line. |
| -C num | num lines to show Context(after and before) grep line. |


```terminal
[user@serverlinux ~]$ grep error /var/log/app.log
```
Grep también puede ser complementado con la salida del comando anterior gracias al pipe "|"
```terminal
[user@serverlinux ~]$ cat /var/log/app.log | grep error

[user@serverlinux ~]$ grep -E "word1|word2|word3" /path/to/file
[user@serverlinux ~]$ grep -vE "word4|word5|word6" /path/to/file

```