<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

•	Step 1 – Create a Resource Group
<br>
•	Step 2 – Create Windows Virtual Machine
<br>
•	Step 3 – Create Linux Virtual Machine
<br>
•	Step 4 – Download and Install Wireshark in Windows VM

<h2>Actions and Observations</h2>

<br>**Create a Resource Group**</br>

Before creating a virtual machine on Azure, you must first create a Resource Group. On the Azure portal, navigate to Resource Groups and click "Create". After clicking Create, be sure to provide it with a unique name of your choosing as well as the region.

![image](https://github.com/user-attachments/assets/403aad64-0f10-4471-9b7c-3ae4f42a01f5)

 
![image](https://github.com/user-attachments/assets/ac2300bd-b765-40eb-b9d5-cd5864b11a6e)
 

<br>**Create a Virtual Machine**</br>

After creating your Resource Group, the next step is to create a Virtual Machine. In this case, there will be two virtual machines, Windows and Linux. However, we will make sure that each step is clearly explained to help you understand how the process works.

![image](https://github.com/user-attachments/assets/caf62a0e-23a6-4120-86e6-73c160dec0d2)


 
<br>**Create a Windows 10 Virtual Machine**</br>

In the first of two virtual machines, here is a step-by-step process of creating a virtual machine. After clicking Create, ensure that you assign your virtual machines to the previously created Resource Group. Once that is complete, proceed to make the Windows 10 VM. Provide a unique name as well as a region for where it’ll be based on Azure.

![image](https://github.com/user-attachments/assets/905c7398-b143-49a2-960f-5fd85fa3d2fa)


 
Under Image, select “Windows 10 Pro version 22HZ – x64” and the size as “Standard”

<img width="975" height="439" alt="image" src="https://github.com/user-attachments/assets/342045b3-4231-4481-aa1b-62a56b1cc9c5" />

 
Once that is complete, provide a unique username and password to log in to the virtual machine using your PC’s application to access Remote Desktop.

<img width="975" height="438" alt="image" src="https://github.com/user-attachments/assets/50c691c9-8e4f-41d3-bc73-ea8129a9d85e" />

 
Once the basic settings have been configured, go to Networking and create a New Virtual Network and Subnet.

<img width="975" height="440" alt="image" src="https://github.com/user-attachments/assets/baa98fff-e901-4c80-b76d-57cb7feefa74" />
 
After creating the virtual network and subnet, navigate to Review + Create and ensure that all your settings are configured to your preferences.

<img width="975" height="439" alt="image" src="https://github.com/user-attachments/assets/0090ee97-6b10-451e-9230-bd2f762409f8" />
 
After reviewing the settings of the Windows 10 VM, click Create and observe the deployment of the virtual machine once it’s completed.
 
<img width="975" height="547" alt="image" src="https://github.com/user-attachments/assets/8d28337e-ca57-45fc-b24b-ae65a1c12ad9" />
 
<img width="975" height="468" alt="image" src="https://github.com/user-attachments/assets/4406c087-eed5-4d40-9c96-3882809db982" />

<br>**Create a Linux Virtual Machine**</br>

Once the Windows VM has been made, it is now time to start creating the Linux VM in Azure. Just like the Windows VM, provide a unique name as well as the region where it’ll be assigned. Ensure the Linux VM is located within the same Resource Group as the Windows VM.

<img width="975" height="439" alt="image" src="https://github.com/user-attachments/assets/1098ff8b-3e21-4bf8-a4c8-e7522d7747f5" />

 
Under the image, click Ubuntu Server.

<img width="975" height="440" alt="image" src="https://github.com/user-attachments/assets/f4788db8-1923-456f-8397-be4dcbdd2b52" />

 
Provide a unique Username and Password before exiting this page. In this case, the same username was used for both the Linux VM and the Windows VM. However, that is up to you.

<img width="975" height="439" alt="image" src="https://github.com/user-attachments/assets/b169e068-d069-489b-8af8-fec89cea8c1c" />

 
Click Next and go to “Networking”. This is a crucial step to take, as you must ensure the Linux VM is under the same Resource Group and Virtual Network as the Windows VM to achieve a successful exercise.

<img width="975" height="441" alt="image" src="https://github.com/user-attachments/assets/fa5cad30-dc1d-44e7-a53e-81a6372ada36" />

 
After customizing the settings above, go to “Review+Create” and ensure all your settings are correct before clicking “Create.”

<img width="975" height="439" alt="image" src="https://github.com/user-attachments/assets/e8d40776-0118-42da-9358-80c0ac6ef402" />

 
After clicking Create, observe the deployment process of the Linux VM as seen in the screenshots below:

<img width="975" height="441" alt="image" src="https://github.com/user-attachments/assets/0de3f751-7536-46ae-8407-71b7b05949f0" />

<img width="975" height="438" alt="image" src="https://github.com/user-attachments/assets/cb1a9a06-6874-4362-a830-457d3cf08fd7" />


 
 
After ensuring both virtual machines are in the same subnet and resource group, you may access the machines through Azure under the resource group created below:

<img width="975" height="441" alt="image" src="https://github.com/user-attachments/assets/f5ce90f9-a212-46bb-af84-ede27964ebe7" />

 
One thing to be aware of is that the virtual machines created can incur a significant maintenance fee. Therefore, you would want to disable the machines when you are not using them in case you want to take a break, as shown here:

<img width="975" height="442" alt="image" src="https://github.com/user-attachments/assets/84262866-0785-46ac-b9eb-a7e49a9e3698" />

 
<br>**Log in to the Windows Virtual Machine using your Remote Desktop Application on your PC (Observe ICMP Traffic)**</br>

After creating the virtual machines in Azure, the next step is to log in to the Windows VM using a Remote Desktop Application that is pre-installed on your PC. If not, go ahead and install it now.
 
After logging in, this is what the Remote Desktop will look like on the Windows VM in this exercise.
 
On your Windows VM, download and install Wireshark. Follow the instructions as observed below:
 
 
After installing Wireshark, open the application and start the packet capture process
 
Once you start the packet capture process, observe it to understand the process and how it works visually.
 
From there, filter the packet capture for “ICMP”
 
Right now, you don’t see anything when the ICMP filter has been placed on the packet capture. However, this is where we return to Azure on the physical PC to have it ping the Linux VM. From there, retrieve the private IP address of the VM from Azure.
 
After retrieving the Linux Private IP address shown above, return to the Windows VM and run Windows PowerShell as an administrator. This is where we start the process to ping the Linux VM from the Windows VM.
 
After pinging the Linux VM, return to Wireshark and observe the ping from there.
 
After observing the ping activity using Wireshark, the next step is to initiate a non-stop ping from the Windows VM to the Linux VM. Return to Powershell and type out the ping command with the IP address, followed by “-t”.
 
Return to Wireshark and observe the communication between the two VMs in terms of pinging.
 

Now that you have seen what a non-stop ping looks like between two virtual machines, the next exercise is disabling incoming traffic (ICMP). For this to work, we must return to the Azure Portal and go to Network Settings on the Linux VM
 
From there, go to Network Security Group and Inbound Security Rules
 
Create a rule that would disable any ping activity between the two VMs
 
Return to the Windows 10 VM and observe how the ping is denied on PowerShell with the words “request timed out.”
 
Additionally, return to Wireshark and observe the packet capture using the same ICMP filter to see how the ping is denied.
 
See the difference between the previous packet capture and the current one? During the last packet capture, you can see “request” and “reply”, indicating the ping is working and the two virtual machines are communicating with each other. With this filter and the ping denied from Azure’s portal, it's only a “request”. However, the good news is we can restart the ping.
Return to the Azure portal and initiate the process of deleting the security rule that denies the ping.
 
After clicking “Yes”, verify that the security rule has been deleted 
 
After deleting the security rule that disabled the ping activity, the ping should resume as it was previously. To verify, return to the Windows 10 VM and check the PowerShell for the ping activity.
 
Additionally, verify the ping activity resumption using Wireshark and observe the activity.
 
That concludes the exercise for observing ping activity within the ICMP traffic. Before we conclude the activity and move on to the next exercise, we must go to PowerShell to stop the ping activity by pressing “Ctrl C” as the command. As shown below, the nonstop ping has ceased.
 
Verify on Wireshark that the nonstop ping activity has ceased
 
To summarize, this is how you observe ICMP traffic. The tools needed for this are Wireshark Packet Capture, Powershell, as well as the Azure Portal to configure the virtual machines. Next, we will observe the SSH traffic and demonstrate how to do it effectively.

Observe SSH traffic

After filtering for ICMP traffic, the next step is to observe the SSH traffic on Wireshark. To do so, start up Wireshark Packet Capture and filter for SSH. As you may notice below, there is currently nothing there. Please be patient, as the process will unfold in the following steps.
 
After filtering for SSH on Wireshark, open Powershell as an administrator and type in “ssh labuser@(private IP address on Linux VM)”. From there, type YES to continue and then enter the username and password of the Linux VM to begin the SSH process.
 
After starting the SSH process on Powershell, return to Wireshark and observe the packet capture with the SSH filter
 
After filtering for SSH on Wireshark, return to Powershell and enter these commands for SSH as shown below:
 
After entering the commands on Powershell, return to Wireshark and observe the packet capture, and notice the difference 
 
Additionally, you can also filter for “tcp port 22”
 
After observing all the packet captures under the SSH filter in Wireshark and entering commands in Powershell, you can end the process by typing the command “exit”.
 
After you end the SSH process on PowerShell, please return to Wireshark to verify the end of the SSH packet capture.
 
This concludes the exercise of observing SSH traffic.

Observing DHCP Traffic

In this exercise, we will observe DHCP traffic on both PowerShell and Wireshark. The first step in the process is to open Wireshark and filter for DHCP. At first, you won’t see anything, but this will be explained in the following steps.
 
Open PowerShell as an administrator and run the command “ipconfig /renew” (without the quotation marks).
 
Please return to Wireshark and observe the DHCP activity after running the command in PowerShell.
 
Alternatively, you can also filter on Wireshark using UDP filters such as “udp.port == 67 || udp.port == 68”
 
This concludes the exercise for observing DHCP filters.

Observe DNS Traffic

In this exercise, we will observe DNS traffic on Wireshark as well as using PowerShell to generate a nslookup of select websites to observe its traffic. The first thing to do is open up Wireshark and filter for DNS. Unlike previous exercises where the starting point of creating a filter is empty, there’s a lot more activity this time around.
 
Return to PowerShell and attempt to do an nslookup for two websites. The first website is Disney.com. Once you type in nslookup Disney.com, you will see the IP addresses of both the virtual machine and Disney’s website.
 
After you type in the nslookup, please return to Wireshark and observe the DNS activities shown below.
 
The following example of the nslookup is Pixar.com. Just like the first example, type in nslookup Pixar.com in PowerShell, and you can see the result
 
Return to Wireshark and observe the nslookup activity of Pixar’s website
 
Alternatively, you can use the filters udp.port == 53 || tcp.port == 53 to observe the DNS traffic
 
This concludes the exercise for observing DNS traffic.

Observe RDP Traffic

In this final and brief exercise, we will observe RDP traffic in Wireshark. To begin, we must filter for RDP traffic using this filter: tcp.port == 3389. After setting the filter, please review the example provided below.
 
As you may have noticed, the traffic is non-stop compared to other commands. The reason is that the RDP protocol constantly displays a live stream of traffic between two computers, hence why the traffic is non-stop.

This concludes the tutorial on Network Security Groups. Before completing this activity, please ensure that the virtual machines and resource groups on Microsoft Azure are deleted to avoid recurring charges. To do this, we must close the Remote Desktop Connection. After that, delete the Resource Groups created in the beginning. 

(Resource Group 1 being deleted as shown in the screenshot below)
 
(Resource Group 2 being deleted as shown in the screenshot below)
 
(Confirmation of Resource Group 1 being deleted)
 
(Confirmation of Resource Group 2 being deleted)
 






<br />
