---?image=assets/images/gitpitch-audience.jpg
@title[Title-UEFI Overview]
<br><br><br><br><br>
## <span class="gold"   >&nbsp;UEFI & EDK II Training</span>

####  &nbsp;&nbsp;EDK II Build Process
<br>
<span style="font-size:0.75em" >&nbsp;&nbsp;&nbsp;<a href='http://www.tianocore.org'>tianocore.org</a></span>
Note:
  PITCHME.md for UEFI / EDK II Training EDK II Build Process

  Copyright (c) 2018, Intel Corporation. All rights reserved.<BR>

  Redistribution and use in source (original document form) and 'compiled'
  forms (converted to PDF, epub, HTML and other formats) with or without
  modification, are permitted provided that the following conditions are met:

  1) Redistributions of source code (original document form) must retain the
     above copyright notice, this list of conditions and the following
     disclaimer as the first lines of this file unmodified.

  2) Redistributions in compiled form (transformed to other DTDs, converted to
     PDF, epub, HTML and other formats) must reproduce the above copyright
     notice, this list of conditions and the following disclaimer in the
     documentation and/or other materials provided with the distribution.

  THIS DOCUMENTATION IS PROVIDED BY TIANOCORE PROJECT "AS IS" AND ANY EXPRESS OR
  IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF
  MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO
  EVENT SHALL TIANOCORE PROJECT  BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
  SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO,
  PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS;
  OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY,
  WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR
  OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS DOCUMENTATION, EVEN IF
  ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.



---  
@title[Lesson Objective]
<br>
### <p align="center"<span class="gold"   >Lesson Objective </span></p><br>

<!---  Add bullets using https://fontawesome.com/cheatsheet certificate
-->
 @fa[certificate gp-bullet-green]<span style="font-size:0.9em">&nbsp;&nbsp;Define EDK II </span><br><br>
 @fa[certificate gp-bullet-cyan] <span style="font-size:0.9em">&nbsp;&nbsp;Describe EDK II’s elements including file extensions,<br> 
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;directories, modules, packages, and libraries </span><br><br>
 @fa[certificate gp-bullet-yellow] <span style="font-size:0.9em">&nbsp;&nbsp;Explain the EDK II build process </span> <br><br>
 @fa[certificate gp-bullet-magenta] <span style="font-size:0.9em">&nbsp;&nbsp;Explain the Build tools</span> 

---?image=assets/images/binary-strings-black2.jpg
@title[EDK II Overview Section]
<br><br><br><br><br>
## <span class="gold"  >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;EDK II Overview </span>
<span style="font-size:0.9em" > &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;The EDK II Infrastructure </span>

---?image=/assets/images/slides/Slide4.JPG
<!-- .slide: data-transition="none" -->		  
@title[Philosophy of EDK II]
#### <p align="right"><span class="gold" > Philosophy of EDK II </span></p>


Note:
Support all UEFI and PI development needs <br>
Separate tool code from source code<br>
  - 	note : only older Intel Platforms:<br>
           Build existing EDK modules<br>
Via EDK Compatibility Package (ECP)<br>
Package Definition File: DEC<br>
DEC defines package of modules<br>
FLASH Mapping Tool <br>
Move as much code as possible to C<br>
Open source EDK II on http://tianocore.org<br>



EDK II Goals <br>

- so the main goal for EDK II to make it easer in porting  of platforms and building  UEFI Drivers<br>
-  First off EDK II is open source on tianocore.org<br>

One goal is to Support all UEFI and PI development needs<br>
UEFI Stands Unified Extensible Firmware Interface and UEFI and PI are making references to the Specifications that are managed by the UEFI Form on www.UEFI.org. 
The goal of EDK II is to support the implementations of these specs, and to make the implementation useful in a way to support one stand alone Driver or stand alone application or to build one Platform.
We wanted to Separate tool code from product code
On tianocore there is one storage for the Tools and a separate one for the Product code 
Because there are a lot of people using the EDK and there is a lot investment in EDK 1, (ie 1117) we wanted to make sure EDK II would build existing EDK modules
Via EDK Compatibility Package (ECP)<br>

We have a new Package Definition File: DEC<br>
One level between a platform and a single piece of code or a module
DEC defines package of modules 
Example – 3 drivers all related to the same piece of hardware they would go inside a logical package i.e. the NIC driver  a NIC.DEC

We have a FLASH Mapping Tool – we made improvements on this from the previous EDK build process.  There is more emphasis on what the flash device layout will look like.

