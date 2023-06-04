<p align="center">
<img src="https://i.imgur.com/MwrkwEQ.png" alt="DNS Photo"/>
</p>

<h1>Understanding DNS</h1>
This lab focuses on DNS and how it is used. DNS is a fundamental concept in IT and many sources go over the theory behind it. I will be configuring DNS records and seeing how it works in practice. This is building up from a previous lab where I have a client joined to my domain ernestotest.com. I am logged in as Jane Doe (an admin account) on both the client and domain controller VMs. In order for the lab to work, you need to be logged in as an administrator. <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 Pro (21H2)

<h2>DNS Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/5pjgtVz.png" height="80%" width="80%" alt="DNS Steps"/>
<img src="https://i.imgur.com/Zl04Jyt.png" height="80%" width="80%" alt="DNS Steps"/>
<img src="https://i.imgur.com/96xUgLF.png" height="80%" width="80%" alt="DNS Steps"/>
</p>
<p>
While logged in to the client as an admin, open the command prompt. When we ping "mainframe" it will fail. Nslookup "mainframe" provides similar results and shows that there is no DNS record for it. A DNS A-record will have to be created for mainframe on the domain controller. On the domain controller, open the DNS Manager and go to the domain you created within the Forward Lookup Zones tab. In my case, it is ernestotest.com. Right click on the page and create a New Host. For name, input mainframe and the IP address should be the same IP as the domain controller so that ping can resolve. Refresh the DNS server so that the new record can be updated. Upon returning to the client, ping mainframe once again to see that it will now resolve.
</p>
<br />

<p>
<img src="https://i.imgur.com/nLlOGKl.png" height="80%" width="80%" alt="DNS Steps"/>
<img src="https://i.imgur.com/p0VcajB.png" height="80%" width="80%" alt="DNS Steps"/>
<img src="https://i.imgur.com/ds0SCKW.png" height="80%" width="80%" alt="DNS Steps"/>
<img src="https://i.imgur.com/d4cXTCS.png" height="80%" width="80%" alt="DNS Steps"/>
</p>
<p>
This next exercise will showcase the DNS cache. On the domain controller, I changed mainframe's record address to 8.8.8.8 (Google) and refreshed the DNS server. When pinging mainframe on the client, it will still ping the old IP address. When the command ipconfig /displaydns is run, it will reveal that the DNS cache still has the old IP. In order to update the cache, we need to clear it. The command ipconfig /flushdns will empty the cache so that when we ping mainframe again, the IP address will be updated to the new one on the client side. When pinging mainframe, the new IP address of the record will show.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="DNS Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
