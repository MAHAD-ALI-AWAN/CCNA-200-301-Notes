Take a look at this picture it has many interfaces and it has 24 ports.

![[Pasted image 20261007043524.png]]

* **Let's Take a close look at the picture:**
	* It has 24 interfaces also known as the ports, it has a lot of interfaces.
	* Look at the top of the picture
		*![[Pasted image 20261007043723.png]]
		* `10/100/1000Base-T Ports(1-24)--Ports are Auto-MDIX`
		* Don't worry we will cover these later.
	* Do you remember the shape?
		![[Pasted image 20261007044036.png]]
		* You would see these interfaces on back of your computer or router.
		* These are called `RJ-45 ports`, `RJ` means `Registered Jack`
		* **RJ-45 Cables**:
			![[Pasted image 20261007044323.png]]
			* These are all cables with `RJ-45` Connectors.
			* There are variations in color, but all these fit perfectly in the switch interfaces.
			* `RJ-45 Connector` is used at the end of `Copper Ethernet Cable`
			* There are also cables which do not use copper wires, we will come back to it later.

* **What is Ethernet?**
	* Ethernet is a collection of network protocols/standards.
	* Ethernet has cabling standards, plus other standards but in this lecture we will other talk about cabling standards.
	* **Why do we need Standards?**
		![[Pasted image 20261007044957.png]]
		* For example two person wanna talk, and if one person only speak English and other only speak Japanese, then there would be a lot of confusion.
		* They need some standards so that they can communicate without any issues.
		* That goes same for cabling and that is why `Standards` exists.
	* Let's take an example
		![[Pasted image 20261007045238.png]]
		* If you want to connect to a network switch, but the maker of the switch and the maker of cable hasn't agreed upon the size and shape of the connector and port, you wont be able to connect them.
		![[Pasted image 20261007045408.png]]
		* That is why there are industry standards, so that everyone can follow.
* **Bits and Bytes**
	* Connection between a device in a network operate at a set speed.
	* These are measured in `bits per second`
	* **What is a bit?**
		* It is a value represented by either 0 or 1.
		* It is a binary number.
		* 0 means `OFF`.
		* 1 means `ON`.
		* That is how computers work.
	* When communicating a copper network cable a variation in the electric signal is interpreted by the receiving device as a `0` or a `1`.
	* **What is a Byte?**
		![[Pasted image 20261007050138.png]]
		* Eight bits is equal to `1` byte.
		* Speed is measured in `bits per second`.
		* However, data on a hard-drive is measured in `bytes per second` .
		* So, remember a `GIGA BYTE` is `8` times larger than a `GIGA BIT`.
	* **Reference of various speeds:**
		![[Pasted image 20261007050705.png]]
		* Dont worry you don't need to memorize all these.
		* For network speed `TB` is the last one which we need to know about.
* **Ethernet Standards**
	* Defined in the `IEEE 802.3 standard in 1823`.
	* `IEEE` means `Institute of Electrical and Electronics Engineer`.
	* **Ethernet Standards for Copper:**
		![[Pasted image 20261007051132.png]]
		* `BASE refers to baseband signaling`.
		* `T means Twisted Pair`, we will discuss this later.
		* Don't worry about this much, this out of scope of `CCNA`.
		* Memorize these standards.
