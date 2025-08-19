## Introduction:
Networking is the backbone of modern communication, enabling billions of devices to connect and exchange information across the globe. Whether you're browsing a website, sending an email, or streaming a video, networking concepts are working behind the scenes to make it possible.
In this blog, I’ve summarized key networking fundamentals including how the Internet works, types of networks (LAN, WAN, MAN, PAN), the OSI and TCP/IP models, IP & MAC addressing, network devices like routers and switches, essential protocols and ports, firewall basics, and the client-server architecture.
If you're starting your journey in tech, preparing for DevOps roles, or aiming to strengthen your fundamentals, this blog will serve as a comprehensive guide to networking essentials.
________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________
## How does the Internet work?
1.	It basically uses the Optical fiber cable that is placed in the oceans at a large deptth. View that visit: https://www.submarinecablemap.com/
2.	There are 3 tiers of company architecture used to provide the Internet to end users.
 
    Tier 1: A company that owns the optical fiber cable in the ocean, companies like AT&T, NTT, Verizon

  	Tier 2: A company like Jio, Airtel, and BSNL that takes the cable on RENT and provides it to their end users

  	Tier 3: Small companies that also take internet from TIER 2 companies and provide the internet in a small area like, Jio fiber, You Broadband
________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________

## Types of Network:

<p align="center">
<img width="470" height="222" alt="image" src="https://github.com/user-attachments/assets/3d082ca4-1114-471c-adc3-ffcddee34a04" />
</p>

#### 1.	WAN (Wide Area Network):

    Scope:  
          Covers a very large geographic area, potentially spanning across cities, countries, or even continents.
    
    Characteristics:
          Often involves complex infrastructure and can be a combination of public and private networks. 
          Generally offers lower speeds and higher latency compared to LANs and MANs.
    
    Examples:
          The Internet is a multinational corporation's network connecting offices across different countries.

#### 2.	MAN (Metropolitan Area Network):
    
    Scope: 
          Covers a larger geographic area than a LAN, typically a city or a large campus

    Characteristics: 
          Can be owned by a single entity or multiple organizations. 
          Offers moderate speed and is suitable for connecting multiple LANs within a city.

    Examples:
          A city-wide network connecting different government agencies, or a network connecting multiple university campuses within a metropolitan area.

#### 3.	LAN (Local Area Network):

    Scope: 
          Limited geographic area, such as a home, office building, or school.
          
    Characteristics: 
          Typically privately owned and managed. Offers high-speed data transmission and low latency (delay).
          
    Examples: 
          Your home Wi-Fi network, a computer lab in a school, or the network within a single office building.
          
#### 4.	PAN (Personal Area Network):

    Scope Characteristics : 
          Connects devices within a very close proximity, typically a few meters, for an individual's personal use. 
          
    Examples : 
          include Bluetooth connections between a phone and headphones or a wireless mouse connected to a computer.

________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________
## OSI Model & TCP/IP Model

#### A. OSI(Open Systems Interconnection) Model:

The OSI (Open Systems Interconnection) Model is a set of rules that explains how different computer systems communicate over a network. The OSI Model was developed by the International Organization for Standardization (ISO). The OSI Model consists of 7 layers, and each layer has specific functions and responsibilities.

<p align="center">
<img width="500" height="300" alt="image" src="https://github.com/user-attachments/assets/84452fe4-d189-436b-912c-35955991e50a" />
</p>

##### 1.	Application Layer (Layer 7)
      o	What It Does: Provides network services directly to user applications, like web browsers or email clients. It’s the layer you interact with when you use the internet.
      o	Key Tasks: Handles protocols like HTTP (for web browsing), SMTP (for email), or FTP (for file transfers). It ensures apps can communicate over the network.
      o	Example: When you type a URL into your browser, the Application Layer formats the request to fetch the webpage.
      o	Analogy: The front desk of a hotel, where guests (users) make requests for services like room bookings or dining.
