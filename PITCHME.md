---?image=assets/images/gitpitch-audience.jpg
@title[Title-UEFI Overview]
## <span class="brick"   >UEFI & EDK II Training</span>
<p><span class="slide-title"><b>Using class=slide-title </b></span></p>

#### <span class="gold"> UEFI and Platform Initialization (PI) Overview </span>

<br>
<span style="font-size:0.75em" ><a href='http://www.tianocore.org'>tianocore.org</a></span>
Note:
  PITCHME.md for UEFI / EDK II Training

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
##### <p align="center"<span class="gold"   >Lesson Objective </span></p><br>

<!---  Add bullets using https://fontawesome.com/cheatsheet certificate
-->
 @fa[certificate gp-bullet-green]<span style="font-size:0.9em">&nbsp;&nbsp;Review PI and UEFI Boot Process  </span><br><br>
 @fa[certificate gp-bullet-cyan] <span style="font-size:0.9em">&nbsp;&nbsp;Answer web-based training related questions </span><br><br>
 @fa[certificate gp-bullet-yellow] <span style="font-size:0.9em">&nbsp;&nbsp;Answer: Where does Intel® FSP Fit? </span> <br><br>
 @fa[certificate gp-bullet-magenta] <span style="font-size:0.9em">&nbsp;&nbsp;What’s new in UEFI.org</span> 




---?image=assets/images/binary-strings-black2.jpg
@title[UEFI Boot Flow Section]
#### <span class="gold"  >UEFI Boot Execution Flow </span>
<span style="font-size:0.75em" > Starting at the processor reset vector </span>
---

@title[UEFI Boot Flow]
#### <p align="center"><span class="gold" >UEFI - PI & EDK II Boot Flow </span></p>

<p><span class="slide-text5">Press "S" to see Speaker notes. Speaker notes are added using key word "Note:" at the ende of the slide and before the next slide</span></p>
<p><span class="slide-text5"><b>UEFI  and Platform Initialziation (PI) Boot Execution Flow</b></span></p>

![UEFI Boot Execution Flow](/assets/images/bootflow.JPG)

<!--- comment this does not work
<p>
<img src=https://github.com/Laurie0131/PitchSample/blob/master/assets/images/bootflow.JPG width="425"/></p>
-->
<p><span class="slide-text5"><b>UEFI  and Platform Initialziation (PI) Boot Execution Flow</b></span></p>

Note:
The next set of slides will detail the phases of the boot execution flow for UEFI

---
@title[UEFI Boot Flow Sec]
#### <p align="center"><span class="gold" > UEFI - PI & EDK II Boot Flow </span><span style="color:white;">&nbsp;&nbsp;&nbsp;&nbsp;-&nbsp;<b>SEC</b> </span></p>

![UEFI Boot Execution Flow](/assets/images/bgpages/bg4.png =10x)


Note:
SEC Function <Br>
          Consumes the Reset vector on IA
Serving as the root of trust in the system
Initial code that takes control of the system
May choose to authenticate the PEI Foundation 


+++
@title[SEC - characteristics ]
#### <p align="center"><span class="gold" >Processor Executes SEC starting at the reset vector </span></p>
- SEC Consumes the Reset vector 
- Serving as the root of trust 
- May choose to authenticate the PEI Foundation
- Init the APs waking stub
- Early microcode update
- Collect BIST (Built-in Self Test)
- Other charactistics of SEC   
    - Executed in place from flash
    - Written in assembly (16-bit & 32-bit) on Intel Architecuture	- 
Note:
SEC Function <Br>
          Consumes the Reset vector on IA
Serving as the root of trust in the system
Initial code that takes control of the system
May choose to authenticate the PEI Foundation 

Switch to 32-bit flat mode
Initialize the Boot strap processor BSP
Initialize PEI temporary memory NEM / CAR
Transfer control to PEI Core

SEC will have Platform specific functions
- AP waking stub
- Early microcode update
- Collect BIST (Built-in Self Test)
- Other charactistics of SEC   
  - Executed in place from flash
  - Written in assembly (16-bit & 32-bit)
+++
@title[SEC - Firmware Terms ]
#### <p align="center"><span class="gold" >Terms to know about the Flash Device </span></p>
- Firmware Volume (FV) 
  - The basic storage with a firmware device
- Firmware File System (FFS)
  - Describes the organization of files within a FV

Note:
-A Firmware Volume (FV) is a logical firmware device. The basic storage <br>
repository for data and/or code is the firmware volume. Each firmware volume is organized into a
file system. As such, the file is the base unit of storage for firmware

-Firmware Volume (FV) <br>
A firmware file system (FFS) describes the organization of files and (optionally) free space within
the firmware volume. Each firmware file system has a unique GUID, which is used by the firmware
to associate a driver with a newly exposed firmware volume

