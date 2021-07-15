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
