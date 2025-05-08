## 1.DevOps:-
	
 Def:-DevOps is a process of improving the application delivery:
1)Quality 
2)Automation 
3)Continuous Monitoring 
4) Continuous Testing 

-Before DevOps Developer Team, Testing Team, Deployment Team, Maintenance Team working speratly.

## 2.SDLC(Software Development Life Cycle):-
Phases of SDLC:
1.	Requirement Gathering and Analysis
o	Understand what the client/user needs.
2.	Planning
o	Define scope, timelines, resources, and risk assessment.
o	Choose a suitable SDLC model (e.g., Waterfall, Agile).
3.	Design
o	Create architectural and technical design (e.g., UML diagrams).
o	Decide on technologies, database structure, and system architecture.
4.	Implementation / Coding
o	Developers write the actual code based on the design documents.
o	Tools: IDEs, version control (e.g., Git).
5.	Testing
o	Conduct unit testing, integration testing, system testing, and user acceptance testing.
o	Aim: detect and fix bugs before deployment.
6.	Deployment
	->Release the software to production.
7.	Maintenance
	->Fix bugs, patch security issues, and make enhancements as needed.
        ->Monitor performance and user feedback.
## ANS:- 4,5,6,7 These steps are combined together and working an automated in DevOps

## 3.Virtual Machine:-
-A Virtual Machine (VM) is a software-based simulation of a physical computer.
-It runs an operating system and applications just like a real computer, but it's hosted on another machine called a host system.
1) hypervisor -(like VMware, VirtualBox, or Hyper-V) creates and manages VMs.
2) Host machine runs the hypervisor and shares its hardware (CPU, RAM, storage) with VMs.
3) Each VM (guest) acts like a separate computer with its own OS (Windows, Linux, etc.).

## 4.AWS & Azure:-
To create a virtual machine (VM) on AWS, you typically launch an EC2 (Elastic Compute Cloud) instance. Here's a step-by-step guide:
Step-by-Step: Launch a Virtual Machine (EC2 Instance) on AWS
1. Sign in to AWS Console
2. Navigate to EC2 Dashboard
	->Click "EC2" to go to the EC2 Dashboard.
3. Launch Instance
	->Click the “Launch Instance” button.
4. Configure Your Instance
You’ll need to set up several options:
   -Name: Give your instance a name.
   -AMI (Amazon Machine Image): Choose an OS (e.g., Ubuntu, Amazon Linux, Windows).
   -Instance Type: Choose hardware (e.g. free tier).
   -Key Pair: Create or select an existing key pair (used for SSH access).
   -Network Settings: Set up or use a default VPC and subnet. Allow SSH (port 22) or RDP (port 3389) depending on the OS.
   -Storage: Default (8 GB for Linux is typical; increase if needed).
5. Launch the Instance
	->Click “Launch Instance” after reviewing settings.
6. Steps to connect your EC2 instance with terminal 
## SSH (for Linux): Use the .pem key with ssh -i /path of your key value pair file.pem ubuntu@PublicIPAddress


