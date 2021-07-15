## Linux pingsweep
### Oneliner
```sh
 for i in {1..254} ;do (ping -c 1 192.168.1.$i | grep "bytes from" &) ;done
 ```

### quick script

```sh
#!/bin/bash
if [[ -z $1 ]]; then
        echo ""
        echo "USAGE: ${0} [Subnet prefix]"
        echo ""
        echo "NOTE: /24 only, prefix format is 192.168.1 without the last octet"
        echo "Sweep will hit 254 hosts"
        echo ""
        exit
fi

for i in {1..254} ;do
(ping -c 1 $1.$i | grep "bytes from" &)
done
```


## TCP Scanner using nc
```sh
#!/bin/bash
if [[ -z $1 ]] ;then
  echo "Usage: ./port.sh [IP]"
  echo "Example ./port.sh 192.168.1.10"
else
  echo "Please wait while it is scanning all the open ports..."
  nc -nvz $1 1-65535 > $1.txt 2>&1
fi
tac $1.txt
rm -rf $1.txt
```
