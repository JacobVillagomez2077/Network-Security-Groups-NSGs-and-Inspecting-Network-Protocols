# Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols
<p align="center">
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/f64f4a5b-bc43-4cd8-acfd-20bc707d00aa"/>
</p>
<p align="center">
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/f5f49e52-5670-4340-8351-ba4e5d54b343"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Video Demonstration</h2>

- ### [YouTube: Lab 2 :  Configuring On premises Active Directory within Azure VMs](https://youtu.be/1EPNPQBD2os)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDP, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- First create a Resource Group
- Create a Virtual Machine in Windows
- Create a Virtual Machine in Linux
- Remote Desktop Connection into both VM
- Download Wireshark in VM1
- Open Command prompt and perform a endless ping -t from VM1 to VM2
- Create a Network Security Group in Azure for denying the endless ping
- Open Wireshark and monitor protocols (SSH,DNS,RDP, and ICMP)
- Open Powershell and log into VM2 using SSH
- Run Powershell Commands in VM2
- Exit VM1
- Delete Resource Groups in Azure for both VM's


<h2>Actions and Observations</h2>

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/eafc0d88-04d2-45ed-9a1a-828545d2b543"/>
</p>
<p>
First go to Microsoft Azure and type Resource Groups in the search bar
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/180c4847-c7ac-444f-bf10-9c196cd39753"/>
</p>
<p>
Next for the Resource Group name type RG-LAB-02 and the region under US West US 3
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/c1886bb1-df0e-493b-bf4d-f47648bc9d46"/>
</p>
<p>
Then go to the Review and Create section and let the validation passed
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/328ef8c6-1791-4584-9adf-fbd2ddc9bc0d"/>
</p>
<p>
Now go back to Resource Groups and you will see it was created
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/55047fc7-28b7-4b98-810f-c9ffb7d900d5"/>
</p>
<p>
Type Virtual Machines in the search bar
</p>
<br />


<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/56ba9d47-8215-4b55-acf5-a26652e0a2e0"/>
</p>
<p>
Now for the Resource Group click the one we created RG-LAB-02.
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/b0865c84-9f51-426e-8268-41d286ad044c"/>
</p>
<p>
Next type the VM name VM1, and the region under US West US 3, the Image under Windows 10 Pro, and the size under Standard E2s
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/a497a209-c4ac-47cc-931f-26d04bfd2878"/>
</p>
<p>
Next the username will be named labuser and the password can be your own unique password. The Licensing check the box
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/90988751-5779-473b-b8de-84b02d40dc9e"/>
</p>
<p>
Now go to the Networking tab and make sure the Virtual Network, Subnet, and Public IP all says (new)
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/23d49724-a9eb-4114-87b9-91b812ac7185"/>
</p>
<p>
Now go to the Review and create tab and click the Create tab on the bottom left
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/706080ec-1b1b-4aea-a837-580bc1f7051a"/>
</p>
<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/710a84ef-0239-48a0-9eff-4d05861e0694"/>
</p>
<p>
Next let the deployment process load, once its done a green check will emerge near the deployment
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/087b7069-7434-4169-86a3-243c5052aa19"/>
</p>
<p>
Next go type Virtual Machine and click VM1
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/5f905f73-3bea-44d9-8c69-1fc3d5f04717"/>
</p>
<p>
Now click create Azure Virtual Machine 
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/34471641-08dc-46f6-b7d9-e375507826c8"/>
</p>
<p>
Next click the Resource group name under RG-LAB-02, the Vritual Machine Name under VM2 and the region US WEST US 3
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/12b7e3ea-d98a-499d-9120-c684fa83b381"/>
</p>
<p>
Now for the Image put Ubuntu Sever Gen2 and the size under Standard E2
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/5cec14e8-6b7a-4bf2-b38e-7a086dc5304a"/>
</p>
<p>
Next for the authentication type click password, under Username type labuser and the password tpye the password
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/d9cc47ae-10b4-4151-9802-f064dec766f0"/>
</p>
<p>
Now go to the networking tab and make sure virtual network, subent, and public IP all says (new)
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/3317e873-cb0f-4811-bc68-d45161b14ddf"/>
</p>
<p>
Next go to the Review and create tab and click create at the bottom left
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/ac445adc-0b2b-4afd-a80f-4cac79202329"/>
</p>
<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/d6588b6f-e9e9-4eb3-9625-5288dd80bdc9"/>
</p>
<p>
Now the deployment process will begin. Then once it's done a green check will appear
</p>
<br />