* **UTP Cables:**
	![[Pasted image 20261007051555.png]]
	* The `Copper cables` used in Ethernet Standards are `UTP` Cables.
	* `UTP` stands for `Unshielded Twisted Pair`.
		* `Unshielded` means the wire has no metallic shield, which can make them vulnerable to electrical interference.
		* Twisted means they are twisted, and they help protect against electromagnetic interference or `EMI`.
		![[Pasted image 20261007051948.png]]
		* Pair means they are paired.
		* In total there are `4` pairs of wires twisted together, that makes 8 wires.
	* Let's look at the `RJ-45` connector we saw earlier.
		![[Pasted image 20261007052211.png]]
		* If you count the number of pins you will find that there are 8 pins.
		* Not all standards use same amount of wires.
		![[Pasted image 20261007052401.png]]
		* `10BASE-T` and `100BASE-T` use 2 pairs, 4 wires in total.
		* While `1000BASE-T` and `10GBASE-T` uses 4 pairs, 8 wires in total.
		* Let's focus on top 2 for now.
	* `10BASE-T` and `1000BASE-T`:
		* Let's imagine we are connecting a PC with a switch with a fast Ethernet connection.
		![[Pasted image 20261007052844.png]]
		* These number represents the pins on the `RJ-45` on the **PC** network's interface cards an on the **Switch** interface.
		* There are `8` but we will use only `2` pairs.
		* The first pair is at pin position `1` and `2` so, we will pair them together and we will connect pins potion `1` and `2`  on `Switch's` network interface.
		![[Pasted image 20261007053428.png]]
		* Here, Wires looks straight, but in `UTP` cables pairs are twisted together.
		* The `PC` will use pin `1` and `2` to transmit data to the switch, which we can write as `TX`.
		![[Pasted image 20261007053716.png]]
		* `PC` is transmitting data so that is why we used `TX`.
		* While `Switch` can't be `TX` because it is not transmitting data, in fact it is receiving data, so we will use `RX`.
		![[Pasted image 20261007053853.png]]
		* The network interface on `PC` or `Server` transmit data on pins `1` and `2`, while the interfaces on the `Switch` receives data on pins `1` and `2`.
		![[Pasted image 20261007054125.png]]
		* Now the next pair is not `3` and `4` it is `3` and `6`, the function of each pin is opposite of the pair of pins `1` and `2`.
		* On `Switch` pins `3` and `6` are used to `Transmit` data while on `PC` or `Server` pins `3` and `6` are used to `Recieve` data.
		![[Pasted image 20261007054328.png]]
		* This allows `FULL DUPLEX TRANSMISSION`.
		* What is `FULL DUPLEX TRANSMISSION`?
			* It means both devices can `send` and `receive` data at the same time, and no problem like collision will occur, because you separate the wires to `transmit` and `receive` data.
			![[Pasted image 20261007054812.png]]
		* Let's change the device on the `left` from `PC` to a `Router`
			![[Pasted image 20261007055133.png]]
			* A `Switch` usually connects to a router.
			![[Pasted image 20261007055521.png]]
			* Pin `1` and `2` of `Switch's` interfaces receives data while pins `3` and `6` `transmit` data.
			* While for `Router` it also acts like a `PC`, on pin `1` and `2` of `Router Network Card`it `transmits` data and on pin `3` and `6` it `receives` data.
			* Regular cable works well in this situation and it is called `Straight Through Cable`.
		* Lets' change the device on the `right` from `Switch` to a `Router`
			*![[Pasted image 20261007060204.png]]
			* It will not work because both are Routers.
			* So how can we connect two devices together, in this case `2` `Routers`, or maybe how can we connect `2` `Switches` or `2` PCs together?
			* `Crossover Cable:`
				* While a `STRAIGHT THROUGH CABLE` connects pin `1` to pin `1`.
				* A `Crossover Cable` connects pin `1` on the one side connects to pin `3` on the other side, and pin `2` on the one side connects to pin `6` on the other side.
				![[Pasted image 20261007060752.png]]
				* As you can see the pins are reversed.
				* Same goes for the other side.
				![[Pasted image 20261007060922.png]]
				* Now, the two devices can send data to each other with no problems.
		* `Chart` for `pins` the devices use to `transmit` and `recieve` data
			![[Pasted image 20261007061156.png]]
		* `AUTO MDI-X`
			* It allows devices to automatically which pins their `neighbor` is `transmitting` data on and then adjust which pins they use to `transmit` and `receive` data.
	* `1000BASE-T` and `10GBASE-T`
		![[Pasted image 20261007065418.png]]
		* For Copper wires it is straight forward.
		* Each pair is Bi-Directional, meaning each pair is dedicated to transmitting data or receiving data.
* **Fiber Optics Connection:**
	* `Copper UTP` wires can be used within `100 meters`.
	* `Fiber Optic Cable` does not emit any signal outside of the cable.
	* But what about larger connections?
	* Let's look at the switch
		![[Pasted image 20261007070108.png]]
		* We have `UDP` ports but right next to it, we have different ports as well.
		* In those interfaces we insert `SFP Transceiver` also known as `Small Form-Factor Pluggable`.
		* What kind of cable connects to one of these?
			![[Pasted image 20261007070333.png]]
			* We connect this cable with `SFP` it is called `Fibre Optic Cable`.
			* This cable send light over `Glass Fiber`.
			* There are `two connectors` at each end, this is because.
				* We need one connector to `transmit` data.
				* One connector to `receive` data on each end.
			* The `Copper UTP` cable use `separate` wires within the cable to `transmit` and receives data.
			* While the `Fibre Optic Cable` use `separate` cable to `transmit` and `receive` data.
			![[Pasted image 20261007070947.png]]
	* Structure of the Cable:
		![[Pasted image 20261007071143.png]]
		* There are 4 parts of it.
			* `Fiber Glass Core` itself.
				* Light is transmitted down this core, to transmit data from one device to another.
			* `Cladding` that reflects light.
			* A `protective` buffer
				* It prevents `Fiber Glass` from breaking.
			* `Outer Jacket` of the cable.

	    * Main Types of `Fiber Optic Cables`
		    * `Multimode Fiber`
			    ![[Pasted image 20261007071809.png]]
			    * The center `represents` the `Fiber Glass Core`
			    * The `Blue represents` the reflecting `cladding` that `reflects` the `light` down the cable.
			    * `Core Diameter` is `wider` than `Single-Mode Fiber`.
			    * `Wider Core` allows `multiple angles(modes)` of light waves to enter the `Fibre Glass Core`.
			    * Allows longer cables than `UTP`, but shorter cables than `Single-Mode Fiber`.
			    * `Cheaper` than `Single-Mode Fiber` (due to cheaper `LED-Based SFP transmitters`).
			* `Single-Mode Fiber`
				![[Pasted image 20261007072641.png]]
				* The center `represents` the `Fiber Glass Core`.
				* The `Blue represents` the reflecting `cladding` that `reflects` the `light` down the cable.
				* Core `diameter` is `narrower` than `Multi-mode Fiber`.
				* `Light` enters at a `single angle (mode)` from a `Laser-Based Transmitter`.
				* Allows `Longer Cables` than both `UTP` and `Multi-Mode Fibre`.
				* `More Expensive` than `Multi-Mode Fiber Cables (due to the more expensive laser-based SFP transmitter)`. 
	* Standards
		![[Pasted image 20261008002525.png]]