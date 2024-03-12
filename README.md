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




<h2>Actions and Observations</h2>

![Screenshot 2024-03-12 045120](https://github.com/hectorvalencia2/azure-network-protocols/assets/161524174/c4c43be3-cfdb-4469-b1d7-3e50ade554cc)
![Screenshot 2024-03-12 045727](https://github.com/hectorvalencia2/azure-network-protocols/assets/161524174/827ed689-874e-4731-9da2-b5b33d8a5576)

Create a Resource Group. Create a Windows 10 Virtual Machine (VM). While creating the VM, select the previously created Resource Group. While creating the VM, allow it to create a new Virtual Network (Vnet) and Subnet.
Create a Linux (Ubuntu) VM. While create the VM, select the previously created Resource Group and Vnet Observe Your Virtual Network within Network Watcher

![image](https://github.com/hectorvalencia2/azure-network-protocols/assets/161524174/ba99eb05-3463-4b65-968a-228edf96105c)
![Screenshot 2024-03-12 050343](https://github.com/hectorvalencia2/azure-network-protocols/assets/161524174/aba005b4-6d74-4c64-951b-a63ca8555f08)

Use Remote Desktop to connect to your Windows 10 Virtual Machine. Within your Windows 10 Virtual Machine, Install Wireshark. Open Wireshark and filter for ICMP traffic only. Retrieve the private IP address of the Ubuntu VM and attempt to ping it from within the Windows 10 VM. Observe ping requests and replies within WireShark. From The Windows 10 VM, open command line or PowerShell and attempt to ping a public website (such as www.google.com) and observe the traffic in WireShark. Initiate a perpetual/non-stop ping from your Windows 10 VM to your Ubuntu VM. 

![Screenshot 2024-03-12 051135](https://github.com/hectorvalencia2/azure-network-protocols/assets/161524174/e1c92c5a-532e-4de7-8677-65bcf0b0a5f2)
![Screenshot 2024-03-12 051034](https://github.com/hectorvalencia2/azure-network-protocols/assets/161524174/cd3cf64f-3c1c-4cd2-b1c6-5502e1a79eac)


Open the Network Security Group your Ubuntu VM is using and disable incoming (inbound) ICMP traffic. Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity. Re-enable ICMP traffic for the Network Security Group your Ubuntu VM is using. Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity (should start working). Stop the ping activity
