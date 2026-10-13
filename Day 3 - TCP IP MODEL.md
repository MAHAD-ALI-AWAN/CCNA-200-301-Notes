
* **Protocols and Standards**
	* A **protocol** is a set of rules defining how data should be communicated between devices over the network.
	* Meanwhile, a **standard** is an agreed specification that describes how a **protocol** or **technology** should work.
	* With **vendor-neutral** standards, devices of all types can communicate with each other.
			* An `Apple MacBook` can access a website hosted on a web server running Linux.
			* A PC running `Windows` can send an email that can be read on a `smartphone running Android`.
* **
* **A bit of history**
	* Early work on the computer networks that would evolve into `today's Internet began in the 1960s`.
		* The `US Department of Defense's ARPA (Advanced Research Projects Agency) funded ARPANET`, which came online in `1969 to connect mainframes at universities and labs`.
		* Originally used a protocol called `NCP(Network Control Program)`.
	* `Vint Cerf and Bob Kahn (working at DARPA)` began developing `TCP(Tranmission Control Program) in 1974`.
		* Later divided into `two protocols` still used today.
			* `Tranmission Control Protocol(TCP)`.
			* `Internet Protocol(IP)`.
	* These two protocols form the foundation of the protocol suite known as `TCP/IP` today.
		* `APRANET` fully switched to `TCP/IP` on `January 1, 1983`.
* **
* **Who defines the standards?**
	* Most networking standards are developed by independent standards organizations, not by a single vendor, with participation from engineers at many companies.
	* But, when it comes to networking we should know about these two companies.
		* **IEEE(Institute of Electrical and Electronics Engineers)**
			* Developed many of the technologies used on local area networks.
				* `Ethernet(802.3)`
				* `Wi-Fi(802.11)`
		* **IETF(Internet Engineering Task Force)**
			* Open community that defines protocols used on the internet such as:
				* `TCP`
				* `IP`
				* `UDP`
				* `HTTP`
				* `DNS` etc.
			* Publishes standards in documents called `RFCs(Requests for Comments)`.
			* They make standards and vendors like `CISCO` implements them, so that devices from different companies can work together.
* **
* **Layered models**
	* Networks do a lot of different jobs to move data from one computer to another.
	* A model lets us group related jobs into layers.
		* Each layer has a specific role.
		* Each layer used the services of the layer below and provides service to the layer above.
	* Protocols live (mostly) at one layer/
		* Together they form a stack of products that work as a team (the network stack.)
		 ![[Pasted image 20261008035347.png]]