##### 2.	Presentation Layer (Layer 6)
      o	What It Does: Translates data between the application and the network, ensuring it’s in a usable format. It handles encryption, compression, and data formatting.
      o	Key Tasks: Converts data (e.g., text, images) into a standard format, encrypts sensitive data (like passwords), and compresses data to save bandwidth.
      o	Example: When you send an encrypted email, the Presentation Layer encrypts the message before it’s sent.
      o	Analogy: A translator who converts your words into a language the recipient understands.
##### 3.	Session Layer (Layer 5)
      o	What It Does: Manages communication sessions between devices, ensuring connections are established, maintained, and terminated properly.
      o	Key Tasks: Sets up, coordinates, and ends conversations between applications. It handles session recovery if a connection drops.
      o	Example: During a video call, the Session Layer keeps the connection active and reconnects if the call briefly drops.
      o	Analogy: A meeting coordinator who schedules, starts, and ends a conference call.
##### 4.	Transport Layer (Layer 4)
      o	What It Does: Ensures reliable data transfer between devices, managing flow control, error checking, and data segmentation.
      o	Key Tasks: Uses protocols like TCP (reliable, ordered delivery) or UDP (fast, less reliable). It breaks data into packets and reassembles them at the destination.
      o	Example: When downloading a file, TCP ensures all packets arrive correctly and in order.
      o	Analogy: A courier service that ensures packages are delivered intact and in the right sequence.
##### 5.	Network Layer (Layer 3)
      o	What It Does: Routes data packets between different networks, determining the best path to the destination.
      o	Key Tasks: Uses IP addresses to route packets. Protocols like IP (IPv4 or IPv6) operate here.
      o	Example: When you visit a website, the Network Layer routes your request from your home network to the website’s server across the internet.
      o	Analogy: A GPS system that finds the best route for your package to travel across cities.
##### 6.	Data Link Layer (Layer 2)
      o	What It Does: Handles communication between devices on the same network, ensuring error-free data transfer.
      o	Key Tasks: Uses MAC addresses to identify devices. It detects and corrects errors from the Physical Layer. Protocols include Ethernet.
      o	Example: In your home Wi-Fi network, the Data Link Layer ensures your laptop and router exchange data correctly.
      o	Analogy: A local mailroom sorting letters to ensure they reach the right office within a building.
##### 7.	Physical Layer (Layer 1)
      o	What It Does: Manages the physical connection between devices, transmitting raw bits over hardware like cables or Wi-Fi.
      o	Key Tasks: Defines hardware standards (e.g., cables, connectors, signal voltages). It converts data into electrical or optical signals.
      o	Example: When you connect to Wi-Fi, the Physical Layer sends radio signals between your device and the router.
      o	Analogy: The physical roads or wires that carry packages from one place to another. 
##### Real-World Example: Sending an email involves all layers. 
      The Application Layer formats the email
      The Presentation Layer encrypts it 
      The Session Layer maintains the connection 
      The Transport Layer ensures reliable delivery 
      The Network Layer routes it to the recipient’s server 
      The Data Link Layer handles local network communication and 
      The Physical Layer sends the data over cables or Wi-Fi.

#### B. TCP/IP Model:

The TCP/IP model (Transmission Control Protocol/Internet Protocol) is a four-layer networking framework that enables reliable communication between devices over interconnected networks. It provides a standardized set of protocols for transmitting data across interconnected networks, ensuring efficient and error-free delivery. Each layer has specific functions that help manage different aspects of network communication, making it essential for understanding and working with modern networks.

TCP/IP was designed and developed by the Department of Defense (DoD) in the 1970s and is based on standard protocols. The TCP/IP model is a concise version of the OSI model. It contains four layers, unlike the seven layers in the OSI model.

<p align="center">
<img width="500" height="300" alt="image" src="https://github.com/user-attachments/assets/1fe290df-664e-4be9-b494-ce4e98602ad6" />
</p>  

