* **OSI Model**
	* Let's review `OSI` Model.
	* We are gonna review, first two layers only.
		* **Physical Layer**
			* Defines physical characteristics of the medium used to transfer data between devices.
			* For example, voltage levels, maximum transmission distances, physical; connectors, cable specifications, etc.
			* Digital bits are converted into electrical (for wired connections) or radio (for wireless connections) signals.
			* All of the information in Day's 2 Notes is related to `Physical` Layer. 
		* **Data Link**
			* Provides node-to-node connectivity and data transfer(for example, PC to Switch, Switch to Router, Router to Router).
			* Defines how data is formatted for transmission over a physical medium (for example, copper `UTP` cables).
			* Detects and (possibly) corrects Physical Layer errors.
			* Uses `Layer 2` addressing, separate from `Layer 3` addressing.
		* **PDUs**
			* This shows `encapsulation` where data is sent over the network.
				![[Pasted image 20261009052340.png]]
				* At the top data prepared by the upper layer of the `OSI` Model is simply called data.
				* A `Layer 4 header` is added, and this combination is called a `Segment`.
				* A `Layer 3 header` is added to the `segment` and it is called a `Packet`.
				* Finally `Layer 2 Header and a Trailer` are added to the `packet` and it is called a Frame.
* **
* Local Area Network**
	* It is a network contained in a relatively small area.
		![[Pasted image 20261009051521.png]]
	* There are `4 LAN's`
		![[Pasted image 20261009051710.png]]
	* In this lecture we will see how traffic is sent and receive in `LAN's` like these.
* **
* Ethernet Frame**
	* It encapsulate a `packet` with a `header` and a `trailer`.
	* Total Size of `Ethernet Frame` is `26 bytes (header + trailer)`.
		 ![[Pasted image 20261009052709.png]]
	* **Header**
		* There are 5 fields in the `Ethernet Header`.
			* `Preamble and SFD`
				* `Preamble`
					* It's length is `7 bytes`.
					* It is a series of alternating` 1's` and `0's`.
					* It's bit pattern is `10101010 * 7`
					* It allows devices to synchronize their receiver clocks to make sure they are read to receive the rest of the frame and data inside.
				* `SFD`
					* It Stands for `Start Frame Delimiter`.
					* It's length is `1 byte`.
					* It's bit pattern is `10101011 * 1`.
					* It indicates the end of the preamble, and the beginning of the rest of the frame.
						![[Pasted image 20261009053002.png]]
			* `Destination and Source`
				* It indicates the devices sending and receiving the frame.
				* `Destination` and `Source` both length is `6 bytes` each.
				* The address  in the Ethernet are the destination and source `MAC addresses`.
				* **MAC**
					* `MAC` stands for `Media Access Control`.
					* The `MAC` address is a `6 byte (48 - bit)` address of the physical device.
					* This is separate from a `Logical` address like an `IP` Address.
					* It is assigned to the device when it is made.
			* `Type / Length`
				* It is `2 bytes (16 bit) field`.
				* It can be use to represent either the `type of the encapsulated packet`  or `the length of the encapsulated packet`.
				* It indicates the `Layer 3` protocol used in `encapsulated packet`.
				* Sometime it is the `length` field indicating the length of the `encapsulated data`, depending upon the version of the `Ethernet`.
					* A value of `1500 or less` in this field indicates the `LENGTH` of the `encapuslated` packet (in bytes).
					* A value of `1536 or greater` in this field indicates the `TYPE` of the `encapsulated` packet (usually `IPv4` or `IPv6`), and the `length` is determined via other methods.
					* Examples
						* Example 1:
							* A value of `IPv4 = 0x0800` which is written in `hexadecimal`.
							* It is equal to `2048 in decimal`.
							* `2048` is greater than `1536` and it is use to indicate that `encapsulated` packet is `IPv4` packet.
						* Example 2:
							* A value of `IPv6 = 0x86DD` which is already written in `hexadecimal`.
							* It is `34525 in decimal`.
							* `34525` is greater than `1536` and it is use to indicate that `encapsulated` packet is `IPv6` packet.
								![[Pasted image 20261009053458.png]]
	* **Trailer**
		* There is only 1 field in` Ethernet Trailer`
			* `FCS`
				* It stands for `Frame Check Sequence`.
				* It's length is `4 bytes (32 bits)`.
				* It detects corrupted data by running a `CRC algorithm` over the received data.
				* It is used by the receiving device to detect any errors that might have occurred in transmission.
				* `Ethernet Frame's Frame Check Sequence` is a `Cyclic Redundancy Check`.
				* **CRC**
					* `CRC` means `Cyclic Redundancy Check`.
					* `Cyclic`
						* Refers to something called `Cyclic codes`.
					* `Redundancy`
						* Refers to the fact that these `4 bytes` at the end of the message enlarges the message without adding any new information, so they are `redundant`
					* `Check`
						* Refers to the fact that it `checks`, or `verifies the data for errors`.