---
@title[UEFI Boot Flow PEI]
#### <p align="center"><span class="gold"  >UEFI - PI & EDK II Boot Flow </span><span style="color:white;">&nbsp;&nbsp;&nbsp;&nbsp;-&nbsp;<b>PEI</b> </span></p>


![UEFI Boot Execution Flow](/assets/images/bgpages/bg4_1.png =10x)


Note:
PEI Function <Br>
- PEI Primary goals:
  -	Discover boot mode (Normal, S3, Recovery)
  - Discover and initialize some RAM that won’t be reconfigured
  -	Discover location of FV(s) containing DXE Core & Architecture Protocols and Launch DXE core

- PEI Phases – 
   - Pre – memory Init
   - Memory reference code (MRC)
   - Post Memory Init

Components: 
- Binaries: PEI Core and PEI Modules (PEIMs)
PEIMs are modules scheduled by the PEI core in the early phase of platform initialization. PEIMs are typically executed in place before system memory is available. 
- On IA running in No Eviction mode (NEM) aka.  Cache as RAM

Interfaces: Methods of Inter-PEIM communication
Core set of services (PeiServices), PEIM to PEIM Interfaces (PPIs), and simple Notifies (no timer in PEI)




---
@title[UEFI Boot Flow PEI-DXEIPL  & Hobs ]
#### <p align="center"><span class="gold"  >UEFI - PI & EDK II Boot Flow </span><span style="color:white;">-&nbsp;<b>Hobs DXEIPL</b> </span></p>

![UEFI Boot Execution Flow](/assets/images/bgpages/bg5.png =10x)


Note:
PEI - Hobs <Br>
Transition to DXE :
- HOBS  – a series of data structures in memory, created during PEI, that describe platform features, configuration, or data. HOBs are produced during PEI, and read-only during DXE (consumer). 
+++
@title[UEFI Boot Flow PEI-DXEIPL ]
#### <p align="center"><span class="gold"   >DXE IPL Characteristics   </span>
- No hard coded addresses allowed
- Find Largest Physical Memory HOB
   - Ideally this should be near Top Of Memory (TOM)
   - Allocate DXE Stack from Top of Memory
- Build HOB that describes DXE Stack
- Search FVs from HOB List for DXE Core
- Load DXE Core into Memory (PE/COFF)
- Build HOB that describes DXE Core
- Switch Stacks and Handoff to DXE Core

---
@title[UEFI Boot Flow DXE]
#### <p align="center"><span class="gold"   >UEFI - PI & EDK II Boot Flow </span><span style="color:white;">&nbsp;&nbsp;&nbsp;&nbsp;-&nbsp;<b>DXE</b> </span></p>

![UEFI Boot Execution Flow](/assets/images/bgpages/bg5_1.png =10x)


Note:
DXE <Br>

Works after system memory has been discovered and initialized
DXE drivers are typically stored in flash in compressed form and must be decompressed into memory before execution
+++
@title[DXE Characteristics]
#### <p align="center"><span class="gold"   >DXE Characteristics & Responsibilities  </span></p>
- Consumes HOB List from PEI
- Builds UEFI and DXE Service Tables  
- EFI System Table
- UEFI Boot Services Table & UEFI Runtime Services Table
- Hands off control to the DXE Dispatcher
- and more  . . . 
	

Note:
DXE Characteristics
- Consumes HOB List from PEI
- Builds UEFI and DXE Service Tables  
- EFI System Table
- UEFI Boot Services Table & UEFI Runtime Services Table
- DXE Services Table
- Makes Memory-Only Boot Services Available that will be in memory until ExitBootServices()
- Hands off control to the DXE Dispatcher
- Requires access to Firmware Volumes
- Requires LoadImage(), StartImage(), Exit()
- DXE Drivers will build the Architectural Protocols
- May require decompression service
 
- DXE FOUNDATION Theory of Operation
- The First goal is to Initialize the Platform – Initialize the Chipset and the platform 

- We want to Load Drivers to construct an environment that can support boot manager and  boot the OS 

 
---
## START of EXAMPLE 
The next slides show examples for templates
---

## Tips!

<br>

@fa[arrows gp-tip](Press F to go Fullscreen)

@fa[microphone gp-tip](Press S for Speaker Notes)



---
## Template Features

- Code Presenting |
- Repo Source, Static Blocks, GIST |
- Custom CSS Styling |
- Slideshow Background Image |
- Slide-specific Background Images |
- Custom Logo, TOC, and Footnotes |

---?code=sample/SampleApp/SampleApp.c&lang=c++&title=C File

