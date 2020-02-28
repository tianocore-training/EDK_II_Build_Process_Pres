---?image=assets/images/gitpitch-audience.jpg
@title[Title-UEFI Overview]
<br><br><br>
<br><br>
## <span class="gold"   >&nbsp;UEFI & EDK II Training</span>

####  &nbsp;&nbsp;EDK II Build Process
<br>
<span style="font-size:0.75em" >&nbsp;&nbsp;&nbsp;<a href='http://www.tianocore.org'>tianocore.org</a></span>


Note:
  PITCHME.md for UEFI / EDK II Training EDK II Build Process

  Copyright (c) 2020, Intel Corporation. All rights reserved.<BR>

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
#### <p align="center"><span class="gold" > Philosophy of EDK II </span></p>

@snap[north-west span-35]
<br>
<br>
<br>
@box[bg-royal text-white  waved  fragment](<b>Support UEFI & PI needs</b><br><br>)
@snapend

@snap[north span-35]
<br>
<br>
<br>
@box[bg-green text-white waved fragment](<b>Separate tool & source code</b><br><br>)
@snapend

@snap[north-east span-35]
<br>
<br>
<br>
@box[bg-blue text-white waved fragment](<b>Package Definition file: DEC</b><br>)
@snapend

@snap[south-west span-35]
@box[bg-yellow text-blue  waved fragment](<b>Flash Mapping Tool</b><br><br>)
<br>
<br>
@snapend

@snap[south span-35]
@box[bg-lt-orange text-white waved fragment](<b>Move as much code to C</b><br><br>)
<br>
<br>
@snapend

@snap[south-east span-35]
@box[bg-purple-pp text-white waved fragment](<b>Open source <br>EDK II on tianocore.org</b><br>)
<br>
<br>
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



---?image=/assets/images/slides/Slide5.JPG
@title[Implementation of EDK II]
#### <p align="right"><span class="gold" > Implementation of EDK II </span></p>


@snap[west span-90]
@box[bg-blue-trans text-white  rounded  fragment](<Br><span style="font-size:01.25em" >@color[yellow](<b>EDK II == UEFI / PI Implementation</b>)</span><br><br>)
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
		  

---?image=/assets/images/slides/Slide8.JPG

@title[EDK II Directory Structure]
<p align="right"><span class="gold" >@size[1.1em](<b> EDK II Directory Structure  </b>)</span><span style="font-size:0.75em;" >  </span></p>

@snap[north-east span-65]
<br>
<br>
<br>
<br>
<ul style="list-style-type:disc; line-height:0.75;">
 <li class="fragment"><span style="font-size:0.75em;" >Package concept for each EDK II sub-directory  </span></li>
 <li class="fragment"><span style="font-size:0.75em;" >Platforms are contained in an EDK II package  </span></li>
 <li class="fragment"><span style="font-size:0.75em;" >EDK II build process reflects the package  </span></li>
 <li class="fragment"><span style="font-size:0.75em;" >Concept of "Work Space" :<br>&nbsp;&nbsp; <font face="Consolas">$HOME/src/edk2-ws/edk2</font>  </span></li>
</ul>
@snapend


@snap[south-east span-39 fragment]
@box[bg-grey-15 text-white  my-box-pad2  ](<p style="line-height:35%" align="left" ><span style="font-size:0.45em; font-family:Consolas;" >&nbsp;bash$&nbsp;  cd $HOME/src/edk2-ws/edk2<br>&nbsp;bash$&nbsp;  . edksetup.sh<br>&nbsp;bash$&nbsp;  make –C BaseTools/<br>&nbsp;Bash$&nbsp;  build<br>&nbsp;</span></p>)
<br>
@snapend

Note:
EXPLAINS WHAT IS IN THE DIRECTORY

Coding explains Workspace Build commands

- EDK II build process reflects the package structure … the build command specifies the .DSC file for a platform
- These directories are from the github edk2 project

---
@title[Organization Directory Structure]
<p align="right"><span class="gold" >@size[1.1em](<b>Organization Directory Structure</b>)</span></span></p>


@snap[north span-50 ]
<br>
<br>
@box[bg-grey-15 text-white rounded my-box-pad2  ](<p style="line-height:60%"><span style="font-size:0.9em;" ><b>&nbsp;</b><br><br>&nbsp;</span></p>)
@box[bg-grey-15 text-white rounded my-box-pad2  ](<p style="line-height:60%"><span style="font-size:0.9em;" ><b>&nbsp;</b><br><br>&nbsp;</span></p>)
@box[bg-grey-15 text-white rounded my-box-pad2  ](<p style="line-height:60%"><span style="font-size:0.9em;" ><b>&nbsp;</b><br><br>&nbsp;</span></p>)
@box[bg-grey-15 text-white rounded my-box-pad2  ](<p style="line-height:60%"><span style="font-size:0.9em;" ><b>&nbsp;</b><br><br>&nbsp;</span></p>)
@snapend


@snap[north-west span-30 ]
<br>
<br>
@box[bg-gold2 text-white rounded my-box-pad2  ](<p style="line-height:60% "><span style="font-size:0.9em;" ><b>Common</b><br><br>&nbsp;</span></p>)
@box[bg-gold2 text-white rounded my-box-pad2  ](<p style="line-height:60%"><span style="font-size:0.9em;" ><b>Platform</b><br><br>&nbsp;</span></p>)
@box[bg-gold2 text-white rounded my-box-pad2  ](<p style="line-height:60%"><span style="font-size:0.9em;" ><b>Board</b><br><br>&nbsp;</span></p>)
@box[bg-gold2 text-white rounded my-box-pad2  ](<p style="line-height:60%"><span style="font-size:0.9em;" ><b>Silicon</b><br><br>&nbsp;</span></p>)
@snapend



