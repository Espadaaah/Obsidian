```shell
cd /var/www/html
```

```shell
sudo mkdir /var/www/html/adminpro
```

```shell
echo "super confidencial" | sudo tee /var/www/html/adminpro/info.txt > /dev/null
```

```shell
dirb http://192.168.182.151 /usr/share/wordlists/dirb/common.txt
```

