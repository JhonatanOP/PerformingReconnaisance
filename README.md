<h1>Performing Reconnaisance on a Network</h1>

<h2>Description</h2>
<n>In this lab, we will perform reconnaisance on a network:</n>

</br>
Performing reconnaisance on a netwrok involves using various tools and techniques to gather information about the network's infrastructure and potential vulnerabilities. This process includes discovering live hosts, scanning open ports, identifying running services, fingerprinting the operating system, and collecting DNS information. The gathered data helps security professionals assess network security and develop strategies for protection.

**NOTE:** The information provided here is for educational purposes only and should not be used to harm or disrupt systems or networks without proper authorization.
Unauthorized access to computer systems and networks is illegal and can result in severe penalties. Please use this information responsibly and ethically.
<br />

<h2> Languages and Utilities Used</h2>

- <b> Basic knowledge of the Linux command line interface</b>

- <b> Nmap (Network Mapper)</b>

- <b> [Nmap Cheat Sheet](https://www.stationx.net/nmap-cheat-sheet/)

- <b> VMware Workstation</b>

<h2>Environments Used </h2>

- <b>Kali Linux 2024.3</b>

<h2>LAB walk-through:</h2>

<p align="center">
At the top, on the menu bar, click the "Terminal" icon to open a terminal session: <br/>
</br>
<img src="https://imgur.com/hpzLulf.png" height="80%" width="80%" alt="Terminal Steps"/>
<br />
In the Terminal, execute the following command to discover host and services:  <br/>
</br>
nmap <br/>
</br>
<img src="https://imgur.com/03FSuDw.png" height="80%" width="80%" alt="NMAP"/>
<br/>
Execute the following command to display the complete manual for the tool: <br/>
</br>
man nmap <br/>
</br>
Press h for help or q to quit, when ready type q to quit the manual <br/>
</br>
<img src="https://imgur.com/lloN5W4.png" height="80%" width="80%" alt="Nmap manual"/>
<br />
<br />
Execute the following command:  <br/>
</br>
nmap -sn 10.0.0.1/24<br/>
<br/>
<img src="https://imgur.com/hS88EjC.png" height="80%" width="80%" alt="nmap -sn command"/>
<br />
- <b> the nmap -sn 10.0.0.1/24 command is used to perform a Ping Scan on a range of IP addresses in the 10.0.0.1/24. When you run this command, Nmap will send ICMP Echo Request packets to each IP address in the specified range and report which hosts respond, indicating that they are online. This is a useful initial step in network reconnaisance to identify live hosts before performing more detailed scans or security assessments. </b>
<br/>
</br>
<br/>
Execute the following command to perform a network scan on the IP address 10.0.0.1:  <br/>
</br>
nmap -ov 10.0.0.1<br/>
</br>
<img src="https://imgur.com/EXesfaq.png" height="80%" width="80%" alt="nmap -ov command"/>
</br>
- <b> The command nmap -ov 10.0.0.1 is used to increases the verbosity level, causing Nmap to print more information about the scan in progress. Open ports are shown as they are found and completion time estimates are provided when Nmap thinks a scan will take more than a few minutes. Use it twice or more for even greater verbosity. Most changes only affect interactive output, and some also affect normal and script kiddie output. The other output types are meant to be processed by machines, so Nmap can give substantial detail by default in those formats without fatiguing a human user. However, there are a few changes in other modes where output size can be reduced substantially by omitting some detail. For example, a comment line in the grepable output that provides a list of all ports scanned is only printed in verbose mode because it can be quite long. </b>
<br/>
</br>
Execute the following command:  <br/>
</br>
nmap -sT -PN -n 10.0.0.1<br/>
</br>
<img src="https://imgur.com/IemV0K0.png" height="80%" width="80%" alt="nmap -sT -PN -n command"/>
<br/>
The command "nmap -sT -PN -n 10.0.0.1" uses 3 different options:
</br>
- <b> sT (TCP Connect Scan):  TCP connect scan is the default TCP scan type when SYN scan is not an option. This is the case when a user does not have raw packet privileges or is scanning IPv6 networks. Instead of writing raw packets as most other scan types do, Nmap asks the underlying operating system to establish a connection with the target machine and port by issuing the connect system call. This is the same high-level system call that web browsers, P2P clients, and most other network-enabled applications use to establish a connection. It is part of a programming interface known as the Berkeley Sockets API. Rather than read raw packet responses off the wire, Nmap uses this API to obtain status information on each connection attempt. </b>
<br/>
- <b> PN (No Ping): This option skips the Nmap discovery stage altogether. Normally, Nmap uses this stage to determine active machines for heavier scanning. By default, Nmap only performs heavy probing such as port scans, version detection, or OS detection against hosts that are found to be up. Disabling host discovery with -PN causes Nmap to attempt the requested scanning functions against every target IP address specified. So if a class B sized target address space (/16) is specified on the command line, all 65,536 IP addresses are scanned. Proper host discovery is skipped as with the list scan, but instead of stopping and printing the target list, Nmap continues to perform requested functions as if each target IP is active. To skip ping scan and port scan, while still allowing NSE to run, use the two options -PN -sP together. </b>
</br>
- <b> n (no DNS Resolution) : Tells Nmap to never do reverse DNS resolution on the active IP addresses it finds. Since DNS can be slow even with Nmap´s built-in parallel stub resolver, this option can slash scanning times. </b>
</br>
<br/>
Execute the following command:  <br/>
</br>
nmap -sA 10.0.0.1<br/>
</br>
<img src="https://imgur.com/6CyjUQR.png" height="80%" width="80%" alt="nmap -sA command"/>
<br/>
- <b> sA (TCP ACK Scan):  This scan is different than the others discussed so far in that it never determines open (or even open|filtered) ports. It is used to map out firewall rulesets, determining whether they are stateful or not and which ports are filtered. The ACK scan probe packet has only the ACK flag set (unless you use --scanflags). When scanning unfiltered systems, open and closed ports will both return a RST packet. Nmap then labels them as unfiltered, meaning that they are reachable by the ACK packet, but whether they are open or closed is undetermined. Ports that don´t respond, or send certain ICMP error messages back (type 3, code 1, 2, 3, 9, 10, or 13), are labeled filtered. </b>
<br/>
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