We waned to Move as much as possible to C code
Eliminated a lot of the java
Eliminated a lot of the Assembly


+++?image=/assets/images/slides/Slide5.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[Philosophy of EDK II 02]
#### <p align="right"><span class="gold" > Philosophy of EDK II </span></p>

Note:
Separate tool code from source code<br>
  - 	note : only older Intel Platforms:<br>
           Build existing EDK modules<br>
Via EDK Compatibility Package (ECP)<br>

+++?image=/assets/images/slides/Slide6.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[Philosophy of EDK II 03]
#### <p align="right"><span class="gold" > Philosophy of EDK II </span></p>

Note:
+++?image=/assets/images/slides/Slide7.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[Philosophy of EDK II 04]
#### <p align="right"><span class="gold" > Philosophy of EDK II </span></p>

Note:
+++?image=/assets/images/slides/Slide8.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[Philosophy of EDK II 05]
#### <p align="right"><span class="gold" > Philosophy of EDK II </span></p>

Note:

+++?image=/assets/images/slides/Slide9.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[Philosophy of EDK II 06]
#### <p align="right"><span class="gold" > Philosophy of EDK II </span></p>

Note:

---?image=/assets/images/slides/Slide11.JPG
@title[Implementation of EDK II]
#### <p align="right"><span class="gold" > Implementation of EDK II </span></p>



Note:
You’ve already learned about the UEFI/PI specification from the web-based training.  Now, let’s talk about EDK II, the implementation of UEFI/PI

The primary purpose of the firmware boot loader is to initialize a platform and boot to a shell application or operating system.

EDK II architecture discussions primarily focus on UEFI (OS-to-firmware interface) and PI (firmware-to-firmware interface)



+++?image=/assets/images/slides/Slide12.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[Implementation of EDK II 02]
#### <p align="right"><span class="gold" > Implementation of EDK II </span></p>

Note:
You’ve already learned about the UEFI/PI specification from the web-based training.  Now, let’s talk about EDK II, the implementation of UEFI/PI

The primary purpose of the firmware boot loader is to initialize a platform and boot to a shell application or operating system.

EDK II architecture discussions primarily focus on UEFI (OS-to-firmware interface) and PI (firmware-to-firmware interface)


---?image=/assets/images/slides/Slide14.JPG
<!-- .slide: data-transition="none" -->		  
@title[EDK II File Extensions]
<p align="center"><span style="font-size:1.0em" > &nbsp;&nbsp;&nbsp;<font color="#e49436">EDK II File Extensions</font></span>
<span style="font-size:0.7em" ><font color="white"><br>-&nbsp;Located on <a href='http://www.tianocore.org'>tianocore.org</a> project edk2  </font> </span></p>

Note:
So for file extensions <br>

-So first we have a DSC file this is for platform description. This is an extension of the existing DSC file from EDK 1.  This describes the build rules, libraries and components that are going to get Built. 
-We have the DEC file which is the Package Declaration. Each package has a package declaration or DEC file, and it declares all the interfaces that the package has.  This is one of the new files
Next we have INF file 	- Module Definition this is a description of one module and what it has
Next we have a FDF file -Flash Description File – this information used to be part of the original DSC file but has been split off into a new file. This describes which module or modules weather it was built as part of the DSC or included in a binary – it describes which module gets to go where in the flash – which one is comprised – which one goes in to recover - it is a or mapping of the flash device –
Next we have a DXS file which is a Dependency expression file -  this is used by the DXE and in PEI modules to Define what prerequisites they have before they can run
Finally we have the FV file - Firmware Volume image file - 
 
First four have a specification file located on tianocore.org.

See EDK II Build Specification Documentation: 
          http://tianocore.org/  
		  
+++?image=/assets/images/slides/Slide15.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->		  

@title[EDK II File Extensions 02]
<p align="center"><span style="font-size:1.0em" > &nbsp;&nbsp;&nbsp;<font color="#e49436">EDK II File Extensions</font></span>
<span style="font-size:0.7em" ><font color="white"><br>-&nbsp;Located on <a href='http://www.tianocore.org'>tianocore.org</a> project edk2  </font> </span></p>

Note:
		  
+++?image=/assets/images/slides/Slide16.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->		  

