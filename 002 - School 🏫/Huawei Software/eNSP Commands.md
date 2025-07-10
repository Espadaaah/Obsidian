# 1. *R1*
[Entrar no modo configuração]

	system-view
---
[Alterar nome do equipamento e retornar ao default]

		sysname R1DanielEspada
		undo sysname

---
 [Configurar IP numa interface, eliminar a configuração e ativar interface]

		int g0/0/0 # Entrar na interface
		ip add 192.168.10.1 255.255.255.0 # Adicionar o ip à interface
		undo ip add # Remover o ip à interface
		undo shutdown # Dar start à interface
		quit

---
[Configurar mensagem do dia (MOTD)]

		header login information "APENAS ACESSO AUTORIZADO!" # Adicionar um banner no login
		header shell information "APENAS ACESSO AUTORIZADO!" # Adicionar um banner quando se entra na cli
---
[Configurar a hora e data]

		clock timezone Lisboa add 0
		clock datetime xx:xx:xx xxxx-xx-xx
		clock daylight-saving-time Lisboa repeating 00:00 last Sunday March 1:00 last Sunday October 1:00 # Configuração mudança de hora
--------------------
[Configuração de password na consola (AR1220)]

		user-interface con 0
		authentication-mode password (colocar password)
---
[Habilitar o servidor telnet e configuração de password nas vty // Tempo de inatividade ]

		telnet server enable
		user-interface 0 4
		authentication-mode password (colocar password)
		protocol inbound telnet
		user privelege level 15
		idle-timeout 2 0
---
# 2. *SW1*
	
# 3. *SW2*
	