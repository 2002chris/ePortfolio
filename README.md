# ePortfolio
## Installation Guide
You need to install Virtualbox and import the images provided in this [Zip File](https://www.mediafire.com/file/q2r1kl4sbx8cgvn/VMs.zip/file). You can do this by pressing "file" on the top left corner and then click on "import appliance" and select the corresponding image.  
After that you need to create a new host network in the host network manager. To get to the host network manager you have to again click on "file" and then select "host network manager". Then a new window will open, where you can click on "create" to create a new host network. After that click on your newly created host network and then click on "properties". There you want to configure your adapter manually. Enter as "IPv4 Address" `192.168.56.1` and as "IPv4 Network Mask" `255.255.255.0`. The fields with IPv6 can be left as they are, because we don't need them. Be sure that the DHCP server is **not** enabled. Now you can close the network manager.  
Now you have to check the network interfaces of the virtual machines. For the firewall click on that machine and then click on the top center on "Settings". Then navigate to the network tab. The first Adapter should be attached to a "Bridged Adapter" and the name should be the name of the network interface of your computer. The second adapter should be attached to a "Host-only Adapter" and the name should be the network that you created earlier. Do the same for every eport virtual machine but the first adapter should be attached to a "Host-only Adapter" and the rest of the adapters should be disabled.  
Now start every machine starting with "pfSenseEportfolio". If every machine is started select the console of the pfSense VM and enter 2. then you will be asked, for the network interface. Enter the number that's next to "WAN" and press enter. Then you you will be asked if you want to configure the IPv4 address of WAN with DHCP. Type `y` and enter. On the following question type every time `n`. After all the question you will be redirected to the menu again and your able to see the IP address of the WAN interface. If you visit `https://<WAN-IP>:4443` you are able to log in to the web interface of pfSense. The credentials are `admin` and as password `1234`. If you want to login on the other machines the credentials are `eport` and as password `1234`.  
If there are any connection issues you need to clear the ARP table. To do that visit the web interface of the firewall and navigate to Diagnostics>ARP Table. Theres a red button to clear the ARP table.  
To change the settings of the reverse Proxy navigate to Services>HAProxy. In this repo there is already a configured HAProxy with 3 backends. If you want to experiment with the Settings feel free to do that, everything should be now set up correctly. If there are any issues feel free to message me on discord.