@title[EDK II File Extensions 03]
<p align="center"><span style="font-size:1.0em" > &nbsp;&nbsp;&nbsp;<font color="#e49436">EDK II File Extensions</font></span>
<span style="font-size:0.7em" ><font color="white"><br>-&nbsp;Located on <a href='http://www.tianocore.org'>tianocore.org</a> project edk2  </font> </span></p>

Note:

---?image=/assets/images/slides/Slide23.JPG

@title[EDK II Directory Structure]
####  <p align="right"><span class="gold" > EDK II Directory Structure </span></p>		  
@div[right-50]
<br>
@ul[brighten]
- Package concept for each EDK II sub-directory
- Platforms are contained in an EDK II package
- EDK II build process reflects the package
- Concept of “Work Space” - <font face="Courier New"><b>$HOME/src/edk2</b></font>
@ulend
@divend

Note:
EXPLAINS WHAT IS IN THE DIRECTORY

Coding explains Workspace Build commands

EDK II build process reflects the package structure … the build command specifies the .DSC file for a platform
These directories are from the github edk2 project
---?image=/assets/images/slides/Slide25.jpg
<!-- .slide: data-transition="none" -->		  
@title[Directory Structure - Real Platform]
####  <p align="right"><span class="gold" > Directory Structure - Real Platform</span></p>

Note:
Open Source Directory COLUMN 1
Platform and Silicon Directory COLUMN 2

Minnowboard MAX (Native EDK II) is the example directory structure


+++?image=/assets/images/slides/Slide26.jpg
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->		  
@title[Directory Structure - Real Platform 02]
####  <p align="right"><span class="gold" > Directory Structure - Real Platform</span></p>

Note:
+++?image=/assets/images/slides/Slide27.jpg
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->		  
@title[Directory Structure - Real Platform 03]
####  <p align="right"><span class="gold" > Directory Structure - Real Platform</span></p>

Note:
+++?image=/assets/images/slides/Slide28.jpg
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->		  
@title[Directory Structure - Real Platform 04]
####  <p align="right"><span class="gold" > Directory Structure - Real Platform</span></p>

Note:

---?image=/assets/images/slides/Slide30.JPG
<!-- .slide: data-transition="none" -->	
@title[Modules]
####  <p align="right"><span class="gold" > Modules</span></p>



Note:

Image - Creative commons https://leadinginnovation11a.wikispaces.com/Where+is+Your+Hardhat%3F+-+Leadership+in+a+21st+Century+School <br> 
So the first thing we have in trying to break EDK II down is Modules:<br>
 
A module is the smallest separate object compiled in the EDK II.  A module is a single resultant .EFI file.<br>
Module examples:<br>
A UEFI/DXE driver <br>
A PEIM<br>
A UEFI application<br>
A Library <br>

All of these could be a module.  A modules could  be one entity<br>

+++?image=/assets/images/slides/Slide31.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->		  
@title[Modules 02]
####  <p align="right"><span class="gold" > Modules</span></p>

Note:

+++?image=/assets/images/slides/Slide32.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->		  
@title[Modules 03]
####  <p align="right"><span class="gold" > Modules</span></p>

Note:
+++?image=/assets/images/slides/Slide33.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->		  
@title[Modules 04]
####  <p align="right"><span class="gold" > Modules</span></p>

Note:


---?image=/assets/images/slides/Slide35.JPG

@title[Packages]
<br>
####  <p align="center"><span class="gold" > Packages</span></p>
@div[Left-50]
<br><br>
@ul[brighten]
- EDK II projects are made up of packages
- Make your own packages
- Package contains only the necessities
- Remove packages from  projects when not required
@ulend
@divend
@div[Right-50]
 <br> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
 <br> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
 <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
 <br>
 <br>
@divend

Note:

EDK II projects are made up of packages<br>
EDK II Enable developers to make their own packages<br>
Package contains only what is needed<br>
Remove packages from projects when not required<br>
<br><br><br>
We have this Package Philosophy and what do we mean by a package?<br>
So what we wanted to do is as we get more standards and specifications and as these standards evolve there is a need to target your development on the set of standards you care about.
For example, maybe you need some things from the PI specification and others from the UEFI 2.x Specifications and you want to put those things together. So one of the things we wanted to do is provide a mechanism for doing this. So it allows, for instance, a platform developer to get just the things he needs off the shelf and not get the things he dosen’t need. We did this with this concept of using packages
<br>
Some history about EDKI :<br>
The EDK I was kind of this monolithic block- it had this environment to build a module – it had the generic code for the  green “H” and this NT32 emulation but one thing that was not so good was you need the WHOLE thing in order to build just one thing.  Ie, like just building a driver.  It would be nice if it came in pieces instead of one big module.
If you are developing just drivers you May not care if you have the code for the green “H” or not.
SO instead it would be nice if the things came in packages instead of a large source tree.
<br>

