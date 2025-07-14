---
banner: Obsidian_Notes/CISEG0525/UFCD Images support/Pasted image 20250617010725.png
---
## Objetivos dados neste modulo

- Definir os componentes da Frame Ethernet
- Caracterizar VLANS
- Conhecer o protocolo GARP e GVRP
- Explorar as especificidades do protocolo STP
- Efetuar as configurações em L2


### Ethernet Frame

![](../../../attachments/Teste%202%20Redes%20Proença%201-1.png)

##### LLC/SNAP and EtherType

We talked about the 2 frames that operate in modern networks.

- Ethernet II`
- IEEE 802.3

Esses frames têm principalmente 2 tipos de Identificador de protocolo. 

O trabalho do Ethertype é para identificar o protocolo acima carrega, como se fosse uma label.
Essentially  SNAP provides a more versatile method for this identification.



| Features                | Ethernet II                                                     | IEEE 802.3 with SNAP                                                   |
| ----------------------- | --------------------------------------------------------------- | ---------------------------------------------------------------------- |
| Protocol Identification | Uses 2 byte Type<br>(EtherType) field                           | Uses 5 byte SNAP header<br>following type LLC header                   |
| Field in Header         | Has a **Type** Field                                            | Has a **Length** field                                                 |
| Overhead                | Lower overhead as it doesn't require extra LLC and SNAP headers | Higher overhead due to the 8 additional bytes for the LLC              |
| Flexibility             | Limited to protocols that use EtherType                         | More flexible, using SNAP gives the possibility to use more protocols. |

O SNAP é basicamente uma campo que vem depois do LLC. Pensem no SNAP como se fosse um conversor ou um adaptador que permite usar protocolos mais antigos com o LLC. Existem diversos protocolos que usam EtherType.

Analogia para terminar o pensamento.

- O **cabeçalho** **LLC** é como se fosse uma tomada elétrica com um padrão mais recente mas tem poucas entradas compatíveis.

- Os **protocolos** como **IP**, que usam EtherType, são aparelhos que têm uma ficha mais antiga e não são compatíveis com a "tomada" LLC.

- O **SNAP** é o adaptador que voce conecta na tomada LLC que permite as fichas antigas ligarem-se.

O SNAP não permite que os protocolos antigos usem LLC, mas que deem de certa forma bypass as limitações do LLC.

##### Size of the Headers


| Field         | Ethernet II                                                                                   | IEEE 802.3 SNAP                                                                                                                                                                                        |
| ------------- | --------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| SMAC e DMAC   | 6 bytes each                                                                                  | same as Ethernet II                                                                                                                                                                                    |
| EtherType     | 2 bytes, common values:<br>0x0800 - IPv4<br>0x0806 - ARP<br>0x86DD - IPv6<br>0xXXX - RARP<br> | Doesn't have Ethertype                                                                                                                                                                                 |
| LCC with SNAP | Doesn't have                                                                                  | Length: Indica o tamanho da (LLC+SNAP+Payload)<br>LLC:<br>   ->    DSAP: 1 byte<br>   ->    SSAP: 1 byte<br>   ->    LLC/Control: 1 byte<br>SNAP: <br>   ->    OUI:   3 byte<br>   ->    Type:  2 byte |
| Data/Payload  | 46 to 1500 bytes                                                                              | Because the header ends up being bigger, it consumes payload size availability.<br>So technically with SNAP the **max payload size is 38 to 1492**.                                                    |
| FCS           | 4 byte                                                                                        | Same as Ethernet II                                                                                                                                                                                    |
>[!Nota]
>Se o SNAP tiver a ser usado o SSAP e DSAP ficam a 0xAA

### Dominios de Colisão

Sabemos o que colisão de pacotes é o que o nome sugere.

***Quando ocorrem colisões?***

- Redes que usem um Hub em vez de um switch

- Redes que funcionem em Half-Duplex, onde não haja coordenação de envio.

- Quando há muitos dispositivos a tentar comunicar ao mesmo tempo.

- Falhas de configuração dos dispositivos

Quando acontece uma colisão a transmissão é parada por um tempo aleatório, e retoma. Protocolo CSMA/CD (Carrier Sense Multiple Access with Collision Detection) trata disso.


***Full-Duplex***

Em Full-Duplex cada direção de comunicação usa um canal próprio. Ou seja colisões são praticamente eliminadas, a não ser uma falha no equipamento.


###### CSMA/CD

Usado em IEEE 802.3 em config Half-Duplex.
- Se o canal estiver livre transmite, deteta colisões após acontecerem.
- Após as colisões os endpoints mandam sinal de congestionamento.
- Os dispositivos para a transmissão por tempo aleatório e voltam a transmitir após esse tempo.

###### CSMA/CA

Carrier Sense Multiple Access with Collision Avoidance

- Usado no standard IEEE 802.11 (Wifi)
- Mais difícil detetar colisões em rede WIFI.
- Remetente espera fixa + aleatoriamente antes de transmitir.
- Aguarda ACK do recetor, senão repete o processo de transmissão.


## VLANS


##### Safety and Performance

VLAN todos sabemos que é segmentar a rede logicamente e não fisicamente. Assim poupamos caché, espaço físico etc etc. 
Um dos biggest gains, é a performance e a segurança adicional.

**Segurança**: 
Faz que a superfície de ataque seja reduzida. um atacante não pode ir para outra VLAN sem passar por Firewall ou Router.
Ao limitar domínios de broadcast, faz com que não haja data leakage de outras Vredes.
Melhor criação de Firewall rules quando está tudo organizado.
Podemos isolar servidores por exemplo, e outros dispositivos não podem acede-los.


**Performance**:
Ao compartimentalizar os domínios de broadcast há menos congestionamento da rede.
Criação de departamentos, por exemplo, permite melhor organização. 


##### Tagged and Untagged

A Vlan tag é basicamente para identificar a que VLAN pertence o frame.

Numa vlan que seja tag. Uma **4-byte** tag (A **802.1Q**) é metida entre o ***Source MAC e o EtherType/Length field.***

Com essa tag vem também o **VLAN ID** que tem **12 bits** (permite 4094 VLANS), priority e outra info.

**Estrutura do frame:**

`[Dest MAC][Src MAC][802.1Q Tag: VLAN ID][Type][Payload]`


###### Porque o Acess Port e o Trunk?


| Port Type | Tags nas Frames? | Proposito                                |
| --------- | ---------------- | ---------------------------------------- |
| Access    | No               | Connects endpoints                       |
| Trunk     | Yes              | Connecta Switches or VLAN aware devices. |


***Access Ports:***

- Apenas carregam trafico para uma VLAN.
- O switch remove qualquer tag antes de mandar o frame para o endpoint.
- O Switch sabe a que endpoint o frame vai por causa da configuração do port.

***Trunk ports:***

Carregam trafego de varias VLANs (dai a tag).
Cada frame vem com a tag da vlan para que o receiving switch saiba o que fazer com o frame.
Trunks são essenciais entre switches, routers, and APs para manter a separação entre VLANS.


Vou usar o Lab 3.4 como exemplo para explicar tag and untagged.

Como usamos "Router-on-a-stick" e as portas tiveram de estar em access, acho que se entende bem.

O processo de tagging e untagging do ID é feito de forma automática pelo switch. Com base no tipo de porta e config.

Vamos imaginar de acordo com o lab, o **PC3 (VLAN 10 ligado aso SW2)**, manda um pacote para o **PC4 (VLAN 20 ligado aso SW2)**.

1. **O SW2 não vê nenhuma tag**, mas sabe que o que entra pela porta do PC3 que pertence à **VLAN 10**.
2. O **frame entra untagged** -> o **SW2 adiciona a tag VLAN 10**.
3. O frame atravessa o **trunk** entre SW2 e SW1 -> **vai com a tag VLAN 10**.
4. O **SW1 lê a tag VLAN 10** -> sabe que deve enviar para a interface do router ssociada à VLAN 10.
5. A porta do **SW1 ligada ao RTR está em modo access e associada à VLAN 10**.
6. O **SW1 remove a tag** e envia o frame **untagged** para o RTR.
7. O **RTR recebe o frame pela interface VLAN 10**, e com base na **IP de destino da VLAN 20**, decide encaminhar para a sub-rede correspondente.
8. O **RTR envia o pacote pela interface configurada para VLAN 20**, sem tag.
9. O **SW1 recebe o frame untagged numa porta access VLAN 20**, e **adiciona a tag VLAN 20**.
10. O frame segue pela **trunk para o SW2**, com a nova **tag VLAN 20**.
11. O **SW2 lê a tag VLAN 20** -> encaminha para a porta configurada como **access VLAN 20** (por exemplo, para o PC5).
12. O **SW2 remove a tag** e entrega o frame **untagged** ao PC5.



