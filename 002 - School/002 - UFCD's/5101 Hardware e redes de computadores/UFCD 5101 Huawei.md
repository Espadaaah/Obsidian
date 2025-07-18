
## Conceito De Redes De Computador

Dispositivos de computação interconectados.

Podem trocar dados e compartilhar recursos.

Usam um sistema de regras chamados de protocolos de comunicação.

Dados podem ser transmitidos por meio de tecnologias físicas ou sem fio.

![[Pasted image 20250605161611.png]]

Podemos averiguar acima uma espécie de senso comum na nomenclatura das redes, apenas uma estimativa de distancia e não regra geral.


#### LAN 

Consiste apenas numa Network que seja de mais de um dispositivo conectado. nas nossas "proximidades" . Por exemplo se tivermos um PC ligado a um switch e a um servidor já temos uma LAN.
![[Pasted image 20250605162254.png]]


#### MAN 

![[Pasted image 20250605162335.png]]

Joins 2 LANs over a span of distance.

#### WAN

![[Pasted image 20250605162459.png]]


#### Other Networks

**WLAN - Wireless LAN**


**VLAN - Virtual LAN**


**VPN - Virtual Private Network**


## Modos de Transmissão

##### Simplex

Comunicação só acontece numa direção entre dispositivos.

Apenas o remetente pode enviar informações.

Exemplos: teclado, monitor.


**Half-Duplex**

Comunicação só acontece numa direção de cada vez

Podem enviar e receber informações mas separadamente

Exemplos: walkie-talkie, hub


**Full-Duplex**

Comunicação pode acontecer em ambas as direções em simultâneo

Ambos podem enviar e receber informações

Exemplos: Telefone, Full-duplex Ethernet


## Estrutura Cliente Servidor

#### PEER-TO-PEER (P2P)

Um ou mais clientes solicita serviços ou dados de um servidor central.

O servidor gere as solicitações e fornece os recursos.

Vantagens de gerenciar, monitorizar e escalar a rede.

Desvantagem de ser um único ponto de falha.

Os peers (nodes/nós) atuam simultaneamente como clientes e servidores.

A descentralização traz menor custo de implementação e resiliência. 

Difícil monitorizar e garantir a segurança.

Menor escalabilidade e performance

Por exemplo: pirataria nos serviços P2P de torrents.

#### POINT-TO-POINT e POINT-TO-MULTIPOINT

![[Pasted image 20250605164244.png]]

## Topologias

##### BUS
![[Pasted image 20250605164328.png]]

Todos os nodes estão interligados pelo cabo do backbone.

Só uma comunicação em simultâneo. Se falhar os outros não afetados.

Pouca escalabilidade, sendo apenas adequada a pequenas redes.

Pouca segurança e performance, e difícil de fazer troubleshooting.

| Pros                            | Cons                                       |
| ------------------------------- | ------------------------------------------ |
| Easy to install                 | One fault can bring down the whole network |
| Cost-effective (small networks) |                                            |
Rare in modern networks, mostly legacy systems.

##### ÁRVORE (TREE)

![[Pasted image 20250605164737.png]]

**Structure**: Combines characteristics of star and bus topologies in a hierarchical manner.

| Pros       | Cons                                         |
| ---------- | -------------------------------------------- |
| scalable   | maintenance and configuration can be complex |
| structured |                                              |
Common in large enterprises and ISP Networks.

##### ANEL (RING)

![[Pasted image 20250605164754.png]]
**Structure**: Each device is connected to two others, forming a ring.

| Pros                  | Cons                                                                      |
| --------------------- | ------------------------------------------------------------------------- |
| Predictable data path | A break anywhere affects the entire network (unless dual rings are used). |
Mostly obsolete, but used in some Fiber Distributed Data Interface (FDDI) networks.

##### ESTRELA (STAR)

![[Pasted image 20250605164827.png]]
**Structure**: All devices are connected to a central hub or switch.

| Pros             | Cons                                                      |
| ---------------- | --------------------------------------------------------- |
| Easy to manage   | If the central device fails, the whole network goes down. |
| Isolate problems |                                                           |
Very common in homes and offices (via Ethernet and Wi-Fi access points).