Another advantage where packages will help,  is for example, if you want to add new functions/features - you could package your source together and distribute it as a package instead a monolithic tree. Then you could give this to a customer that has an EDK II build environment allowing them to build with your new functions and features.
<br>
Grouping the things together that you need with out the WHOLE kitchen sink Lets leave the Kitchen sink behind
<br>

EDK II Enable developers to make their own packages<br>
Package contains only what is needed<br>
Remove packages from projects when not required<br>
<br>
We have this Package Philosophy and what do we mean by a package?
So what we wanted to do is as we get more standards and specifications and as these standards evolve there is a need to target your development on the set of standards you care about.
For example, maybe you need some things from the PI specification and others from the UEFI 2.x Specifications and you want to put those things together. So one of the things we wanted to do is provide a mechanism for doing this. So it allows, for instance, a platform developer to get just the things he needs off the shelf and not get the things he dosen’t need. We did this with this concept of using packages
Some history about EDKI :
The EDK I was kind of this monolithic block- it had this environment to build a module – it had the generic code for the  green “H” and this NT32 emulation but one thing that was not so good was you need the WHOLE thing in order to build just one thing.  Ie, like just building a driver.  It would be nice if it came in pieces instead of one big module.
If you are developing just drivers you May not care if you have the code for the green “H” or not.
SO instead it would be nice if the things came in packages instead of a large source tree.

<br>
Another advantage where packages will help,  is for example, if you want to add new functions/features - you could package your source together and distribute it as a package instead a monolithic tree. Then you could give this to a customer that has an EDK II build environment allowing them to build with your new functions and features.
<br>
Grouping the things together that you need with out the WHOLE kitchen sink Lets leave the Kitchen sink behind
<br>



---?image=/assets/images/slides/Slide38_1.JPG
<!-- .slide: data-transition="none" -->		  
@title[EDK II Package Examples: Specs]
#### <p align="right"><span class="gold" > EDK II Package Examples: Specs</span></p>



Note:

MdePkg<br>
Include files and libraries for Industry Standard Specifications (i.e. UEFI, PI, PCI, USB, SMBIOS, ACPI, SMBIOS, etc)<br>
MdeModulePkg<br>
Modules (PEIMs + DXE Drivers + UEFI Drivers + UEFI Applications) that only definitions from the Industry Standard Specification defined in the MdePkg<br>
IntelFrameworkPkg<br>
Include files and libraries for those parts of the Intel Platform Innovation Framework for EFI specifications that were not adopted “as is” by the UEFI or PI specifications<br>
IntelFrameworkModulePkg<br>
Contains modules (PEIMs + DXE Drivers + UEFI Drivers) that make reference to one or more definitions in the IntelFrameworkPkg<br>



+++?image=/assets/images/slides/Slide39_1.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->		  
@title[EDK II Package Examples: Specs 02]
#### <p align="right"><span class="gold" > EDK II Package Examples: Specs</span></p>

Note:
MdeModulePkg<br>
Modules (PEIMs + DXE Drivers + UEFI Drivers + UEFI Applications) that only definitions from the Industry Standard Specification defined in the MdePkg<br>

+++?image=/assets/images/slides/Slide40_1.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->		  
@title[EDK II Package Examples: Specs 03]
#### <p align="right"><span class="gold" > EDK II Package Examples: Specs</span></p>

Note:


+++?image=/assets/images/slides/Slide41_1.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->		  
@title[EDK II Package Examples: Specs 04]
#### <p align="right"><span class="gold" > EDK II Package Examples: Specs</span></p>

Note:
MdePkg<br>
Include files and libraries for Industry Standard Specifications (i.e. UEFI, PI, PCI, USB, SMBIOS, ACPI, SMBIOS, etc)<br>
MdeModulePkg<br>
Modules (PEIMs + DXE Drivers + UEFI Drivers + UEFI Applications) that only definitions from the Industry Standard Specification defined in the MdePkg<br>
IntelFrameworkPkg<br>
Include files and libraries for those parts of the Intel Platform Innovation Framework for EFI specifications that were not adopted “as is” by the UEFI or PI specifications<br>
IntelFrameworkModulePkg<br>
Contains modules (PEIMs + DXE Drivers + UEFI Drivers) that make reference to one or more definitions in the IntelFrameworkPkg<br>


