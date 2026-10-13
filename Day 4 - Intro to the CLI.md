- **What is a CLI?**
	- `CLI` means `Command Line Interface`.
	- The `interface` you use to `configure Cisco devices`.
	 ![[Pasted image 20261009015754.png]]
	- There is another `interface` called `GUI` which means `Graphical User Interface`.
	 ![[Pasted image 20261009015926.png]]
- **How to Connect to a Cisco device?**
	![[Pasted image 20261009020103.png]]
	* There are a couple methods, but we will talk about connecting via the `console` port.
	* There are two console ports.
		* `RJ-45`
		* `USB Mini-B	`	 
			![[Pasted image 20261009020335.png]]
		* Now, you need a cable to connect, we will use `Crossover` cable.
			![[Pasted image 20261009020539.png]]
		* The cable on the left side is the one, it has `RJ-45` connector one one end and on the other end is `DB-9` connector.
		* Nowadays most laptops, doesn't have a port for `DB-9` connector so we are gonna use a `USB` port adapter, which is on the right side. 
	* **Rollover Cable**
			* The name of the cable on the left is `Rollover Cable`.
			* Name is similar to `Crossover` Cable.
			* But it is different than` Ethernet UTP cross over cable`.
			* In `UTP Crossover` there are `8 pins` which are used.
			* In `Rollover Cable` we connect pins like this.
				![[Pasted image 20261009021150.png]]
	* **Putty**
		* You need a `terminal` editor and for that we will use `Putty` which is a popular choice.
			![[Pasted image 20261009021448.png]]
		* Click `Serial` and the click Open, and you should be connected to the `CLI`.			 
			![[Pasted image 20261009021547.png]]
		* You should be able to connect with default setting.
		* But click on Serial
			![[Pasted image 20261009021654.png]]
		* You will be able to edit the default settings for the Serial connection.
		* For `exam` you don't have to know what system configuration means, for example what Data bits means, just remember the values for the `CCNA` exam.
	* **Cisco IOS CLI** 
		* **Once you are connect you will be greeted with a screen like this.**
			![[Pasted image 20261009022308.png]]
			* When you first enter the `CLI`, you will be in default called `User EXEC Mode` and it is indicated by `>` sign, next to the `host-name` of the device, note that the `host-name` of this device is `Router` and if we pair with `EXEC MODE` it becomes `Router>`.
		* **EXEC MODE**
			* `EXEC Mode` is very limited
			* Users can look at some things, but can't make any changes to the configuration.
			* Also Called `USER Mode`
		* **Privileged EXEC MODE**
			* If you type enable next to `Router>` you will be placed in Privileged `EXEC Mode`.
			    ![[Pasted image 20261009023001.png]]
			* Provides complete access to view the device's configuration, restart the device, etc.
			* Cannot change the configuration, but can change the time on the device, save the configuration file, etc.
			* You can use the `?` to view the available commands.
				![[Pasted image 20261009023301.png]]
		* **Global Configuration Mode**
			* When we want to make the changes to the `Router's configuration`, then we enter `Global Configuration Mode`, and the command to enter is `configure terminal`.
				![[Pasted image 20261009023707.png]]
			* **Enable Password**
				* Now, we don't want anyone to be able to make changes to network configuration or just be able to look at the configuration, 
				* We can protect Privileged EXEC Mode with a password.
					![[Pasted image 20261009024256.png]]
					* **We used `enable password?`**
						* `?` next to `password` is used to check if there are any other options starting with password.
						* Next we did, `enable password ?`, this command tell us the further options we can get.
						* Note enable password and enable password? are two different commands.
							* `enable password?` check if there are any other words starting with `password` word.
							* `enable password ?` checks if there are any sub-options.
					* **Testing**
						* We typed `exit` to `Exit Priviledge Mode`.
						* From `Priviledge Mode` if i type `exit` again, i will be logged out from device, and i will be able to see start screen.
							![[Pasted image 20261009024900.png]]
						* If we press `enter` i will be brought back to `USER EXEC MODE`
							![[Pasted image 20261009025000.png]]
						* If we enter the `enable` command we will ask for a password.
							![[Pasted image 20261009025051.png]]
						* The password does `not` display as you type it (for security purposes).
						* If you type `wrong` password three times you will see `Bad Secrets` text.
							![[Pasted image 20261009025228.png]]
		* **Config Files**
			* There are two configuration files kept on the device.
				* `running-config`
					* The current, active configuration file on the device, As you enter commands in the `CLI`, you can edit the active configuration.
					* Use the `show running-config` command to view the configuration file.
						![[Pasted image 20261009025723.png]]
					* Ways to save `running-configuration` file to make it `startup-configuration,` and all commands are executed from `Privileged Exec Mode`.
						* `write`.
						* `write memory`.
						* `copy running-config startup-config`.
				* `startup-config`
					* The `Configuration` file that will be loaded upon restart of the device.
					* For startup config you can use `show startup-config` command.
						![[Pasted image 20261009025905.png]]
						* As you can see it says `startup-config is not present` because we haven't saved the running configuration yet.
					* Now after saving the file if i type `show startup-config` it displays the same configuration as `show running-config` command.
						![[Pasted image 20261009030543.png]]
						* As you can see, we can see password `CCNA` which is huge risk, if anyone opens this `configuration` file then he can easily see the password, so we have to encrypt it using `service password-encryption` command.
							![[Pasted image 20261009030759.png]]
							* Remember we used `conf t` it is a shortcut as i have explained above, it is same as `configure terminal`.
							* Now if we run `show running-config` command again we can see our `encrypted` password.
								![[Pasted image 20261009031025.png]]
								* `7` means the type of encryption used to encrypt the password. 
		* **Service Password Encryption**
			* It is not so `secure` anyone and anyone can `decrypt` it easily.
				![[Pasted image 20261009031330.png]]
			* There is a more secure enable password.
			* For more secure we can use `enable secret` command. 
			* Then i write `do sh run`.
				* `do` allows to execute `Privileged EXEC Mode` commands.
			* It used `MD5 Encryption`, it is much secure.
				![[Pasted image 20261009031747.png]]
			* As we can see both `enable secret` and `enable password` are there, but the `enable password` will be ignored, only the `enable secret` will be valid.
		* **Cancelling Commands**
			* We can type `no` in front of the command to cancel.
			* If we type `no service password-encryption` command then future password will no longer be encrypted.
			* `Passwords` which are already `encrypted`, will not be `decrypted`.
			* But if i enter a new `password`, it will be in clear text, not in `encrypted` form.
				![[Pasted image 20261009032315.png]]