[session1](../../session10/) | [Cloud Computing Azure ](../docs/AzureExercises1.md)

# Cloud Computing With Azure

One of the most fundamental aspect of cloud computing is the ability to create run and delete virtual machines on demand.
A virtual machine simulates the cpu, memory and disks of a computer and can run an operating system just like a physical machine.
In reality it is being hosted on top of physical computers in a data centre run by a cloud provider. 

We will be creating a virtual machine in the Microsoft Azure cloud platform.

## Signing up for an Azure account

All students are eligible for a Microsoft Azure student account which allows up to $100 of resources usage a year and up to 750 hours of virtual machine run time. 

Sign up for a student account using your university email at [Azure Student Accounts](https://azure.microsoft.com/en-gb/free/students/)

![alt text](../docs/images/AzureForStudents-initial.png "Figure AzureForStudents-initial.png ")

(You should not need to provide a credit card).


## Creating a Virtual Machine

1. log in to your new Azure account

3. First you need to find which regions you can use to create a machine with your student account;
   
   [https://portal.azure.com/#view/Microsoft_Azure_Policy/PolicyMenuBlade/%7E/Assignments](
https://portal.azure.com/#view/Microsoft_Azure_Policy/PolicyMenuBlade/%7E/Assignments)
   
   Select `Assignments>Allowed resource deployment regions`
      
   ![alt text](../docs/images/azureRegions.png "Figure asureRegions.png ")
   
   You should see a list like `["italynorth","norwayeast","switzerlandnorth","germanywestcentral","swedencentral"]`

2. Back at the Azure main dashboard, select `Virtual Machines`

   ![alt text](../docs/images/AzureForStudents-dashboard.png "Figure AzureForStudents-dashboard.png ")

3. select `Create>Azure Virtual lMachine`

   ![alt text](../docs/images/AzureForStudents-create-vm.png "Figure AzureForStudents-create-vm.png ")
   
4. You will be presented with a configuration page for the new machine

   ![alt text](../docs/images/AzureForStudents-create-basic.png "Figure AzureForStudents-create-basic.png ")

5. Fill in the values similar to this example page.
   
   * create a new resource group `COM304-2025`
   * select a new virtual machine name `com314-test-1`
   * choose one of the regions from the list above. (Any other region and you will not be allowed to create the machine). I chose `Norway East` because it allows automatic shutdown of machines. 
   
6. Select a machine size from `sizes`
   Different sizes are available in each region.
   We want a very small machine so `B1s` is the beast choice 1 CPU, 1G RAM at $9.64 per month
   
![alt text](../docs/images/AzureForStudents-create-basic.png "Figure AzureForStudents-create-basic.png ")

7. Select Authentication Type 
   * SSH Public key
   * Username azureuser
   * Generate New Key pair RSA SSH Format
   * enter a key pair name e.g. `com314-test-1_key`
   
8. Select inbound ports SSH(22) HTTP (80)

7. On the Disks Page Select a Hard Disk HDD (Not SSD)

![alt text](../docs/images/AzureForStudents-create-disks.png "Figure AzureForStudents-create-disks.png ")

8. On the Management page select auto shutdown ( very important)

![alt text](../docs/images/azure-autoshutdown.png "Figure azure-autoshutdown.png ")

8. Finally select `Review + Create`