---?image=/assets/images/slides/Slide43.JPG

<!-- .slide: data-transition="none" -->		  
@title[Additional Package Examples: ]
#### <p align="right"><span class="gold" >Additional EDK II Package Examples:</span></p>

Note:
Platforms <br>
Nt32Pkg – contains drivers and applications required for running over Windows <br>
OvmfPkg – Virtual Machine Firmware

+++?image=/assets/images/slides/Slide44.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	
@title[Additional Package Examples: 02 ]
#### <p align="right"><span class="gold" >Additional EDK II Package Examples:</span></p>

Note:

Chipset/Processor<br>
IA32FamilyCpuPkg.- Intel Architecture <br>
Ich9Pkg – Intel I/O controller hub (ICH9 )

+++?image=/assets/images/slides/Slide45.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	
@title[Additional Package Examples: 03 ]
#### <p align="right"><span class="gold" >Additional EDK II Package Examples:</span></p>

Note:
Functionality<br>
ShellPkg – Application - command line interface<br>
NetworkPkg – Network drivers and Applications

---?image=/assets/images/slides/Slide47.JPG
<!-- .slide: data-transition="none" -->	

@title[Libraries ]
#### <p align="right"><span class="gold" >Libraries </span></p>


Note:

Famous Time line picture <br>
SEC –Platform code to Turn on the Cache so  having libraries would be useful<br>
PEI – Executing from the Flash device - No memory – constrained environment – turn on memory control – Set libraries to help write code in this environment  <br>
DXE – Main phase of Firmware – Platform interfaces – DXE Drivers, UEFI 2.x interfaces – Run EFI option roms – So we have libraries that are common between these environments <br>
<br>
Base Libraries – generic libraries that can run anywhere – not only in the EDK II but anywhere – generic environment for writing stand alone C code <br>
<br>
BDS – Policy happens – Screen turns – boot policy <br>
“Same lib classes exist across multiple phases but can have different lib instances”<br>

+++?image=/assets/images/slides/Slide48.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	
@title[Libraries 02]
#### <p align="right"><span class="gold" >Libraries </span></p>


Note:
Famous Time line picture <br>
SEC –Platform code to Turn on the Cache so  having libraries would be useful<br>
PEI – Executing from the Flash device - No memory – constrained environment – turn on memory control – Set libraries to help write code in this environment  <br>
DXE – Main phase of Firmware – Platform interfaces – DXE Drivers, UEFI 2.x interfaces – Run EFI option roms – So we have libraries that are common between these environments <br>
<br>
Base Libraries – generic libraries that can run anywhere – not only in the EDK II but anywhere – generic environment for writing stand alone C code <br>
<br>
BDS – Policy happens – Screen turns – boot policy <br>
“Same lib classes exist across multiple phases but can have different lib instances”<br>

+++?image=/assets/images/slides/Slide49.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	
@title[Libraries 03]
#### <p align="right"><span class="gold" >Libraries </span></p>


Note:
Famous Time line picture <br>
SEC –Platform code to Turn on the Cache so  having libraries would be useful<br>
PEI – Executing from the Flash device - No memory – constrained environment – turn on memory control – Set libraries to help write code in this environment  <br>
DXE – Main phase of Firmware – Platform interfaces – DXE Drivers, UEFI 2.x interfaces – Run EFI option roms – So we have libraries that are common between these environments <br>
<br>
Base Libraries – generic libraries that can run anywhere – not only in the EDK II but anywhere – generic environment for writing stand alone C code <br>
<br>
BDS – Policy happens – Screen turns – boot policy <br>
“Same lib classes exist across multiple phases but can have different lib instances”<br>

+++?image=/assets/images/slides/Slide50.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	
@title[Libraries 04]
#### <p align="right"><span class="gold" >Libraries </span></p>


Note:
Famous Time line picture <br>
SEC –Platform code to Turn on the Cache so  having libraries would be useful<br>
PEI – Executing from the Flash device - No memory – constrained environment – turn on memory control – Set libraries to help write code in this environment  <br>
DXE – Main phase of Firmware – Platform interfaces – DXE Drivers, UEFI 2.x interfaces – Run EFI option roms – So we have libraries that are common between these environments <br>
<br>
Base Libraries – generic libraries that can run anywhere – not only in the EDK II but anywhere – generic environment for writing stand alone C code <br>
<br>
BDS – Policy happens – Screen turns – boot policy <br>
“Same lib classes exist across multiple phases but can have different lib instances”<br>