<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/985f1bc1-e23e-4f69-934f-39e3191f736d"/>
</p>
<p>
Next you can upload all the info in a notepad file
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/7c7c1e49-e7e2-49f4-bd0f-7719c4fe55bc"/>
</p>
<p>
Next type Virtual Machine in the search bar
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/3f609f82-1e60-4995-a335-68817e960034"/>
</p>
<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/b01814be-7d8e-46ac-b115-64ee446e7a7b"/>
</p>
<p>
Next you will see the VM has been created click VM1 and copy the public IP address 
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/1c1882df-c967-4a17-9c3c-e17a758326ee"/>
</p>
<p>
Next type Remote Desktop Connection in the search bar
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/4492891b-4d35-438e-841f-7ebfc8d61e3f"/>
</p>
<p>
Next type the public IP of VM1 in the computer seciton and click the connect buttton
</p>
<br />


<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/cf6e558f-9dce-435f-81ed-da213b8aa962"/>
</p>
<p>
Next type the username as labsuer and the password as the password you created, then click the blue ok button
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/e9bf21e7-673e-4d12-85f8-6c962879de4c"/>
</p>
<p>
Then click the yes button 
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/aeeeb482-ae64-41f3-84b8-2ba09c6197f7"/>
</p>
<p>
Then click no for all of the following in the image above
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/53dfbcf4-7bec-4265-b871-5f40ff4bfacb"/>
</p>
<p>
Then once the networking tab loads click the yes button 
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/635e5b7f-36f7-445c-b242-3dd7657d5e22"/>
</p>
<p>
Next load Microsoft Excel and click start without yuor data 
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/0b3954de-a815-4925-ab20-281f00b6bdd6"/>
</p>
<p>
Next click continue without this data
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/7d3ef272-5a59-4762-b478-82853a259fde"/>
</p>
<p>
Now click confirm and continue 
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/9ede1e3a-0f9e-41ad-9055-dc84881b77d6"/>
</p>
<p>
Next click confirm and start browsing
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/cc24e06b-d005-44bd-875b-1df9e5ae99eb"/>
</p>
<p>
Now type download wireshark in the search bar 
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/68b0f045-3074-4433-9c09-985104a61ced"/>
</p>
<p>
Now click go to download 
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/da49f9cc-3ef1-435d-bac2-b1f6805ff647"/>
</p>
<p>
Now click windows x64 installer 
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/1950ba4a-ce67-4179-896f-71dba49088d5"/>
</p>
<p>
Once the process is done click the file to open in or go to file explorer and open the file in the downloads folder
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/0ca3e412-11a7-4b93-b22e-95393ece8171"/>
</p>
<p>
Next go to file explorer and double click Wireshark to load the software
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/0da125ab-07d5-412f-8a8d-1972c8b5e61b"/>
</p>
<p>
Now click next
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/920504a6-f881-4351-ad3f-2e7a4798fa0c"/>
</p>
<p>
Now click next 
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/b0d455d4-5768-4171-aa8c-44fc7b02bb1d"/>
</p>
<p>
Now finally click Install
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/6579f47f-4b85-45c4-8c6b-f21da6d4c310"/>
</p>
<p>
The installation progess will start
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/a08df02f-f23f-46e1-8cc7-20b1a0f3f53d"/>
</p>
<p>
Once the process is done click finish 
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/8bcaf36e-1986-458b-818b-7e093373889e"/>
</p>
<p>
Next type Wireshark in the search bar on the VM, then double click to open the software
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/b1e73cf0-34dc-40f5-8a91-514f283e28f5"/>
</p>
<p>
Next click the Ethernet on Wireshark
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/ec25f85b-cb86-48c9-90ce-e246c1757d34"/>
</p>
<p>
Now go back to Miscrosoft Azure and click VM2, copy the  IP or the Private IP address 
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/a143350c-05b6-4d87-ab36-647868cb4198"/>
</p>
<p>
Now open Windows Powershell and type ping (then type the private IP address) Example >>[ping 10.0.0.4] 
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/5dfc1eec-581d-4529-bec5-c4de82e48f83"/>
</p>
<p>
You can see that 4 packets where sent and received
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/1811defd-3241-4157-a310-8270d5030c69"/>
</p>
<p>
Now we can ping a website to see the same results, ping www.google.com
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/6c5107dd-1045-499e-824d-0bb4f51a0058"/>
</p>
<p>
Next we can do a endless ping by typing ping (then type the private IP address) -t Example >>[ping 10.0.0.4 -t] 
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/70b43316-bb55-4c2c-aab5-dd62312a0fa0"/>
</p>
<p>
Now go to Microsoft Azure and type Network Security Groups 
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/22b4bf7c-925e-4891-bbf4-d812b662ffc5"/>
</p>
<p>
Next click VM2 and then click +Add 
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/43455509-8482-481d-ade2-fc65ab238c19"/>
</p>
<p>
Now source can be under any, Protocol you need to click ICMP and the action will be deny, because we are going to deny the endless ping to stop. The priority needs to be lower than all the others for this example I put 200 and the name will be DENYICMPPINGFROMANYWHERE
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/eecc1871-c484-428e-aa37-729de07edbb0"/>
</p>
<p>
Now if we go back to VM1 we can see the ping stop when can now click Ctrl + C to go back to the home on commandline
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/4c909721-d741-42ec-a722-4258b94c4074"/>
</p>
<p>
Next type ssh in the search bar in Wireshark to see ssh traffic (SSH Stands for Secure Shell)
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/aa488c98-ed3b-4ef0-9696-10f884091246"/>
</p>
<p>
Next type dns in the search bar in Wireshark to see dns traffic (DNS stands for Domain Name Systems)
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/38f57097-6744-4d0d-aa05-83c845dcc95b"/>
</p>
<p>
Next type rdp in the search bar in Wireshark to see rdp traffic (RDP stands for Romote Desktop Protocol)
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/ee6b6f1b-a2c8-4e8c-9711-aa900170fae9"/>
</p>
<p>
Next each of these protocols have port numbers type tcp.port==22 this port is for ssh Secure Shell
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/de202578-c687-49a5-bf17-09457ffa69dc"/>
</p>
<p>
Next type udp.port==53 this port is for dns Domain Name System
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/0d6df577-0e3d-4116-a6a7-6130841f43e4"/>
</p>
<p>
Next type tcp.port==3389 this port is for rdp Romote Desktop Protocol
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/c0335500-65a3-47e8-a3b7-f36f48e02c50"/>
</p>
<p>
Now go back to Microsoft Azure and copy the Public IP address or the Private IP address of VM2 
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/85c0824e-6a6c-47b3-a083-55568f64497f"/>
</p>
<p>
Now go back to VM1 and type ssh labuser@ Public IP Address or Private IP Address. So this is using ssh to take into VM2 through VM1. ssh then the name of the VM which was labuser, then type the private or public IP address. Next type yes to allow the connection. Then type in your password the password wont show on the screen just have faith you are typing it correctly then press ENTER
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/951bd9f2-b930-4794-95fe-a839698959d7"/>
</p>
<p>
You will know it worked if you see a green name under labuser@VM2. Next type pwd (Print Working Directory) to show the directory 
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/bb8ef7c0-260e-4b36-9f55-784ca71ffd64"/>
</p>
<p>
Now type id to show all the identification in VM2
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/f80f6995-17a1-495a-8725-c27d685cb620"/>
</p>
<p>
Now type ip to see all the list of ip commands 
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/c1430caa-5ec1-433f-9a21-05d6412f41ca"/>
</p>
<p>
Now to create a txt file we can type touch hi.txt this will create a hi txt file 
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/58630770-e854-438d-ae72-e55381a24ca4"/>
</p>
<p>
Now to see the txt file we just created type ls -lasth
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/5c50bc61-e67a-4763-b2c7-4d2078d7e89c"/>
</p>
<p>
Now we can also create multiple files at once by typing touch hi my name is. Anything after touch will be its own file created. Then type ls -lasth to see the files
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/ccf9e494-b5fd-46a4-9518-c36cc178d697"/>
</p>
<p>
Now type uname -a this shows a string with all the os info running on it
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/137ce63c-ccf4-4bab-a5ad-516ef726b840"/>
</p>
<p>
Now to exit out of VM2 type exit 
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/65e27c16-2fc4-4d7c-b85a-2ad49e161775"/>
</p>
<p>
Next out of VM2 in the command line type nslookup this shows the IP or the DNS
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/32fd1c33-f37d-4ff5-85b0-5c67f30cce3d"/>
</p>
<p>
Next type ipconfig in the command line this shows the current TCP/ IP also machine IP
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/54752c57-d5eb-4c50-81fd-8a4cbbdf816d"/>
</p>
<p>
Now go back to Microsoft Azure and go to the Resource Groups we created. Click RG-LAB-02 and retype it in the delete section, then click the red delete button
</p>
<br />

<p>
<img src="https://github.com/Jacobvillagomez1/Network-Security-Groups-NSGs-and-Inspecting-Network-Protocols/assets/143027686/68037d2b-ea6b-444b-97b9-6f4c90bb6877"/>
</p>
<p>
Now go to the NetworkWatcherRG and delete that one as well
</p>
<br />
