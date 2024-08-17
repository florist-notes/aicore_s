# Essence of Computation & Networking

We are problem solvers and we often come across computational needs in order to reach our solutions for the problems at hand. It is a tradeoff!  We need good hardware for good computational needs. Networking hardware acts as data pipeline and investing in good hardware aids in good research and problem solving.  

Here is a series of blogs I prepared on hardware and electronics. These blogs are for educational purposes only.

### Essence of Computation:

Let's start from the very basics with 1 (on / high voltage) and 0 (off/low voltage). Here is a beautiful comprehensive video of how everything started  [ (history) --- (of) ---- (hardware) ](https://youtu.be/M4d3FXu9-3I),  everything in CS is either 0 or 1 ( except qbit's probabilistic state but eventually it will be either a 0 or 1 ). BINARY! We speak binary [ [ Why Do Computers Use 1s and 0s? ](https://youtu.be/Xpk67YzOn5w?si=8q64tARIvxdm19Ef), [ Exploring How Computers Work ](https://youtu.be/QZwneRb-zqA?si=zn9y0sI8oqr7rlWD) ].

Networking hardware comprises the physical devices necessary for communication and data exchange across networks. These devices facilitate the interconnection of computers, servers, and other network-enabled devices, enabling efficient and reliable data transfer.

Data (image/video/audio/text etc) travels around as sequences of 0s and 1s. ------ 01100100 01100001 01110100 01100001 (data/packets) ------→ ( Internet ) ------→ (AI work station) . ISP (WAN) provides internet connection via optical fiber and we need networking harware to accept the WAN connection, create a LAN, switch and route packets to appropriate addresses/ devices. We will quickly take a quick peek into good networking hardware we use.




### Networking Hardware:
<br />

<img src="img/dm.png" height=260px><a> </a><img src="img/asus.png" height=260px><a> </a><img src="img/rj45.png" height=250px>
<br />

<table style="width:100%" >
<tr>
<th>Hardware Number</th>
<th>Hardware Name</th>
<th>Product</th>
</tr>

<tr>
<td>1</td>
<td>Switch+Router</td>
<td>Ubiquiti Networks UniFi Dream Machine Pro Managed Gigabit Ethernet (10/100/1000) </td>
</tr>

<tr>
<td>2</td>
<td>Router</td>
<td>Asus ROG Rapture GT-AXE16000</td>
</tr>

<tr>
<td>3</td>
<td>Switch</td>
<td>Ubiquiti Networks UniFi Switch Flex XG Managed L2 10G Ethernet (100/1000/10000) Power over Ethernet (PoE)</td>
</tr>

<tr>
<td>4</td>
<td>RJ-45 10G Transceiver </td>
<td>Ubiquiti Networks UACC-CM-RJ45-10G Netzwerk-Transceiver-Modul Kupfer 10000 Mbit/s RJ-45</td>
</tr>

<tr>
<td>5</td>
<td>RJ-45 Cable</td>
<td>Kabelmeister® RJ45 patch cord with Cat. 7 raw cable and locking lug protection (RNS®), S/FTP, PiMF, halogen-free, 500MHz, OFC</td>
</tr>


</table>
<br />

<img src="img/net/1.jpg" width=26%x><a> </a><img src="img/net/2.jpg" width=26%x><a> </a><img src="img/net/3.jpg" width=46%x>
<br />

You see the blue wire in the first picture is of optical fiber cable incoming into the lab switch. The yellow/ white ones are 10-G RJ45 Ethernet cable going to different rooms. The rightmost picture is of Unifi Deam Machine Pro in my lab.

<br />

## Why Unifi Hardware?

You can visualize every aspect of your networking hardware from unifi mobile app (unifi network + ui verify + wifi man) and web app. It allows us to see realtime status, log files, open ports, tunelling (vpn) and detailed information of connected devices. In addition you can also do signal strength mapping of your lab in AR (check [my demo](https://youtu.be/soBF9LdwTZ8)).

<img src="img/net/viz.png">
<br />

highlighting some of the features I used in lab :

<img src="img/net/4-min.jpg" height=552px><a> </a><img src="img/net/5-min.jpg" height=552px><a> </a><img src="img/net/6-min.jpg" height=552px><a> </a> <img src="img/net/7-min.jpg" height=552px>
<br />

[Exclusive Insight: Visiting one of the Most Advanced Datacenters in the World](https://youtu.be/bpTNcbnZjvY), [networking-devices](https://www.nwkings.com/network-devices).