---?image=/assets/images/slides/Slide52.JPG

<!-- .slide: data-transition="none" -->	
@title[Example-Library-Debuglib]
#### <p align="right"><span class="gold"  >Example - Library</span><span style="color:white;">&nbsp;&nbsp;<font face="Courier New"><b>Debuglib</b> </font></span></p>


Note:
DebugLib library class name <br>
The debugging characteristics might be different during the different boot up phases.<br>
SEC – Null or no code<br>
PEI-DXE-BDS – Code to output to serial port/ port 80 codes<br>
Library Class names can be linked with different Processor resolutions (IA32/ x64) & different boot phases<br>

+++?image=/assets/images/slides/Slide53.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	
@title[Example-Library-Debuglib 02]
#### <p align="right"><span class="gold"  >Example - Library</span><span style="color:white;">&nbsp;&nbsp;<font face="Courier New"><b>Debuglib</b> </font></span></p>


Note:
DebugLib library class name <br>
The debugging characteristics might be different during the different boot up phases.<br>
SEC – Null or no code<br>
PEI-DXE-BDS – Code to output to serial port/ port 80 codes<br>
Library Class names can be linked with different Processor resolutions (IA32/ x64) & different boot phases<br>

+++?image=/assets/images/slides/Slide54.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	
@title[Example-Library-Debuglib 03]
#### <p align="right"><span class="gold"  >Example - Library</span><span style="color:white;">&nbsp;&nbsp;<font face="Courier New"><b>Debuglib</b> </font></span></p>


Note:
DebugLib library class name <br>
The debugging characteristics might be different during the different boot up phases.<br>
SEC – Null or no code<br>
PEI-DXE-BDS – Code to output to serial port/ port 80 codes<br>
Library Class names can be linked with different Processor resolutions (IA32/ x64) & different boot phases<br>

---?image=/assets/images/slides/Slide56.JPG

@title[PCD Title page]
#### <p align="right"><span class="slide-title75" >Platform Configuration Database (PCD)</span></p>



Note:
Defining database - like global variables <br>

Many components of a database to help fine tune the BIOS or Firmware - build & runtime


---?image=/assets/images/slides/Slide57.JPG
<!-- .slide: data-transition="none" -->	

@title[Platform Configuration Database]
<p align="center"><span class="slide-title75" >Platform Configuration Database (PCD)</span></p>


Note:
So what is the platform configuration database goal? <br>

First off, PDC entries are used for module parameterization. Examples are define statements, variables etc.<br>

What are the benefits, we want to reduce the need to edit the source code. <br>
Also there is no need for searching for a magic #define  statement, for example like base address registers. These can all be PCD values.<br>
Purporting we want to maximize the module reuse across platforms and 
also will have APIs for accessing the PCD entries<br><br>

What the PCD store, the store platform information like the vital product data serial number, we can use variable PCBs for setup options etc.<br>

+++?image=/assets/images/slides/Slide58.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	

@title[Platform Configuration Database 02]
<p align="center"><span class="slide-title75" >Platform Configuration Database (PCD)</span></p>


Note:
So what is the platform configuration database goal? <br>

+++?image=/assets/images/slides/Slide59.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	

@title[Platform Configuration Database 03]
<p align="center"><span class="slide-title75" >Platform Configuration Database (PCD)</span></p>


Note:
So what is the platform configuration database goal? <br>


+++?image=/assets/images/slides/Slide60.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	

@title[Platform Configuration Database 04]
<p align="center"><span class="slide-title75" >Platform Configuration Database (PCD)</span></p>


Note:
So what is the platform configuration database goal? <br>

First off, PDC entries are used for module parameterization. Examples are define statements, variables etc.<br>

What are the benefits, we want to reduce the need to edit the source code. <br>
Also there is no need for searching for a magic #define  statement, for example like base address registers. These can all be PCD values.<br>
Purporting we want to maximize the module reuse across platforms and 
also will have APIs for accessing the PCD entries<br><br>

What the PCD store, the store platform information like the vital product data serial number, we can use variable PCBs for setup options etc.<br>



---?image=/assets/images/slides/Slide62.JPG
<!-- .slide: data-transition="none" -->	

