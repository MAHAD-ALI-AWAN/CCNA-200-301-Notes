- **Ethernet Frame**
	- The `Peramble + SFD` is usually not considered part of the Ethernet header.
	- The minimum size of Ethernet Frame is `64 bytes`.
	- `64 bytes - 18 bytes (header + trailer)` = `46 bytes`.
	- Therefore, the minimum `payload (packet)` size is `46 bytes`.
	- If `payload` is less than `46 bytes`, `padding bytes` are added.
		- `Padding Bytes` are all `0's`.
* **Ethernet LAN Switching**
	* When a device send some data to the another device, it doesn't just include the `source` and `destination` `MAC` addresses, `encapsulated` within that frame is an `Internet Protocol`, Known as `IP packet` and that `IP packet` `source` and `destination` IP address.
		![[Pasted image 20261009090827.png]]
	* If `PC1` wants to send some data to `PC2`, it has `IP address`, but on `Layer 2` it needs `MAC address`, for that it uses something called `ARP`.
* **ARP (Address Resolution Protocol)**
	* `ARP` stands for `Address Resolution Protocol`.
	* `ARP` is used to discover `Layer 2 address (MAC address)` of a known `Layer 3 address (IP address)`.
	* It consist of `two Messages`:
		* **ARP Request**:
			* Sent by the device, which want to know the `MAC` address of the other device.
		* **ARP Reply**
			* Which is sent to inform the requesting device of the `MAC` address.
	* `ARP Request` is send as a `broadcast ethernet frame`.
		* `Broadcast` means it is sent to all hosts on the network.
	* `ARP Reply` is `unicast`.
		* Meaning it is sent to only `one host (the host that sent the request)`.
* **How this works?**
	* If `PC1` wants to send data to `PC2`, it has to send `ARP Request Frame` first.
		 ![[Pasted image 20261009092150.png]]
	* `FFFF.FFFF.FFFF` is the `broadcast MAC address`.
	* This is the `destination MAC address` used, when a device wants to send an `Ethernet Frame` to all other devices on the `local network`.
	* Example
		![[Pasted image 20261009092823.png]]
		* `PC1` has prepared the `ARP REQUEST` to be sent.
		* It sent the `frame` out of its `network's interface`.
		* It is then received by the `Switch 1`.
		* `Switch 1` then adds `PC1` `MAC address` to its `MAC Address Table`.
		* Since the `Destination MAC address is all Fs`.
		* `Switch1` broadcast the frame out of all of its interfaces, except the one it was received on.
		* `PC2` receives it, but it ignores the `frame`.
			* That is because `destination IP address` doesn't match `PC2 IP address`.
		* Then `Switch 2` learns the `PC1` `MAC address` and add it to its `MAC address table`.
			![[Pasted image 20261009093155.png]]
		* However `PC3` recognizes that the `destination IP address` does match its own `IP Address`, so it doesn't ignore the `ARP request`.
		* What it does, it sends the `ARP reply`.
		* The `source MAC` is `PC3` MAC address.
		* The `destination MAC` is `PC1's` MAC Address.
		* `PC3` send the frame out of its network interface, and is received by the `Switch 2`.
		* `Switch2` learns the `PC3` MAC address, and enters it into `MAC address table` associating with the `G0/0` interface.
		* `Switch 2` will send the `frame` to `Switch 1`, because it knows the `MAC` address of `PC1`.
			![[Pasted image 20261012081346.png]]
* **ARP Table**
	* You can use `arp -a` to view the ARP table.
		 ![[Pasted image 20261012081650.png]]
		* `Internet Address` column displays `IP Addresses (Layer 3 address)`.
		* `Physical Address` column displays `MAC Addresses (Layer 2 address)`.
		* If `Type` column displays `static`, it means it is a `default` entry.
		* If `Type` column displays `dynamic`, it means it is `learned via ARP` entry.
* **MAC Address Table**
	* We can see `address table` with the command `show mac address-table`.
		![[Pasted image 20261012083024.png]]
		* `Vlan`, it means `Virtual Local Area Network`, the default value is `1`, and we will learn this later.
		* Next is `MAC address` column, `PC1` is at top and `PC3` at the bottom.
		* Next is `Type` column.
		* Finally we have `PORTS` column, which is another word for `interfaces`.
* **Aging**
	* `MAC addresses` are `removed` from` MAC address table` after `5 minutes`, it is called `Aging`.
	* We can also manually remove `addresses` from the table.
	* We can use this command: `clear mac address-table dynamic`.
		![[Pasted image 20261012083619.png]]
	* As you can see all the `dynamic MAC addresses` has been removed.
	* If you want to remove a single `address` from the table you can use this command: `clear mac address-table dynamic address 0c2f.b011.9d00`.
		![[Pasted image 20261012083828.png]]
	* We can also remove this the interface with this command: `clear mac address-table dynamic interface Gi0/0`.
		 ![[Pasted image 20261012084116.png]]