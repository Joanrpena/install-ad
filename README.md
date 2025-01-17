<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Installing Active Directory in Azure</h1>
<p>
  This lab will describe the steps I used to install Active Directory using Azure on a Virtual Machine that will act as a domain controller. This setup will serve as the ground work for my upcoming lab on configuring Active Directory on Azure. (Please make sure to have a separate client VM deployed on the same virtual network as your domain controller VM, as it will be required later on.)
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
<img src="https://github.com/Joanrpena/install-ad/assets/131486928/b458ca56-c68b-48a4-9150-462c618608b4" height="60%" width="60%" alt="Installation Steps"/>
<img src="https://github.com/Joanrpena/install-ad/assets/131486928/5c7e4408-9b16-456f-b202-d5bf9d3e7a74" height="60%" width="60%" alt="Installation Steps"/> 
</p>

- After configuring the static IP on the Domain Controller VM, we can proceed to check if the client VM is able to communicate with the Domain Controller VM. To do this will open up the command prompt by typing CMD in the lower left search bar. Once opened we will use command ping -t &lt;ip address&gt;(using your domain controller VM private IP address). The connection is initially timing out meaning the client cannot communicate with the domain controller, this is because we need to enable ICMPv4 on our domain controller(DC) VM. Connect to your DC VM, and type wf.msc on the search bar > Click on Inbound Rules > Right click and Enable BOTH Core Netowrking Diagnostics - ICMP Echo Request (ICMPv4-In) settings. Now we can switch back to our client VM and retest if both VMs can communicate. Success!
<br />

<p align="center">
<img src="https://github.com/Joanrpena/install-ad/assets/131486928/eed09f03-b457-47f7-a532-2b539424a0e7" height="60%" width="60%" alt="Installation Steps"/>
</p>

- We can now begin installing Active Directory on our DC VM. On the Server Manager Dashboard screen, click on Add roles and features and click Next. You should now be on the Installation Type screen, click Role-based or feature-based installation > On Server Selection confirm the private IP adress of your DC VM then click Next > we should now be on the Server Roles section, click on Active Directory Domain Services a pop up should appear, click Add Features then click Next until you reach Confirmation then press Install. Active Directory is now installed but we're not finished yet. 
<br />

<p align="center">
<img src="https://github.com/Joanrpena/install-ad/assets/131486928/3db0e1f2-e15c-44a6-b657-8d8646230852" height="60%" width="60%" alt="Installation Steps"/>
<img src="https://github.com/Joanrpena/install-ad/assets/131486928/2d6fb418-9b2b-41d8-a18d-e2aed5ab4314" height="60%" width="60%" alt="Installation Steps"/>
</p>

-  Now that we have installed Active Directory on our DC VM, on your Server Manager you will see a flag notification on the top right. This is because we have to promote this server to a Domain Controller. Click on "Promote this server to a Domain Controller" > Tick "Add a new forest" > Now specify a name for your domain. In this case I will use joandctest.com and click next > Specify a password for your domain > Click next until you reach the Prerequisites check, then click Install. When install is complete your computer will restart. 

<h3> Important!!! </h3>
<p align="center">
  <img src="https://github.com/Joanrpena/install-ad/assets/131486928/ba006a0c-689c-4012-a62c-026362662ee3" height="30%" width="30%" alt="Installation Steps"/>
</p>
When it is time to RDP back into your domain controller VM you will not be able to use the standard user account. You will have to log in with the credentials of the domain. Use the domain path, and then the name of the user. Example: joandctest.com\labuser.
<br />

<h2>Conclusion</h2>
<p>
In this lab, we successfully installed and configured Active Directory on a virtual machine in Azure, setting it up as a domain controller. We ensured communication between the domain controller VM and a client VM by configuring static IP addresses and enabling necessary network protocols. The domain was established and the server was promoted to a domain controller. This setup forms the foundation for the configuration of Active Directory in Azure in upcoming labs.
</p>

