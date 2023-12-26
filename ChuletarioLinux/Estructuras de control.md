### If, else
```bash
#!/bin/bash

if [ ¿? ]; then
    echo "Soy true"
else
    echo "Soy false"
fi
```
```terminal
[user@serverlinux ~]$ if [[ "a" == "a" ]];then echo "Soy A"; else echo "No soy A";fi
```

### While / until
```bash
while [ ¿? ]
do
    ¿?
done
```

### For
```bash
for i in $(seq 1 10)
do
    echo "$i"
done
```
```terminal
[user@serverlinux ~]$ for i in $(seq 1 10);do echo "$i";done
```

### Case
```bash
case i in
  A) ¿? ;;
  B) ¿? ;;
  C) ¿? ;;
esac
```