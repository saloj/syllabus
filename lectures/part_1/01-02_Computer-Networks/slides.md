<!-- HERE STARTS THE ACTUAL LECTURE -->
## This is a three part lecture

* Who is who?
* The OSI model
* Some TCP/IP protocols


---

## Part 1: Who is who?
### in (computer) communication

* Some Latin to get us started
* Some important words (with Latin roots)
* A general communication system


--

### Some Latin to get us started

* communicato
* informatio
* caudex
* medium
* datum (datus)


--

### An example with humans (and a cat)

![Lion or a cat?](images/lion-and-cat.png)

What is <em>communication</em>, <em>information</em>, <em>code</em>, <em>data</em> and <br />a <em>medium</em> in this picture?

<!-- {_style="font-size: 75%;"} -->


--

### Some important words (I)

* message
* source
* destination


--

### The same example again

![Lion or a cat?](images/lion-and-cat.png)

What is the <em>message</em>, who is the <em>source</em> and who is <br />the <em>destination</em>?

<!-- {_style="font-size: 75%;"} -->


--

### Some important words (II)

* transmitter
* signal
* channel
* noise
* receiver


--

### The same example (yet) again

![Lion or a cat?](images/lion-and-cat.png)

What is the <em>transmitter</em>, <em>channel</em>, <em>signal</em> and <em>receiver</em>?<br />Can we identify any <em>noise</em>?

<!-- {_style="font-size: 75%;"} -->


--

### A schematic diagram of a general communication system

