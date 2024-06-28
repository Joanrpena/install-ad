<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Installing Active Directory in Azure</h1>
<p>
  This lab will describe the steps I used to install Active Directory using Azure. This setup will serve as the ground work for my upcoming lab on configuring Active Directory on Azure. We will be setting up this virtual machine to act as a domain controller.
</p>

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 Pro (22H2)

<h2>Installation Steps</h2>

<p align="center">  
  <img src="https://github.com/Joanrpena/install-ad/assets/131486928/250db769-cb2a-4823-bd76-3766b78a24ad" height="60%" width="60%" alt="Installation Steps"/>
</p>

 <p align="center"><b>IMPORTANT!!</b></p>
 
- Before continuing, we must set the IP address on the domain controller VM to static. If left as dynamic the two VM's will not be able to communicate with eachother later on, and our client VM will not be able to connect to the domain we create in later steps which will be necessary for the next lab. From the Virtual Machines page on the Azure portal click on your domain controller VM > On the left hand side under the Networking tab click Network settings > Click on the link directly under "Network Interface" which should be your virtual NIC(Network Interface Card) > Now that you're on the NIC page open the settings lab on the left hand-side > Click on IP Configurations > Make sure you tick the static IP setting > Save your settings.   
<br />

<p align="center">
<img src="https://github.com/Joanrpena/install-ad/assets/131486928/bc0fd271-bc7c-40f5-852a-5d4f51399082)" height="80%" width="80%" alt="Installation Steps"/>
</p>

- Place holder text. Be back soon!

<br />