@snap[north-east span-67 ]
<br>
<br>
@css[text-white fragment](<p style="line-height:60%" align="left" ><span style="font-size:0.7em;" >&bull; No direct HW requirements<br><br><br></span></p>)
@css[text-white fragment](<p style="line-height:60%" align="left" ><span style="font-size:0.7em;" >&bull; Enable a specific <br>&nbsp;&nbsp;&nbsp;platform's capabilities <br><br><br> </span></p>)
@css[text-white fragment](<p style="line-height:60%" align="left" ><span style="font-size:0.7em;" >&bull; Board specific code <br><br><br><br> </span></p>)
@css[text-white fragment](<p style="line-height:60%" align="left" ><span style="font-size:0.7em;" >&bull; Hardware specific code </span></p>)
@snapend


Note:
The architecture makes use of four primary classifications of code that are generally instantiated in different EDK II packages.
- Common (EDK II) is code that does not have any direct HW requirements other than the basics required to execute machine code on the processor (stack, memory, IA registers, etc).
   - Producer(s): TianoCore.org


- Platform defines the actions needed to enable a specific platform's capabilities. In this architecture, capabilities are divided into mandatory and advanced features. Mandatory features are enabled in stages prior to Stage VI. Advanced features are enabled in Stage VI and later.
  - Minimum Platform Producer(s): TianoCore.org
  - Advance Feature Producer(s): TianoCore.org, OEM, BIOS vendor
  - Board packages contains board specific code for one or more motherboards.
  - Producer(s): Device manufacturer, BIOS vendor, Board user

- Silicon, also often called hardware code, has some tie to a specific class of physical hardware. Sometimes governed by industry standards, sometimes proprietary. Silicon or hardware code is usually not intended to have multiple implementations for the same hardware.
  - Producer(s): Silicon vendor


---
@title[Open Source EDK II Workspace - directories]
<p align="right"><span class="gold" >@size[1.1em](<b>Open Source EDK II Workspace<br> - directories</b>)</span></span></p>

@snap[north-west span-50 ]
<br>
<br>
@box[bg-black text-white rounded my-box-pad2  ](<p style="line-height:60% "><span style="font-size:0.9em;" ><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>&nbsp;</span></p>)
@snapend


@snap[north span-30 ]
<br>
<br>
@box[bg-gold2 text-white rounded my-box-pad2 fragment ](<p style="line-height:60% "><span style="font-size:0.9em;" ><b>Common</b><br><br>&nbsp;</span></p>)
@box[bg-gold2 text-white rounded my-box-pad2 fragment ](<p style="line-height:60%"><span style="font-size:0.9em;" ><b>Platform</b><br><br>&nbsp;</span></p>)
@box[bg-gold2 text-white rounded my-box-pad2 fragment ](<p style="line-height:60%"><span style="font-size:0.9em;" ><b>Board</b><br><br>&nbsp;</span></p>)
@box[bg-gold2 text-white rounded my-box-pad2 fragment ](<p style="line-height:60%"><span style="font-size:0.9em;" ><b>Silicon</b><br><br>&nbsp;</span></p>)
@snapend



@snap[north-west span-60 ]
<br>
<br>
<p style="line-height:50%" align="left" ><span style="font-size:0.5em; font-family:Consolas;">
&nbsp;MyWorkSpace/<br>&nbsp;&nbsp;
@color[yellow](edk2)/<br>&nbsp;&nbsp;&nbsp;&nbsp;
  - "@color[#FFC000](<font face="Arial">edk2 Common</font>)"<br>&nbsp;&nbsp;
@color[yellow](edk2-platforms)/<br>&nbsp;&nbsp;&nbsp;&nbsp;
  Platform/ "@color[#FFC000](<font face="Arial">Platform</font>)"<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
     Intel/<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
       MinPlatformPkg/<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
          BoardX/ “@color[#FFC000](<font face="Arial">Board</font>)”<br>&nbsp;&nbsp;&nbsp;&nbsp;
  Silicon/ "@color[#FFC000](<font face="Arial">Silicon</font>)"<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
     Intel/<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
       MinPlatformPkg/<br>&nbsp;&nbsp;
@color[yellow](edk2-non-osi)/<br>&nbsp;&nbsp;&nbsp;&nbsp;
  Silicon/<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
     Intel/<br>&nbsp;&nbsp;
@color[yellow](FSP)/"@color[#FFC000](<font face="Arial">Silicon</font>)"<br>&nbsp;&nbsp;&nbsp;&nbsp;
   . . ./<br>&nbsp;&nbsp;
</span></p>
@snapend


Note:
The build process creates
   this directory -> Build/
MyWorkSpace – directory from the “git” of repositories

Build –p .dsc from the BOARD Directory

The architecture is designed to support a maintainer ownership model. For example, board developers should not directly modify (fork) the platform, silicon, or common code. More details on conventional usage of the package classifications can be found in supplemental literature from UEFI Forum, TianoCore.org, and others.


---
@title[ EDK II Open Board Tree Structure]
<p align="right"><span class="gold" >@size[1.1em](<b>EDK II Open Board Tree Structure  </b>)</span><br>
<span style="font-size:0.75em;" > - KabyLake w/ FSP </span></p>

@snap[north-west span-70 ]
<br>
<br>
@box[bg-black text-white rounded my-box-pad2  ](<p style="line-height:60% "><span style="font-size:0.9em;" ><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>&nbsp;</span></p>)
@snapend



@snap[north-west span-70 ]
<br>
<br>
<p style="line-height:50%" align="left" ><span style="font-size:0.5em; font-family:Consolas;">
&nbsp;&nbsp;
@color[yellow](edk2)/  <a href="https://github.com/tianocore/edk2"> github.com/edk2</a><br>&nbsp;&nbsp;&nbsp;&nbsp;
. . .<br>&nbsp;&nbsp;
@color[yellow](edk2-platforms)/  <a href="https://github.com/tianocore/edk2-platforms"> github.com/edk2-platforms</a><br>&nbsp;&nbsp;&nbsp;&nbsp;
  Platform/ <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
     Intel/<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
       AdvancedFeaturePkg/<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
       KabylakeOpenBoardPkg/<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
          KabylakeRvp3/ <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
       MinPlatformPkg/<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
       Vlv2TbltDevicePkg/<br>&nbsp;&nbsp;&nbsp;&nbsp;
  Silicon/ <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
     Intel/<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
       KabylakeSiliconPkg/<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
       &nbsp;. &nbsp;. &nbsp;./<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
       Vlv2DeviceRefCodePkg/<br>&nbsp;&nbsp;
@color[yellow](edk2-non-osi)/<a href="https://github.com/tianocore/edk2-non-osi/tree/devel-MinPlatform">github.com/edk2-non-osi</a><br>&nbsp;&nbsp;&nbsp;&nbsp;
  Silicon/<br>&nbsp;&nbsp;
@color[yellow](FSP)/<a href="https://github.com/IntelFsp/FSP">github.com/Intel/FSP</a><br>&nbsp;&nbsp;&nbsp;&nbsp;
   KabylakeFspBinPkg/<br>&nbsp;&nbsp;
</span></p>
@snapend



@snap[north-east span-60 fragment ]
<br>
<br>
<p style="line-height:50%" align="left" ><span style="font-size:0.5em; font-family:Consolas;">
@color[#A8ff60](&larr;)&nbsp;@color[#FFC000](<font face="Arial">Common</font>)<br><br>
<br>
<br>
<br>
<br>
@color[#A8ff60](&larr;)&nbsp;@color[#FFC000](<font face="Arial">Platform</font>)<br>
@color[#A8ff60](&larr;)&nbsp;@color[#FFC000](<font face="Arial">Board</font>) <br>
@color[#A8ff60](&larr;)&nbsp;@color[#FFC000](<font face="Arial">Common</font>)<br>
<br>
<br>
<br>
@color[#A8ff60](&larr;)&nbsp;@color[#FFC000](<font face="Arial">Silicon</font>)<br>
<br>
<br>
<br>
<br>
<br>
@color[#A8ff60](&larr;)&nbsp;@color[#FFC000](<font face="Arial">Silicon</font>)<br>&nbsp;&nbsp;
</span></p>
@snapend


Note:
This is an example of the MinPlatform for the Intel Architecture (IA)
With Kabylake and  Vlv2TbltDevicePkg (Minnowboard MAX) as examples


Notice the 3 different repositories for the different sources align similarly to the COMMON, PLATFORM, BOARD & SILICON layout

Not shown is the edk2 repository since this should always be considered as common



---?image=/assets/images/slides/Slide12.JPG
@title[Directory Structure - Real Platform]
<p align="right"><span class="gold" >@size[1.1em](<b>Directory Structure - Real Platform   </b>)</span><span style="font-size:0.75em;" >  </span></p>

@snap[north-east span-20 ]
<br>
<br>
<br>
@box[bg-grey-15 text-white  my-box-pad2  ](<p style="line-height:30% "><span style="font-size:0.5em;" ><br><br><br><br>&nbsp;</span></p>)
@snapend

@snap[north-east span-18 ]
<br>
<br>
<p style="line-height:40%" align="left" ><span style="font-size:0.5em; font-family:Consolas;"><br>
&nbsp;&nbsp;&nbsp;&nbsp;@color[yellow](<b><u>Key</u></b>)<br>
@color[#75deFF](slicon/Chipset)<br>
@color[cyan](Platform)<br>
@color[yellow](Repository)<br>
</span></p>
@snapend

@snap[north-west span-70 ]
<br>
<br>
<p style="line-height:80%"><span style="font-size:0.9em" >@color[#87E2A9](Open Source Directories)</span></p>

<p style="line-height:50%" align="left" ><span style="font-size:0.5em; font-family:Consolas;">
MyWorkSpace /<br>&nbsp;&nbsp;
Build /<br>&nbsp;&nbsp;
@color[yellow](edk2)/  <br>&nbsp;&nbsp;&nbsp;&nbsp;
<font face="Arial"><i>- "edk2 common Source"</i></font><br>&nbsp;&nbsp;
@color[yellow](edk2-platforms)/ <br>&nbsp;&nbsp;&nbsp;&nbsp;
  Platform/ Intel <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
       AdvancedFeaturePkg/<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
       @color[cyan](Vlv2TbltDevicePkg) /<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<font face="Arial"><i>- "All platform modules"</i></font><br>&nbsp;&nbsp;&nbsp;&nbsp;
  Silicon/ Intel <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
       @color[#75deFF](Vlv2DeviceRefCodePkg)/<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
	     @color[#75deFF](ValleyView2Soc) / <br>&nbsp;&nbsp;
@color[yellow](edk2-non-osi)/<br>&nbsp;&nbsp;&nbsp;&nbsp;
  Silicon/ Intel <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
    @color[#75deFF](Vlv2SocBinPkg)<br>
<br>
<font face="Arial">
@size[1.1em](Non- MinPlatformPkg &  Non - FSP)
</font><br>&nbsp;&nbsp;&nbsp;&nbsp;
</span></p>
@snapend



Note:
Open Source Directory COLUMN 1
Platform and Silicon Directory COLUMN 2

Minnowboard MAX (Native EDK II) is the example directory structure


---?image=/assets/images/slides/Slide13.JPG
@title[Modules]
####  <p align="right"><span class="gold" > Modules</span></p>
@css[text-white fragment](<b> Smallest separate object compiled in EDK II</b>)
<br>
<br>
<br>
<br>
@css[text-yellow fragment](<b>@color[yellow](Compiles to)<br>@color[yellow](<font face="Consolas">.EFI</font> File)</b>)


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


---?image=/assets/images/slides/Slide14.JPG

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
@box[bg-blue text-white rounded](<span style="font-size:02.5em" ><font face="Consolas">MdePkg</font></span>#Includes files and libraries for Industry Standard Specifications<br><br>)
@snapend

@snap[east span-45 fragment]
@box[bg-orange text-white rounded ](<span style="font-size:02.5em" ><font face="Consolas">MdeModulePkg</font></span>#Modules only definitions from the Industry Standard Specification defined in the MdePkg)
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
@title[Additional Package Examples: ]
#### <p align="right"><span class="gold" >Additional EDK II Package Examples:</span></p>
<br>
@ul[no-bullet]
- @fa[certificate gp-bullet-gold]&nbsp;&nbsp;<span style="font-size:01.2em"><b>Platforms</b></span><br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;@color[#00ffff](<font face="Consolas">EmulatorPkg</font>) &nbsp;&nbsp;&nbsp; & &nbsp;&nbsp;&nbsp; @color[#00ffff](<font face="Consolas">OvmfPkg</font>)</span><br><br><br>
- @fa[certificate gp-bullet-magenta]&nbsp;&nbsp;<span style="font-size:01.2em"><b>Chipset/Processor</b></span><br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;@color[#00ffff](<font face="Consolas">IntelSiliconPkg</font>) &nbsp;&nbsp;&nbsp;& &nbsp;&nbsp;&nbsp;@color[#00ffff](<font face="Consolas">KabylakeSiliconPkg</font>)</span><br><br><br>
- @fa[certificate gp-bullet-green]&nbsp;&nbsp;<span style="font-size:01.2em"><b>Functionality</b></span><br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;@color[#00ffff](<font face="Consolas">ShellPkg</font>)&nbsp;&nbsp;&nbsp; & &nbsp;&nbsp;&nbsp; @color[#00ffff](<font face="Consolas">NetworkPkg</font>)</span><br>
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



---?image=/assets/images/slides/Slide17.JPG
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

+++?image=/assets/images/slides/Slide18.JPG
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

+++?image=/assets/images/slides/Slide19.JPG
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

+++?image=/assets/images/slides/Slide20.JPG
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



---?image=/assets/images/slides/Slide_Libraries.jpg
@title[Example-Library-Debuglib]
#### <p align="right"><span class="gold"  >Example - Library</span><span style="color:white;">&nbsp;&nbsp;<font face="Consolas"><b>Debuglib</b> </font></span></p>


@snap[north-west span-25 fragment]
<br>
<br>
<br>
@box[bg-lt-orange-trans text-black ](<b><font face="Consolas">NULL</font></b> <br><br><br><br><br><br><br><br><br>)
@snapend

@snap[north span-40 fragment]
<br>
<br>
<br>
@box[bg-blue-trans text-black ](<b>Robust Functions </b><br>Port 80<br>Serial Output<br>Data Hub<br>etc. . .<br><br><br><br><br>)
@snapend



Note:
DebugLib library class name <br>
The debugging characteristics might be different during the different boot up phases.<br>
SEC PEI – Null or no code but all reffernces will be resolved with the BaseDebugLibNull Implementation of the DebugLib<br>
DXE-BDS – Code to output to serial port/ port 80 codes<br>
Library Class names can be linked with different Processor resolutions (IA32/ x64) & different boot phases<br>


---?image=/assets/images/slides/Slide22.JPG

@title[PCD Title page]
#### <p align="right"><span class="gold" >Platform Configuration Database (PCD)</span></p>



Note:
Defining database - like global variables <br>

Many components of a database to help fine tune the BIOS or Firmware - build & runtime


---
@title[Platform Configuration Database-Goals]
#### <p align="right"><span class="gold" >Platform Configuration Database (PCD)</span></p>
@box[bg-royal text-white rounded my-box-pad2 ](<span style="font-size:01.5em" >Goals</span>)



@snap[west span-45 ]
@box[bg-brick text-white rounded fragment](<span style="font-size:01.125em "><font color="yellow"><b>Define module parameters</b></font></span><br> Store module / platform configurations)
<br>
@snapend

@snap[east span-45 ]
@box[bg-brick text-white rounded fragment](<span style="font-size:01.125em " ><font color="yellow"><b>Reduce source edits</b></font></span><Br><br> Maximize module reuse across platforms)
<br>
@snapend

@snap[south-west span-45]
@box[bg-brick text-white rounded fragment](<span style="font-size:01.125em " ><font color="yellow"><b>Remove  &nbsp;&num;define </b></font></span><br> No searching for "<i>magic</i>" &num;define statements )
@snapend

@snap[south-east span-45 ]
@box[bg-brick text-white rounded fragment](<span style="font-size:01.125em " ><font color="yellow"><b>API functions</b></font></span><br> Get and Set functions for access to PCD variable DB)
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
@box[bg-yellow text-blue rounded my-box-pad2 ](<span style="font-size:01.5em" ><b>Advantages</b></span>)



@snap[west span-45 ]
@box[bg-purple-pp text-white rounded fragment](<span style="font-size:01.125em " ><font color="yellow"><b>Binary Modularity</b></font></span><br> Configure firmware settings in binaries without building )
@snapend

@snap[east span-45 ]
@box[bg-purple-pp text-white rounded fragment](<span style="font-size:01.125em " ><font color="yellow"><b>Configure</b></font></span><br> Provide for options to configure firmware features)
@snapend

@snap[south span-45]
@box[bg-purple-pp text-white rounded fragment](<span style="font-size:01.125em " ><font color="yellow"><b>Patching </b></font></span><br> Simplify the binary patching process )
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
@box[bg-royal text-white waved fragment](<span style="font-size:01.25em" >@color[yellow](<b>Packages</b>)</span><br>List of related modules )
@snapend


@snap[north-west span-45 fragment]
@css[text-yellow]( <br><br><br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="font-size:03.25em" >+</span>)
@snapend


@snap[midpoint span-30 ]
@box[bg-royal text-white waved fragment](<span style="font-size:01.25em" >@color[yellow](<b>Libraries</b>)</span> Same name & interface)
@snapend

@snap[north span-45 fragment]
@css[text-yellow]( <br><br><br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="font-size:03.25em" >+</span>)
@snapend

@snap[east span-30]
@box[bg-royal text-white waved fragment](<span style="font-size:01.25em" >@color[yellow](<b>PCDs</b>) </span><br> Platform Config. DB )
@snapend


Note:

Summary <br>
- Packages<br>
  - list of modules<br>
- Libraries<br>
   - Same Names with different implementation but same interface<br>
- PCD
  - Platform configuration database



---?image=assets/images/binary-strings-black2.jpg
@title[Build Tools Section]
<br><br><br><br><br>
## <span class="gold"  >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Build Tools </span>
<span style="font-size:0.9em" > &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;EDK II Build Tools and Configuration Files </span>

---
@title[Development Environment]
#### <p align="center"><span class="gold" >Development Environment</span></p>

@snap[west span-45 ]
@box[bg-brick text-white rounded](<span style="font-size:01.125em" ><b>Compiler Tool Chains</b></span>)
<span style="font-size:0.8em" >&nbsp;<br>&nbsp;<br>&nbsp;<br>&nbsp;<br>&nbsp;<br>&nbsp;<br>&nbsp;<br&nbsp;><br>&nbsp;<br></span>  
@snapend

@snap[east span-45 ]
@box[bg-green-pp text-white rounded](<span style="font-size:01.125em" ><b>Operating Systems</b>)</span>    
<span style="font-size:0.8em" >&nbsp;<br>&nbsp;<br>&nbsp;<br>&nbsp;<br>&nbsp;<br>&nbsp;<br>&nbsp;<br&nbsp;><br>&nbsp;<br></span>  
@snapend
<span style="font-size:0.8em" ><br><br></span>

<div class="left">
<ul style="line-height:0.8;"><font color=#fcb813>
  <li><span style="font-size:0.8em" >@color[#fcb813](Microsoft Visual Studio &lpar;VS2017, VS2015, VS2013, VS2012, VS2010, etc.&rpar; ) </span></li>
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
  <li><span style="font-size:0.8em" >@color[#A6ce39](Clear Linux* Project ) </span></li>
</ul>

</div>

@snap[south-west span-45 ]
<p align="left"><span style="font-size:0.8em" ><br>@color[white](&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Python 3.7.<i>n</i>  & Nasm)</span><br><br></p>
@snapend

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
@box[bg-blue text-white rounded my-box-pad2 ](Set by <span style="font-size:01.2em; font-family:Consolas; " > @color[yellow](edksetup) </span><br>Window = .bat<br>Linux = .sh )
@snapend
<br>
<br>
<br>
<br>
<div class="left-2">
  <span style="font-size:0.8em" >&nbsp;  </span>
</div>
<div class="right-2">
<ul style="list-style-type:none" style="line-height:0.7;">
  <li><span style="font-size:0.8em" >1.&nbsp;&nbsp; EDK_TOOLS_PATH  </span></li>
  <li><span style="font-size:0.8em" >2.&nbsp;&nbsp; PATH  </span></li>
  <li><span style="font-size:0.8em" >3.&nbsp;&nbsp; WORKSPACE  </span></li>
  <li><span style="font-size:0.8em" >4.&nbsp;&nbsp; EFI_SOURCE / EDK_SOURCE  </span></li>
  <li><span style="font-size:0.8em" >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<i>Outside</i> <font face="Consolas"> @color[yellow](edksetup )</font></span></li>
  <li><span style="font-size:0.8em" >&nbsp;@color[orange](* )&nbsp;&nbsp;PACKAGES_PATH @color[black]((<i>optional</i> &rpar;)  </span></li>
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

<ul style="list-style-type:none; line-height:0.7;">
<li class="fragment">@fa[circle gp-bullet-gold]&nbsp;&nbsp;<span style="font-size:01.02em"><font face="Consolas">edksetup.bat or edksetup.sh</font></span><br><br><br><br><br></li>
<li class="fragment">@fa[circle gp-bullet-magenta]&nbsp;&nbsp;<span style="font-size:01.02em">First time use will set up the configuration files:</span> <span style="font-size:0.550em"><font face="Consolas"><br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Conf/@color[#87E2A9](build_rule).txt <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Conf/@color[#00ffff](target).txt  <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Conf/@color[yellow](tools_def).txt </font></span><br><br></li>
<li class="fragment">@fa[circle gp-bullet-green]&nbsp;&nbsp;<span style="font-size:01.02em">Setup & verify a developer's workspace</span></li>
</ul>

@snap[north span-50 fragment]
@css[text-yellow]( <br><br><br>&nbsp;)
![ubuntu](/assets/images/ubuntu-edksetup.png)
@snapend

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




---
@title[Multiple Workspace Environment Variable]
<p align="right"><span class="gold" ><b>Multiple Workspace Environment Variable </b></span></p>

@snap[north span-40 ]
<br>
<br>
@box[bg-green-pp text-white rounded my-box-pad2]( <span style="font-size:01.2em; ; font-family:Consolas;">PACKAGES_PATH</span>)
@snapend

@snap[north-west span-50 fragment]
<br>
<br>
<br>
<br>
<p style="line-height:65%"><span style="font-size:0.7em; font-family:Consolas;">@color[#A8ff60](WORKSPACE)<br>@color[#A8ff60](PACKAGES_PATH )- <i>Optional</i><br></span>
<p style="line-height:70%" align="left"><span style="font-size:0.75em">
Multiple paths that will be searched when attempting to resolve the location of packages. 
</span></p>
@snapend

 
@snap[north-east span-50 fragment]
<br>
<br>
<br>
<br>
<br>
<ul style="list-style-type:disc; line-height:0.7;">
  <li><span style="font-size:0.7em">Highest search Priority / Build Directory  </span></li>
  <li><span style="font-size:0.7em">Additional Paths in Priority order. Must be set before @color[#87E2A9](<font face="Consolas">edksetup</font>)  and @color[red](NOT) set by @color[#87E2A9](<font face="Consolas">edksetup</font>) </span><br></li>
</ul>
@snapend 


@snap[south-east span-97 fragment]
<p style="line-height:47%" align="left"><span style="font-size:0.8em">@color[yellow](Example:)</span></p>
@box[bg-black text-white rounded my-box-pad2  ](<p style="line-height:30%" align="left"><span style="font-size:0.47em; font-family:Consolas;">&nbsp;&nbsp;bash$ export WORKSPACE=$PWD<br>&nbsp;&nbsp;bash$ export PACKAGES_PATH=$WORKSPACE/edk2:$WORKSPACE/edk2-libc<br>&nbsp;</span></p>)
<br>
@snapend


@snap[south-east span-35 fragment]
![PackagesPath](/assets/images/Packages_Path.png)
<br>
<br>
<br>
@snapend



Note:

Package_Path<br>

An update to the EDKII build tools now allows the setting of multiple paths that will be searched when attempting to resolve the location of packages. This new feature allows for more flexibility when designing a tree layout or combining sources from different sources. The new functionality is enabled through the addition of a new environment variable (PACKAGES_PATH).
The PACKAGES_PATH variable is an ordered list of additional search paths using the default path separator of the host OS between each entry. The first path in the list has the highest priority and the last path has the lowest priority. The path specified by the WORKSPACE variable always has the highest search priority over any PACKAGE_PATH entries.
To use this feature, the PACKAGES_PATH environment variable must be set prior to running the edksetup script. The reason for this is that the edksetup script determines the location of the Conf and BaseTools directory location based on the values of the WORKSPACE and PACKAGES_PATH environment variables.
The use of the PACKAGES_PATH environment variable is optional and if it is not defined the build will function like it has in the past.

Why and when:
In this case WORKSPACE is the container for two trees as well as the location of the Build directory. The example assumes the set of code packages for a given platform are contained in the platform directory. While the code packages from the open source repository are contained in the edk2 directory.

When the build tools are run with this configuration the directories will be scanned in the following order to find packages listed in the DSC and FDF files.
 

---
@title[Using target.txt]
<p align="right"><span class="gold" >@size[1.1em](<b>Using <font face="Consolas">target.txt </font></b>)</span><span style="font-size:0.75em;" >  </span></p>

@snap[north-west span-100 ]
<br>
<br>
<table id="recTable">
	<tr>
		<td bgcolor="#0070C0"><p style="line-height:10%"><span style="font-size:0.65em" >Tag&nbsp;</span></p></td>
		<td bgcolor="#0070C0"><p style="line-height:10%"><span style="font-size:0.65em" >Description &nbsp;</span></p></td>
	</tr>
	<tr class="fragment">
		<td align="left" bgcolor="#404040" height=".0025"><p style="line-height:010%"><span style="font-size:0.460em; font-family:Consolas; " >ACTIVE_PLATFORM</span></p></td>
		<td align="left" bgcolor="#404040" height=".0025"><p style="line-height:010%"><span style="font-size:0.6em" >Pointer to DSC file being built</span></p></td>
	</tr>
	<tr class="fragment">
		<td align="left" bgcolor="#404040" height=".0025"><p style="line-height:010%"><span style="font-size:0.460em; font-family:Consolas; " >TARGET</span></p></td>
		<td align="left" bgcolor="#404040" height=".0025"><p style="line-height:010%"><span style="font-size:0.6em" >Build mode: DEBUG or RELEASE</span></p></td>
	</tr>
	<tr class="fragment">
		<td align="left" bgcolor="#404040" height=".0025"><p style="line-height:010%"><span style="font-size:0.460em; font-family:Consolas; " >TARGET_ARCH</span></p></td>
		<td align="left" bgcolor="#404040" height=".0025"><p style="line-height:010%"><span style="font-size:0.6em" >Build architecture (IA32, IPF, X64, EBC, ARM)</span></p></td>
	</tr>
	<tr class="fragment">
		<td align="left" bgcolor="#404040" height=".0025"><p style="line-height:010%"><span style="font-size:0.460em; font-family:Consolas; " >@color[#FFC000](TOOL_CHAIN_TAG)</span></p></td>
		<td align="left" bgcolor="#404040" height=".0025"><p style="line-height:010%"><span style="font-size:0.6em" >Compiler/tool set to use, based on definitions in tools_def.txt</span></p></td>
	</tr>
</table>
<br>
<br>
@snapend


@snap[south span-95 fragment ]
<p style="line-height:50%" align="left"><span style="font-size:0.6em"> <font face="Consolas">MAX_CONCURRENT_THREAD_NUMBER</font> - defaults to Number of threads available to the build process (multi-threaded build) </span></p>
<br>
<br>
@snapend

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
<p align="right"><span class="gold" >@size[1.1em](<b>Using <font face="Consolas">tools_def.txt </font></b>)</span><span style="font-size:0.75em;" >  </span></p>

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
<p align="right"><span class="gold" >@size[1.1em](<b>First Make  </b>)</span><span style="font-size:0.95em;" ><font face="Consolas"><b>BaseTools</b></font>  </span></p>

@snap[north span-35 ]
@css[text-yellow]( <br>&nbsp;)
@box[bg-royal text-white rounded my-box-pad2](<span style="font-size:01.2em" > @color[yellow](<b><font face="Consolas">BaseTools</font></b>) </span> )
@snapend
<br>
<p style="line-height:90%">The first step is to make / "<font face="Consolas">nmake</font>" the "<font face="Consolas">BaseTools</font>" with the host OS & compiler environment.</p>

<p style="line-height:90%"><span style="font-size:0.8em" >For @fa[linux gp-bullet-gold] Linux GCC5 the command is: </span>
@box[bg-grey-05 text-white rounded my-box-pad2](<p align="left"><span style="font-size:0.6em" >&nbsp;  <font face="Consolas">bash$ make -C BaseTools</font> </span></p>)
<hr>
<span style="font-size:0.8em" >For @fa[windows gp-bullet-cyan] Windows Visual Studio with  Python 3.7 the command is: </span>

@box[bg-grey-05 text-white rounded my-box-pad2](<p align="left"><span style="font-size:0.6em" >&nbsp;    <font face="Consolas">&gt; edksetup.bat Rebuild</font> </span></p>)
<br>
   
@snap[south-west span-100 ]
<p style="line-height:90%" align="right"><span style="font-size:0.50em;  " >
@color[white](Building &nbsp;<font face="Consolas">"BaseTools"</font> &nbsp;only needs to be done once )
</span></p>
@snapend

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
<span style="font-size:0.9em" > &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;EDK II Build Process and Build Text Files</span>
 
---?image=/assets/images/slides/Slide35.JPG
<!-- .slide: data-transition="none" -->	
@title[Build Process Overview]
#### <p align="right"><span class="gold" >Build Process Overview </span></p>

Note:


+++?image=/assets/images/slides/Slide36.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 
@title[Build Process Overview 03]
#### <p align="right"><span class="gold" >Build Process Overview </span></p>

Note:

+++?image=/assets/images/slides/Slide37.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 
@title[Build Process Overview 04]
#### <p align="right"><span class="gold" >Build Process Overview </span></p>

Note:
+++?image=/assets/images/slides/Slide38.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 
@title[Build Process Overview 05]
#### <p align="right"><span class="gold" >Build Process Overview </span></p>

Note:
+++?image=/assets/images/slides/Slide39.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 
@title[Build Process Overview 06]
#### <p align="right"><span class="gold" >Build Process Overview </span></p>

Note:
+++?image=/assets/images/slides/Slide40.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 
@title[Build Process Overview 07]
#### <p align="right"><span class="gold" >Build Process Overview </span></p>

Note:
+++?image=/assets/images/slides/Slide41.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 
@title[Build Process Overview 08]
#### <p align="right"><span class="gold" >Build Process Overview </span></p>

Note:

+++?image=/assets/images/slides/Slide42.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 
@title[Build Process Overview 08]
#### <p align="right"><span class="gold" >Build Process Overview </span></p>

Note:


---
@title[Basic Build Steps]
<p align="right"><span class="gold" >@size[1.1em](<b>Basic Build Steps  </b>)</span>
<span style="font-size:0.75em;" >  </span></p>


@snap[west span-45 ]
@box[bg-royal text-white rounded](<span style="font-size:01.125em" ><b>Platform</b></span>)
<span style="font-size:0.8em" >&nbsp;<br>&nbsp;<br>&nbsp;<br>&nbsp;<br>&nbsp;<br>&nbsp;<br>&nbsp;<br&nbsp;><br>&nbsp;<br></span>  
@snapend

@snap[east span-45 ]
@box[bg-brick text-white rounded](<span style="font-size:01.125em" ><b>Module</b>)</span>    
<span style="font-size:0.8em" >&nbsp;<br>&nbsp;<br>&nbsp;<br>&nbsp;<br>&nbsp;<br>&nbsp;<br>&nbsp;<br&nbsp;><br>&nbsp;<br></span>  
@snapend
<span style="font-size:0.8em" ><br><br></span>

@snap[north-west span-50 ]
<br>
<p style="line-height:60%" align="left" ><span style="font-size:0.7em;" ><br><br><br><br>&nbsp;
</span></p>

<ul style="list-style-type:none; line-height:0.7;">
  <li><span style="font-size:0.7em" >1.&nbsp;&nbsp; Navigate (CD) to root of EDK II<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; workspace </span></li>
  <li><span style="font-size:0.7em" >2.&nbsp;&nbsp; Make the <font face="Consolas">BaseTools</font>  </span></li>
  <li><span style="font-size:0.7em" >3.&nbsp;&nbsp; Run @color[#87E2A9](<font face="Consolas">edksetup</font>)  </span></li>
  <li><span style="font-size:0.7em" >4.&nbsp;&nbsp; Run <font face="Consolas">build</font>  </span></li>
  <li><span style="font-size:0.7em" >5.&nbsp;&nbsp; @color[cyan](Output):&nbsp;   firmware image (FD)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; file under Build directory </span></li>
</ul>
@snapend

@snap[north-east span-48 ]
<br>
<p style="line-height:60%" align="left" ><span style="font-size:0.7em;" ><br><br><br><br>&nbsp;
</span></p>

<ul style="list-style-type:none; line-height:0.7;">
  <li><span style="font-size:0.7em" >1.&nbsp;&nbsp; Navigate (CD) to root of EDK II<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; workspace </span></li>
  <li><span style="font-size:0.7em" >2.&nbsp;&nbsp; Make the <font face="Consolas">BaseTools</font>  </span></li>
  <li><span style="font-size:0.7em" >3.&nbsp;&nbsp; Run @color[#87E2A9](<font face="Consolas">edksetup</font>)  </span></li>
  <li><span style="font-size:0.7em" >4.&nbsp;&nbsp; @color[yellow](<b>Change to directory with<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; desired INF file</b> ) </span></li>
  <li><span style="font-size:0.7em" >5.&nbsp;&nbsp; Run <font face="Consolas">build</font>  </span></li>
  <li><span style="font-size:0.7em" >6.&nbsp;&nbsp; @color[cyan](Output):&nbsp;  <font face="Consolas">.EFI</font> file under Build<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; directory </span></li>
</ul>

@snapend


@snap[south-west span-45 ]
<span style="font-size:0.5em" >&nbsp;&nbsp;&nbsp;Note: Module .inf must be in .dsc components </span>
<br>
<br>
@snapend

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


---?image=/assets/images/slides/Slide44.JPG
<!-- .slide: data-transition="none" -->	 
@title[Build Output Location]
#### <p align="right"><span class="gold" >Build Output Location</span></p>

Note:

+++?image=/assets/images/slides/Slide45.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 

@title[Build Output Location 02]
#### <p align="right"><span class="gold" >Build Output Location</span></p>

Note:

+++?image=/assets/images/slides/Slide46.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 

@title[Build Output Location 03]
#### <p align="right"><span class="gold" >Build Output Location</span></p>

Note:

+++?image=/assets/images/slides/Slide47.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 

@title[Build Output Location 04]
#### <p align="right"><span class="gold" >Build Output Location</span></p>

Note:

+++?image=/assets/images/slides/Slide48.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 

@title[Build Output Location 05]
#### <p align="right"><span class="gold" >Build Output Location</span></p>

Note:

+++?image=/assets/images/slides/Slide49.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 

@title[Build Output Location 06]
#### <p align="right"><span class="gold" >Build Output Location</span></p>

Note:

+++?image=/assets/images/slides/Slide50.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 

@title[Build Output Location 07]
#### <p align="right"><span class="gold" >Build Output Location</span></p>

Note:

+++?image=/assets/images/slides/Slide51.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 

@title[Build Output Location 08]
#### <p align="right"><span class="gold" >Build Output Location</span></p>

Note:

+++?image=/assets/images/slides/Slide52.JPG
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
<p style="line-height:80%"><span style="font-size:0.8em" >Process source code files to create PE32/PE32+/COFF images processed to UEFI format using <font face="Consolas">$(MAKE)</font> tool </span></p>
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


---?image=/assets/images/slides/Slide54.JPG


@title[EDK II Build AutoGen Stage]
#### <p align="right"><span class="gold" >EDK II Build: AutoGen Stage</span></p>

@snap[south-east span-90 ]
<p style="line-height:30%" align="left" ><span style="font-size:0.57em;; font-family:Consolas;" >
build -p OvmfPkg/OvmfX64Pkg.dsc
<br>
</span></p>
<br>
<br>
<br>
<br>
<br>
@snapend

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
@css[text-yellow](<br><br>&nbsp;)
@box[ bg-green-pp text-white rounded my-box-pad2 ](<span style="font-size:0.9em" >Uses assemblers/compilers/linkers to generate PE32/PE32+ COFF image file<br>&nbsp;</span>)
@snapend

@snap[midpoint span-90 ]
<br>
@box[ bg-lt-blue-pp text-white rounded my-box-pad2 ](<span style="font-size:0.9em" >Uses <font face="Consolas">ImageGen</font> tools to modify PE32/PE32+/COFF image file<br>Creates UEFI file &lpar;EFI_IMAGE_SECTION_HEADER structure&rpar;<br>&nbsp;</span>)
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
@css[text-black](&nbsp;&nbsp; <font face="Consolas">GenFW</font><br><br><br><br>)
@snapend


@snap[south span-25 ]
@css[text-black](<font face="Consolas">GenFds</font><br><br><br><br>)
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




---?image=/assets/images/slides/Slide56.JPG

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

---?image=/assets/images/slides/Slide57.JPG
<!-- .slide: data-transition="none" -->	 
@title[Build Flow For OpROM]
#### <p align="right"><span class="gold" >Build Flow For OpROM</span></p>

Note:


+++?image=/assets/images/slides/Slide58.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 

@title[Build Flow For OpROM 02]
#### <p align="right"><span class="gold" >Build Flow For OpROM</span></p>

Note:



---
@title[Build Command]
<br>
<p align="center"><span class="gold" >@size[1.1em](<b>The <font face="Consolas">@color[white](build)</font> Command  </b>)</span><span style="font-size:0.75em;" >  </span></p>
<br>
<ul style="list-style-type:disc; line-height:0.85;">
 <li class="fragment"><span style="font-size:0.85em;" >Accepts command line arguments to support scripted builds  </span> </li>
 <li class="fragment"><span style="font-size:0.85em;" >Overrides most settings found in <font face="Consolas">target.txt</font> </span> </li>
 <li class="fragment"><span style="font-size:0.85em;" >Overrides DSC with a minimal INF build  </span> </li>
 <li class="fragment"><span style="font-size:0.85em;" >Overrides some settings in DSC file (.FDF)  </span> </li>
 <li class="fragment"><span style="font-size:0.85em;" >Choose settings from the FDF file (ROMIMAGE, FVIMAGE) </span> </li>
 <li class="fragment"><span style="font-size:0.85em;" >Choose <font face="Consolas">$(make)</font> options (silent, verbose, quiet) </span> </li>
</ul>


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

---?image=/assets/images/slides/Slide60.JPG
<!-- .slide: data-transition="none" -->	 
@title[Using EDK II build Command]
<p align="right"><span class="gold" >@size[1.1em](<b>Using EDK II <font face="Consolas">@color[white](build)</font> Command  </b>)</span><br>
<span style="font-size:0.75em;" >  </span></p>

@snap[south span-35 ]
<p style="line-height:60%" align="left" ><span style="font-size:0.8em; font-family:Consolas;" >
bash$ build -h
</span></p>
<br>
@snapend

Note:

This is not the complete list … run build --help from the command prompt to see all of the build options

+++?image=/assets/images/slides/Slide61.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 
 
@title[Using EDK II build Command 02]
<p align="right"><span class="gold" >@size[1.1em](<b>Using EDK II <font face="Consolas">@color[white](build)</font> Command  </b>)</span><br>
<span style="font-size:0.75em;" >  </span></p>

@snap[south span-35 ]
<p style="line-height:60%" align="left" ><span style="font-size:0.8em; font-family:Consolas;" >
bash$ build -h
</span></p>
<br>
@snapend

Note:

This is not the complete list … run build --help from the command prompt to see all of the build options


+++?code=sample/buildoutput.txt&lang=shell&title=<p align="right"><font face="Consolas" color="white"><b>build -h&nbsp;&nbsp;Command </b></font> </p>

@[1,5-25](options to overide .DSC, .INF and .FDF and Target.txt settings)
@[60,65-74](Using the -Y and -y options for Reports)

Note:
output from 
Build -h command

---?image=/assets/images/slides/Slide63.JPG
@title[Using Build-Y Reports]
<p align="right"><span class="gold" >@size[1.1em](<b>Using <font face="Consolas">@color[white](build -Y)</font> Reports  </b>)</span><span style="font-size:0.75em;" >  </span></p>


@snap[south-west span-75 ]
<p style="line-height:60%" align="left" ><span style="font-size:0.7em; " >
Example:<br>&nbsp;&nbsp;
@size[.7em](<font face="Consolas">bash$ build  –Y  PCD –y pcd.log</font>)<br>
For all reports:<br>&nbsp;&nbsp;
@size[.7em](<font face="Consolas">bash$ build –y MyReport.log  </font>)<br>&nbsp;&nbsp;
</span></p>
@snapend

Note:
build  –Y  PCD,  LIBRARY, FLASH, DEPEX, BUILD_FLAGS, FIXED_ADDRESS <Br>

-Y REPORTTYPE<Br>
--report-type=REPORTTYPE<Br>

Flags that control the type of build report to generate.  Must be one of: [PCD, LIBRARY, FLASH, DEPEX, BUILD_FLAGS, FIXED_ADDRESS, EXECUTION_ORDER].<Br>

To specify more than one flag, repeat this option on the command line and the default flag set is [PCD, LIBRARY, FLASH, DEPEX, BUILD_FLAGS, FIXED_ADDRESS]<Br>

EXEC ORDER is  best done on the Host build machine

+++
@title[Using Build-Y Reports Example]
<p align="right"><span class="gold" >@size[1.1em](<b>Using <font face="Consolas">@color[white](build -Y)</font> Reports  </b>)</span><span style="font-size:0.75em;" >  </span></p>

- @size[.8em](Scroll through examples of reports from the <font face="Consolas">build -Y</font> commands)

Note:
TBD


+++?code=sample/Reports/depex.log&lang=shell&title=<p align="right"><font face="Consolas" color="white"><b>build -Y DEPEX</b></font><font color="#E49436">&nbsp;&nbsp;Command </font> </p>

Note:

+++?code=sample/Reports/pcd.log&lang=shell&title=<p align="right"><font face="Consolas" color="white"><b>build -Y PCD</b></font><font color="#E49436">&nbsp;&nbsp;Command </font> </p>

Note:


+++?code=sample/Reports/library.log&lang=shell&title=<p align="right"><font face="Consolas" color="white"><b>build -Y LIBRARY</b></font><font color="#E49436">&nbsp;&nbsp;Command </font> </p>

Note:

+++?code=sample/Reports/flash.log&lang=shell&title=<p align="right"><font face="Consolas" color="white"><b>build -Y FLASH</b></font><font color="#E49436">&nbsp;&nbsp;Command </font> </p>

Note:

+++?code=sample/Reports/build_flag.log&lang=shell&title=<p align="right"><font face="Consolas" color="white"><b>build -Y BUILD_FLAGS</b></font><font color="#E49436">&nbsp;&nbsp;Command </font> </p>

Note:

+++?code=sample/Reports/fixed_address.log&lang=shell&title=<p align="right"><font face="Consolas" color="white"><b>build -Y FIXED_ADDRESS</b></font><font color="#E49436">&nbsp;&nbsp;Command </font> </p>

Note:

+++?code=sample/Reports/ExecOrder_EmulatorPkg.log&lang=shell&title=<p align="right"><font face="Consolas" color="white"><b>build -Y EXECUTION_ORDER</b></font><font color="#E49436">&nbsp;&nbsp;Command </font> </p>
<p style="line-height:65%" align="left" ><span style="font-size:0.75em" > Report.html is generated on the host build machine - pop up this in the Browser window.</span></p>

Note:
This is best done on the Host build machine

+++?code=sample/Reports/Emulator.report&lang=shell&title=<p align="right"><font face="Consolas" color="white"><b>build -y MyReport.log</b></font><font color="#E49436">&nbsp;&nbsp;Command </font> </p>

Note:



---
@title[Build Tool Binaries]
#### <p align="center"><span class="gold"  >Build Tool Binaries</span></p>


<table id="recTable">
	<tr>
		<td bgcolor="#002060" height=".0025"><p align="center" style="line-height:20%"><span style="font-size:0.85em" >&nbsp;<b>Utility</b></span></p></td>
		<td bgcolor="#002060" height=".0025"><p align="center" style="line-height:20%"><span style="font-size:0.85em" >&nbsp;<b>Description</b></span></p></td>
	</tr>
	<tr>
		<td bgcolor="#00b0f0" height=".0025"><p style="line-height:20%"><span style="font-size:0.75em" ><font face="Consolas">Build.exe</font></span></p></td>
		<td bgcolor="#00b0f0" height=".0025"><p style="line-height:60%"><span style="font-size:0.6em" >Tool is written in Python and calls <font face="Consolas">AutoGen.exe</font>, then it calls <font face="Consolas">$(MAKE) –f  Makefile.out</font>, and finally, it calls <font face="Consolas">GenFds.exe</font></span></p></td>
	</tr>
	<tr>
		<td bgcolor="#fdb813" height=".0025"><p style="line-height:20%"><span style="font-size:0.75em" ><font face="Consolas">EfiRom.exe</font>&nbsp;</span></p></td>
		<td bgcolor="#fdb813" height=".0025"><p style="line-height:20%"><span style="font-size:0.6em" >used to build an option ROM image&nbsp;</span></p></td>
	</tr>
	<tr>
		<td bgcolor="#00b0f0" height=".0025"><p style="line-height:20%"><span style="font-size:0.75em" ><font face="Consolas">PatchModule.exe</font>&nbsp;</span></p></td>
		<td bgcolor="#00b0f0" height=".0025"><p style="line-height:60%"><span style="font-size:0.6em" >used to patch a binary module that has a PCD of type PATCHABLE_IN_MODULE&nbsp;</span></p></td>
	</tr>
	<tr>
		<td bgcolor="#fdb813" height=".0025"><p style="line-height:20%"><span style="font-size:0.75em" ><font face="Consolas">PatchPlatform.exe</font>&nbsp;</span></p></td>
		<td bgcolor="#fdb813" height=".0025"><p style="line-height:60%"><span style="font-size:0.6em" >used to modify either the PCD Database or the VPD settings in a flash device image&nbsp;</span></p></td>
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

---
@title[return to main]
<p align="center"><span class="gold"   >@size[1.2em](<b>Return to Main Training Page</b>)</span></p>
<br>
<br>
<br>
<br>
<br>
<p align="center"><span style="font-size:0.9em">Return to Training Table of contents for next presentation <a href="https://github.com/tianocore-training/Tianocore_Training_Contents/wiki#schedule--outline">link</a></span></p>

@snap[north span-30 ]
<br>
<br>
<br>
<a href="https://github.com/tianocore-training/Tianocore_Training_Contents/wiki#schedule--outline">
![trainingLogo](/assets/images/returnTrainingLogo.png)</a>
@snapend


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

Copyright (c) 2020, Intel Corporation. All rights reserved.
**/

```



---?image=assets/images/binary-strings-black2.jpg
@title[Backup Section]
<br><br><br><br><br>
## <span class="gold"  >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Backup </span>
<span style="font-size:0.9em" > &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span>




---
@title[EDK II vs. UDK]
#### <p align="center"><span class="gold" >EDK II vs. UDK(2010|2017 .. 2018)</span></p>
<br>
@box[bg-blue  text-white rounded](<span style="font-size:01.1em" ><b>UEFI Developer's Kit 2018 &lpar;UDK2018&rpar;</b> </span>)
<br>
@box[bg-purple-pp text-white rounded](<span style="font-size:01.1em" ><b>Stable build of the EDK II project</b> </span>)
<br>
@box[bg-brick text-white rounded](<span style="font-size:01.1em" ><b>Neither contain Intel silicon or platform code</b></span>)

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