##### MALHA (MESH)

![[Pasted image 20250605164847.png]]
**Structure**: Devices are interconnected with many redundant links.

| Pros                | Cons                   |
| ------------------- | ---------------------- |
| Very fault-tolerant | Expensive to implement |
|                     | Complex to implement   |
Used in backbone networks, data centers, and wireless mesh networks (e.g., smart homes or cities).

##### HIBRIDA/COMBINADA
![[Pasted image 20250605164859.png]]
**Structure**: Mix of two or more topologies (e.g., star-bus, star-ring).

| Pros              | Cons      |
| ----------------- | --------- |
| Flexible          | Expensive |
| Tailored to needs | Complex   |


#### Most common used today

- **Star Topology**: Standard for most small to medium-sized LANs.

- **Mesh Topology**: Gaining popularity with Wi-Fi 6 and smart device ecosystems.

- **Hybrid Topology**: Enterprise and cloud infrastructure often rely on hybrids.

****
## Equipamentos e Hardware

#### Placas de rede ou NIC

***BUS + Ethernet***

***Fibra ótica***

***Wireless***

Possuem várias velocidades consoante a tecnologia usada.

Permite conectar computadores a uma determinada interface.

#### Equipamentos de Rede

***HUB***

***Switch***

***Router***

##### HUB

Opera apenas na camada 1 do modelo OSI.

Não filtra trafego.

Retransmite os dados para todas as portas (exceto da que recebeu).

Opera em Half-duplex.

Pode gerar colisões e delays na rede.

Hubs passivos: não amplificam o sinal.

Hubs ativos: amplificam o sinal a retransmitir.

Simples de configurar e baixo custo.


#### Switch

Opera na camada 2 do modelo OSI.

Filtra tráfego.

Operam em half-duplex e full-duplex (FDX).

Separam domínios de colisões.

Acesso de dispositivos de utilizadores finais.

Funções básicas de segurança.

Não fazem roteamento de VLANs.

#### Switch Layer 3

Na maioria das vezes usado como core switch.

Opera na Camada 2 e na Camada 3.

Faz roteamento de VLANs.

Capacidades de roteamento.

Menos features de roteamento que um router.


#### Router

Opera na camada 3 do modelo OSI.

Comunicação entre redes.

Isolamento de domínios de Broadcast.

Manutenção da tabela de roteamento.

Seleção de rotas e encaminhamento de pacotes.

Implementação de acesso WAN.

Tradução de endereços de rede (NAT).

### Dispositivos Wireless

***AC - Access Controller***

***AP - Access Point***

#### Wireless AP - Modo Local

The **AP** serves clients directly and tunnels traffic to the AC.

All wireless traffic goes:

- `Client → AP → WLC or AC → LAN/Internet`

**The AP does not switch traffic locally** — it depends on the controller.


| Pros                                       | Cons                           |
| ------------------------------------------ | ------------------------------ |
| Strong control and visibility              | Latency (specially if AC far)  |
| Centralized securioty and QoS              | AC is the single failure point |
| Roaming support across AP's via controller |                                |


#### Wireless AP - Modo Bridged

The AP bridges directly to the local LAN.

Client traffic goes:

- `Client → AP → Local switch/router`


| Pros                                  | Cons                     |
| ------------------------------------- | ------------------------ |
| Lower latency                         | Less centralized control |
| Works even if no AC                   | Requires careful VLAN    |
| Efficient for distributed enviroments |                          |

### Firewall

Hardware/Software concebidos para prevenir accesso não autorizado.

Regras baseadas no IP de destino ou origem de uma determinada rede.

Também analisar ,o numero das portas utilizadas e padrões de trafego.

Instalação na juncão de redes (Normalmente antes do border router).


## Modelo OSI - Open System Interconnection

Layer - 7 - Application
Layer - 6 - Presentation
Layer - 5 - Session
Layer - 4 - Transport
Layer - 3 - Network
Layer - 2 - Data Link
Layer - 1 - Physical

##### Layer 1

Transmite bits, basicamente os impulsos elétricos. 

