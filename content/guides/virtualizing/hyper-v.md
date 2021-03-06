+++
type = "article"
title = "Virtualizing Haiku In Hyper-V"
date = "2013-01-14T10:32:53.000Z"
tags = []
+++

There are several methods offered for installing Haiku. These include RAW images, ISO images and Anyboot images; which are a hybrid of the latter two images. The RAW images are pre-installed environment, in which the Virtual Hard Disk size cannot be customized, but going through the installation process is not required. The ISO images on the other hand can be burnt to a writeable CD or DVD, but can used in hyper-V to create a virtual CD-ROM that can be used to install Haiku onto a virtual Hard Disk. This guide will show you how to get Haiku up and running in Microsoft’s Hyper-V using the ISO images. 

The required image files can be found at on the "Get Haiku" page of this website which is located <a href="/get-haiku">here</a>. Hyper-V can be found as bundled software on Windows 8 Pro and Windows Server 2012, and can installed from the Programs and Features panel in the Control Panel on Windows 8 Pro.

<h3>Step One: Configuration Wizard</h3>
First of all, you will need to install Hyper-V. Then once you have done that, you will need to run the Hyper-V Manager;  which can be run by going Action > New > Virtual Machine. This will guide you through a configuration wizard that will help you to set up Haiku on Hyper-V. It will first give you the informal window Before You Begin, click Next. This next window is the Specify Name and Location window. Here you will first need to add the name of your virtual machine (try “Haiku testing”), then secondly you will need to specify the location of where you want your virtual machine to be on your computer (somewhere with lots of room). Click next and after this you will taken to the Assign Memory window. You need to tell Hyper-V how much memory it can use with this virtual machine. Use half of what Ram you have on your computer; so if you have 2048mb or ram, allow Hyper V to use around 1024mb for the virtual machine.  You can also check the checkbox Use Dynamic Memory, to also allow Hyper-V to use more RAM memory if it needs it. (Picture 2-1).



<img width="660" src="/files/image1_2.png" />
<em>Picture 2-1</em>

After clicking next again you will arrive at the configure networking screen, however as Haiku does not  yet work with Hyper-V’s network adapter without some extra steps, just leave it as it is, and click next and well will come back to it later. On the following screen you are asked to create virtual hard disk or attach to an existing virtual hard disk. We will need to create virtual hard disk, so give it the name haiku.vhdx. You will also be asked how large you want the virtual hard disk to be. Haiku can happily run with only a 1GB hard drive but it will need something over 5GB in order do the things you want. You are also asked give location of where the virtual hard disk will be kept; give it lots of room! (Picture 2-2).When you are finished click next again to go the following screen, here you are asked to specify where your installation media are. Choose Install an operating system from a boot CD/ROM, and then select Image file. Now click browse and select the Haiku image that you downloaded prior. (Picture 2-3). We are now finished with this wizard so click finish.

<img width="660" src="/files/image2.png" />
<em>Picture 2-2</em>


<img width="660" src="/files/image3_0.png" />
<em>Picture 2-3</em>


<h3>Step Two: Installing Haiku</h3>
Now that we have created the virtual machine, we need to start the virtual machine and install Haiku. On the main screen, double  click the virtual machine we just created, which should be located in the column Virtual Machines. Now on the window that pops up click Action > Start.  This will start the virtual machine and the installation will begin. You first need to choose your language, than set up the partitions, choose on which partition you will install Haiku and begin the installation (3-1). To free your mouse from virtual machine click <span class="button">Ctrl</span>+<span class="button">Alt</span>+<span class="button">&rarr;</span>.

<img width="660" src="/files/image4_0.png" />
<em>Picture 3-1</em>

<h3>Additional Steps</h3>
<h5>Step One: Networking</h5>
Now we need to create network connection, to have network access:
1. Go to Action > Virtual Switch Manager, choose external and click Create Virtual Switch.

2. Open up Control Panel > Network and Internet > Network Connections. You will find that you now have “Ethernet” and “vEthernet (Your Switch Name)” connections.

3. Right click on “Ethernet” and click “Properties”.  Under the Networking Tab select all items in the “This connection uses the following items” and then click “OK” (Picture 4-2).

Windows will now give you a nice warning about items being disabled (such as IPv4, etc).  Click “Yes” on this dialog. At this point you will see the “vEthernet” connection suddenly switch to “Identifying…..” and a few moments later you’ll be connected to your network (if you’re on a Windows domain the domain name will show).


<img width="660" src="/files/image5_0.png" />
<em>Picture 4-1</em>

Now go to the settings of the virtual machine in hardware > network adapter > virtual switch, choose your connection and apply (Picture 4-3).


<img width="660" src="/files/image6_0.png" />
<em>Picture 4-2</em>


<img width="660" src="/files/image7.png" />
<em>Picture 4-3</em>

<h5>Step Two: Audio</h5>
About audio, first go to services in task manager, and start Windows Audio (if it’s not started) (Picture 4-4). Next open the Remote Desktop Connection and choose Show Options. On the Local Resources tab under Remote Audio, choose Settings. Ensure that “Play on this computer” is selected (Picture 4-5).

<img src="/files/image8_1.png" />
<em>Picture 4-4</em>


<img src="/files/image9_0.png" />
<em>Picture 4-5</em>

<h3>Troubleshooting</h3>
If you have problems with starting the virtual machine, than your computer doesn’t support virtualization or you need to activate from the BIOS. Data Execution Prevention need to be enabled, you may find in advanced settings in BIOS. Another problem is that Hyper-V doesn’t support USB.