##### 1.	Application Layer
      o	What It Does: Combines the OSI’s Application, Presentation, and Session layers. It handles user-facing services, data formatting, and session management.
      o	Key Tasks: Supports protocols like HTTP (web), SMTP (email), FTP (file transfer), and DNS (domain name resolution). It ensures apps can communicate over the network.
      o	Example: When you visit a website, the Application Layer sends an HTTP request to the server and displays the webpage.
      o	Analogy: A one-stop service desk handling customer requests, translations, and session coordination.
##### 2.	Transport Layer
      o	What It Does: Manages end-to-end data transfer, ensuring reliability and flow control. It’s identical to the OSI Transport Layer.
      o	Key Tasks: Uses TCP for reliable, ordered delivery (e.g., for emails) or UDP for faster, less reliable delivery (e.g., for streaming). It segments data into packets.
      o	Example: When streaming a video, UDP sends packets quickly, prioritizing speed over perfection.
      o	Analogy: A shipping company that decides whether to use guaranteed delivery (TCP) or express shipping with some risk of loss (UDP).
##### 3.	Network Layer
      o	What It Does: Routes data packets across different networks, finding the best path to the destination. Matches the OSI Network Layer.
      o	Key Tasks: Uses IP (IPv4 or IPv6) to assign addresses and route packets. Works with routing protocols to navigate the internet.
      o	Example: When you send a message via WhatsApp, the Network Layer routes it from your phone to the recipient’s server.
      o	Analogy: A postal service that forwards packages across cities using addresses.
##### 4.	Network Access Layer
      o	What It Does: Combines the OSI’s Data Link and Physical layers. It handles data transfer within a single network and the physical transmission of bits.
      o	Key Tasks: Uses MAC addresses for local communication and manages hardware (e.g., Ethernet, Wi-Fi). Converts data into signals for cables or wireless.
      o	Example: In your home network, the Network Access Layer ensures your laptop’s data reaches your router via Wi-Fi.
      o	Analogy: A local delivery truck that picks up packages and sends them over physical roads or airwaves.
##### Real-World Example: When you stream a movie, 
      The Application Layer handles the streaming app’s interface and protocols (e.g., HTTPS), 
      The Transport Layer uses UDP to deliver video packets quickly, 
      The Network Layer routes packets to the streaming server, and 
      The Network Access Layer sends signals over your Wi-Fi or Ethernet cable.
________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________

## What is IP & MAC Address?

### A. IP:

##### 1. Internet Protocol (IP):

    It's a fundamental protocol that defines how data is transmitted across networks.

    It ensures that data packets (small chunks of data) are correctly routed to their destination.

    Essentially, it's the language that devices use to communicate with each other on the internet.

##### 2. IP Address:

    An IP address is a unique numerical identifier assigned to each device connected to a network that uses the Internet Protocol.

    It acts like a postal address for your device on the internet, enabling other devices to find and communicate with it.

    There are two main versions of IP addresses: IPv4 and IPv6

        IPv4: addresses are 32-bit numbers, typically written in dotted-decimal notation (e.g., 192.168.1.1).

        IPv6: addresses are 128-bit numbers, designed to address the shortage of IPv4 addresses.

    IP addresses can be public (visible to the outside world, used for internet communication) or private (used within a local network).

### B. MAC Address:

    Physical Address: 
    MAC addresses are unique, hardware-level identifiers permanently assigned to a network interface card (NIC).
  
    Local Network Communication: 
    They are used for communication within a local network, like a home or office network, to ensure data packets reach the correct device.
  
    Unchanging: 
    MAC addresses are typically fixed and do not change.

________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________

## Routers & Switches

### A. Routers:

<p align="center">
<img width="500" height="300" alt="image" src="https://github.com/user-attachments/assets/c12ce39f-40ce-450b-8441-12ac76840e9e" />
</p>

    •	Function: A router connects multiple networks, allowing devices on different networks to communicate, including connecting your local network to the internet. It acts as a traffic director between different networks.
    •	Layer: Routers operate at the Network Layer (Layer 3) of the OSI model.
    •	Connectivity: Connects LANs to other LANs or to the Internet.
    •	Example: A router connects your home network (LAN) to your internet service provider's network, enabling you to access the internet.

### B. Switches:

