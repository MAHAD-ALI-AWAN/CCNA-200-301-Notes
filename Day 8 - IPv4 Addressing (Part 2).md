- **IPv4 Classes**
	![[Pasted image 20261013110041.png]]
	* `127` is reserved for the `Loopback addresses`.
	* `0` and `127` is reserved, so `Class A` ranges starts from `1-126`.
* **Maximum Hosts per Network**
	* **Class C Address**
		* `192.168.1.0/24`.
		* The last portion is `Host`, so it could range from:
			* `192.168.1.0/24` - `192.168.1.255/24`.
			* `0 - 255` gives us `256` addresses which is `2^8 = 256`.
			* We have to subtract `Network and Broadcast Address`, so it would be `256 - 2 = 254` addresses.
	* **Class B Address**
		* `172.16.0.0/16`.
		* It ranges from `172.16.0.0/16 - 172.16.255.255/16`.
		* The Host portion is last `2 Octets` which are
			* `2^16 = 65,536`.
		* We have to subtract `Network and Broadcast Address`, so it would be `65,536 - 2 = 65,534` addresses.
	* **Class A Address**
		* `10.0.0.0/8`.
		* It ranges from `10.0.0.0/8 - 10.255.255.255/8`.
		* The Host portion is last `3 Octets` which are
			* `2^24 = 16,777,216`.
		* We have to subtract `Network and Broadcast Address`, so it would be `16,777,216 - 2 = 16,777,214` addresses.
	* **Formula**
		* The formula for determining `Number of Host` is:
			* `2^n - 2`.
* **First/Last Usable Address**
	* **Class C**
		* `First Usable Address`
			* `192.168.1.0/24`
				* So, this address `00000000` with a Host Portion of all `0's`, is the `network` address or network ID.
				* Add one with changing the last 1 `00000001`, and you get `192.168.1.1/24` which is `first usable address`.
		* `Last Usable Address`
			* `192.168.1.255/24`.
				* So, this address `11111111` with a Host Portion of all `1's`, is the `broadcast` address.
				* Subtract one from this address from switching the last bit from `1` to `0`, which is `11111110`.
				* You will get `192.168.1.254/24` which is the `last usable address`.
	* **Class B**
		* `First Usable Address`
			* `172.16.0.0/16`
				* So, this address `00000000 00000000` with a Host Portion of all `0's`, is the `network` address or network ID.
				* Add one with changing the last 1 `00000000 00000001`, and you get `172.16.0.1/16` which is `first usable address`.
		* `Last Usable Address`
			* `172.16.255.255/16`.
				* So, this address `11111111 11111111` with a Host Portion of all `1's`, is the `broadcast` address.
				* Subtract one from this address from switching the last bit from `1` to `0`, which is `11111111 11111110`.
				* You will get `172.16.255.254/16` which is the `last usable address`.
	* **Class A**
		* `First Usable Address`
			* `10.0.0.0/8`
				* So, this address `00000000 00000000 00000000` with a Host Portion of all `0's`, is the `network` address or network ID.
				* Add one with changing the last 1 `00000000 00000000 00000001`, and you get `10.0.0.1/8` which is `first usable address`.
		* `Last Usable Address`
			* `10.255.255.255/8`.
				* So, this address `11111111 11111111 11111111` with a Host Portion of all `1's`, is the `broadcast` address.
				* Subtract one from this address from switching the last bit from `1` to `0`, which is `11111111 11111111 11111110`.
				* You will get `10.255.255.254/8` which is the `last usable address`.
* **Configuring a Cisco Router**
	![[Pasted image 20261013113221.png]]
	* `10.0.0.0/8`
		* This is not a realistic network.
		* `PC1` has the first usable address `10.0.0.1`.
		* Last usable is `10.255.255.254`.
			![[Pasted image 20261013113516.png]]
	* `172.16.255.254`
		* `PC2` has the first usable address `172.16.0.1`.
		* Last usable is `172.16.255.254.
			![[Pasted image 20261013113657.png]]
	* `192.168.0.0/24`
		* `PC3` has the first usable address `192.168.0.1`.
		* Last usable is `192.168.0.254.
			![[Pasted image 20261013113844.png]]
	* `CLI of R1`
		* Type `en` to enable and enter `Priviledge Exec Mode`.
		* Type `show ip interface brief` to show each status of the device as well as their `IP` addresses.
			* `Interface` column list the interfaces of the device.
			* `IP-Address` column list the `IP` address of each interface.
			* `OK` is legacy and it is not relevant anymore, basically it says whether or not `IP` address is valid or not.
			* In Modern devices, it won't allow you to assign invalid `IP` addresses.
			* `Method`column indicates the method by which interface was assigned an IP address.
			* `Status` column shows `administratively down`.
				* It is the `Layer 1 status`.
				* It means the interface has been disabled with the `shutdown` command.
				* This is the default `Status` of `Cisco` router interface.
			* `Protocol` column is the `Layer 2 status`.
				* Interfaces are down at `Layer 1`, `Layer 2` can't operate, so all of those interfaces are down at `Layer 2`. 
			![[Pasted image 20261013115249.png]]
		* Type `conf t` to enter `Global Config Mode`.
			* To configure interface itself, we have to type `interface gigabiteethernet 0/0`.
				![[Pasted image 20261013115457.png]]
			* You can also use this `shortcut` command `in g0/0`.
				 ![[Pasted image 20261013115713.png]]
		* Let's set the `IP` addresses.
			* `10.0.0.0/8`
				* Type `ip address 10.255.254 255.0.0.0`.
				* Type `no shutdown` to enable the interface.
				* Type `do sh ip int br` to show each status of the device, it is same as `show ip interface brief`.
					![[Pasted image 20261013120213.png]]
			* `172.16.0.0/16`
				![[Pasted image 20261013120604.png]]
			* `192.168.0.0/24`
				![[Pasted image 20261013120807.png]]
		* More Commands
			* `show interfaces g0/0`, it shows detail about `Layer 1 `and `Layer 2` interface, also some `Layer 3`.
				* `GigabitEthernet0/0 is up`, that means `Layer 1` is working.
				* `line protocol is up`, that means `Layer 2` is working.
				* `Hardware is iGbE`, means `1 Gigabit Ethernet`.
				* `address is 0c1b.8444.f000`, shows `Interface's MAC` address.
				* Internet address is `10.255.255.254/8`, this is `IP` address.
					![[Pasted image 20261013121525.png]]
			* `show interfaces description`, it shows `Status, Protocol along with Description` column.
			* Let's go back and configure description.
				* `Type int g0/0`.
				* Type `description ##<description>##`.
					* You can use `#` to make description noticeable.
						![[Pasted image 20261013121902.png]]