Protocolos: 1100HBASE E-TX (type of Coaxial protocol), SDH. 

##### Layer 2

Encapsula pacotes em **frames**. Deteta e corrige erros da camada 1  para enviar para a camada 3. Transfere dados na mesma LAN.

Protocolos: Ethernet, PPP, PPPoE

##### Layer 3

Roteamento de endereços dos diferentes dispositivos. É feito o endereçamento na fragmentação dos pacotes. 

Protocolos: IPv4, IPv4, OSPF, ICMP, IGMP

##### Layer 4

Gere o tráfego entre o host e os dispositivos de destino. Verifica erros antes da retransmissão.

Protocolos: TCP, UDP

##### Layer 5

Procedimentos para criar, suspender, terminar ou reiniciar a sessão entre dispositivos.

Protocolos: NetBIOS, RPC, SMB

##### Layer 6

Encriptação/desencriptação dos dados, encode para um formato compreensível (e decode), e compressão e descompressão.

Protocolos: TLS, ZIP, Base64, ASCII.

#### Layer 7 

Permite que os softwares acedam à rede, interpreta/processa dados, acessos/autenticação.

Protocolos: HTML, FTP, DNS, SSH, Telnet, HTTP

### Modelo TCP/IP

Junta as 3 layers de cima **(Session, Presentation and Application)** and calls it just **Application Layer**. and joins the **Layer 1 with the Layer 2** and calls with **Network Access/ Link**.
![[Pasted image 20250605184112.png]]


>[!Important]
>Huawei model just gather the **last 3 layers** (Application Layer). Not the 1 and 2.


### PDU

Chamamos á transferência de dados nomes diferente conforme vai se complementado com as layers.

| Layer       | Name    |
| ----------- | ------- |
| Physical    | Bits    |
| Data Link   | Frame   |
| Network     | Packet  |
| Transport   | Segment |
| Application | Data    |

![[Pasted image 20250605184604.png]]

For example:

Hub - Operates at Layer 1

Switch - Operates at Layer 2

Router - Operates at Layer 3


## Versatile Routing Platform or VRP

VRP é o sistema Operativo que os produtos Datacom da Huawei usam.

**VRP**
Design centralizado.
Dispositivos low-end to mid-range.
baixa performance.

**VRP 2**
Design distribuído

**VRP 3**
Plataforma distribuída
Suporte para routers core

**VRP 5**
Component based design
Maior performance

**VRP 8**
Multi-process
Component based design
Suporte para multi CPU e multi chassis.

#### Sistema de Ficheiros VRP

Flash - Memoria flash é não volátil e pode evitar a perda de dados em caso de corte de energia. É usada para armazenar o software do sistema, ficheiros de configs entre outros...

SDRAM - Memoria volátil que armazena informações ou parâmetros de funcionamento.

NVRAM - Uma memoria não volátil utilizada para armazenar ficheiros de buffer de registos. Os registos serão escritos na memoria flash apos o tempo limite expirar ou quando op buffer tiver cheio.

SD Card - Expansão de memoria que pode evitar perda de memoria caso corte de energia.

USB - Utilizada como interface para ligar um método de armazenamento de grande capacidade, com o objetivo de atualizar o dispositivo ou transmitir dados. 

### BOOT Sitstema

O bootROM é o software utilizado para fazer boot ao dispositivo.

Lê o ficheiro de configuração na flash para iniciar o dispositivo.

#### Gestão de Interfaces

**Gestão de Sistema**

GUI - via HTTP/HTTPs

CLI - consola, ssh, telnet

**Interfaces**

Consola - gestão local

VTY - gestão remota via telnet/ssh

### Níveis de Permissões


| Nível do user | Nivel do Comando | Nome | Comandos Disponíveis |
| ------------- | ---------------- | ---- | -------------------- |
|               |                  |      |                      |
|               |                  |      |                      |
|               |                  |      |                      |
|               |                  |      |                      |

## Comandos Básicos de Configuração

**HELP** and **CONFIG**

**Mostra Parametros de Arranque**
display current-configuration  # Shows current config

display saved-configuration  # Shows saved-configuration


**Guardar e Configurar Configs Files**
save  # Saves configuration

