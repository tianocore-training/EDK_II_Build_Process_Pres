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
 @fa[certificate gp-bullet-cyan]<span style="font-size:0.9em">&nbsp;&nbsp;Describe EDK II’s elements including file extensions,<br> 
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;directories, modules, packages, and libraries </span><br><br>
 @fa[certificate gp-bullet-yellow]<span style="font-size:0.9em">&nbsp;&nbsp;Explain the EDK II build process </span> <br><br>
 @fa[certificate gp-bullet-magenta]<span style="font-size:0.9em">&nbsp;&nbsp;Explain the Build tools</span> 

---?image=assets/images/binary-strings-black2.jpg
@title[EDK II Overview Section]
<br><br><br><br><br>
## <span class="gold"  >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;EDK II Overview </span>
<span style="font-size:0.9em" > &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;The EDK II Infrastructure </span>



---
@title[Philosophy of EDK II]
<br>
#### <p align="center"><span class="gold" > Philosophy of EDK II </span></p>

@snap[west span-35]
@box[bg-blue text-white  waved  fragment](<b>Support UEFI & PI needs</b><br><br>)
@snapend

@snap[midpoint span-35]
@box[bg-gray text-white waved fragment](<b>Separate tool & source code</b><br><br>)
@snapend

@snap[east span-35]
@box[bg-green text-white waved fragment](<b>Package Definition file: DEC</b><br>)
@snapend

@snap[south-west span-35]
@box[bg-yellow text-blue  waved fragment](<b>Flash Mapping Tool</b><br><br>)
@snapend

@snap[south span-35]
@box[bg-orange text-white waved fragment](<b>Move as much code to C</b><br><br>)
@snapend

@snap[south-east span-35]
@box[bg-purple text-white waved fragment](<b>Open source <br>EDK II on tianocore.org</b><br>)
@snapend

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



---?image=/assets/images/slides/Slide11.JPG
@title[Implementation of EDK II]
#### <p align="right"><span class="gold" > Implementation of EDK II </span></p>


@snap[west span-90]
@box[bg-blue text-white  rounded  fragment](<Br><span style="font-size:01.25em" ><b>EDK II == UEFI / PI Implementation</b></span><br><br>)
@snapend


Note:
You’ve already learned about the UEFI/PI specification from the web-based training.  Now, let’s talk about EDK II, the implementation of UEFI/PI

The primary purpose of the firmware boot loader is to initialize a platform and boot to a shell application or operating system.

EDK II architecture discussions primarily focus on UEFI (OS-to-firmware interface) and PI (firmware-to-firmware interface)


---
@title[EDK II File Extensions]
<p align="center"><span style="font-size:1.0em" > &nbsp;&nbsp;&nbsp;<font color="#e49436"><b>EDK II File Extensions</b></font></span>
<span style="font-size:0.7em" ><font color="white"><br>-&nbsp;Located on <a href='http://www.tianocore.org'>tianocore.org</a> project edk2  </font> </span></p>


