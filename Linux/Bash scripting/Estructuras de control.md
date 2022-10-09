## Estructuras de control
### If, else
```
if [ ¿? ]; then
    echo "Soy true"
else
    echo "Soy false"
fi
```
```
[user@serverlinux ~]$ if [[ "a" == "a" ]];then echo "Soy A"; else echo "No soy A";fi
```

### While / until
```
while [ ¿? ]
do
    ¿?
done
```

### For
```
for i in $(seq 1 10)
do
    echo "$i"
done
```
```
[user@serverlinux ~]$ for i in $(seq 1 10);do echo "$i";done
```

### Case
```
case i in
  A) ¿? ;;
  B) ¿? ;;
  C) ¿? ;;
esac
```

## Operadores para las comparaciones
| Elemento | Descripción |
|:--------:|-------------|
| == | Igual (str) |
| -eq | Igual (int) |
| != | Distinto (str) |
| -ne | Distinto (int) |
| < | menor que |
| -lt | menor que (int) |
| <= | menor o igual que |
| -le | menor o igual que (int) |
| > | mayor que | |
| -gt | mayor que (int) |
| -ge | mayor o igual que (int) |
| >= | mayor o igual que |
| -z | string null |
| -n | string not null |
| -a, && | and |
| -o, \|\| | or |

## Operadores para los int
```
[user@serverlinux ~]$ echo "$((5 + 3))"
8
```
| Elemento | Descripción |
|:--------:|-------------|
| + | suma |
| - | resta |
| \\* | mutiplicación |
| / | división |
| % | resto |
| ** | potencia |
| += | suma y asigna |
| -= | resta y asigna |
| \*= | mutiplica y asigna |
| \/= | divide y asigna |
| \%= | resto y asigna |