- **OSI Model - Network Layer (Layer 3)**
	- Provides connectivity between `end hosts` on different networks (i.e outside the LAN).
	- Provides `logical addressing(IP addresses)`.
	- Provides path selection between `source` and `destination`.
	- `Routers` operate at `Layer 3`.
- **Routing**
	![[Pasted image 20261013081107.png]]
	* These `PC's` are connected by `Switches`, so they are part of the same network.
	* But what if we put a `Router` between `Switches`?
		* Now instead of one `network`, the `PC` has been spitted into `two networks`.
			![[Pasted image 20261013081538.png]]
		* Now `PC1` and `PC2` are one `192.168.1.0/24` network, but `PC3` and `PC4` are on `192.168.2.0/24` network.
		* `192.168.1` or `192.168.2` represents the `network` itself and `.1` or `.2` represents the `end-host` devices.
		* `/24` tells what part of the address represents `network`, and which part represents the `end-hosts`.
			* `/24` represents the first `3` group of number represents the `network`.
		* Now Router also needs an `ip address` not one, but `1` IP for each network it is connected to.
			![[Pasted image 20261013082129.png]]
			* Let's give IP address to Router on interface `g0/0` `192.168.1.254`.
			* Let's give IP address to Router on interface `g0/1` `192.168.2.254`.
* **IPv4 Header**
	![[Pasted image 20261013082421.png]]
	* `IPv4` is the primary used protocol used today.
	* As you can see there are a lot of fields in `IPv4` headers.
	* For now, lets just focus on:
		* **Source IP Address**
			* The length is `32 bits (4 bytes)`.
		* **Destination IP Address**
			* The length is `32 bits (4 bytes)`.
	* Lets look at an example
		* `192.168.1.254`.
		* Each of its number represents `8 bits`.
			![[Pasted image 20261013083000.png]]
		* The way of writing in `1's` and `0's` is called `Binary`.
		* For humans understanding `Binary` is difficult.
		* So `IP` addresses are written, with something called `Dotted Decimal`, because they are `4` decimal numbers, which are `192.168.1.254`.
		* Each `8 bit` group is called `Octet`. 
* **IPv4**
	* `IPv4` is a series of `24 bits`.
	* It has `4` octets.
		![[Pasted image 20261013084647.png]]
	* Example
		![[Pasted image 20261013094711.png]]
		* `12` is the network portion, and remaining are the host portion.
		* Because:
			* There is `8`, and `8 bit` is `1 byte` so only `12` is the network portion.
* **IPv4  Classes**
	* It is split up in `5` different classes.
		![[Pasted image 20261013095004.png]]
	* The class of an `IPv4 address` is determined by the first `octet` of the address.
	* We will be focusing on class `A, B and C`, class `D` is reserved for `Multiclass addresses`.
	* Class `E` is reserved for experimental uses.
	* The end of the class `A` range is usually to be considered `126`, why is that?
		* The `127` is reserved for the `loop back addresses`.
		* Address range is: `127.0.0.0 - 127.255.255.255`.
		* These addresses are used to test the `network stack` on the local device.
			![[Pasted image 20261013095720.png]]
		* Notice the round trip is `0`, because `PC` is sending and receiving `ping to itself`.
	![[Pasted image 20261013095841.png]]
	* `Class A` addresses use the `/8` prefix.
		* There are fewer possible network addresses, however the network portion is very long, there can be many host on each network.
	* `Class B` addresses use the `/16` prefix.
	* `Class C` addresses use the `/24` prefix.
		* `Class C` is the opposite of `Class A`, there are many possible networks, because the host portion is smaller there are fewer `hosts` on each network.
		![[Pasted image 20261013100056.png]]
	![[Pasted image 20261013100440.png]]
	* `Leading bits` column refers to the first bit of the first `octet`.
	* `Size of network number bit field` displays the number of `bits` in the  `network proportion` in the IP address.
	* `Size of rest bit field` indicate the remaining number of `bits` in the address, which is the host portion of the address.
	* `Number of networks` displays the number of possible networks in each class. 
	* `Addresses per network` displays the number of hosts in each network.
	* However, because the first address in each network is the network address, it cant be assigned to `hosts`, also the last address of the network is the `broadcast address`, the `Layer 3` address used when you want to send traffic to all `hosts` and it also cant be assigned to `hosts`.
	* So `host` count is too less, for example `254` in `Class C`.
* **Netmask**
	* `Cisco devices` still use an older slightly more complicated way of writing the prefix length, that is used the `Dotted Decimal Netmask`.
	* A `Netmask` is written in `Dotted Decimal`, like an `IP` address.
		![[Pasted image 20261013101829.png]]
* **Types of Addresses**
	* **Network Address**
		* If the `Host portion` of the address is all `0's` then it is a `Network Address`.
		* The `Network address` cannot be assigned to a host.
			* The `Network address` is the first address of the network, but the first usable address is one above the `network address`.
			* In this case it is `192.168.1.1`, which is assigned to `PC1`.
				![[Pasted image 20261013102305.png]]
	* **Broadcast Address**
		* If the `Host portion` of the address is all `1's` then it is a `Broadcast Address`.
		* The `Broadcast address` cannot be assigned to a host.
			* So, although it is the last address in the network, the last usable address is actually the one under the broadcast address.
			* In this case it is the `192.168.1.254`.
	* So, the `Broadcast address` is the `Layer 3` address used to send a packet to all hosts on the local network.
	* If a packet is sent with `Destination IP address`, the destination `MAC address` of the frame it is encapsulated in would be `FFFF.FFFF.FFFF.FFFF`.
	* If `PC1` sent a ping to `192.168.1.255`, it would be received by `PC2` and `R1's G0/0` interface.