reset saved-configuration  # reset saved-configuration

display startup  # displays start up config

copy flash:/filename.zip flash:/meu-file-de-backup.cfg   # backsup the config to another file

startup saved-configuration flash:/meu-file-de-backup.cfg  # Changes startup file



reboot  # reboots the system

undo terminal monitor  # Desativa os logs no terminal.

autosave

d?

delete

system-view - equal enable or root access


**Login Messages**
header login information -  # Same as a banner motd  (Before login)

header shell information -  # Same as a banner motd (After login)


**Hostame**
sysname # Hostname change

undo sysname # cancels the sysname

**Relógio**

HISTORICO
history-comand max-size 20  # MAX command history size

ftp server enable # ftp server start

undo ftp server # undos ftp server

**CONSOLE CONF**
user-interface con 0  # enters interface of the console

authentication-mode password  # enter password config

set authentication password simple (password) # Sets password clear-text

set authentication password cipher (password)  # Sets password encriptada

user privilege level 15  # utilizador com máximo privilegio


**LINE VTY**

telnet server enable - starts telnet connection

user-interface vty 0 4 - goes to the vty lines

authentication-mode password  # enters password mode

set authentication password cipher YOUR_PASSWORD  # creates password

protocol inbound (telnet/ssh/etc..)   # Allows only the connection via *

user privileges 15   # Gives max permissions

display telnet server status  # displays server status

display telnet user-information  # displays

**TIMEOUT TIME**
idle-timeout 10 0   # Time until connection goes down


**CONFIGURE USER AUTHENTICATION**

**VLAN**

vlan -number-   # creates vlan

interface Vlanif[number]  # Enters vlan interface

ip address IP SUBNETMASK  # set vlan ip


**ROUTER ONLY**

interface Ex: GigabitEthernet 0/0/0 -  # Enters interface

ip address IP Subnet-Mask  # Give IP to the interface

ospf 1  # Enters the ospf protocol

area 0  # This command is used to enter OSPF area from the OSPF view

description  # On a interface makes a comment 

display interface  # Displays interface info

display interface brief  # Brief display info

display interface description  # Displays description interface

display interface description interface  # Display interface description info of the selected interface

**COMANDOS ARP** 

arp-ping

arp -a  # Checks arp cache

display mac-address  # displays mac address table

display arp  # displays arp table

>[!Nota]
>Basically "undo" before a command undoes the command.

### Cabo Coaxial

![[Pasted image 20250605203727.png]]

### Pares de Cobre

![[Pasted image 20250605203850.png]]

### Normas de pares entrançados

![[Pasted image 20250605204008.png]]

O A começa com Branco/Verde, Verde

O B começa Branco/Laranja, Laranja

O B é o mais usado.

## Fibra Ótica

![[Pasted image 20250605204332.png]]

### Modos de Transmissão e Conectores

![[Pasted image 20250605204552.png]]


## Camada Data Link

#### MAC address

![[Pasted image 20250605205227.png]]
![[Pasted image 20250605205236.png]]
![[Pasted image 20250605205335.png]]

### MAC Table

Saves the MAC address with the physical port/porta number 
like:

| Adress            | Port  |
| ----------------- | ----- |
| 11:22:33:44:55:66 | Fa0/3 |
| 11:22:33:44:55:67 | Gb0/1 |
| 11:22:33:44:55:68 | Fa0/2 |

#### ARP 

Trabalha na camada 2. Resolve endereços de IPv4 em MAC.

Os switches têm tabela MAC que faz a relação para a porta (física).

Os hosts, SW L3 (Switch layer 3) e router têm tabela ARP que faz a relação com os IPs.

O ARP pode ser atacado através de ARP spoofing por exemplo.

Tabela ARP:

| IP            | MAC               | Interface |
| ------------- | ----------------- | --------- |
| 10.10.10.10   | 11:22:33:44:55:66 | VLAN 1    |
| 172.16.30.34  | 11:22:33:44:55:67 | VLAN 3    |
| 192.168.16.10 | 11:22:33:44:55:68 | Fa0/3     |

![[Pasted image 20250617010725.png]]

