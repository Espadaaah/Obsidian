#Network/Sessão-1/Transmissões-de-Dados

[Simplex](#Simplex)
[Half-Duplex](#Half-Duplex)
[Full-Duplex](#Full-Duplex)

## Simplex

![](Imagens/SIMPLEX.png)

### Advantages of Simplex Mode

1. ****Simplicity:**** Simplex mode is simple to implement because data travels in only one direction. This reduces the difficulty of the communication system.
2. ****Cost-Effective:**** Since communication is single directional, the hardware required (e.g., cables, connectors) can be less costly compared to more complex modes like half-duplex or full-duplex.
3. ****No Collision :**** As data travels in only one direction, there's no risk of data collision, making the communication secure and consistent.
4. ****Efficient Use for Specific Applications:**** Ideal for applications where only one-way communication is necessary, such as broadcasting, keyboard input to a computer, or sending data to a printer.

### Disadvantages of Simplex Mode

1. ****Lack of Bidirectional Communication:****The most significant disadvantage is the incapacity to send data back in the opposite way. This limitation makes it unsuitable for interactive communication.
2. ****Inefficiency for Complex Tasks:**** Simplex mode is not suitable for tasks requiring response or acknowledgment, such as error-checking or data authentication, which are crucial in many communication systems.
3. ****Limited Flexibility:**** Simplex systems lack flexibility because they cannot be easily adjusted to situations where bidirectional communication might become necessary.
4. ****Not Ideal for Modern Networks:**** Most advanced communication systems require bidirectional data flow, making simplex mode largely antiquated in networking scenarios.

---
## Half-Duplex

![](Imagens/HALF-DUPLEX.png)

## Advantages of Half-Duplex Mode

****1. Efficient Use of Channel:**** Half-duplex allows for bidirectional communication over a single channel, making it effective for scenarios where parallel transmission isn't required.

****2. Cost-Effective:**** It requires less complicated and less costly hardware than full-duplex systems, as only one device conveys at a time.

****3. Simplified Collision Handling:**** Since only one device can transmit at a time, crashes are reduced, reducing the need for complicated collision detection and management protocols.

****4. Suitable for Periodic Communication:**** Optimal for situations where communication doesn't need to happen concurrently in both directions, such as walkie-talkies or specific network protocols.

## Disadvantages of Half-Duplex Mode

****1. Slower Data Transmission:**** Since data can only run in one direction at a time, communication is naturally delayed compared to full-duplex systems where data can be delivered and received simultaneously.

****2. Increased Latency:**** The need to exchange between sending and receiving modes introduces delay, which can affect performance in congestion applications.

****3. Not Ideal for High-Traffic Networks:**** In networks with congestion or applications requiring constant communication, half-duplex mode can become a restriction.

****4. Inefficient for Complex Communications:**** For tasks that require frequent two way communication, half-duplex can be less effective as it forces devices to wait their turn, which can lead to pauses.

---
## Full-Duplex

![](Imagens/FULL-DUPLEX.png)

## Advantages of Full-Duplex Mode

1. ****High-Speed Communication:**** Data transfer is quicker because there is no delaying for the channel to clear before sending or receiving data.
2. ****Reduced Latency:**** Since communication is parallel, time lag is minimized, which is critical for real-time applications like web conferencing.
3. ****Better Utilization of Bandwidth:**** The available transmission capacity is used more efficient because both directions of communication can occur at once.

## Disadvantages of Full-Duplex Mode

1. ****Complexity and Cost:**** Executing full-duplex systems requires more complicated hardware and can be more costly than simplex or half-duplex systems.
2. ****Requires Quality Infrastructure:**** Full-duplex communication demands a advanced quality of architecture, such as better cabling and more refined networking equipment, to avoid interference and assure smooth data flow.

## Difference Between Simplex, Half duplex, and Full Duplex Transmission Modes

|Parameters|Simplex|Half Duplex|Full Duplex|
|---|---|---|---|
|****The direction of communication****|[Simplex mode](https://www.geeksforgeeks.org/computer-networks/difference-between-simplex-transmission-modes-and-full-duplex-transmission-modes/) is a uni-directional communication.|[Half Duplex](https://www.geeksforgeeks.org/computer-networks/difference-between-simplex-transmission-modes-and-half-duplex-transmission-modes/) mode is a dual directional communication but one at a time.|[Full Duplex mode](https://www.geeksforgeeks.org/computer-networks/difference-between-half-duplex-transmission-modes-and-full-duplex-transmission-modes/) is a two-way directional communication simultaneously.|
|****Sender and Receiver****|In simplex mode, sender can send the data but that sender can't receive the data.|In Half Duplex mode, sender can send the data and also can receive the data but one at a time.|In Full Duplex mode, sender can send the data and also can receive the data simultaneously.|
|****Channel usage****|Usage of one channel for the transmission of data.|Usage of one channel for the transmission of data.|Usage of two channels for the transmission of data.|
|****Performance****|The simplex mode provides less performance than half duplex and full duplex.|The Half Duplex mode provides less performance than full duplex.|Full Duplex provides better performance than simplex and half duplex mode.|
|****Bandwidth Utilization****|Simplex utilizes the maximum of a single bandwidth.|The Half-Duplex involves lesser utilization of single bandwidth at the time of transmission.|The Full-Duplex doubles the utilization of transmission bandwidth.|
|****Suitable for****|It is suitable for those transmissions when there is requirement of full bandwidth for delivering data.|It is suitable for those transmissions when there is requirement of sending data in both directions, but not at the same time.|It is suitable for those transmissions when there is requirement of sending and receiving data simultaneously in both directions.|
|****Examples****|Example of simplex mode are: Keyboard and monitor.|Example of half duplex mode is: Walkie-Talkies.|Example of full duplex mode is: Telephone.|
