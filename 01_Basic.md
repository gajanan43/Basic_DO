# Day-01
## 1.DevOps:-
	
 Def:-DevOps is a process of improving the application delivery:<br>
1)Quality<br>
2)Automation <br>
3)Continuous Monitoring <br>
4) Continuous Testing <br>

-Before DevOps Developer Team, Testing Team, Deployment Team, Maintenance Team working speratly.<br>

# Day-02

## 2.SDLC(Software Development Life Cycle):-
Phases of SDLC:<br>
1.	Requirement Gathering and Analysis<br>
o	Understand what the client/user needs.<br>
2.	Planning<br>
o	Define scope, timelines, resources, and risk assessment.<br>
o	Choose a suitable SDLC model (e.g., Waterfall, Agile).<br>
3.	Design<br>
o	Create architectural and technical design (e.g., UML diagrams).<br>
o	Decide on technologies, database structure, and system architecture.<br>
4.	Implementation / Coding<br>
o	Developers write the actual code based on the design documents.<br>
o	Tools: IDEs, version control (e.g., Git).<br>
5.	Testing<br>
o	Conduct unit testing, integration testing, system testing, and user acceptance testing.<br>
o	Aim: detect and fix bugs before deployment.<br>
6.	Deployment<br>
o	Release the software to production.<br>
7.	Maintenance<br>
o	Fix bugs, patch security issues, and make enhancements as needed.<br>
o	Monitor performance and user feedback.<br>
## ANS:- 4,5,6,7 These steps are combined together and working an automated in DevOps<br>

# Day-03

## 3.Virtual Machine:-
-A Virtual Machine (VM) is a software-based simulation of a physical computer.<br>
-It runs an operating system and applications just like a real computer, but it's hosted on another machine called a host system.<br>
1) hypervisor -(like VMware, VirtualBox, or Hyper-V) creates and manages VMs.<br>
2) Host machine runs the hypervisor and shares its hardware (CPU, RAM, storage) with VMs.<br>
3) Each VM (guest) acts like a separate computer with its own OS (Windows, Linux, etc.).<br>

# Day-04

## 4.AWS & Azure:-
To create a virtual machine (VM) on AWS, you typically launch an EC2 (Elastic Compute Cloud) instance. Here's a step-by-step guide:<br>
Step-by-Step: Launch a Virtual Machine (EC2 Instance) on AWS<br>
1. Sign in to AWS Console<br>
2. Navigate to EC2 Dashboard<br>
	->Click "EC2" to go to the EC2 Dashboard.<br>
3. Launch Instance<br>
	->Click the “Launch Instance” button.<br>
4. Configure Your Instance<br>
You’ll need to set up several options:<br>
   -Name: Give your instance a name.<br>
   -AMI (Amazon Machine Image): Choose an OS (e.g., Ubuntu, Amazon Linux, Windows).<br>
   -Instance Type: Choose hardware (e.g. free tier).<br>
   -Key Pair: Create or select an existing key pair (used for SSH access).<br>
   -Network Settings: Set up or use a default VPC and subnet. Allow SSH (port 22) or RDP (port 3389) depending on the OS.<br>
   -Storage: Default (8 GB for Linux is typical; increase if needed).<br>
5. Launch the Instance<br>
	->Click “Launch Instance” after reviewing settings.<br>
6. Steps to connect your EC2 instance with terminal <br>

# AWS
## SSH (for Linux): Use the .pem key with ssh -i /path of your key value pair file.pem ubuntu@PublicIPAddress

# Azure
## SSH (for Linux): Use the .pem key with ssh -i /path of your key value pair file.pem azureuser@PublicIPAddress


