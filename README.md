# DNS Server Model
A simple system with four servers and dynamic number of clients, with a DNS server and the associated functionality.  Also has a basic routing protocol to facilitate communication. Built in C and C++, using socket programming. 

## Required Functionality
In this assignment we had to implement three basic concepts of networks.
- DNS (Domain Name Server), whenever we enter a destination name (website name) it is hosted against some IP and it is resolved by the DNS server

- Simple Routing, after getting IP address from DNS server about destination we need to senddata from source to destination.  A routing protocol specifies how routers communicate with each other, distributing routing information that enables them to select routes between any two nodeson a computer network. These routing protocols share their routing table with each other so that whenever a node has to communicate with another node, the router should know here to forward this packet. 

- The routing protocol here is a kind of prototype of routing protocol that will work on the basis of hop count. [This diagram](https://imgur.com/a/cBdcRl0) is the network topology for this assignment.

## Major Functionality
- In order to forward data towards the destination each router has a routing table (data structure or txt file).

- This routing table will be shared with other routers so each router should have information about the connected networks/clients with other routers. 

- As the routing table sharing is a broadcast msg in our case but every router should have one routing table, it should not have multiple copies.

- Whenever a client gets connected to any server a message will be generated and passed to all the routers. This message contains information about client numbers. For example C 1 connected with Server 1.

- All clients should communicate with each other. Like C1 from Server 1 should be able to communicate with C6 of Server 4.
-
- We will consider it as a circuit switch network that means if C1 and C6 are communicating then C2 and C4 can not communicate. If they want to do so there should be an error message displayed on their screens that Link 1 is already in use by C1.

- When two clients stop communicating by sharing a message of “close” then this link will be free and other clients can use it.

## DNS Server
- DNS server will have a file that has few websites such as www.google.com and its IP address 8.8.8.8. There is a functionality in client that it will enter a website name then its IP address will be fetched from DNS server and displayed in the client. It should display the route that the information is coming from.

- If a client recently asks for a website like google.com and another client also asks about that then the proxy server will reply to that query and provide their respective IP address. When a response message will be displayed on the client it has details about the replying server and this time it would be the proxy server (s3).

## Compilation and Execution
The files s1.cpp, s2.cpp and s4.cpp represent the servers. c.cpp represents a client. dns.txt containts website names and respective IPs and cache.txt is used by the proxy server to maintain a cache.

### How to Run
Note: This was built on Ubuntu.

- Compile s1, s2, s4, c and proxy.cpp
- In separate terminals, run the executables of all server files in this order s1 -> s2 -> s4 -> proxy
- Again in separate terminals, run the client executable. For multiple clients, run the same executable in different terminals
- Select whatever you wish the clients to do from the provided menu.