@title[Platform Configuration Database - Advantages]
<p align="center"><span class="slide-title75" >Platform Configuration Database (PCD)</span></p>


Note:

What are the Advantages and the purpose of the platform configuration database?<br><br>

It has common definitions that are established for platform component settings in the database. The contents of this database are intended to standardize the exposure of platform and module settings which can in-turn facilitate platform porting. One of the goals is to help us with platform porting.<br>

There are some build time aspects – <br>
	A collection of component information is established from the PCD  component definitions that will be associated with a given module.<br>

There are run time aspects – <br>
	by providing APIs which allow common access to component settings during the operation of the platform, we can allow for binary distribution models which are PCD compliant. In other words, Not everyone has the source!<br>

And finally, there are binary edit aspects -<br>
	One of the stated goals is that a module can carry their own PCD data in their binary image and have it exposed so that they can be edited in the flash image.<br>


+++?image=/assets/images/slides/Slide63.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	
@title[Platform Configuration Database - Advantages 02]
<p align="center"><span class="slide-title75" >Platform Configuration Database (PCD)</span></p>


Note:


+++?image=/assets/images/slides/Slide64.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	
@title[Platform Configuration Database - Advantages 03]
<p align="center"><span class="slide-title75" >Platform Configuration Database (PCD)</span></p>


Note:

What are the Advantages and the purpose of the platform configuration database?<br><br>

It has common definitions that are established for platform component settings in the database. The contents of this database are intended to standardize the exposure of platform and module settings which can in-turn facilitate platform porting. One of the goals is to help us with platform porting.<br>

There are some build time aspects – <br>
	A collection of component information is established from the PCD  component definitions that will be associated with a given module.<br>

There are run time aspects – <br>
	by providing APIs which allow common access to component settings during the operation of the platform, we can allow for binary distribution models which are PCD compliant. In other words, Not everyone has the source!<br>

And finally, there are binary edit aspects -<br>
	One of the stated goals is that a module can carry their own PCD data in their binary image and have it exposed so that they can be edited in the flash image.<br>



---?image=/assets/images/slides/Slide66.JPG

<!-- .slide: data-transition="none" -->	
@title[EDK II Infrastructure Summary]
<br><br>
<p align="center"><span class="slide-title" >EDK II Infrastructure Summary</span></p>

Note:

Summary <br>
- Packages<br>
  - list of modules<br>
- Libraries<br>
   - Names with different implimentation<br>
- PCD
	
+++?image=/assets/images/slides/Slide67.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	
@title[EDK II Infrastructure Summary 02]
<br><br>
<p align="center"><span class="slide-title" >EDK II Infrastructure Summary</span></p>

Note:

Summary <br>
- Packages<br>
  - list of modules<br>
- Libraries<br>
   - Names with different implimentation<br>
- PCD

+++?image=/assets/images/slides/Slide68.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	
@title[EDK II Infrastructure Summary 03]
<br><br>
<p align="center"><span class="slide-title" >EDK II Infrastructure Summary</span></p>

Note:

Summary <br>
- Packages<br>
  - list of modules<br>
- Libraries<br>
   - Names with different implimentation<br>
- PCD

---?image=/assets/images/slides/Slide70.JPG

@title[EDK II vs. UDK]
#### <p align="center"><span class="gold" >EDK II vs. UDK(2010|2017 .. 2018)</span></p>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>

<span style="font-size:0.75em" >&nbsp;&nbsp;&nbsp;&nbsp;wiki on tianocore.org
<a href='https://github.com/tianocore/tianocore.github.io/wiki/Differences-between-UDK-and-EDK-II'>Differences between UDK - EDK II</a></span>	

Note:

The UEFI Developer's Kit 2010 (UDK2010) is an open-source driver & application development kit built on validated EDK II code <br>
UDK2018 is a stable build of the EDK II project<br>
Based on a snapshot of the EDK II project<br>
Validated on a variety of Intel platforms<br>
Validated with different OS & application software<br>
The open-source EDK II & UDK2010 do not contain code for Intel silicon or platforms<br>

Explain differences here so references later in the presentation make more sense.<br>

UEFI Developer's Kit 2010 (UDK2018) = open-source driver & application development kit containing EDK II (second generation EFI development kit) validated common-core sample code. The open-source UDK2010 is a stable build of the EDK II project, and has been validated on a variety of Intel platforms, operating systems, and application software.<br>

Intel® UEFI Developer’s Kit 2018 (Intel® UDK 2018, also called the Intel® UDK2018), Intel Corporation, 2018. 