<table id="recTable">
	<tr>
		<td bgcolor="#121212"><p style="line-height:70%"><span style="font-size:0.75em" ><b>@color[#00ffff](.DSC) <br>.DEC &nbsp;&nbsp;<br>@color[#00ffff](.INF)<br>.FDF</b></span></p></td>
		<td bgcolor="#121212"><p style="line-height:70%"><span style="font-size:0.75em" ><b>@color[#00ffff](- Platform Description ) <br>- Package Declaration <br>@color[#00ffff](- Module Definition <i>define a component</i>) <br>- Flash Description </b></span></p></td>
	</tr>
	<tr>
		<td bgcolor="#323232"><p style="line-height:50%"><span style="font-size:0.65em" >&nbsp;<br><br>&nbsp;&nbsp;&nbsp;</span></p></td>
		<td bgcolor="#323232"><p style="line-height:50%"><span style="font-size:0.65em" >&nbsp;<br><br></span></p></td>
	</tr>
	<tr>
		<td bgcolor="#323232"><p style="line-height:50%"><span style="font-size:0.65em" >&nbsp;<br></span></p></td>
		<td bgcolor="#323232"><p style="line-height:50%"><span style="font-size:0.65em" >&nbsp;<br></span></p></td>
	</tr>

</table>


+++
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[EDK II File Extensions]
<p align="center"><span style="font-size:1.0em" > &nbsp;&nbsp;&nbsp;<font color="#e49436"><b>EDK II File Extensions</b></font></span>
<span style="font-size:0.7em" ><font color="white"><br>-&nbsp;Located on <a href='http://www.tianocore.org'>tianocore.org</a> project edk2  </font> </span></p>


<table id="recTable">
	<tr>
		<td bgcolor="#121212"><p style="line-height:70%"><span style="font-size:0.75em" ><b>@color[#00ffff](.DSC) <br>.DEC &nbsp;&nbsp;<br>@color[#00ffff](.INF)<br>.FDF</b></span></p></td>
		<td bgcolor="#121212"><p style="line-height:70%"><span style="font-size:0.75em" ><b>@color[#00ffff](- Platform Description ) <br>- Package Declaration <br>@color[#00ffff](- Module Definition <i>define a component</i>) <br>- Flash Description </b></span></p></td>
	</tr>
	<tr>
		<td bgcolor="#323232"><p style="line-height:50%"><span style="font-size:0.65em" >.VFR <br>.UNI <br>.c & .h </span></p></td>
		<td bgcolor="#323232"><p style="line-height:50%"><span style="font-size:0.65em" >- Visual Forms Representation for User interface <br>- Unicode String text files w/ ease of localization<br>- Source code files</span></p></td>
	</tr>
	<tr>
		<td bgcolor="#323232"><p style="line-height:50%"><span style="font-size:0.65em" >.FD <br>.FV </span></p></td>
		<td bgcolor="#323232"><p style="line-height:50%"><span style="font-size:0.65em" >- Final Flash Device Image  <br>- Firmware Volume File</span></p></td>
	</tr>

</table>

@snap[north-east span-30]
@css[ text-yellow fragment](<span style="font-size:01.45em" ><b><i><br><br>&nbsp;@color[yellow](EDK II Spec)<br><br><br>&nbsp;@color[yellow](Source)<br><br>&nbsp;@color[yellow](Output)</i></b> </span>)
@snapend



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
+++?image=/assets/images/slides/Slide28_1.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->		  
@title[Directory Structure - Real Platform 04]
####  <p align="right"><span class="gold" > Directory Structure - Real Platform</span></p>

Note:

---?image=/assets/images/slides/Slide30.JPG
@title[Modules]
####  <p align="right"><span class="gold" > Modules</span></p>
@css[text-white fragment](<b> Smallest separate object compiled in EDK II</b>)
<br>
<br>
<br>
<br>
@css[text-yellow fragment](<b>@color[yellow](Compiles to)<br>@color[yellow](`.EFI` File)</b>)


@snap[east span-35]
@css[ text-white fragment](<b>UEFI/DXE Driver <br>@color[yellow](PEIM)<br>@color[orange](UEFI App.) </b>or <b><br>@color[#00ffff](Library) </b>)
@snapend

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


---?image=/assets/images/slides/Slide35.JPG

@title[Packages]
<br>
###  <p align="center"><span class="gold" > Packages</span></p>
@div[Left-50]

@ul[brighten]
- EDK II projects are made<BR> up of packages<br>
- Make your own packages<br>
- Package contains only the <BR>necessities<br>
- Remove packages from  <BR>projects when not required
@ulend
@divend
@div[Right-50]
 <br> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
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


---

@title[EDK II Package Examples: Specs]
#### <p align="right"><span class="gold" > EDK II Package Examples: Specs</span></p>


@snap[west span-45 fragment]
@box[bg-blue text-white rounded](<span style="font-size:02.5em" >`MdePkg`</span>#Includes files and libraries for Industry Standard Specifications<br><br>)
@snapend

@snap[east span-45 fragment]
@box[bg-orange text-white rounded ](<span style="font-size:02.5em" >`MdeModulePkg`</span>#Modules only definitions from the Industry Standard Specification defined in the MdePkg)
@snapend



Note:

MdePkg<br>
Include files and libraries for Industry Standard Specifications (i.e. UEFI, PI, PCI, USB, SMBIOS, ACPI, SMBIOS, etc)<br>
MdeModulePkg<br>
Modules (PEIMs + DXE Drivers + UEFI Drivers + UEFI Applications) that only definitions from the Industry Standard Specification defined in the MdePkg<br>
IntelFrameworkPkg<br>
Include files and libraries for those parts of the Intel Platform Innovation Framework for EFI specifications that were not adopted “as is” by the UEFI or PI specifications<br>
IntelFrameworkModulePkg<br>
Contains modules (PEIMs + DXE Drivers + UEFI Drivers) that make reference to one or more definitions in the IntelFrameworkPkg<br>

+++
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->		  


@title[EDK II Package Examples: Specs]
#### <p align="right"><span class="gold" > EDK II Package Examples: Specs</span></p>


@snap[west span-45 ]
@box[bg-blue text-white rounded](<span style="font-size:02.5em" >`MdePkg`</span>#Includes files and libraries for Industry Standard Specifications<br><br>)
@snapend

@snap[east span-45 ]
@box[bg-orange text-white rounded ](<span style="font-size:02.5em" >`MdeModulePkg`</span>#Modules only definitions from the Industry Standard Specification defined in the MdePkg)
@snapend

@snap[south-west span-45]
@box[bg-gray text-white rounded ](<span style="font-size:02.5em" >`IntelFrameworkPkg`</span>#Include files and libraries for those parts of the specifications that were not adopted “as is” by the UEFI or PI specifications)
@snapend

@snap[south-east span-45 fragment]
@box[bg-gray text-white rounded ](<span style="font-size:01.75em" >`IntelFrameworkModulePkg`</span>#Contains modules such as PEIMs + DXE Drivers + UEFI Drivers from definitions in the IntelFrameworkPkg <br>)
@snapend


Note:

MdePkg<br>
Include files and libraries for Industry Standard Specifications (i.e. UEFI, PI, PCI, USB, SMBIOS, ACPI, SMBIOS, etc)<br>
MdeModulePkg<br>
Modules (PEIMs + DXE Drivers + UEFI Drivers + UEFI Applications) that only definitions from the Industry Standard Specification defined in the MdePkg<br>
IntelFrameworkPkg<br>
Include files and libraries for those parts of the Intel Platform Innovation Framework for EFI specifications that were not adopted “as is” by the UEFI or PI specifications<br>
IntelFrameworkModulePkg<br>
Contains modules (PEIMs + DXE Drivers + UEFI Drivers) that make reference to one or more definitions in the IntelFrameworkPkg<br>


---
<!-- .slide: data-transition="none" -->		  
@title[Additional Package Examples: ]
#### <p align="right"><span class="gold" >Additional EDK II Package Examples:</span></p>
<br>
@ul[no-bullet]
- @fa[certificate gp-bullet-gold]&nbsp;&nbsp;<span style="font-size:01.2em"><b>Platforms</b></span><br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;@color[#00ffff](`Nt32Pkg`) &nbsp;&nbsp;&nbsp; & &nbsp;&nbsp;&nbsp; @color[#00ffff](`OvmfPkg`)</span><br><br><br>
- @fa[certificate gp-bullet-magenta]&nbsp;&nbsp;<span style="font-size:01.2em"><b>Chipset/Processor</b></span><br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;@color[#00ffff](`Ia32FamilyCpuPkg`) &nbsp;&nbsp;&nbsp;& &nbsp;&nbsp;&nbsp;@color[#00ffff](`BroxtonSiPkg`)</span><br><br><br>
- @fa[certificate gp-bullet-green]&nbsp;&nbsp;<span style="font-size:01.2em"><b>Functionality</b></span><br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;@color[#00ffff](`ShellPkg`)&nbsp;&nbsp;&nbsp; & &nbsp;&nbsp;&nbsp; @color[#00ffff](`NetworkPkg`)</span><br>
@ulend


Note:
Platforms <br>
Nt32Pkg – contains drivers and applications required for running over Windows <br>
OvmfPkg – Virtual Machine Firmware

Chipset/Processor<br>
IA32FamilyCpuPkg.- Intel Architecture <br>
Ich9Pkg – Intel I/O controller hub (ICH9 )

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
#### <p align="right"><span class="gold" >Platform Configuration Database (PCD)</span></p>



Note:
Defining database - like global variables <br>

Many components of a database to help fine tune the BIOS or Firmware - build & runtime
---
@title[Platform Configuration Database-Goals]
#### <p align="right"><span class="gold" >Platform Configuration Database (PCD)</span></p>
@box[bg-blue text-white rounded](<span style="font-size:02.0em" >`Goals`</span>)



@snap[west span-45 ]
@box[bg-orange text-white rounded fragment](<span style="font-size:01.5em" >Define module parameters</span># Store module / platform configurations)
@snapend

@snap[east span-45 ]
@box[bg-orange text-white rounded fragment](<span style="font-size:01.5em" >Reduce source edits</span># Maximize module reuse across platforms)
@snapend

@snap[south-west span-45]
@box[bg-orange text-white rounded fragment](<span style="font-size:01.5em" >Remove &num;`define` </span># No searching for “<i>magic</i>” &num;`define` statements )
@snapend

@snap[south-east span-45 ]
@box[bg-orange text-white rounded fragment](<span style="font-size:01.5em" >API functions</span># Get and Set functions for access to PCD variable DB)
@snapend

Note:
So what is the platform configuration database goal? <br>

First off, PDC entries are used for module parameterization. Examples are define statements, variables etc.<br>

What are the benefits, we want to reduce the need to edit the source code. <br>
Also there is no need for searching for a magic #define  statement, for example like base address registers. These can all be PCD values.<br>
Purporting we want to maximize the module reuse across platforms and 
also will have APIs for accessing the PCD entries<br><br>

What the PCD store, the store platform information like the vital product data serial number, we can use variable PCBs for setup options etc.<br>


---
@title[Platform Configuration Database - Advantages]
#### <p align="right"><span class="gold" >Platform Configuration Database (PCD)</span></p>
@box[bg-yellow text-blue rounded](<span style="font-size:02.0em" >`Advantages`</span>)



@snap[west span-45 ]
@box[bg-purple text-white rounded fragment](<span style="font-size:01.5em" >Binary Modularity</span># Configure firmware settings in binaries without building )
@snapend

@snap[east span-45 ]
@box[bg-purple text-white rounded fragment](<span style="font-size:01.5em" >Configure</span># Provide for options to configure firmware features)
@snapend

@snap[south span-45]
@box[bg-purple text-white rounded fragment](<span style="font-size:01.5em" >Patching </span># Simplify the binary patching process )
@snapend


Note:

What are the Advantages and the purpose of the platform configuration database?<br><br>

It has common definitions that are established for platform component settings in the database. The contents of this database are intended to standardize the exposure of platform and module settings which can in-turn facilitate platform porting. One of the goals is to help us with platform porting.<br>

There are some build time aspects – <br>
	A collection of component information is established from the PCD  component definitions that will be associated with a given module.<br>

There are run time aspects – <br>
	by providing APIs which allow common access to component settings during the operation of the platform, we can allow for binary distribution models which are PCD compliant. In other words, Not everyone has the source!<br>

And finally, there are binary edit aspects -<br>
	One of the stated goals is that a module can carry their own PCD data in their binary image and have it exposed so that they can be edited in the flash image.<br>


---
@title[EDK II Infrastructure Summary]
<br>
#### <p align="center"><span class="gold" >EDK II Infrastructure Summary</span></p>



@snap[west span-30 ]
@box[bg-blue text-white waved fragment](<span style="font-size:01.25em" >@color[yellow](<b>Packages</b>)</span><br>List of related modules )
@snapend


@snap[north-west span-45 fragment]
@css[text-yellow]( <br><br><br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="font-size:03.25em" >+</span>)
@snapend

	
@snap[midpoint span-30 ]
@box[bg-blue text-white waved fragment](<span style="font-size:01.25em" >@color[yellow](<b>Libraries</b>)</span> Same name & interface)
@snapend

@snap[north span-45 fragment]
@css[text-yellow]( <br><br><br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="font-size:03.25em" >+</span>)
@snapend

@snap[east span-30]
@box[bg-blue text-white waved fragment](<span style="font-size:01.25em" >@color[yellow](<b>PCDs</b>) </span><br> Platform Config. DB )
@snapend


Note:

Summary <br>
- Packages<br>
  - list of modules<br>
- Libraries<br>
   - Same Names with different implementation but same interface<br>
- PCD
  - Platform configuration database



---
@title[EDK II vs. UDK]
#### <p align="center"><span class="gold" >EDK II vs. UDK(2010|2017 .. 2018)</span></p>
<br>
@box[bg-blue  text-white rounded](<span style="font-size:01.1em" ><b>UEFI Developer's Kit 2018 &lpar;UDK2018&rpar;</b> </span>)
<br>
@box[bg-purple text-white rounded](<span style="font-size:01.1em" ><b>Stable build of the EDK II project</b> </span>)
<br>
@box[bg-green text-white rounded](<span style="font-size:01.1em" ><b>Neither contain Intel silicon or platform code</b></span>)

<br>
<span style="font-size:0.75em" >&nbsp;&nbsp;&nbsp;&nbsp;wiki on tianocore.org: <a href='https://github.com/tianocore/tianocore.github.io/wiki/Differences-between-UDK-and-EDK-II'>Differences between UDK - EDK II</a></span>	

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
@title[Build Tools Section]
<br><br><br><br><br>
## <span class="gold"  >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Build Tools </span>
<span style="font-size:0.9em" > &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;EDK Build Tools and Configuration Files </span>

---
@title[Development Environment]
#### <p align="center"><span class="gold" >Development Environment</span></p>

@snap[west span-45 ]
@box[bg-orange text-white](<span style="font-size:01.125em" ><b>Compiler Tool Chains</b></span>)
<span style="font-size:0.8em" >&nbsp;<br>&nbsp;<br>&nbsp;<br>&nbsp;<br>&nbsp;<br>&nbsp;<br>&nbsp;<br&nbsp;><br>&nbsp;<br></span>  
@snapend

@snap[east span-45 ]
@box[bg-green text-white](<span style="font-size:01.125em" ><b>Operating Systems</b>)</span>    
<span style="font-size:0.8em" >&nbsp;<br>&nbsp;<br>&nbsp;<br>&nbsp;<br>&nbsp;<br>&nbsp;<br>&nbsp;<br&nbsp;><br>&nbsp;<br></span>  
@snapend
<span style="font-size:0.8em" ><br><br></span>

<div class="left">
<ul style="line-height:0.8;"><font color=#fcb813>
  <li><span style="font-size:0.8em" >@color[#fcb813](Microsoft Visual Studio &lpar;VS2015, VS2013, VS2012, VS2010, etc.&rpar; ) </span></li>
  <li><span style="font-size:0.8em" >@color[#fcb813]( Microsoft WDK) </span></li>
  <li><span style="font-size:0.8em" >@color[#fcb813]( Intel C/C++ compiler) </span></li>
  <li><span style="font-size:0.8em" >@color[#fcb813](Intel C EFI Byte Code &lpar;EBC&rpar; compiler ) </span></li>
  <li><span style="font-size:0.8em" >@color[#fcb813]( GCC V5.x or later) </span></li>
</ul>
</div>

<div class="right1">
<ul style="line-height:0.8;"><font color=#A6ce39>
  <li><span style="font-size:0.8em" >@color[#A6ce39](Microsoft Windows XP/7/8/10 ) </span></li>
  <li><span style="font-size:0.8em" >@color[#A6ce39](Apple Mac OS X ) </span></li>
  <li><span style="font-size:0.8em" >@color[#A6ce39](RedHat Enterprise Linux) </span></li>
  <li><span style="font-size:0.8em" >@color[#A6ce39](Novell SuSE Linux) </span></li>
  <li><span style="font-size:0.8em" >@color[#A6ce39](Ubuntu 16.04 ) </span></li>
</ul>

</div>

Note:
The development environment is one of the primary changes to EDK II.<br>
We wanted a change, build wood work dramatically <br>
We have Compiler tool chains:<br>
    we still support Microsoft C compiler and WDK and Intel C/C++ compiler<br>
      now we also support GCC<br>
We still support Intel C UEFI Byte code compiler<br>
You  can build across multiple Operating Systems –Windows, Mac, Linux flavors<br>
All of these are supported across all the modules in the write.<br>
  NOTE: this does not mean someone can write some assembly language code that was specific to the Microsoft compiler or assembler that in turn does not work on GCC. The standards we set for the core components are that they will work across everything. It is up to you as a developer to make sure the code you write meets the requirements of what ever compiler you use. <br>
For example, the byte code compiler does not do floating point.  So if you add code that does floating point, be aware that you cannot compile that into byte code. 



---?image=/assets/images/BK_grey-box-bottom.jpg
@title[Environment Variables]
#### <p align="center"><span class="gold" >Environment Variables</span></p>




@snap[north span-35 ]
@css[text-yellow]( <br>&nbsp;)
@box[bg-blue text-white rounded](Set by <span style="font-size:01.2em" > @color[yellow](`edksetup`) </span><br>Window = `.bat`<br>Linux = `.sh` )
@snapend
<br>
<br>
<br>
<br>
<br>
<div class="left-2">
  <span style="font-size:0.8em" >&nbsp;  </span>
</div>
<div class="right-2">
<ul style="list-style-type:none" style="line-height:0.8;">
  <li><span style="font-size:0.9em" >1.&nbsp;&nbsp; EDK_TOOLS_PATH  </span></li>
  <li><span style="font-size:0.9em" >2.&nbsp;&nbsp; PATH  </span></li>
  <li><span style="font-size:0.9em" >3.&nbsp;&nbsp; WORKSPACE  </span></li>
  <li><span style="font-size:0.9em" >4.&nbsp;&nbsp; EFI_SOURCE / EDK_SOURCE  </span></li>
  <li><span style="font-size:0.7em" >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<i>Outside</i>  @color[yellow](`edksetup` )</span></li>
  <li><span style="font-size:0.9em" >&nbsp;@color[orange](* )&nbsp;&nbsp;PACKAGES_PATH @color[black]((<i>optional</i> &rpar;)  </span></li>
</ul>
</div>
  
  

Note:
EDK II depends on Environment variables – <br>
The EDK_TOOLS_PATH –tells the build system the location of the binary tools directory. By default they will be in the build tools directory. However, there may be a difference if you are on a server and you share build tools.  Or, for example, if you compile build tools for Linux and another for windows, and you want to set your build path based on which OS you are building from.<br>

The PATH is the directory location for any binary tools needed for the operating system.<br>

The WORKSPACE –tells EDK II your workspace . You would want to set it to the location where you downloaded the source code.<br>

EFI_SOURCE and EDK_SOURCE are used for the EDK compatibility package ECP when you are building an old module from EDK 1.<br>
The last two are not used for native EDK II at all.<br>


---
@title[Configuration Files - Scripts]
#### <p align="right"><span class="gold" >Configuration Files - Scripts</span></p>
@snap[north span-50 ]
@css[text-yellow]( <br><br><br><br>&nbsp;)
![ubuntu](/assets/images/ubuntu-edksetup.png)
@snapend

@ul[no-bullet]
- @fa[circle gp-bullet-gold]&nbsp;&nbsp;<span style="font-size:01.02em">`edksetup.bat` or `edksetup.sh`</span><br><br><br><br>
- @fa[circle gp-bullet-magenta]&nbsp;&nbsp;<span style="font-size:01.02em">First time use will set up the configuration files:</span> <span style="font-size:0.80em"><br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `Conf/`@color[green](`build_rule`)`.txt` <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `Conf/`@color[#00ffff](`target`)`.txt`  <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `Conf/`@color[yellow](`tools_def`)`.txt` </span><br><br><br>
- @fa[circle gp-bullet-green]&nbsp;&nbsp;<span style="font-size:01.02em">Setup & verify a developer's workspace</span>
@ulend

Note:
edksetup.bat or edksetup.sh
<br>
2.  First time use will set up configuration files<br>
Conf/build_rule.txt (SIMPLE NOTHING TO SAY)<br>
Conf/target.txt   (WILL GO INTO DETAIL NEXT SLIDE)<br>
Conf/tools_def.txt  (WILL GO INTO DETAIL TWO SLIDES)<br>

<br>
3.Setup & verify a developer’s workspace

This slide describes some script files<br>
edksetup  (.bat or .sh)— used to setup and verify your workspace<br>
These also set the environment variables  like the WORKSPACE and EDK_TOOLS_PATH, etc.<br>
When you run these scripts, the files set up your workspace and some configuration files (if they are not already there). <br>
If you run this script file and those files are already there, it won’t do anything.  But if it doesn’t find these three files—
 target.txt, tools_def.txt, build_rule.txt—it will create them from templates.



---?image=/assets/images/slides/Slide82_1.JPG
<!-- .slide: data-transition="none" -->	

@title[Multiple Workspace Environment Variable]
<p align="right"><span class="gold" ><b>Multiple Workspace Environment Variable </b></span></p>


Note:

Package_Path<br>

An update to the EDKII build tools now allows the setting of multiple paths that will be searched when attempting to resolve the location of packages. This new feature allows for more flexibility when designing a tree layout or combining sources from different sources. The new functionality is enabled through the addition of a new environment variable (PACKAGES_PATH).
The PACKAGES_PATH variable is an ordered list of additional search paths using the default path separator of the host OS between each entry. The first path in the list has the highest priority and the last path has the lowest priority. The path specified by the WORKSPACE variable always has the highest search priority over any PACKAGE_PATH entries.
To use this feature, the PACKAGES_PATH environment variable must be set prior to running the edksetup script. The reason for this is that the edksetup script determines the location of the Conf and BaseTools directory location based on the values of the WORKSPACE and PACKAGES_PATH environment variables.
The use of the PACKAGES_PATH environment variable is optional and if it is not defined the build will function like it has in the past.

Why and when:
In this case WORKSPACE is the container for two trees as well as the location of the Build directory. The example assumes the set of code packages for a given platform are contained in the platform directory. While the code packages from the open source repository are contained in the edk2 directory.

When the build tools are run with this configuration the directories will be scanned in the following order to find packages listed in the DSC and FDF files.
 
+++?image=/assets/images/slides/Slide83_1.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 
@title[Multiple Workspace Environment Variable 02]
<p align="right"><span class="gold" >Multiple Workspace Environment Variable </span></p>


Note:

Package_Path<br>

+++?image=/assets/images/slides/Slide84_1.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 
@title[Multiple Workspace Environment Variable 03]
<p align="right"><span class="gold" >Multiple Workspace Environment Variable </span></p>


Note:

Package_Path<br>
 
An update to the EDKII build tools now allows the setting of multiple paths that will be searched when attempting to resolve the location of packages. This new feature allows for more flexibility when designing a tree layout or combining sources from different sources. The new functionality is enabled through the addition of a new environment variable (PACKAGES_PATH).
The PACKAGES_PATH variable is an ordered list of additional search paths using the default path separator of the host OS between each entry. The first path in the list has the highest priority and the last path has the lowest priority. The path specified by the WORKSPACE variable always has the highest search priority over any PACKAGE_PATH entries.
To use this feature, the PACKAGES_PATH environment variable must be set prior to running the edksetup script. The reason for this is that the edksetup script determines the location of the Conf and BaseTools directory location based on the values of the WORKSPACE and PACKAGES_PATH environment variables.
The use of the PACKAGES_PATH environment variable is optional and if it is not defined the build will function like it has in the past.

Why and when:
In this case WORKSPACE is the container for two trees as well as the location of the Build directory. The example assumes the set of code packages for a given platform are contained in the platform directory. While the code packages from the open source repository are contained in the edk2 directory.

When the build tools are run with this configuration the directories will be scanned in the following order to find packages listed in the DSC and FDF files.

+++?image=/assets/images/slides/Slide84_2.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 
@title[Multiple Workspace Environment Variable 04]
<p align="right"><span class="gold" >Multiple Workspace Environment Variable </span></p>


Note:

Package_Path<br>
 
An update to the EDKII build tools now allows the setting of multiple paths that will be searched when attempting to resolve the location of packages. This new feature allows for more flexibility when designing a tree layout or combining sources from different sources. The new functionality is enabled through the addition of a new environment variable (PACKAGES_PATH).
The PACKAGES_PATH variable is an ordered list of additional search paths using the default path separator of the host OS between each entry. The first path in the list has the highest priority and the last path has the lowest priority. The path specified by the WORKSPACE variable always has the highest search priority over any PACKAGE_PATH entries.
To use this feature, the PACKAGES_PATH environment variable must be set prior to running the edksetup script. The reason for this is that the edksetup script determines the location of the Conf and BaseTools directory location based on the values of the WORKSPACE and PACKAGES_PATH environment variables.
The use of the PACKAGES_PATH environment variable is optional and if it is not defined the build will function like it has in the past.

Why and when:
In this case WORKSPACE is the container for two trees as well as the location of the Build directory. The example assumes the set of code packages for a given platform are contained in the platform directory. While the code packages from the open source repository are contained in the edk2 directory.

When the build tools are run with this configuration the directories will be scanned in the following order to find packages listed in the DSC and FDF files.

+++?image=/assets/images/slides/Slide84_3.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 
@title[Multiple Workspace Environment Variable 05]
<p align="right"><span class="gold" >Multiple Workspace Environment Variable </span></p>


Note:

Package_Path<br>
 
An update to the EDKII build tools now allows the setting of multiple paths that will be searched when attempting to resolve the location of packages. This new feature allows for more flexibility when designing a tree layout or combining sources from different sources. The new functionality is enabled through the addition of a new environment variable (PACKAGES_PATH).
The PACKAGES_PATH variable is an ordered list of additional search paths using the default path separator of the host OS between each entry. The first path in the list has the highest priority and the last path has the lowest priority. The path specified by the WORKSPACE variable always has the highest search priority over any PACKAGE_PATH entries.
To use this feature, the PACKAGES_PATH environment variable must be set prior to running the edksetup script. The reason for this is that the edksetup script determines the location of the Conf and BaseTools directory location based on the values of the WORKSPACE and PACKAGES_PATH environment variables.
The use of the PACKAGES_PATH environment variable is optional and if it is not defined the build will function like it has in the past.

Why and when:
In this case WORKSPACE is the container for two trees as well as the location of the Build directory. The example assumes the set of code packages for a given platform are contained in the platform directory. While the code packages from the open source repository are contained in the edk2 directory.

When the build tools are run with this configuration the directories will be scanned in the following order to find packages listed in the DSC and FDF files.




---?image=/assets/images/slides/Slide86_1.JPG
<!-- .slide: data-transition="none" -->	 
@title[Using target.txt]
#### <p align="right"><span class="gold" >Using <span style="color:white;">&nbsp;&nbsp;<font face="Courier New"><b>target.txt</b></font></span></font></span></p>

Note:

Scroll to last slide

+++?image=/assets/images/slides/Slide86_2.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 
@title[Using target.txt 02]
#### <p align="right"><span class="gold" >Using <span style="color:white;">&nbsp;&nbsp;<font face="Courier New"><b>target.txt</b></font></span></font></span></p>

Note:

Scroll to last slide

+++?image=/assets/images/slides/Slide87_1.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 
@title[Using target.txt 03]
#### <p align="right"><span class="gold" >Using <span style="color:white;">&nbsp;&nbsp;<font face="Courier New"><b>target.txt</b></font></span></font></span></p>

Note:

Scroll to last slide

+++?image=/assets/images/slides/Slide88_1.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 
@title[Using target.txt 04]
#### <p align="right"><span class="gold" >Using <span style="color:white;">&nbsp;&nbsp;<font face="Courier New"><b>target.txt</b></font></span></font></span></p>

Note:

Scroll to last slide

+++?image=/assets/images/slides/Slide89_1.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 
@title[Using target.txt 05]
#### <p align="right"><span class="gold" >Using <span style="color:white;">&nbsp;&nbsp;<font face="Courier New"><b>target.txt</b></font></span></font></span></p>

Note:

Scroll to last slide

+++?image=/assets/images/slides/Slide90_1.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 
@title[Using target.txt 06]
#### <p align="right"><span class="gold" >Using <span style="color:white;">&nbsp;&nbsp;<font face="Courier New"><b>target.txt</b></font></span></font></span></p>

Note:

Scroll to last slide

+++?image=/assets/images/slides/Slide91_1.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 
@title[Using target.txt 07]
#### <p align="right"><span class="gold" >Using <span style="color:white;">&nbsp;&nbsp;<font face="Courier New"><b>target.txt</b></font></span></font></span></p>

Note:

You may considering changing these based on your compiler and platform<br>


So let’s go over each of these files, starting with target.txt<br>

target.txt contains six pieces of information that are important for your entire workspace<br>
One - What DSC file represents the platform that you are building? <br>
	So are you trying to build by default a particular platform? For example,  a Lakeport? Or the NT32 emulation. When you type build you do not have to do anything else. You can type build and go on. <br>

Two, the Target – are you trying to build a release build or a debug build?<br>

Three, the Target architecture- are you trying to build IA32, Itanium, X64? We have this in the target.txt file is so you do not have to type in a long build command line. <br>
Most of these have the option on the build command line to give it a target architecture or target, but having it in the target.txt file it allows you to type in minimal on the command line. <br>

The next three are less commonly changed:<br>
  Four, the Path to the tools_def  or tools default file – so if you want to move that to the tools default to a shared location<br>
   Five, the TOOL_CHAIN_TAG – says in the tools default file which section or compiler tools we are using<br>
Six, is how many threads to use to do the build – so if you have a brand-new Core i7 processor to do the build you set this to the number of processors, and that’s how you can get the build down to less than 30 seconds<br>


---
@title[Using Tools_Def.txt 03]
#### <p align="right"> <span class="gold" >&nbsp;&nbsp;&nbsp;&nbsp;Using <span style="color:white;">&nbsp;&nbsp;<font face="Courier New"><b>Tools_Def.txt</b></font></span></font></span></p>

@ul[no-bullet]
- @fa[certificate gp-bullet-magenta]&nbsp;&nbsp;<span style="font-size:01.02em"><b>Paths for compilers, assemblers, and linkers</b></span><span style="font-size:0.80em"><br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-&nbsp;&nbsp;&nbsp;&nbsp;@color[#00ffff](Comes with definitions for all compilers ) </span><br><br>
- @fa[certificate gp-bullet-gold]&nbsp;&nbsp;<span style="font-size:01.02em"><b>Only modify this file when …</b></span><span style="font-size:0.80em"><br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-&nbsp;&nbsp;&nbsp;&nbsp;@color[#00ffff](Tools are installed in a non-default location) <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-&nbsp;&nbsp;&nbsp;&nbsp;@color[#00ffff](Different compilers/tools need to be added)</span><br><br>
- @fa[certificate gp-bullet-ltgreen]&nbsp;&nbsp;<span style="font-size:01.02em"><b>Default values are set by edksetup script</b></span><span style="font-size:0.80em"><br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-&nbsp;&nbsp;&nbsp;&nbsp;@color[#00ffff](Default values will cover most compiler needs)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-&nbsp;&nbsp;&nbsp;&nbsp;@color[#00ffff](If there are problems with the file after editing, just delete)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;@color[#00ffff]( and re-run edksetup &lpar;restores default&rpar;)</span><br>
@ulend


   

Note:
Paths for compilers, assemblers, and linkers <br>
  Comes with definitions for all compilers <br>
Only modify this file when …<br>
   Tools are installed in a non-default location<br>
   Different compilers/tools need to be added<br>
Default values are set by edksetup script<br>
   Default values will cover most compiler needs<br>
   If there are problems with the file after editing, just delete and re-run edksetup (restores default)<br>

---
@title[BaseTools]
#### <p align="right"> <span class="gold" >&nbsp;&nbsp;&nbsp;&nbsp;First Make <span style="color:white;">&nbsp;&nbsp;<font face="Courier New"><b>BaseTools</b></font></span></font></span></p>

@snap[north span-35 ]
@css[text-yellow]( <br>&nbsp;)
@box[bg-blue text-white rounded](<span style="font-size:01.2em" > @color[yellow](`BaseTools`) </span> )
@snapend
<br>
<br>
<p style="line-height:90%">The first step is to make / '`nmake`' the '`BaseTools`' with the host OS & compiler environment.</p>

<span style="font-size:0.8em" >For Linux GCC the command is: </span>

```
  bash$> make -C BaseTools
```
<br>
<span style="font-size:0.8em" >For Windows VS the command is: </span>
```
   > set PYTHON_HOME=C:\Python27
   > edksetup.bat Rebuild
```
   
<br>
Note:
the first step is to make / nmake the BaseTools with the host OS / compiler environment.

For GCC the command is: make -C BaseTools

For Windows the command is: 
-        set PYTHON_HOME=C:\Python27
-        edksetup.bat Rebuild

---?image=assets/images/binary-strings-black2.jpg
@title[Build Process Section]
<br><br><br><br><br>
## <span class="gold"  >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Build Process</span>
<span style="font-size:0.9em" > &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;EDK Build Process and Build Text Files</span>
 
---?image=/assets/images/slides/Slide98_1.JPG
<!-- .slide: data-transition="none" -->	
@title[Build Process Overview]
#### <p align="right"><span class="gold" >Build Process Overview </span></p>

Note:

+++?image=/assets/images/slides/Slide99_1.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 
@title[Build Process Overview 02]
#### <p align="right"><span class="gold" >Build Process Overview </span></p>

Note:

+++?image=/assets/images/slides/Slide100_1.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 
@title[Build Process Overview 03]
#### <p align="right"><span class="gold" >Build Process Overview </span></p>

Note:

+++?image=/assets/images/slides/Slide101_1.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 
@title[Build Process Overview 04]
#### <p align="right"><span class="gold" >Build Process Overview </span></p>

Note:
+++?image=/assets/images/slides/Slide102_1.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 
@title[Build Process Overview 05]
#### <p align="right"><span class="gold" >Build Process Overview </span></p>

Note:
+++?image=/assets/images/slides/Slide103_1.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 
@title[Build Process Overview 06]
#### <p align="right"><span class="gold" >Build Process Overview </span></p>

Note:
+++?image=/assets/images/slides/Slide104_1.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 
@title[Build Process Overview 07]
#### <p align="right"><span class="gold" >Build Process Overview </span></p>

Note:
+++?image=/assets/images/slides/Slide105_1.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 
@title[Build Process Overview 08]
#### <p align="right"><span class="gold" >Build Process Overview </span></p>

Note:

---
@title[Basic Build Steps]
#### <p align="right"><span class="gold" >Basic Build Steps </span></p>



@snap[west span-45 ]
@box[bg-blue text-white](<span style="font-size:01.125em" ><b>Platform</b></span>)
<span style="font-size:0.8em" >&nbsp;<br>&nbsp;<br>&nbsp;<br>&nbsp;<br>&nbsp;<br>&nbsp;<br>&nbsp;<br&nbsp;><br>&nbsp;<br></span>  
@snapend

@snap[east span-45 ]
@box[bg-orange text-white](<span style="font-size:01.125em" ><b>Module</b>)</span>    
<span style="font-size:0.8em" >&nbsp;<br>&nbsp;<br>&nbsp;<br>&nbsp;<br>&nbsp;<br>&nbsp;<br>&nbsp;<br&nbsp;><br>&nbsp;<br></span>  
@snapend
<span style="font-size:0.8em" ><br><br></span>

<div class="left">
<ul style="list-style-type:none" style="line-height:0.8;">
  <li><span style="font-size:0.7em" >1.&nbsp;&nbsp; Navigate (CD) to root of EDK II workspace </span></li>
  <li><span style="font-size:0.7em" >2.&nbsp;&nbsp; Make the `BaseTools`  </span></li>
  <li><span style="font-size:0.7em" >3.&nbsp;&nbsp; Run @color[#c0f0c0]('`edksetup`')  </span></li>
  <li><span style="font-size:0.7em" >4.&nbsp;&nbsp; Run `build`  </span></li>
  <li><span style="font-size:0.7em" >5.&nbsp;&nbsp; Output:  firmware image (FD) file under `Build` directory </span></li>
</ul>
</div>

<div class="right1">
<ul style="list-style-type:none" style="line-height:0.8;">
  <li><span style="font-size:0.7em" >1.&nbsp;&nbsp; Navigate (CD) to root of EDK II workspace </span></li>
  <li><span style="font-size:0.7em" >2.&nbsp;&nbsp; Make the `BaseTools`  </span></li>
  <li><span style="font-size:0.7em" >3.&nbsp;&nbsp; Run @color[#c0f0c0]('`edksetup`')  </span></li>
  <li><span style="font-size:0.7em" >4.&nbsp;&nbsp; @color[yellow](<b>Change to directory with desired `INF` file</b> ) </span></li>
  <li><span style="font-size:0.7em" >5.&nbsp;&nbsp; Run `build`  </span></li>
  <li><span style="font-size:0.7em" >6.&nbsp;&nbsp; Output:  `.EFI` file under `Build` directory </span></li>
</ul>
<span style="font-size:0.5em" >Note: Module `.inf` must be in `.dsc` components </span>
</div>

Note:

Platform:<br>
- Open Terminal prompt
- Navigate to root of EDK II workspace
- Run edksetup
- Edit Conf/target.txt
- Run build
- Output:  firmware image (FD) file under Build directory
<br>
Module:<br>
SAME except - Change to a directory with the proper INF
also NOTE the inf file MUST be a in the components section of the .DSC file


---?image=/assets/images/slides/Slide109.JPG
<!-- .slide: data-transition="none" -->	 
@title[Build Output Location]
#### <p align="right"><span class="gold" >Build Output Location</span></p>

Note:

+++?image=/assets/images/slides/Slide110.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 

@title[Build Output Location 02]
#### <p align="right"><span class="gold" >Build Output Location</span></p>

Note:

+++?image=/assets/images/slides/Slide111.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 

@title[Build Output Location 03]
#### <p align="right"><span class="gold" >Build Output Location</span></p>

Note:

+++?image=/assets/images/slides/Slide112.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 

@title[Build Output Location 04]
#### <p align="right"><span class="gold" >Build Output Location</span></p>

Note:

+++?image=/assets/images/slides/Slide113.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 

@title[Build Output Location 05]
#### <p align="right"><span class="gold" >Build Output Location</span></p>

Note:

+++?image=/assets/images/slides/Slide114.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 

@title[Build Output Location 06]
#### <p align="right"><span class="gold" >Build Output Location</span></p>

Note:

+++?image=/assets/images/slides/Slide115.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 

@title[Build Output Location 07]
#### <p align="right"><span class="gold" >Build Output Location</span></p>

Note:

+++?image=/assets/images/slides/Slide116.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 

@title[Build Output Location 08]
#### <p align="right"><span class="gold" >Build Output Location</span></p>

Note:

+++?image=/assets/images/slides/Slide117_1.jpg
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 

@title[Build Output Location 09]
#### <p align="right"><span class="gold" >Build Output Location</span></p>

Note:

---
@title[EDK II Build Process Stages]
#### <p align="right"><span class="gold" >EDK II Build Process Stages</span></p>

@snap[north-west span-15 fragment]
@css[text-yellow]( <br>&nbsp;)
![ubuntu](/assets/images/AutoGen.png)
@snapend


@snap[north span-65 fragment]
@css[text-yellow](<br><br>&nbsp;)
<p style="line-height:80%"><span style="font-size:0.8em" >Parse meta-data files to generate some C source code files and the make files</span></p>
@snapend


@snap[west span-15 fragment]
![ubuntu](/assets/images/Make.png)
@snapend

@snap[midpoint span-65 fragment]
<p style="line-height:80%"><span style="font-size:0.8em" >Process source code files to create PE32/PE32+/COFF images processed to UEFI format using `$(MAKE)` tool </span></p>
@snapend


@snap[south-west span-15 fragment]
![ubuntu](/assets/images/ImageGen.png)
@css[text-yellow]( <br><br>&nbsp;)
@snapend

@snap[south span-65 fragment]
<p style="line-height:80%"><span style="font-size:0.8em" > Takes the UEFI format files, creates UEFI “FLASH” images, UEFI apps, or UEFI PCI option ROMs <br><br><br></span></p>
@snapend

Note:
Parse meta-data files to generate some C source code files and the make files <Br>

Process source code files to create PE32/PE32+/COFF images processed to UEFI format using $(MAKE) tool<Br>

Takes the UEFI format files, creates UEFI “FLASH” images, UEFI apps, or UEFI PCI option ROMs <Br>


---?image=/assets/images/slides/Slide123.JPG
<!-- .slide: data-transition="none" -->	 

@title[EDK II Build AutoGen Stage]
#### <p align="right"><span class="gold" >EDK II Build: AutoGen Stage</span></p>

Note:
Build –p OvmfPkg/OvmfX64Pkg.dsc<br>
Parse – .DSC, .DEC, .FDF, .INF<br>
DSC File … <br>
Points to own .DEC & .FDF & .INF<br>
Points to other packages (.DEC) and Modules (.INF)<br>

ONE DSC per Build command<br>

DSC points to all the components, Libraries, PCDs, etc needed to build a PACKAGE<br>

+++?image=/assets/images/slides/Slide124.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 
@title[EDK II Build AutoGen Stage 02]
#### <p align="right"><span class="gold" >EDK II Build: AutoGen Stage</span></p>

Note:
Build –p OvmfPkg/OvmfX64Pkg.dsc<br>
Parse – .DSC, .DEC, .FDF, .INF<br>
DSC File … <br>
Points to own .DEC & .FDF & .INF<br>
Points to other packages (.DEC) and Modules (.INF)<br>

ONE DSC per Build command<br>

DSC points to all the components, Libraries, PCDs, etc needed to build a PACKAGE<br>

---
@title[EDK II Build Make Stage]
#### <p align="right"><span class="gold" >EDK II Build: Make Stage</span></p>

@snap[north span-65 ]
@css[text-yellow](<br>&nbsp;)
@box[ bg-green text-white rounded](<span style="font-size:0.9em" >Uses assemblers/compilers/linkers to generate PE32/PE32+ COFF image file<br></span>)
@snapend

@snap[midpoint span-90 ]
@box[ bg-blue text-white rounded](<span style="font-size:0.9em" >Uses `ImageGen` tools to modify PE32/PE32+/COFF image file<br>Creates UEFI file &lpar;EFI_IMAGE_SECTION_HEADER structure&rpar;<br></span>)
@snapend

@snap[south-west span-20 ]
@css[text-black](&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;)
![GenFw](/assets/images/GoldCircle.png)
@css[text-black](<br>&nbsp;)
@snapend


@snap[south span-20 ]
@css[text-black](&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;)
![GenFw](/assets/images/GoldCircle.png)
@css[text-black](<br>&nbsp;)
@snapend


@snap[south-west span-25 ]
@css[text-black](&nbsp;&nbsp; `GenFW`<br><br><br><br>)
@snapend


@snap[south span-25 ]
@css[text-black](`GenFds`<br><br><br><br>)
@snapend

Note:
Uses assemblers, compilers and linkers commonly available to generate a PE32/PE32+/COFF image file <BR>
Uses the ImageGen tools modify the PE32/PE32+/COFF image file to create an UEFI file (EFI_IMAGE_SECTION_HEADER structure)<BR>
GenFw tool must specify the component type derived from the INF meta-data’s Module Type statement <BR>
GenFds application initiates the third stage of the EDK II build <BR><BR>


The build process stages<BR>
The first stage is the autogen stage,which parses the meta-data files: the DEC DSC and INF files. It parses the meta-data files to generate your autogen.C and autogen.h files. <BR>
Additionally we generate the makefiles.  There will be one makefile for each INF file we to be compiled and an additional makefile for the overall process. (The whole build itself gets one makefile.)<BR>

The second stage, the binary makes stage, processes the source code. Now we use the makefiles and your source code to generate the images which are then processed into UEFI format images using the make tool. We end up with .EFI files. <BR>

third and final stage, the ImageGen stage, we take these UEFI formatted files and create the flash image, or leave them as UEFI applications, or perhaps make UEFI-compliant PCI option ROMs. <BR>
This last stage is also configurable.<BR>




---?image=/assets/images/slides/Slide98.jpg

@title[EDK II Build Image GEN Stage]
#### <p align="center"><span class="gold" >EDK II Build: ImageGen Stage</span></p>

@div[left-50]
<br><br>
<ul>
  <li>Builds one image for each specified firmware volume (FV) <br> <br></li>
  <li>The FDF file supports all syntax available in the PI Specification Vol. 3</li>
</ul>
@divend
@div[right-50]
<br>
@divend


Note:
Builds one image for each specified firmware volume (FV) <BR>

The FDF file supports all syntax available in the PI Specification Vol. 3 <BR>
<BR>
the modular build process allows this stage to be changed for different outputs<BR>
Example: how to combine a UEFI Driver & Legacy PCI OpROM into a single binary image for a PCIe card? See next slide …<BR>

third and final stage, the ImageGen stage, we take these UEFI formatted files and create the flash image, or leave them as UEFI applications, or perhaps make UEFI-compliant PCI option ROMs. <BR>
This last stage is also configurable.<BR>

---?image=/assets/images/slides/Slide131_1.JPG
<!-- .slide: data-transition="none" -->	 
@title[Build Flow For OpROM]
#### <p align="right"><span class="gold" >Build Flow For OpROM</span></p>

Note:


+++?image=/assets/images/slides/Slide132_1.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 

@title[Build Flow For OpROM 02]
#### <p align="right"><span class="gold" >Build Flow For OpROM</span></p>

Note:



---
@title[Build Command]
<br>
####  <p align="center"><span class="gold" >&nbsp;&nbsp;The Build Command</span></p>
<br>
- Accepts command line arguments to support scripted builds <br>
- Overrides most settings found in target.txt <br>|
- Overrides DSC with a minimal INF build <br>|
- Overrides some settings in DSC file (.FDF) <br>|
- Choose settings from the FDF file (ROMIMAGE, FVIMAGE)<br> |
- Choose $(make) options (silent, verbose, quiet) |



Note:

THIS IS A BUILD SLIDE - Press Right arrow <br>
Advanced building usage The build tool is the main interface to the complete build process. This is a compiled tool downloaded as part of EDK II, or built if you are running on a non-Windows system. <br>
It runs the rest of the build tools for you<br>
There are command-line tools that are designed for the scripting of the build.  For example, in our group, we scripted it to run the build every night and send out a report. This way so we can see if something has been checked in that could cause the build to break<br>
The goal is to enable enough features to script the build successfully, not to enable absolutely every feature. You can override most of the settings of the target.txt file. For example, you can change the architecture from high x64 to IA64. <br>
<br>
You can change which DSC file you are building. <br>
You can change the target.txt for the toolchain. <br>
You can change the thread count to build with four threads, not one thread, etc.<br>
You can override the DSC and Say “please only build my INF file”.<br>
You can change which FDF file you want for the build.<br>
From inside the FDS file you can change the ROMIMAGE or FVIMAGE settings<br>
You can change the messaging output from the make settings for instance,  making it silent, or verbose, or quiet.<br>
Outside of changing the number of the threads used – if you are building the same code—unlike EDK, we don’t see a dramatic increase in the amount of time required.  For example, if you are letting it output to the screen, the text outputting does not have the same level of impact as an EDK text output.<br>
In advanced build usage you can type build –h, or build –help, and it will give you this information. Although there are more options that you can list, they are used less frequently.<br>

---?image=/assets/images/slides/Slide135.JPG
<!-- .slide: data-transition="none" -->	 
@title[Using EDK II build Command]
#### <p align="right"><span class="gold"  >Using EDK II</span> <span style="color:white;">&nbsp;&nbsp;<font face="Courier New"><b>build</b></font></span><span class="gold"  >&nbsp;&nbsp;Command </span></p>

Note:

This is not the complete list … run build --help from the command prompt to see all of the build options

+++?image=/assets/images/slides/Slide136.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 
 
@title[Using EDK II build Command 02]
#### <p align="right"><span class="gold"  >Using EDK II</span> <span style="color:white;">&nbsp;&nbsp;<font face="Courier New"><b>build</b></font></span><span class="gold"  >&nbsp;&nbsp;Command </span></p>

Note:

This is not the complete list … run build --help from the command prompt to see all of the build options


+++?code=sample/buildoutput.txt&lang=shell&title=<p align="right"><span style="color:white;"><font face="Courier New"><b>build -h</b></font></span><span class="gold"  >&nbsp;&nbsp;Command </span></p>

@[1,5-25](options to overide .DSC, .INF and .FDF and Target.txt settings)
@[60,65-74](Using the -Y and -y options for Reports)

Note:
output from 
Build -h command

---?image=/assets/images/slides/Slide138.JPG
@title[Using Build-Y Reports]
#### <p align="right"><span class="gold"  >Using </span> <span style="color:white;">&nbsp;&nbsp;<font face="Courier New"><b>build -Y</b></font></span><span class="gold"  >&nbsp;&nbsp;for Reports </span></p>

Note:
build  –Y  PCD,  LIBRARY, FLASH, DEPEX, BUILD_FLAGS, FIXED_ADDRESS <Br>

-Y REPORTTYPE<Br>
--report-type=REPORTTYPE<Br>

Flags that control the type of build report to generate.  Must be one of: [PCD, LIBRARY, FLASH, DEPEX, BUILD_FLAGS, FIXED_ADDRESS, EXECUTION_ORDER].<Br>

To specify more than one flag, repeat this option on the command line and the default flag set is [PCD, LIBRARY, FLASH, DEPEX, BUILD_FLAGS, FIXED_ADDRESS]<Br>

EXEC ORDER is  best done on the Host build machine

+++
@title[Using Build-Y Reports Example]
#### <p align="right"><span class="gold"  >Using </span> <span style="color:white;">&nbsp;&nbsp;<font face="Courier New"><b>build -Y</b></font></span><span class="gold"  >&nbsp;&nbsp;for Reports </span></p>

- Scroll through examples of reports from the `Build -Y` commands

Note:
TBD


+++?code=sample/Reports/depex.log&lang=shell&title=<p align="right"><span style="color:white;"><font face="Courier New"><b>build -Y DEPEX</b></font></span><span class="gold"  >&nbsp;&nbsp;Command </span></p>

Note:

+++?code=sample/Reports/pcd.log&lang=shell&title=<p align="right"><span style="color:white;"><font face="Courier New"><b>build -Y PCD</b></font></span><span class="gold"  >&nbsp;&nbsp;Command </span></p>

Note:


+++?code=sample/Reports/library.log&lang=shell&title=<p align="right"><span style="color:white;"><font face="Courier New"><b>build -Y LIBRARY</b></font></span><span class="gold"  >&nbsp;&nbsp;Command </span></p>

Note:

+++?code=sample/Reports/flash.log&lang=shell&title=<p align="right"><span style="color:white;"><font face="Courier New"><b>build -Y FLASH</b></font></span><span class="gold"  >&nbsp;&nbsp;Command </span></p>

Note:

+++?code=sample/Reports/build_flag.log&lang=shell&title=<p align="right"><span style="color:white;"><font face="Courier New"><b>build -Y BUILD_FLAGS</b></font></span><span class="gold"  >&nbsp;&nbsp;Command </span></p>

Note:

+++?code=sample/Reports/fixed_address.log&lang=shell&title=<p align="right"><span style="color:white;"><font face="Courier New"><b>build -Y FIXED_ADDRESS</b></font></span><span class="gold"  >&nbsp;&nbsp;Command </span></p>

Note:

+++?code=sample/Reports/Log_DispatchOrder.log&lang=shell&title=<p align="right"><span style="color:white;"><font face="Courier New"><b>build -Y EXECUTION_ORDER</b></font></span><span class="gold"  >&nbsp;&nbsp;Command </span></p>
- Report.html is generated on the host build machine - pop up this in the Browser window.

Note:
This is best done on the Host build machine




---
@title[Build Tool Binaries]
#### <p align="center"><span class="gold"  >Build Tool Binaries</span></p>


<table id="recTable">
	<tr>
		<td bgcolor="#0071c5"><p align="center"><span style="font-size:0.85em" >&nbsp;<b>Utility</b></span></p></td>
		<td bgcolor="#0071c5"><p align="center"><span style="font-size:0.85em" >&nbsp;<b>Description</b></span></p></td>
	</tr>
	<tr>
		<td bgcolor="#00b0f0"><p style="line-height:70%"><span style="font-size:0.75em" >`Build.exe`</span></p></td>
		<td bgcolor="#00b0f0"><p style="line-height:50%"><span style="font-size:0.65em" >Tool is written in Python and calls `AutoGen.exe`, then it calls `$(MAKE) –f  Makefile.out`, and finally, it calls `GenFds.exe`</span></p></td>
	</tr>
	<tr>
		<td bgcolor="#fdb813"><p style="line-height:50%"><span style="font-size:0.75em" >`EfiRom.exe`&nbsp;</span></p></td>
		<td bgcolor="#fdb813"><p style="line-height:50%"><span style="font-size:0.65em" >used to build an option ROM image&nbsp;</span></p></td>
	</tr>
	<tr>
		<td bgcolor="#00b0f0"><p style="line-height:50%"><span style="font-size:0.75em" >`PatchModule.exe`&nbsp;</span></p></td>
		<td bgcolor="#00b0f0"><p style="line-height:50%"><span style="font-size:0.65em" >used to patch a binary module that has a PCD of type PATCHABLE_IN_MODULE&nbsp;</span></p></td>
	</tr>
	<tr>
		<td bgcolor="#fdb813"><p style="line-height:50%"><span style="font-size:0.75em" >`PatchPlatform.exe`&nbsp;</span></p></td>
		<td bgcolor="#fdb813"><p style="line-height:50%"><span style="font-size:0.65em" >used to modify either the PCD Database or the VPD settings in a flash device image&nbsp;</span></p></td>
	</tr>

</table>

Note:
The build tool binary files <br>
There are four main build tools that we expect people to use frequently<br>
Everybody will use Build.exe. This is the tool that runs the entire build. <br>
EfiRom.exe is good for building EFI ROM images. It is possible to configure build.exe to call EfiRom.exe, but this is not required.<br>
The patch programs PatchModule and PatchPlatform are used for changing PCD values that were defined as patchable. <br>
When you make a PCD it is possible to make it patchable. <br>
The following instructions show you how to do the patching.<br>

<br>
 All of the tools listed here can be run manually.<br>

<br>
Other tools run as part of these 4






---
<!---  END OF SLIDES
-->

@title[Summary]
<br>
##### <p align="center"<span class="gold"   >Summary </span></p><br>

<!---  Add bullets using https://fontawesome.com/cheatsheet certificate
-->
 
 @fa[certificate gp-bullet-green]<span style="font-size:0.9em">&nbsp;&nbsp;Define EDK II </span><br><br>
 @fa[certificate gp-bullet-cyan]<span style="font-size:0.9em">&nbsp;&nbsp;Describe EDK II’s elements including file extensions,<br> 
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;directories, modules, packages, and libraries </span><br><br>
 @fa[certificate gp-bullet-yellow]<span style="font-size:0.9em">&nbsp;&nbsp;Explain the EDK II build process </span> <br><br>
 @fa[certificate gp-bullet-magenta]<span style="font-size:0.9em">&nbsp;&nbsp;Explain the Build tools</span> 




---?image=assets/images/gitpitch-audience.jpg
@title[Questions]
<BR>
![Questions](/assets/images/questions.JPG =10x) 


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
