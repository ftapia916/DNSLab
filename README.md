# Domain Name System (DNS)
<p>The purpose of DNS (Domain Name System) is to make the internet more user-friendly by translating readable domain names such as example.com into IP addresses that computers use to identify each other on the network. This allows users to access websites using easy-to-remember names instead of complex numerical addresses. Essentially, DNS acts as the internet’s phonebook, ensuring that when you type a web address, you are directed to the correct website (reference, cloud flare).</p> 

<h2>Technologies used</h2>
- Remote Desktop <br>
- Microsoft Azure
<h2>Operating Systems Used</h2>
- Windows 10 <br>
- Windows Server 2022 <br>

<h2> Definitions</h2>
<p><b>Ping</b>: is a network tool used to test reachability of a host on an IP network.</p>
<p><b>Nslookup</b>: s a tool that maps IP address information and obtains domain name. Used for troubleshooting and confirming network DNS configurations.</p>
<p><b>Ipconfig</b>: is a tool to display and manage the IP configuration of the network. Details IP addresses, subnet masks, default gateways and DNS servers.</p>

<h2>Prerequisites</h2>
<p>
<p align="center">
    <img src="https://github.com/user-attachments/assets/e0b19458-0154-43b3-8b12-9cd0f2a66eed" height="50%" width="50%" alt="step one"/>
</p>
<p>
The Virtual Machines used are shown in the previous project Active Directory. To paraphrase the previous project; "Virtual machines must be in the same resource group and virtual network to connect. The virtual network can be created separately. The Domain Controller uses Windows Server 2022, while the client computer runs Windows 10. The NIC of the Domain Controller needs to be set to static, and the client's DNS should match the Domain Controller's DNS. Both, NIC as static and DNS can be adjusted in Azure."
<h2> A Record </h2>
<p>
<p align="center">
    <img src="https://github.com/user-attachments/assets/20b4b6a8-6bb8-4e38-b05b-7b0e7bcaf108" height="70%" width="70%" alt="step one"/>
</p>
<p>
From the previous practice, log back into DC-1 and Client-1 as (name)-admin.
<p>
<p align="center">
    <img src="https://github.com/user-attachments/assets/61e9a407-aa8b-4f9f-89a2-b5a82df1cae1" height="70%" width="70%" alt="step one"/>
</p>
<p>
  On Client-1 go to powershell run as admin. Nslookup mainframe. As you can see it did not work. 
  <p>
<p align="center">
    <img src="https://github.com/user-attachments/assets/7df4ecc3-175a-4125-953c-e6d07945fb8f" height="70%" width="70%" alt="step one"/>
</p>
<p>
  For the mainframe to show up on powershell, go to DC-1 search for DNS. Click dc-1, forward lookup zone, my domain, right click, click new host A, create new host, type in mainframe and the dns address of DC-1, finally select the first box below. 
 
<p>
<p align="center">
    <img src="https://github.com/user-attachments/assets/9226114d-d731-484e-ad9f-9ca80a2dcfc1" height="70%" width="70%" alt="step one"/>
</p>
<p>
 Back in client-1, ping mainframe and observe it working. 
</p>

<h2> Local DNS Cache </h2>
  <p>
<p align="center">
    <img src="https://github.com/user-attachments/assets/066b7845-6913-4ec1-9cfa-d5c29329eee6" height="50%" width="50%" alt="step one"/>
</p>
<p>
  Going back to DC-1 and edit the mainframe address to 8.8.8.8.
</p>  
<p>
<p align="center">
    <img src="https://github.com/user-attachments/assets/f32a9c7c-802c-4f91-a635-1afc831f4728" height="70%" width="70%" alt="step one"/>
</p>
<p>
  Ping mainframe again and see it did not work.
<p>
<p align="center">
    <img src="https://github.com/user-attachments/assets/2faecc55-8e56-426e-be76-58b3daaed96d" height="70%" width="70%" alt="step one"/>
</p>
<p>
  In powershell, use ipconfig /displaydns and then ipconfig /flushdns.
<p>
<p align="center">
    <img src="https://github.com/user-attachments/assets/18af0a50-9ecb-447d-a7d3-f67a7e001f85" height="70%" width="70%" alt="step one"/>
</p>
<p>
  Ping to mainframe again and the new address will show appear.
</p>
  
<h2> CNAME Record </h2>
<p>
<p align="center">
    <img src="https://github.com/user-attachments/assets/d042dae2-2d3b-4e3a-8896-f81802e92e39" height="70%" width="70%" alt="step one"/>
</p>
<p>
  CNAME can be found in the place as New Host A in DC-1. Type in search for the first box and www.google.com in the second box. These names are just for the example. 
<p>
<p align="center">
    <img src="https://github.com/user-attachments/assets/532a8f55-7b55-4394-a193-090676bb5727" height="70%" width="70%" alt="step one"/>
</p>
<p>
  Back on client-1 computer ping search.
<p>
<p align="center">
    <img src="https://github.com/user-attachments/assets/53a2021c-b8e4-4b15-ada6-baf1f2ba0057" height="70%" width="70%" alt="step one"/>
</p>
<p>
Finally nslookup search.
</p>

<h2>Resources to learn DNS in depth</h2>

[CloudFlare.com](https://www.cloudflare.com/learning/dns/what-is-dns/)
