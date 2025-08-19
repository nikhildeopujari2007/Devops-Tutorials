## Network Troubleshooting Tools
### 1.ping
  It uses the ICMP protocol’s ECHO_REQUEST datagram to obtain an ICMP ECHO_RESPONSE from a remote host. 
  The Ping command is integrated into all versions of Windows, so all you need to do to start using it is open up your command prompt or application.

  To troubleshoot using ping, first, run it on your own network (the local host) to ensure that your internet network interface works. 
  This is as easy as opening up the command prompt and typing “ping www.google.com”. Then, as you troubleshoot, you can ping hosts and gateways further and further in the network to try and diagnose the location of connectivity problems.

  When you ping, you get information back, including the percentage of lost packets and average round-trip latency.

  <img width="538" height="235" alt="image" src="https://github.com/user-attachments/assets/cebba91f-56c8-4d69-aabf-045f0944ef19" />  
  
  ________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________

### 2.traceroute
  
  Sometimes a network is particularly slow, and you want to track the routes of your packets or identify which gateway is causing delays. It can be challenging to do this manually, which is where the traceroute command comes in handy.
  
  “traceroute” is a diagnostic command (also sometimes written as “tracert”) that can show you possible routes across an IP network and calculate any transit delays in that route. 
  Whereas the ping command only shows a final round trip time for packets to go from host to destination and back, traceroute calculates the total time spent establishing a connection by adding up the mean respective round trip times for each subsequent node along a given route.
  
  The probes always start by sending a packet with TTL=1. Every time a packet hits a router, it lowers the TTL by 1, so we know that when we get a time exceeded message it is because TTL is at 0; we have reached another stop along the route. Thus, the probe increases TTL by one setting every time, slowly adding hops along the route until the destination is found or the maximum number of hops is hit. At the end of it all, you receive information about the specific path a packet follows and each route along the way.
  
  The report you receive shares the following information:
  
      The Time to Live
      The IP addresses of each stop in the route—each gateway that has responded to the probe
      The round trip time for each router along the route
  
  This is valuable information for knowing an exact route and troubleshooting any speed and network issues. But one of the most valuable tools in traceroute is that the report specifically marks with an asterisk (*) for any router on the route that does not send a response within the time limit. Now, you know exactly where to look to troubleshoot.
  
  Here’s an example of a report output from a traceroute command. Take a close look at it.
  
<img width="500" height="300" alt="image" src="https://github.com/user-attachments/assets/a1214d23-f0ce-49a3-843f-dd89000346e8" />


  
  You may notice that lines 2 and 3 are identical. This is an example of a buggy kernel in the second hop that forwards packets with zero TTL – lbl.csam.arpa .
  
  As you can see, traceroute can give you a lot of really helpful diagnostic information quickly and simply. However, it does have limitations. Some networks don’t provide address-to-name translations. When those appear on your report, you have to guess the path that packets take cross-country. This happens in the report sample above at hop number 6 with IP address 128.32.197.4, a router along the NSFNet, which doesn’t give you the named translation.
  
  ________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________

### 3.telnet

  One important caveat to tools like ping and traceroute? A server responding to traceroute or ping does not necessarily mean that it is operational.
  
  Imagine that we have a virtual machine with an Apache HTTP server on it. This means that in order to load web pages, the machine needs to have the Apache daemon up and running. If it’s not running, although the virtual machine may be responsive to ping requests, we will not be able to load anything.
  
  On the flip side, if a server does not respond to ping, – it’s not necessarily down. Some system administrators configure their firewalls to drop all ping requests, so you’d get no response from the server. But the server behind this firewall can still be reachable via other protocols.
  
  Because of these limitations to traceroute and ping, you want to be able to test whether or not the protocol you’re using will allow you to establish a network connection. Telnet is a command that can help with this.
  
  Historically, telnet was used as a command-line interface for accessing remote servers. However, because telnet does not encrypt the data, it is not secure to use it for remote access and has since been replaced by SSH.
  
  But telnet is still helpful. Nowadays, we can use telnet to test if one host can establish a network connection using a certain protocol. 
  
  A telnet command testing the connection to google.com at port 443, for example, looks like this:
  