@[30,32-36](Present code found within any repo source file.)
@[38-48](Without ever leaving your slideshow.)
@[53-60](Using GitPitch code-presenting with (optional) annotations.)

Note:
example of a UEFI application in C

---?code=sample/go/server.go&lang=golang&title=Golang File

@[1,3-6](Present code found within any repo source file.)
@[8-18](Without ever leaving your slideshow.)
@[19-28](Using GitPitch code-presenting with (optional) annotations.)

---

@title[JavaScript Block]

<p><span class="slide-title">JavaScript Block</span></p>

```javascript
// Include http module.
var http = require("http");

// Create the server. Function passed as parameter
// is called on every request made.
http.createServer(function (request, response) {
  // Attach listener on end event.  This event is
  // called when client sent, awaiting response.
  request.on("end", function () {
    // Write headers to the response.
    // HTTP 200 status, Content-Type text/plain.
    response.writeHead(200, {
      'Content-Type': 'text/plain'
    });
    // Send data and end response.
    response.end('Hello HTTP!');
  });

// Listen on the 8080 port.
}).listen(8080);
```

@[1,2](You can present code inlined within your slide markdown too.)
@[9-17](Displayed using code-syntax highlighting just like your IDE.)
@[19-20](Again, all of this without ever leaving your slideshow.)

---?gist=onetapbeyond/494e0fecaf0d6a2aa2acadfb8eb9d6e8&lang=scala&title=Scala GIST

@[23](You can even present code found within any GitHub GIST.)
@[41-53](GIST source code is beautifully rendered on any slide.)
@[57-62](And code-presenting works seamlessly for GIST too, both online and offline.)

---

## Template Help

- [Code Presenting](https://github.com/gitpitch/gitpitch/wiki/Code-Presenting)
  + [Repo Source](https://github.com/gitpitch/gitpitch/wiki/Code-Delimiter-Slides), [Static Blocks](https://github.com/gitpitch/gitpitch/wiki/Code-Slides), [GIST](https://github.com/gitpitch/gitpitch/wiki/GIST-Slides) 
- [Custom CSS Styling](https://github.com/gitpitch/gitpitch/wiki/Slideshow-Custom-CSS)
- [Slideshow Background Image](https://github.com/gitpitch/gitpitch/wiki/Background-Setting)
- [Slide-specific Background Images](https://github.com/gitpitch/gitpitch/wiki/Image-Slides#background)
- [Custom Logo](https://github.com/gitpitch/gitpitch/wiki/Logo-Setting) [TOC](https://github.com/gitpitch/gitpitch/wiki/Table-of-Contents) [Footnotes](https://github.com/gitpitch/gitpitch/wiki/Footnote-Setting)

---

## Go GitPitch Pro!

<br>
<div class="left">
    <i class="fa fa-user-secret fa-5x" aria-hidden="true"> </i><br>
    <a href="https://gitpitch.com/pro-features" class="pro-link">
    More details here.</a>
</div>
<div class="right">
    <ul>
        <li>Private Repos</li>
        <li>Private URLs</li>
        <li>Password-Protection</li>
        <li>Image Opacity</li>
        <li>SVG Image Support</li>
    </ul>
</div>

---

### Questions?

<br>

@fa[twitter gp-contact](@gitpitch)

@fa[github gp-contact](gitpitch)

@fa[medium gp-contact](@gitpitch)

---?image=assets/images/gitpitch-audience.jpg&opacity=100

@title[Download this Template!]

### Get your presentation started!
### [Download this template @fa[external-link gp-download]](https://github.com/Laurie0131/GitPitchTemplate/archive/v1.0.zip)
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
##### <p align="center"<span class="gold"   >Summary </span></p><br>

 @fa[certificate gp-bullet-green]<span style="font-size:0.9em">&nbsp;&nbsp;Review PI and UEFI Boot Process
 </span><br><br>
 @fa[certificate gp-bullet-cyan] <span style="font-size:0.9em">&nbsp;&nbsp;Answer web-based training related questions
</span><br><br>
 @fa[certificate gp-bullet-yellow] <span style="font-size:0.9em">&nbsp;&nbsp;Answer: Where does Intel® FSP Fit? 
</span> <br><br>
 @fa[certificate gp-bullet-magenta] <span style="font-size:0.9em">&nbsp;&nbsp;What’s new in UEFI.org
</span> 



---?image=assets/images/gitpitch-audience.jpg
@title[Questions]
![Questions](/assets/images/Questions.png =10x) 


---?image=assets/images/gitpitch-audience.jpg
@title[Logo Slide]

![Logo Slide](/assets/images/TianocoreLogo.png =10x)

---  
@title[Backup]
##### <p align="center"<span class="gold"   >Backup </span></p>

---
@title[Acknowledgements]
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