---?image=assets/images/binary-strings-black2.jpg
@title[EDK II Overview Section]
<br><br><br><br><br>
## <span class="gold"  >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Build Tools </span>
<span style="font-size:0.9em" > &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;EDK Build Tools and Configuration Files </span>


---
<!---  END OF SLIDES
-->

@title[Packages]
#### <p align="center"><span class="gold" > Packages</span></p>
@div[left-50]
     <span style="color:#9e692e">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<i class="fa fa-gift fa-3x" aria-hidden="true" > </i> </span>
	 <span style="color:#514124">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<i class="fa fa-gift fa-2x" aria-hidden="true" > </i> </span><br>
     <span style="color:#BF5122">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<i class="fa fa-gift fa-5x" aria-hidden="true" > </i> </span>
	 <span style="color:#FFFF99">&nbsp;&nbsp;<i class="fa fa-gift fa-2x" aria-hidden="true" > </i>

@divend
@div[right-50]
<br><br><br>
@ul[brighten]
- EDK II projects are made up of packages
- Make your own packages
- Package contains only the necessities
- Remove packages from projects when not required
@ulend
@divend




Note:
TBD get notes from PackagesORG
---?color=black

### @color[white](Layout text alongside images)

@div[left-50]
<br>
![Modules](/assets/images/slides/bg21.png )
@divend

@div[right-50]
<br><br><br>
@ul[brighten]
- EDK II projects are made up of packages
- Make your own packages
- Package contains only the necessities
- Remove packages from projects when not required
@ulend
@divend

---
@title[lastslide]

<!--- comment END OF THE SLIDE DECK
-->

## <span class="gold"   >Last Slide to use</span>

##### END OF SLIDES 
- Summary
- Q & A
- Tianocore Logo
- Acknowledgements
<br>

Use the next slide as the last example in the slide deck.
---  
@title[Summary]
<br>
##### <p align="center"<span class="gold"   >Summary </span></p><br>

<!---  Add bullets using https://fontawesome.com/cheatsheet certificate
-->
 
 @fa[certificate gp-bullet-green]<span style="font-size:0.9em">&nbsp;&nbsp;Define EDK II </span><br><br>
 @fa[certificate gp-bullet-cyan] <span style="font-size:0.9em">&nbsp;&nbsp;Describe EDK II’s elements including file extensions,<br> 
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;directories, modules, packages, and libraries </span><br><br>
 @fa[certificate gp-bullet-yellow] <span style="font-size:0.9em">&nbsp;&nbsp;Explain the EDK II build process </span> <br><br>
 @fa[certificate gp-bullet-magenta] <span style="font-size:0.9em">&nbsp;&nbsp;Explain the Build tools</span> 




---?image=assets/images/gitpitch-audience.jpg
@title[Questions]
<BR>
![Questions](/assets/images/Questions.png =10x) 


---?image=assets/images/gitpitch-audience.jpg
@title[Logo Slide]
<BR><BR><BR>
![Logo Slide](/assets/images/TianocoreLogo.png =10x)

---  
@title[Backup]
<br><br><br><br><br>
### <p align="center"<span class="gold"   >Backup </span></p>

---
@title[Acknowledgements]
<br>
#### <p align="center"<span class="gold"   >Acknowledgements</span></p>

```c++
/**
Redistribution and use in source (original document form) and 'compiled' forms (converted
to PDF, epub, HTML and other formats) with or without modification, are permitted provided
that the following conditions are met:

Redistributions of source code (original document form) must retain the above copyright 
notice, this list of conditions and the following disclaimer as the first lines of this 
file unmodified.

Redistributions in compiled form (transformed to other DTDs, converted to PDF, epub, HTML
and other formats) must reproduce the above copyright notice, this list of conditions and 
the following disclaimer in the documentation and/or other materials provided with the 
distribution.

THIS DOCUMENTATION IS PROVIDED BY TIANOCORE PROJECT "AS IS" AND ANY EXPRESS OR IMPLIED 
WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND 
FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL TIANOCORE PROJECT BE 
LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES 
(INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, 
DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, 
WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) 
ARISING IN ANY WAY OUT OF THE USE OF THIS DOCUMENTATION, EVEN IF ADVISED OF THE POSSIBILITY 
OF SUCH DAMAGE.

Copyright (c) 2018, Intel Corporation. All rights reserved.
**/

```