![Shannon's schematic diagram of a general communication system](images/homebrewed-shannon-model.png)

Source: Shannon, C. E., "A mathematical theory of communication", in <em>Mobile<br />computing and communications review</em>, volume 5, issue 1, 2001, page 3.

<!-- {_style="font-size: 50%;"} -->


--

### Closing note: A few modes of communication

* Unicast
* Broadcast
* Multicast
* Anycast


--

### Identify the modes

![Broadcast](images/broadcast.png)&nbsp;&nbsp;&nbsp;
![Multicast](images/multicast.png)
<!-- {_style="margin-left: 20px;"} -->

![Unicast/Anycast](images/unicast.png)
<!-- {_style="margin-left: 165px;"} -->


---

## Part 2: The OSI model

### The open systems interconnection<br />basic reference model<br />ISO/IEC 7498-1:1994(E)


--

### What is the OSI model?

* Conceptual 7 layer model
* Defines different aspects of computer communication
* Entities at one level communication with entities at the corresponding layer at the other end


--

### The (empty) model

![Empty OSI model](images/OSI-eNo.png)


--

### Vertical interaction between layers

![Vertical interaction in the model](images/OSI-v.png)


--

### Horizontal interaction between layers

![Horizontal interaction in the model](images/OSI-h.png)


--

### Question about basic needs

![Two computers that need to communicate](images/2-computers-and-cat.png)

What is the first thing we need<br /> for this communication to work?


--

### The answer is in the 1st layer

![OSI model: Physical layer](images/OSI-1.png)


--

### Next we need to control the medium

![OSI model: Data link layer](images/OSI-2.png)


--

### Some (fun) data link stuff

* CSMA/CD
* CSMA/CA
* MAC addresses
* Ethernet frames

![Two computers linked by a medium](images/2-linked-computers.png)


--

### How do we solve this problem?

![Two computers and a cloud](images/2-computers-and-cloud.png)
<!-- {_style="padding-top: 2em"} -->


--

### We add a new layer

![OSI: Network layer](images/OSI-3.png)


--

### Fun stuff found in the network layer

* Routing protocols
* End-to-end encryption
* IP addresses

<!-- {_style="font-size: 80%"} -->

![Two computer linked by a medium](images/2-linked-computers.png)

1. Do we use network layer stuff here?
2. Do we need network layer stuff here?

<!-- {_style="font-size: 50%"} -->


--

### The 4th layer: Transport

![OSI: Transport layer](images/OSI-4.png)


--

### Some features in the transport layer

* Connections oriented
* Connectionless
* Message segmentation
* Error handling
* Flow control


--

### Connection negotiation: the session layer

![OSI: Session layer](images/OSI-5.png)


--

### Functions in the session layer

* Establish
* Manage
* Terminate
* Duplex


--

### Know your duplex

![Simplex](images/simplex.png)

![Half duplex](images/half-duplex.png)

![Full duplex](images/full-duplex.png)


--

### Layer 6: the context provider

![OSI: Presentation layer](images/OSI-6.png)


--

### The top layer: Application

![OSI: Application layer](images/OSI-7.png)


--

### Nota bene!

application layer != "the application"
<!-- {_style="75%; padding-bottom: 1.5em"} -->

What is the "application layer entity"<br />
if you are surfing the Web?
<!-- {_style="padding-bottom: 1.5em"} -->

![Interaction with the application layer](images/interacting-with-the-model.png)


--

### Repetition: the complete model

![OSI model](images/OSI-c.png)
![Now the computers can communication](images/2-computers-and-cat-in-trouble.png)


---

## Part 3: Some TCP/IP protocols


--

### Repetition: the complete (OSI) model

![OSI model](images/OSI-c.png)


--

## Our example

I am asking my application to fetch me<br />
http://test-thison.c9users.io/hello.html
<!-- {_style="padding-top: 2em"} -->

![Entering the network](images/interacting-with-the-model.png)
<!-- {_style="padding-top: 2em"} -->


--

### The application layer

Now my application uses its network skills<br />
to fullfill my request, starting with a<br />
Hypertext transfer protocol (HTTP):
<!-- {_style="padding-top: 1em"} -->

```
GET /hello.html HTTP/1.1
User-Agent: Wget/1.16.1 (linux-gnu)
Accept: */*
Accept-Encoding: identity
Host: test-thison.c9users.io
Connection: Keep-Alive
```
<!-- {_style="padding-top: 2em" class="lnu-code"} -->

![The message so far](images/message_2s_http.png)


--

### The transport layer

Next (but acctually before HTTP is even used) a<br />
connection is established that can now be used<br />
to send the HTTP request. The protocl used for<br />
this is the Transmission control protocol (TCP):
<!-- {_style="padding-top: 1em"} -->

```
Src Port: 44712   Seq: 1      Len: 175
Dst Port: 80      Ack: 1      Flags: ACK
```
<!-- {_style="padding-top: 2em" class="lnu-code"} -->

![The message so far](images/message_2s_tcp.png)


--

### Detour 1: Did we just skip ...???

TCP/IP does not really bother with session<br />
and presentation layers:

<!-- {_style="font-size: 75%"} -->

![TCP/IP model](images/TCPIP-model.png)

&#42; The network layer is usually called "Internet" in the TCP/IP model.
<!-- {_style="font-size: 55%"} -->


--

### Detour 2: The 3-way handshake

TCP supports reliable communication.<br />
To negotiate some initial parameters<br />
it uses "the 3-way handshake".

My application:

<!-- {_style="font-size: 75%; padding-top: 1em"} -->
```
Src Port: 44712	Seq: 0      Len: 0
Dst Port: 80	               Flags: SYN
```
<!-- {_class="lnu-code"} -->

The server:

<!-- {_style="font-size: 75%"} -->
```
Src Port: 80      Seq: 0      Len: 0
Dst Port: 44712   Ack: 1      Flags: SYN, ACK
```
<!-- {_class="lnu-code"} -->

My application:

<!-- {_style="font-size: 75%"} -->
```
Src Port: 44712   Seq: 1      Len: 0
Dst Port: 80      Ack: 1      Flags: ACK
```
<!-- {_class="lnu-code"} -->


--

### The internet/network layer

Here we use the Internet protocol (IP) to get<br />
the data from one network to the other:

<!-- {_style="padding-top: 1em"} -->

```
Version: 4
Time to live: 64
Protocol: TCP (6)
Src: 192.168.1.2
Dst: 192.158.30.16
```
<!-- {_class="lnu-code" style="padding-top: 2em"} -->

![The message so far](images/message_2s_ip.png)


--

### Detour 3: Networks and hosts

* The IPv4 address has 32 bits
* Some bits specify the network address
* Some bits specify the host address
* To help us we have the network mask

<!-- {_style="font-size: 75%"} -->

<pre>
Address: 11000000.101010000.00000001.00000010 (192.168.1.2)
Netmask: 11111111.111111111.11111111.00000000 (255.255.255.0)
Network: 11000000.101010000.00000001.00000000 (192.168.1.0)
Host   : 00000000.000000000.00000000.00000010 (0.0.0.2)

Address: 11000000.100100100.00011110.00010000 (192.158.30.16)
Netmask: 11111111.111111111.11111100.00000000 (255.255.252.0)
Network: 11000000.100100100.00011100.00000000 (192.158.28.0)
Host   : 00000000.000000000.00000010.00010000 (0.0.2.16)
</pre>
<!-- {_class="lnu-code" style="padding-top: 1em"} --->


--

### Detour 4: Special addresses (RFC 5735)

<pre>
0.0.0.0/8        # On "this" network
10.0.0.0/8       # Private A block (RFC 1918)
127.0.0.0/8      # Loopback
169.254.0.0/16   # Link local (RFC 3927)
172.16.0.0/12    # Private B block(s) (RFC 1918)
192.0.0.0/24     # Reserved
192.0.2.0/24     # For documentation and example code
192.88.99.0/24   # 6to4 relay anycast
192.168.0.0/16   # Private C block(s) (RFC 1918)
198.18.0.0/15    # For benchmark testing
198.51.100.0/24  # For documentation and example code
203.0.113.0/24   # For documentation and example code
240.0.0.0/4      # Reserved
</pre>
<!-- {_class="lnu-code" style="padding-top: 1em"} --->

Source: RFC 5735 Special Use IPv4 Addresses (January 2010)
<!-- {_style="padding-top: 3em; font-size: 55%;"} -->


--

### The data link layer

To handle the link we use Ethernet.
<!-- {_style="padding-top: 1em"} -->

```
Src: 60:6c:66:1e:cf:d5
Dst: e8:08:8b:5a:df:82
Type: IP (0x0800)
```
<!-- {_class="lnu-code" style="padding-top: 2em; padding-bottom: 1em"} -->

![The message as we know it](images/message_2s_c.png)