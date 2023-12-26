```terminal
[user@serverlinux ~]$ ./script.sh -n lroca -c Mallorca
I am lroca
And I live in Mallorca
```
Code:
```bash
while getopts n:c: opt
do
    case "$opt" in
          n) name=$OPTARG;;
          c) country=$OPTARG
     esac
done

echo "I am $name";
echo  "And I live in $country";


$OPTARG captura los argumentos pasados en los parámetros
```