* **
* More on MAC Addresses**
	* It is `6 byte (48-bit)` physical address assigned to the device when it is made.
	* It is also known as `Burned-In-Address (BIA)`.
		* It is because the address is burned in to the device when it is made.
	* It is globally unique.
	* The first `3 bytes (24 bits)` are the `OUI (Organizationally Unique Identifier)`, which is assigned to the company making the device.
	* The last `3 bytes` are unique to the device itself.
	* The `MAC addresses` are written as the series of `12 hexadecimal characters`.
	* Let's see how MAC address works
		![[Pasted image 20261009065621.png]]
		* Let's say `PC1` wants to send some data to `PC2`.
		* This kind of frame is called a `Unicast frame`.
			* A frame destined for a `single target (PC2 in this case)`.
			![[Pasted image 20261009065901.png]]
		* `PC1` send the frame through it's network interface card connected with the `Switch 1`.
		* `Switch 1` receives the `frame`.
		* It looks at the source `MAC` address field of the frame and uses that information to learn where the `PC1` is.
		* It adds `AAAA.AA00.0001` to MAC address table.
			![[Pasted image 20261009070224.png]]
			* It also associate it's MAC address with `F0/1` internet.
			* This is known as Dynamically learned MAC address or Dynamic MAC address because it wasn't configured manually on the Switch, the Switch learned it itself.
			* Every Switch will keep a MAC address table like this, and they fill the MAC address table dynamically by looking at the source MAC address of the frame it receives.
		* Now the `Destination MAC address` is `AAAA.AA00.0002`, but `Switch` doesn't know where that is.
		* This is called `Unknown Unicast Frame`.
			* A frame for which the `Switch` doesn't have an entry in it's `MAC` address table.
			* Because the `Switch` doesn't know how to reach the destination and it has only one option that is to **FLOOD** the frame.
				* **FlOOD** means to `forward` the frame out of all of its interfaces, except the one it `receives` the `packet` on.
					![[Pasted image 20261009071153.png]]
		* `Switch` copies the `frame` and sends it out its `F0/2` and `F0/3` interfaces.
		* `PC3` ignores the packet because destination `MAC` address doesn't match its own `MAC` address,and it drops the `packet`.
		* `PC2` receives the `packet` and processes it normally up the `OSI stack`.
		* Unless `PC2` sends a reply of some sort it stops there.
		* `Switch 1` never receives the `packet` from `PC2`, so it cant learn `PC2` `MAC` address and use it to populate `MAC` address table
		* Let's say `PC1` sends an another `frame` to `PC2`
			* The `Switch` already has `MAC` address of `PC1` this time it doesn't add, but it still doesn't have `PC2` `MAC` address so it `FLOODS` the frame.
			* `PC3` drops the `frame` and `PC2` receives it and processes it normally.
			* Lets say now `PC2` wants to send some data to `PC1`, maybe a reply.
			* `PC2` sends the `frame` out of its network interface and `Switch` receives it.
			* `Switch` looks at the source `MAC` address and add to its `MAC address table` associating it with `F0/2` interface.
			* This time it doesn't `flood` the frame this is called `Known Unicast frame`, because the `destination` is already in its `MAC` address table.
				* `Known unicast frames` are forwarded to the destination
			* `PC1` then processes the `frame` up the `OSI stack` through the `de-encapsulation` process.
		* Dynamic `MAC` addresses are removed from the `MAC` address table after `5` minutes of inactivity.
* **
* **Number Systems**
	* **Decimal**
		* It uses `10` possible digits `0,1,2,3,4,5,6,7,8,9`.
		* `9` represents `9 ones`.
	* **Hexadecimal**
		* It uses `16` possible digits.
		* The first `10` are same as `Decimal system`.
		* The other `6` are borrowed from the alphabet which are
			* A
				* It is equivalent to `10 in decimal`.
			* B
				* It is equivalent to `11 in decimal`.
			* C
				* It is equivalent to `12 in decimal`.
			* D
				* It is equivalent to `13 in decimal`.
			* E
				* It is equivalent to `14 in decimal`.
			* F
				* It is equivalent to `15 in decimal`.