<p align="center">
<img width="500" height="300" alt="image" src="https://github.com/user-attachments/assets/8f5e302a-a2a3-46ae-bdb8-eca4d52bf960" />
</p>  

    •	Function: A switch connects devices within the same network, allowing them to communicate with each other. Think of it as a traffic controller within a single office building.
    •	Layer: Switches operate at the Data Link Layer (Layer 2) of the OSI model
    •	Connectivity: Connects devices like computers, printers, and servers within a LAN.
    •	Example: In a home network, a switch might connect your computers, gaming consoles, and smart TVs to your router.

________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________

## Firewall, Ports, Protocols

### A. Firewall

Firewalls act as security checkpoints, inspecting network traffic and enforcing rules to protect networks from unauthorized access and malicious activity. They use protocols and port numbers to identify and filter traffic, allowing or blocking connections based on pre-defined rules. For example, a firewall can be configured to block all traffic on port 21 (FTP) while allowing traffic on port 80 (HTTP) and 443 (HTTPS).

<p align="center">
<img width="500" height="300" alt="image" src="https://github.com/user-attachments/assets/8727aff9-5e39-4f7c-a699-8aad05f324cf" />
</p>  

### B. Ports
      
      •	Ports are virtual locations on a device that are used to identify specific services or applications.
      •	They are identified by numbers, ranging from 0 to 65535.
      •	Each port is associated with a specific protocol and service. For example, port 80 is typically used for HTTP (web traffic), and port 443 is used for HTTPS (secure web traffic).
      •	Ports allow a device to handle multiple network connections simultaneously, directing incoming data to the appropriate application or service.

### C. Protocols

A protocol is a set of rules that govern how data is transmitted and received between devices on a network.

##### 1.	HTTP (Hypertext Transfer Protocol)(Port: 80): 

      The foundation of data communication for the World Wide Web. It's used to transmit hypertext (like web pages) between web browsers and servers.

HTTP Methods     
<p align="center">
 <img width="500" height="300" alt="image" src="https://github.com/user-attachments/assets/1cc86641-55e2-4041-a885-daf961407d31" />
</p> 

HTTP responses:
<p align="center">
<img width="500" height="200" alt="image" src="https://github.com/user-attachments/assets/b4b323ea-6996-465b-8b27-a1c1e56a93e8" />
</p>
<p align="center">
<img width="625" height="830" alt="image" src="https://github.com/user-attachments/assets/965fc158-43be-467f-ad7e-dc6996075dca" />
</p> 

##### 2.	HTTPS (Hypertext Transfer Protocol Secure)(Port: 443): 

      An encrypted version of HTTP. It uses TLS/SSL to provide a secure connection, protecting sensitive data during transmission.
##### 3.	FTP (File Transfer Protocol)(Port: 20 (Data), 21 (Control)): 

      Used to transfer files between computers over a network. It allows for uploading and downloading files.
##### 4.	SMTP (Simple Mail Transfer Protocol)(Port: 25, 465, 587):

      The standard protocol for sending emails. It handles the transmission of email messages from a client to a mail server and between mail servers.
##### 5.	TCP (Transmission Control Protocol):

      A connection-oriented protocol that provides reliable, ordered, and error-checked delivery of data. It's used for applications where accuracy is crucial.
##### 6.	UDP (User Datagram Protocol):   

      A connectionless protocol that offers a faster but less reliable way to transmit data. It's suitable for applications where speed is prioritized over absolute accuracy.
##### 7.	IP (Internet Protocol): 

      The core protocol responsible for routing data packets across networks, ensuring that information reaches its intended destination.
##### 8.	ARP (Address Resolution Protocol): 

      A protocol that translates IP addresses into MAC addresses, enabling devices to locate each other on a local network segment.
##### 9.	SSH(Port: 22): 

      SSH, or Secure Shell, is a network protocol that provides a secure way to access and manage remote computers. 
      It uses encryption to protect data transmitted between a client and a server, making it suitable for use over unsecured networks. 
      Essentially, SSH allows you to securely log in to another computer, execute commands, and transfer files.
________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________
