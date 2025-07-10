# Comandos

**Ajuda total**
```plaintext
<Dispositivo> ?
User view commands:
arp-ping ARP-ping
autosave <Group> autosave command group
```

**Ajuda parcial**
```plaintext
<Dispositivo> d?
debugging <Group> debugging command group
delete Delete a file
```

**Configurar nome dispositivo e restaurar o nome original**
```plaintext
<Dispositivo> system-view
[Dispositivo] sysname SwitchPaudaço
[SwitchPaudaço] undo sysname
[Dispositivo]
```

**Activar servidor ftp e desabilitar o server FTP**
```plaintext
<Switch> system-view
[Switch] ftp server enable
[Switch] undo ftp server
```

**Configurar um IP numa interface, eliminar a configuração e ativar interface**
```plaintext
[Router] interface GigabitEthernet0/0/0
[Router-GigabitEthernet0/0/0] ip address 192.168.1.1 255.255.255.0
[Router-GigabitEthernet0/0/0] undo ip address
[Router-GigabitEthernet0/0/0] description interface apagada em 01/10/1999 por TiagoPaudencio
[Router-GigabitEthernet0/0/0] undo shutdown
```

**Verificar interfaces**
```plaintext
[Router] display interface brief
[Router] display interface description GigabitEthernet0/0/0
```

**Mostrar as configurações atuais**
```plaintext
<Switch> display current-configuration
```

**Mostrar as configurações guardadas**
```plaintext
<Switch> display saved-configuration
```

**Guardar as configurações**
```plaintext
<Switch> save
```

**Apagar as configurações guardadas**
```plaintext
<Switch> reset saved-configuration
```

**Mostrar os parâmetros de configuração do arranque do sistema**
```plaintext
<Switch> display startup
```

**Configurar o ficheiro de configuração para o proximo arranque**
```plaintext
[Switch] save
[Switch] copy flash:/vrpcfg.zip flash:/meu-file-de-backup.cfg
<Switch> startup saved-configuration flash:/meu-file-de-backup.cfg
<Switch> reboot
Warning: All the configuration will be saved to the configuration file for the next startup:flash:/vrpcfg.zip, Continue? [Y/N]: N
System will reboot! Continue? [Y/N]: Y
```

**Reiniciar dispositivo**
```plaintext
<Switch> reboot
```

**Desabilitar as mensagens de logs no terminal**
```plaintext
<Switch> undo terminal monitor
```

**Configurar Mensagem do Dia (MOTD)**
```plaintext
[Switch] header login information "Está mensagem é mostrada no momento do login"
[Switch] header shell information "Está mensagem é mostrada depois do login momento do shell"
```

**Configurar e mostrar o relógio**
```plaintext
<Switch> clock timezone Lisboa add 0
<Switch> clock datetime 14:30:00 2025-10-01
<Switch> clock daylight-saving-time Lisboa repeating 00:00 last Sunday March 1:00 last Sunday October 1:00
<Switch> display clock
```

**Configuração de password na consola**
```plaintext
[Switch] user-interface con 0
[Switch-ui-con0] authentication-mode password
[Switch-ui-con0] set authentication password simple HuaweiPassword # Clear-text
[Switch-ui-con0] set authentication password cipher HuaweiPassword # Encriptada
[Switch-ui-con0] user privilege level 15
```

**Configuração de password na consola**
```plaintext
[Router] user-interface con 0
[Router-ui-con0] authentication-mode password # Encriptada
```

**Configuração de interface VLAN para acesso remoto**
```plaintext
[Switch] interface Vlanif1
[Switch-Vlanif1] ip address 192.168.1.1 255.255.255.0
```

**Habilitar o servidor telnet e configuração de password nas VTY**
```plaintext
Switch:
[Switch] telnet server enable
[Switch] user-interface vty 0 4
[Switch-ui-vty0-4] authentication-mode password
[Switch-ui-vty0-4] set authentication password cipher Password
[Switch-ui-vty0-4] protocol inbound telnet
[Switch-ui-vty0-4] user privilege level 15

Router:
[Router] telnet server enable
[Router] user-interface vty 0 4
[Router-ui-vty0-4] authentication-mode password
[Router-ui-vty0-4] protocol inbound telnet
[Router-ui-vty0-4] user privilege level 15
```

**Confirmar serviços de telnet**
```plaintext
[Switch-ui-vty0-4] display telnet server status
[Switch-ui-vty0-4] display telnet user-information
```

**Tempo de inatividade**
```plaintext
[Switch-ui-vty0-4] idle-timeout 10 0
```

**Bloqueio por limite de tentativas falhadas**
```plaintext
[Switch-ui-vty0-4] authentication failure rate-limit 3 60
```

**Limite de histórico**
```plaintext
[Switch-ui-vty0-4] history-command max-size 20
```

# 3.2
## SW1Tiago
```
system-view
undo info-center enable
sysname SW1Tiago

telnet server enable
user-interface vty 0 4
authentication-mode password
set authentication password cipher huaweiatec
idle-timeout 5 0
quit

user-interface console 0
authentication-mode password
set authentication password cipher huaweiatec
idle-timeout 5 0
quit

header login information "Apenas pessoal autorizado!"
header shell information "Apenas pessoal autorizado!"

vlan 10 
description PC1
vlan 20
description PC2

interface Vlanif1
ip address 192.168.10.70 255.255.255.0
quit

interface Ethernet0/0/2
port link-type access
port default vlan 10
description PC1 VLAN 10
quit

interface Ethernet0/0/3
port link-type access
port default vlan 20
description PC2 VLAN 20
quit

interface Ethernet0/0/1
port link-type trunk
port trunk allow-pass vlan 10 20
description Ligação para SW2
quit

quit
save
```

## SW2Tiago

```
system-view
undo info-center enable
sysname SW2Tiago

telnet server enable
user-interface vty 0 4
authentication-mode password
set authentication password cipher huaweiatec
idle-timeout 5 0
quit

user-interface console 0
authentication-mode password
set authentication password cipher huaweiatec
idle-timeout 5 0
quit

header login information "Apenas pessoal autorizado!"
header shell information "Apenas pessoal autorizado!"

vlan 10 
description PC3
vlan 20
description PC4

interface Vlanif1
ip address 192.168.10.60 255.255.255.0
quit

interface Ethernet0/0/2
port link-type access
port default vlan 10
description PC3 VLAN 10
quit

interface Ethernet0/0/3
port link-type access
port default vlan 20
description PC4 VLAN 20
quit

interface Ethernet0/0/1
port link-type trunk
port trunk allow-pass vlan 10 20
description Ligação para SW2
quit

quit
save
```


## 3.4 

```
interface GigabitEthernet0/0/0
ip address 192.168.10.1 255.255.255.0 
description Ligação à VLAN 10
quit
interface GigabitEthernet0/0/2 
ip address 192.168.20.1 255.255.255.0 
description Ligação à VLAN 20
quit
```

