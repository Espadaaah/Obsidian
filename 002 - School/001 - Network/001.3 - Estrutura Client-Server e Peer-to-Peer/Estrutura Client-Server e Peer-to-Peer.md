#Network/Sessão-1/Client-Server_P2P

[Client-Server](#Client-Server)
[Peer-to-Peer (P2P)](#Peer-to-Peer%20(P2P))

## Client-Server

![](Imagens/Client-Server.png)

## Design Principles for Effective Client-Server Architecture

Designing an effective client-server architecture involves several key principles that ensure the system is robust, scalable, secure, and efficient. Here are the main design principles:

- [****Modularity****](https://www.geeksforgeeks.org/inroduction-to-modularity-and-interfaces-in-system-design/)****:****
    - ****Separation of Concerns:**** Divide the system into distinct modules, such as the client, server, and database, each responsible for specific tasks. This separation simplifies development, testing, and maintenance.
    - ****Reusability:**** Design components that can be reused across different parts of the system or in different projects.
- [****Scalability****](https://www.geeksforgeeks.org/what-is-scalability-and-how-to-achieve-it-learn-system-design/)****:****
    - [****Horizontal Scalability****](https://www.geeksforgeeks.org/system-design-horizontal-and-vertical-scaling/)****:**** Ensure that the system can handle increased load by adding more servers or instances rather than just upgrading existing hardware.
    - [****Vertical Scalability****](https://www.geeksforgeeks.org/system-design-horizontal-and-vertical-scaling/)****:**** Allow for upgrades in server hardware, such as CPU, memory, and storage, to handle more intensive tasks.
- ****Reliability and Availability:****
    - [****Redundancy****](https://www.geeksforgeeks.org/redundancy-system-design/)****:**** Implement redundant components, such as multiple servers, to ensure the system remains operational in case of failures.
    - [****Load Balancing****](https://www.geeksforgeeks.org/what-is-load-balancer-system-design/)****:**** Distribute client requests across multiple servers to prevent any single server from becoming a bottleneck.
- ****Performance Optimization:****
    - ****Efficient Communication:**** Optimize the communication protocols and data exchange formats to reduce latency and bandwidth usage.
    - [****Caching****](https://www.geeksforgeeks.org/caching-system-design-concept-for-beginners/)****:**** Use caching mechanisms to store frequently accessed data closer to the client to improve response times.
- ****Security****:
    - ****Authentication and Authorization:**** Ensure that only authorized clients and users can access the server and its resources.
    - ****Encryption:**** Use encryption protocols (e.g., SSL/TLS) to secure data transmission between clients and servers.
    - ****Regular Audits:**** Conduct regular security audits and updates to identify and address vulnerabilities.
- ****Maintainability****:
    - ****Clean Code:**** Write clear, well-documented, and maintainable code to simplify debugging and future enhancements.
    - ****Version Control:**** Use version control systems to manage changes in the codebase and coordinate among development teams.
- ****Interoperability****:
    - ****Standard Protocols:**** Use standard communication protocols (e.g., HTTP/HTTPS, REST, SOAP) to ensure compatibility between different clients and servers.
    - ****Platform Independence:**** Design the system to support multiple platforms and devices, allowing various clients to interact with the server.

---
## Peer-to-Peer (P2P)

![](Imagens/Peer-to-Peer.png)

### Types of P2P Networks

- ***Unstructured P2P Networks:*** In this type of P2P network, each device is able to make an equal contribution. This network is easy to build as devices can be connected randomly in the network. But being unstructured, it becomes difficult to find content. For example, Napster, Gnutella, etc.
- ***Structured P2P Networks:*** It is designed using software that creates a virtual layer in order to put the nodes in a specific structure. These are not easy to set up but can give easy access to users to the content. For example, P-Grid, Kademlia, etc. 
- ***Hybrid P2P Networks:*** It combines the features of both P2P networks and client-server architecture. An example of such a network is to find a node using the central server.

### Advantages of P2P Network

- ***Easy to Maintain:*** The network is easy to maintain because each node is independent of the other.
- ***Less Costly:*** Since each node acts as a server, therefore the cost of the central server is saved. Thus, there is no need to buy an expensive server.
- ***No Network Manager:*** In a P2P network since each node manages his or her own computer, thus there is no need for a network manager.
- ***Adding Nodes is Easy:*** Adding, deleting, and repairing nodes in this network is easy.
- ***Less Network Traffic:*** In a P2P network, there is less network traffic than in a client/ server network.

## Disadvantages of P2P Network

- ***Data is Vulnerable:*** Because of no central server, data is always vulnerable to getting lost because of no backup.
- ***Less Secure:*** It becomes difficult to secure the complete network because each node is independent. 
- ***Slow Performance:*** In a P2P network, each computer is accessed by other computers in the network which slows down the performance of the user.
- ***Files Hard to Locate:*** In a P2P network, the files are not centrally stored, rather they are stored on individual computers which makes it difficult to locate the files.