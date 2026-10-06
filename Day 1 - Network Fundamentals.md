A computer network is a digital telecommunications network which allows nodes to share resources.

**What is a Node?**
Let us introduce some types of network **nodes**. 

- Router
- Switch
- Firewall
- Server
- Client

Let's see the functions of these network nodes in a network.

**Let's Build a network and examine each node role**

**How a network is formed?**
* Server:
	* Two PC's connected together forms a network.
	![[Pasted image 20261007005416.png]]

	* Server's look like this
	*![[Pasted image 20261007010215.png]]
	* These are powerful server's and you will see rows and rows of these in data centers.
	* However, not all severs looks like this, any of the client could be a too. 
	* **How's that possible:**
		* For better understanding read about **Client** first [[Day 1 - Network Fundamentals#Client|Client Section]]
		* Let's identify a client and a server.
			* See the provided image and could you identify what is a client and what is a server?
			*![[Pasted image 20261007011804.png]]
			* Well **PC1** is the one requesting the service, requesting the image to be sent.
			* **PC2** is the one providing the service, or you could say providing the image.
			* So that makes **PC1 The Client** and **PC2 The Server.**
				*![[Pasted image 20261007012058.png]]
			* Let's look at another example of a **Client** and a **Server** relationship.
				*![[Pasted image 20261007012310.png]]
			     * On the Left you have a mobile or a computer on which you are watching Jeremy's Videos [Jeremy's Youtube Channel](https://www.youtube.com/@JeremysITLab) or reading these notes.
			     * On the right, there is a **Youtube** server which contains the video.
			     * What do you think the blue cloud in the middle represents?
				    ![[Pasted image 20261007013008.png]]
					 * The **Internet**, in network diagrams a Cloud is often use to represent the internet or in any situation where that part of the network aren't necessary.
				     * The internet is a very complex network and according to [Jeremy's Youtube Channel](https://www.youtube.com/@JeremysITLab) and he said **for the sake of the diagram all we need to know that data from your computer passes through the internet to reach the Youtube server.**
				     * So in the above diagram you play a video, in this case the **Client** asks the **Youtube Server** to ask for  the video for you and in response **Youtube** send the video back to the client, which passes through the internet.
				    ![[Pasted image 20261007013820.png]]
					     * However, **Youtube** doesn't send the data all at once, it sends you streams of data.
* Client
	* There can be devices which can we network clients, for example a Laptop, Mobile etc, any device from which we access the internet or a server is a client.
	  ![[Pasted image 20261007005848.png]]
	  
	* So, according to definition **"A client is a device that accesses a service made available by a user"**
	* A client is a device on which you watch videos or play game or make a blog etc.
	* A same device can be a **Client** and a **Server**.
	* **How's that possible?**
		* Let's take on more example, let's say you want a video from your friend via AirDrop.
		![[Pasted image 20261007014446.png]]
		* In this case your phone on the left ask for a video, and your friend's phone on the right sends you the video.
		* **So who is a Client and who is a Server?**
			![[Pasted image 20261007014617.png]]
			* Your phone on the left is **Client** and the phone on the right is the **Server**.
			* If your friend asked you for the video then your phone would be a server and your friend's phone would be client.
			* This type of architecture is called **Peer-to-Peer(P2P)** network.
* Switches
	* Let's build a network further and learn about **Switches**.
	* For example, let's take **Youtube**, it will not have just one warehouse where all servers are present, instead for such big platforms they build multiple warehouses or a place where they can install Servers. They do this to decrease the any kind of downtime.
	* Let's look at the picture, here we will have two warehouses or a building which has many servers in it, yes a branch or a warehouse or a building can have multiple servers.
		* ![[Pasted image 20261007015524.png]]
		* We have two branches, one is in **Tokyo** and one in **New York**.
		* As i explained before a branch can have more than 2 servers, it all depends on the need of an organization.
		* He couldn't fit everything in one slide 😂, so he just added **2 servers per branch**.
		* Coming to point, you cannot connect or ask for a video directly from a server, we use a **Switch**.
		* **Two PC's are connected with Switch1** and **two Servers are connected with Switch2**.
			* ![[Pasted image 20261007020138.png]]
			* Switches has a lot of interfaces, few to connect and few to do other things.
				* ![[Pasted image 20261007020240.png]]
				* Here you can see a switch can plug a **PC** or a **Printer** etc.
				* Switches are used to forward the **Traffic** via a **LAN**
				* **Traffic** means the queries coming to the internet, query could be anything, ask for a video, gossiping with your favourite **AI** or etc.
				* **LAN** is called **Local Area Network** and it means the local network of an organization which cannot be accessed from outside.
				* Now, in New York branch you could plug in some devices in Network **Switch 1** like another PC or a printer all reside on same **Local Area Network**.
					* ![[Pasted image 20261007020709.png]]
				* Same goes for any device connected to **Switch2** in Tokyo Branch.
		* So we have one **LAN** on the left and one **LAN** on the right.
		* Each **LAN** can send a data to each other, for example **PC1** to **PC2**.
			* ![[Pasted image 20261007021008.png]]
		* However, these **Switches** cannot connect directly to the **Internet** and send the data between two LAN's.
			* ![[Pasted image 20261007021122.png]]
		* Let's talk a look at **Switches**
			* ![[Pasted image 20261007021313.png]]
			* Cisco **Switches** are **Enterprise Grade Switches**, and they are used to connect their **LAN's**.
		* **Characteristics of Switches:***
			* Have many network interfaces or ports to connect to usually **24.**
			* It provides connectivity to hosts within the same **LAN**.
			* They don't provide connectivity between **LAN** via the Internet.
* Routers
	* We need another device to connect to the internet and that device is called a **Router**.
	* We can connect the switches to the Router and connect the Routers with the internet.
		* ![[Pasted image 20261007021841.png]]
		* If someone wants from NewYork branch wants to connect with someone on the Tokyo branch they will send their data via R1 which will then forward it to Tokyo Branch LAN via the internet.
			* ![[Pasted image 20261007022047.png]]
	* **Charcteristics:**
		* **ISR 1000** and **ISR 4000** have the network interfaces on the back but **ISR 900** is little bit different.
			* ![[Pasted image 20261007022307.png]]
		* Let's look at the switches from before.
			* ![[Pasted image 20261007022348.png]]
			* Routers have fewer network interfaces than switches.
			* Routers provide connectivity between **LANs**.
			* Routers are used to send data over the internet.
* Firewalls
	* **Firewalls** to the network is as same as the security guard to any ATM, they prevent the intrusions to any machine.
		* ![[Pasted image 20261007022722.png]]
		* **Hackers** try to hack into a network and cause damages.
	* Routers can also provide some basics **security features** but that is not enough.
	* That is where the firewall come in.
		* ![[Pasted image 20261007023029.png]]
		* These are specially devices designed for network security.
		* They control the network traffic entering and exiting the network.
		* It can be placed outside the network like **FW1** or outside of your network like **FW2**.
		* Firewalls must be configured with security rules determine which traffic should be allowed and which should be traffic often labeled as **InBound** and **OutBound** rules.
		* These rules should be configured properly.
			* ![[Pasted image 20261007023428.png]]
			* If a user from **New York** branch ask for a file from someone sitting in **Tokyo** branch then the firewall should be configured to allow the file sharing.
			* However if an **attacker** tries to get the file from **Tokyo** server or **New York** server then the **firewall should block it**.
		* Let's look at the **firewalls**
			* ![[Pasted image 20261007023715.png]]
			* On the left we have **ASA5500-X** and on the right we have **Firepower 2100**.
			* The **ASA550-X** or **Adapted Security Appliance** is Cisco's classic firewall.
			* Moden **ASA** also supports **IPS** also known as **Intrusion Prevention System** which will be discussed later in the course..
			* **Firepower 2100** is next gen firewall as well.
	* Charcteristics:
		* Monitor and Control network traffic based on configured rules.
		* Can be placed inside the network and outside the network.
	* Host-Based firwalls:
		* These are software applications that filter traffic entering and exiting a host machine, like a PC.