<img width="584" height="182" alt="image-2" src="https://github.com/user-attachments/assets/84840215-fe3a-42ab-a83a-72bdb3e3a24e" />

  As you can see above, the command succeeded, which means that a connection is allowed between our local machine and a remote system on a given port.
  ________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________

### 4.curl

As a DevOps engineer, you’re frequently going to have to transfer data, and that means you should know how to use curl. curl is an open-source data transfer tool that supports multiple Application-layer protocols. It’s most commonly used for sending HTTP requests, which are requests for access to a resource on a server. curl is freely available and may already be on your system. If it isn’t, you can easily install it.

The most basic way to use curl is to perform an HTTP GET request (remember from our table earlier in this article that this is a request for a resource (HTTP) that returns the entire entity in the response (GET).

The basic syntax is: .

curl http://example.com

This will send an HTTP GET request to the example.com host.

If you’re checking an exact response code and only want to see response headers, you can use curl -I. The syntax looks like this in our example:

curl -I http://example.com

By default, curl uses the HTTP GET method. If you wanted to use another method to return a certain type of response, you can use the -X flag in your curl command followed by the type of request that you want. For example,

curl -X POST http://example.com

sends a curl HTTP POST (not GET) request (submitting a change to an object—in this case, a change to http://example.com).

curl is the master of data transfer, and we can even download files/store a file’s response with curl by using the -o flag. Syntax for this may look something like this:

curl http://example.com/faile -o output.file.

There are other curl commands, too. Explore curl more deeply on the site for the curl project, where you’ll find a plethora of helpful (and totally free) resources. Once you’re familiar with the tool, you’ll be able to use it to accomplish a number of programming tasks.

  ________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________

### 5.dig

The next tool to learn is “dig”, not “how to dig”, but just “dig” – which stands for Domain Information Groper. 
It is used for troubleshooting Domain Name System (DNS) problems and verifying DNS records. dig performs DNS Lookups and then shows you the answers returned from the name server(s).

The basic syntax of dig for a DNS record lookup is [dig] [domain name]. This will make an NS query and return the “A record”—Address record—for a given domain name.

Let’s break down this example by looking up the DNS record for the domain google.com. At the top, you can see the request: dig google.com. In the ANSWER section of the response, you get a number of pieces of information:

    The queried server (google.com)
    TTL ( in this case 93)
    Query class (IN= internet)
    Query type (A= address)
    The IP address for the queried domain (172.217.0.46)

So there you have it—the google.com DNS record is associated with the IP address 172.217.0.46.

<img width="1024" height="626" alt="image-3-1024x626" src="https://github.com/user-attachments/assets/7d4f958b-3c43-41c1-8adb-b7e9e9d1770f" />

Like with curl, the dig has a default method. By default, dig will attempt to query each server specified using the /etc/resolv.conf file, the automatic file type for configuring DNS name servers. But in some cases, you may want to send queries to a specific DNS server. You can do this with the @ flag.

This example checks the DNS record for google.com on specifically the 8.8.8.8 server. As you can see, it returns a different ANSWER from the /etc/resolv.conf file used in the default above.

<img width="1024" height="668" alt="image-4-1024x668" src="https://github.com/user-attachments/assets/36b97c2e-3bed-4717-ad3c-123280171d09" />

By default, dig also returns an ANSWER of a A record (address). But you can also check different types of DNS records using the -t option. The syntax for this would look like:

dig -t [record type] [domain name]

The example below specifics the TXT record for the google domain.

<img width="1024" height="511" alt="image-5-1024x511" src="https://github.com/user-attachments/assets/a1731b1c-940a-4532-b5d0-e25e5e103965" />

Other dig record types you may want to specifically query:

    MX record- mail exchanger, tells you what mail server accepts email messages for a given domain name
    NS record- all authoritative servers for a domain name
    ALL- all DNS records for a domain name

Dig is a great tool for DevOps engineers to have in their toolbox because it helps you troubleshoot for your name servers, double-check records, and trace IP addresses and their domain names, among other things.

  ________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________

### 6.netstat

netstat is a command that shows you specific information about the communications between your local machine and other machines/devices on the network. Netstat shows active TCP connections as well as ports on which the server is listening. It is useful when you need to see which network services are running on a local machine.

In the example below, we can discover that there is an apache web server listening on the default HTTP port.

<img width="1024" height="134" alt="image-6-1024x134" src="https://github.com/user-attachments/assets/9fd3a55c-830b-423b-b049-e11a0b8cde41" />

In the above example, the command netstat -lp shows only listening servers (-l flag)and their program name (-p flag). Other netstat flag commands include:

    -a: all active ports
    -n: only numerical IP addresses and ports
    -f: whenever possible, provide all names of foreign connections
    -o: show process ID
    -r: routing table

  ________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________

### 7.nmap

The next tool to become familiar with as a DevOps engineer is nmap. nmap, or “network mapper”, is also a free, open-source tool like netstat. A use case for nmap is almost identical to that for netstat, with one minor difference. When you’re using netstat, you have to log into a server. But nmap scans all servers in a network.

nmap sends raw IP packets to determine the hosts available on a given network, what services are offered by these hosts, and what operating systems they are running. System administrators use nmap for tasks such as network inventory and security audits—sometimes known as “white hat” hacking because it identifies vulnerabilities in order to secure and resolve them. However, this tool is also widely used by “black hat” hackers, who use the information provided to exploit vulnerabilities in the network. Because of this potential, some cloud providers do not allow nmap to run on their networks.

In many ways, DevOps engineers are white hat hackers—troubleshooters, security protectors, and network experts. To demonstrate how nmap can be useful for us, let’s go through a simple scenario.

Assume we gained SSH (Secure Shell Protocol) access to an unknown server. Our goal is to find out what else is running on the network.

First, let’s find out the IP of our server and the IP range of our network using our address.

<img width="842" height="377" alt="Screen-Shot-2022-08-02-at-1 07 22-PM" src="https://github.com/user-attachments/assets/558d9630-881c-4033-98df-1e30d4662c58" />

Our IP address is 172.31.44.35 and 255.255.240.0 netmask corresponds to /20
Now that we know this information, we can initiate a nmap ping scan using the following command:

nmap -sn 172.31.44.35/20

<img width="617" height="647" alt="Screen-Shot-2022-08-02-at-1 11 43-PM" src="https://github.com/user-attachments/assets/b89fe545-b63a-4bfe-bf9a-1f84aa3240bd" />

We can see now that there are 15 hosts in the specified subnet.

Let’s test one of these hosts and find out which ports it is listening to. You can do this using the command below:

nmap -A 172.31.36.237

<img width="865" height="420" alt="Screen-Shot-2022-08-02-at-1 13 02-PM" src="https://github.com/user-attachments/assets/be7a3123-58c1-419d-b8eb-a5e77c73efda" />

The nmap command helps us see that the there is an SSH and HTTP processes listening to ports on this server.

Since we know that a curl is a great tool for HTTP, we can then try obtaining the webpage using curl.

<img width="722" height="51" alt="Screen-Shot-2022-08-02-at-1 14 26-PM" src="https://github.com/user-attachments/assets/91d4413f-4251-4493-a82a-7a39f4878296" />

Or we can establish an ssh connection, another portocol which is used multiple times throught a typical day in life of a DevOps engineer
________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________

### 8.ssh

SSH stands for Secure Socket Shell, or just Secure Shell. It’s a network protocol that allows you to log into remote machines and execute commands on them. When you’re logging into remote machines, you can’t always trust the network that you’re using to do so. SSH makes this process safer by encrypting all data, allowing secure communications via an untrusted network. This us hekoful when you’re working with sensitive information (yours or a client’s) or need to troubleshoot an unfamiliar network.

The basic syntax to launch SSH is:

[ssh] [user_name@hostname] or [ssh] [user_name@ipaddress]

See how I’ve used it below.

<img width="1024" height="968" alt="image-7-1024x968" src="https://github.com/user-attachments/assets/8b511fbc-70c0-4cdb-8203-b719668b3e8d" />

After you run the command, the remote server will ask you to provide a password. This is a basic authentication option. However, the more secure best practice is to use a passwordless option whenever possible.
________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________

### 9.scp

The final command that you’ll find helpful is SCP (Secure Copy Protocol). SCP is a similarly secure way to execute actions between a local and remote host, but instead of connecting to a server and executing commands, it transfers files.

See below the syntax for SCP:

<img width="1024" height="99" alt="image-8-1024x99" src="https://github.com/user-attachments/assets/15d6ee1d-57f6-4452-b972-f5ee0f22e2f4" />

________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________
