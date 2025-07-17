1. Faça o filtro icmp. Quantos PDU’s usam esse protocolo?
	Resposta: 2474 PDU's
___icmp___
![](Lab%204.1%20-%20Daniel%20Espada.png)
![](Lab%204.1%20-%20Daniel%20Espada-1.png)

---
2. Chegue ao mesmo resultado do ponto anterior – PDU’s que usam ICMP -, mas desta vez usando as flags do IPv4. 
	Resposta: 2474 PDU's
___ip.proto == 1___
![](Lab%204.1%20-%20Daniel%20Espada-2.png)
![](Lab%204.1%20-%20Daniel%20Espada-3.png)

---
3. Use as flags do IPv4 para indicar quantos PDU’s têm TTL a 128.
	Resposta: 2398 PDU's
___ip.ttl == 128___
![](Lab%204.1%20-%20Daniel%20Espada-4.png)
![](Lab%204.1%20-%20Daniel%20Espada-5.png)

---
4. Através de um filtro, indique os PDU’s que vão possuir mais fragmentos desses pacotes. 
	Resposta: 163 PDU's
___ip.flags.mf == 1___ // ___ip.flags.mf == true___
![](Lab%204.1%20-%20Daniel%20Espada-6.png)
![](Lab%204.1%20-%20Daniel%20Espada-7.png)

---
5. Aplique o filtro ip.dst == 172.217.40.76 e indique qual o campo de identification do primeiro PDU. Analise o mesmo campo do segundo PDU e indique a que conclusões chegou. 
	Resposta: 0xd0fe (53502), a identicacao mantem na mesma identificao de fragmento, porque so assim quem recebe sabe que é do outro pdu


---
6. Analise o PDU n.º 14403 e filtre por stream index. Indique quanto tempo demorou esta conversação, com escala a décimos de segundo (“tens of a second”), mencionando, igualmente, todos os filtros que podem ser utilizados (diretamente e indiretamente) para chegar a esta resposta.
	Resposta: 