* **
* **The TCP/IP Model**
	*  There are `4 or 5 layers in TCP/IP Model`.
	* **Layers**
		* **Application Layer**
			* Protocols for communication between application processes; create or interpret the data.
			* Let's take an example
				* Let's say we have a PC and it is running chrome on it.
				* Additionally we have Server 1 which is running two services.
					* Web Server
					* File Server
				* `PC` user try to view the `webpage` hosted on the `Web Server`.
				* So, chrome will send a request to `Server 1`
				* That is the role of the application layer.
				![[Pasted image 20261008040850.png]]
			* Usually called `Layer 7`.
			* `Protocols` at this layer define `message formats and rules` for specific tasks, **such as:**
				* `Browsing web pages (HTTP/HTTPS)`.
				* `Transferring files (FTP, TFTP)`.
				* `Sending/receiving email (SMTP, POP3, IMAP)`.
		* **Transport Layer:**
			* With `Application` layer we have a problem, we have multiple `instances` or `processes` running on a `Server 1`.
			* So how does `PC` ensure it request reaches to correct server on `Server 1`?
			* That is the role of `Transport` layer
			* **How it works?**
				* Each process on the `Server 1` has a `Port` number associated with it.
					* `80` for the `web server`.
					* `21` for the `file server`.
				* So when PC request a web page it will address the request to `Server 1` on Port `80`.
				* In short `Transport Layer `provides `end-to-end` communication between application processes using port numbers.
				* Runs mainly on the `communicating hosts (PC1 and SRV1)`; routers normally operate based on `IP (Layer 3)`, not on `Transport-layer` information.
				* Protocols at this layer includes:
					* `UDP (User Datagram protocol): simple and efficient.`
					* `TCP (transmission control protocol): more robust features beyond basic message addressing.`
				![[Pasted image 20261008041756.png]]
		* **Internet Layer**
			* Internet means `Inter-Network between networks`.
			* We still have one problem, we still want to make sure the message reaches to the `Server 1` in the first place.
			* `Server 1` has an `IP address` for that purpose.
			* So, it provides end-to-end communication between hosts across networks using IP addresses and routers.
			* Protocols at this layer includes
				* `IP (IPV4, IPV6)`.
				* `ICMP (Internet Control Message Protocol)`.
			![[Pasted image 20261008041915.png]]
		* **Local Network Layer**
			* There are multiple devices between when we send data from `PC` to `Server1` and we want to ensure our data properly passed along between them.
			* Using `protocols` at this layers such as `Ethernet`, each device send the message to the next device on the `LAN`.
			* So, it provides `hop-to-hop` delivery within a local network using MAC addresses and switches.
			* It uses `MAC(Media Access Control)` addresses to identify `interfaces`.
			* **Protocols at this layer include**
				* `Ethernet (IEEE 802.3)
				* `Wi-Fi (IEEE 802.11)`
			![[Pasted image 20261008042358.png]]
		* **Physical Layer**
			* All of these cables connecting the devices and the `transceivers` on the `devices` that `transmits` and `receiver` signals.
			* So it sends bits as electrical, optical, or radio signals over the physical medium.
			![[Pasted image 20261008042758.png]]
	* **Protocol data units**
		* At each stage in the `encapsulation` and `decapsulation` process, there is a name given to the message.
			* The combination of `data` and a `L4 header` is called a `segment (TCP) `or `datagram (UDP)`.
				* `TCP creates segments`.
				* `UDP creates datagrams`.
			* The combination of a `segment/datagram` and a `L3 header` is called a `packet`.
			* The combination of a `packet` and a `L2 header or trailer` is called a `frame`.
				* `This is what they actually send over the wire.`
		* We can use alternative names to describe the message at each stage: `Protocol data unit (PDU)`.
			* `A segment or datagram is a Layer 4 PDU (L4PDU)`.
			* `A packet is a Layer 3 PDU (L3PDU)`.
			* `A frame is a Layer 2 PDU (L2PDU)`.
		* The contents of each `PDU (everything encapsulated by that layer's header/trailer)` are called the `payload`.
			* `A segment or datagram's payload is the application data`.
			* `A packet's payload is a segment or datagram`.
			* `A frame's payload is a packet`.
			![[Pasted image 20261008050112.png]]
	* **Adjacent-Layer Interaction**
		* Each layer provides a service to the layer above it, and is serviced by the layer below it, it is called `Adjacent-Layer Interaction`.
			* `Layer 4` provides a service to `Layer 5` by delivering data to the correct application using `port` numbers.
			* `Layer 3` provides a service to` Layer 4 `by delivering `segments/datagrams` to the correct destination host using `IP` addresses.
			* `Layer 2` provides a service to `Layer 3` by delivering `packets` to the next hop using `MAC` addresses.
			* `Layer 1` provides a service to `Layer 2` by sending and receiving `frames` as `electrical`, `optical` or `radio` signals.
			* Each layer communicates with the same layer on other devices this is called `Same-Layer Interaction`.
				* `The Application layer on one host sends data to the Application layer on the other host.`
				* `A segment/datagram is addressed to the Layer 4 port number of the correct application on the designation host`.
				* `A packet is addressed to the Layer 3 Ip address of the destination host`.
				* `A frame is addressed to the Layer 2 MAC address of the next hop`.
				* `Signals sent out of a physical port are received by a physical port on the connecte device`.
				* `Each layer has its own job and provides a specific service to the layers above`.
					* `The layers are modular`.
					* `As long as each layer keeps its "contract" with the other layers, we can improve or replace protocols at different layers without redesigning everything`.
					* `The flexibility is one of the main benefits of a layered model`.
* **
* **The OSI Model**
	* `TCP/IP` development started in the `1970s`.
	* In the late `1970s and 1980s`, the `International Organization for Standardization (ISO)` designed a `7-layer Open Systems Interconenction (OSI) model` and a matching protocol suite.
		* The goal was to create` international, vendor-neutral networking standards` that could unify existing proprietary stacks and potentially replace `TCP/IP`.
		 ![[Pasted image 20261008052636.png]]
	* `Governments`, including the US, promoted `OSI` as the preferred/recommended stack for new deployments.
	* `OSI` protocols ended up being late and complex, and never gained the same deployments as `TCP/IP`.
		* `TPC/IP "Won"` in the real world, although some `OSI` technologies are still used.
	* Today, almost all real networks use `TCP/IP`, but the `7-Layer OSI model `survives as a `reference/teaching model` and a common way to talk about `"Layers"`.
	* Most networking resources use a `5-Layer model` like the one covered earlier, but the names from the `OSI` model.
		 ![[Pasted image 20261008053001.png]]
		* That is why the `TCP/IP` `Application Layer` is often called `Layer 7`. 
* **
* **Other versions**
	* There are more versions as well except `OSI` and `TCP/IP`.
	* `Five Layer Model is most common one.
		![[Pasted image 20261008053503.png]]