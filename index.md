---
layout: default_c
RefPages:
 
--- 
<table class ="no-border"  style="width:100%;">
  <tr>
    <td style="vertical-align:middle; text-align:left; height:30px;">&nbsp;</td>
    <td style="text-align:right; vertical-align:bottom;  padding-right:20px;">
      <a href="https://nicojane.github.io/Docker-Template-Stacks-Home/"
         style="background:#0078d7; color:white; padding:3px 10px; border-radius:8px; font-size:0.8em; text-decoration:none; font-weight:bold; display:inline-block;">
        🚀 To DTS Stacks
      </a>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:middle; text-align:left;">
      <span style="font-size: 3.2em; font-weight: 550;">W</span>
      <span style="font-size: 2.5em; font-weight: 500; margin-left: -0.2em;">elcome to the WSL-TS</span> <br>
      <span style="color: #409EFF; font-style: italic; font-size:1.1em; position:relative; top:-0.6em; display:inline-block;"> — A WSL Template Components Stack</span>
    </td>
    <td style="text-align:right; vertical-align:middle;">&nbsp;</td>
  </tr>
</table>

WSL Template Stacks provide pre-configured development environments for Windows developers who want to leverage the Windows Subsystem for Linux (WSL) for cross-platform development. Each WSL Template Stack is tailored for specific development scenarios and includes a complete development environment with all necessary tools, dependencies, and a working template project for specific programming languages and frameworks.

<div class="nje-info-box">
📚 <strong>Direct Links to:</strong><br>
 <span class="nje-indent2"><a href="https://nicojane.github.io/WSL-Template-Stacks-Home/#overview-of-wsl-component-stacks"> 🔶 The Available WSL Components</a>
</div>

<div class="nje-info-box">
📚 <strong>Background information</strong><br>
 <span class="nje-indent2"><a href="https://gist.github.com/NicoJanE/34719538ba72e72df4cb451f9001d368"> 🔶 WSL Questions & Answers</a>
</div>
<div class="nje-br1"> </div>

---

## What's Included

WSL Template Stacks are containerized development environments that combine:

- **Pre-configured WSL distribution** with specific programming language toolchains
- **Complete development toolset** including compilers, package managers, and utilities
- **Ready-to-use template projects** demonstrating best practices and architecture
- **Integrated development environment** with VS Code as the default editor

---

## Quick Setup Process

1. **Prerequisites**: Ensure WSL 2 is installed and enabled on your Windows system
2. **Clone**: Clone the appropriate WLS repository template stack for your technology
3. **Setup**: Use the instructions in the ./Howto folder to setup the environment
4. **Develop**: Open the generated project in VS Code and start coding

### Additional setup Information

<div class="nje-br4"> </div>
<details class="nje-note-box" style="margin-top:-18px; margin-left:0px;">
  <summary>General Requirements
  </summary>

- Have **Docker Desktop** installed and running on your Windows **host**
- **WSL** images are tested and supported on the following Windows systems:
  - Supported on Windows 11 ✅
  - Expect to work on Windows 10 uing WSl V2 ✅

</details>
<div class="nje-br4"> </div><div class="nje-br2"> </div>

<details class="nje-note-box" style="margin-top:-18px; margin-left:0px;">
  <summary>Target Audience
  </summary>

- **Windows developers** wanting to use Linux development tools
- **Teams** requiring consistent development environments
- **Developers** starting new projects and wanting to skip initial setup
- **Students and educators** needing quick access to configured development environments
- **Anyone** who values rapid setup and clean, isolated development environments

</details>
<div class="nje-br4"> </div><div class="nje-br2"> </div>

<details class="nje-note-box" style="margin-top:-18px;margin-left:0px;">
  <summary>Key Features
  </summary>

The stacks feature the following <br><br>

<div class="nje-features-box">

- **Rapid Development Setup**
  - Execute a single setup script to create and configure your development environment
  - Automatically provision the WSL container with all required tools and dependencies
  - Launch directly into VS Code with the template project ready for development
  - **Time to productivity: Minutes, not hours**

- **Isolated and Clean Environment**
  - Each stack contains only the tools and dependencies relevant to its specific technology
  - Eliminates version conflicts and dependency issues between different projects
  - Provides a consistent development environment across different machines
  - **No pollution of your host Windows system**

- **Production-Ready Template Projects**
  - Start with a fully functional template application that demonstrates best practices
  - Includes proper project structure, configuration files, and documentation
  - Template can be immediately built, tested, and extended
  - **Skip the boilerplate and focus on your business logic**

- **Cross-Platform Development**
  - Develop applications that run natively on both Linux (WSL) and Windows
  - Test your applications in both environments without dual-boot or separate machines
  - Use Linux tools and utilities while maintaining Windows workflow
  - **One codebase, multiple deployment targets**

</div>
</details>
<div class="nje-br4"> </div>
<hr>
<div class="nje-br2"> </div>


# Overview of WSL Component Stacks

This section provides an overview of the different **WSL Template component stacks** and their documentation. Most of these stacks are designed for developers and include template projects with instructions for use on both **Windows and Linux**. Most stacks support Visual Studio Code, and some also support Visual Studio 2022 (all editions).

### WSL Development stacks

Development stacks. Select one of the options below to view the related project page.

<span class="nje-ident" style="--nje-number-of-spaces: 4px;"></span> 
➡️ [Native Win32 C++ development (Windows)](https://nicojane.github.io/WSL-Development-Stack-Native-Win32-CPP/)  
<small><span class="nje-ident" style="--nje-number-of-spaces: 22px;"/> </small>
<small> - Windows Native API development through a WSL container, using a template project </small> <br>
<span class="nje-ident" style="--nje-number-of-spaces: 4px;"></span> 
➡️ [C++ GLFW-Skia Template project (Linux & Windows)](https://nicojane.github.io/WSL-Development-Stack-GLFW-Skia-CPP-Template/)  
<small><span class="nje-ident" style="--nje-number-of-spaces: 22px;"/> </small>
<small> - Enables you to create windows, handle input and events (GLFW), and defines custom GUI controls (Skia) </small> <br>
<span class="nje-ident" style="--nje-number-of-spaces: 4px;"></span> 
➡️ [Python Flask & FAst Api (Linux & Windows)](https://nicojane.github.io/PY-Flask-FastApi-Template-WSL-Stack/)  
<small><span class="nje-ident" style="--nje-number-of-spaces: 22px;"/> </small>
<small> - Create Python Flask web applications in combination with Fast-API (Todo) </small> <br>

### WSL OS Related

The following repository contains instructions for setting up specific WSL OS distributions.

<span class="nje-ident" style="--nje-number-of-spaces: 4px;"></span> 
➡️ [WSL with Full Desktop GUI](https://github.com/NicoJanE/WSL-OS-With-GUI-Desktop)  
<small><span class="nje-ident" style="--nje-number-of-spaces: 22px;"/> </small>
<small> - WSL with **Mate** full Desktop(Default). Uses X11 Forward to the host (Note: WSLg does not support full desktop) </small> <br>

---

### A note about using X11 instead of WSLg (graphical output)

The default graphical output of WSL is known to be limited. The following instructions show you can use the faster X11 method instead, Refer to the linked document for [details](https://nicojane.github.io/WSL-Template-Stacks-Home/howto_wsl_using_x11)

<br>
<div align="center"> ─── ✦ ───
</div>
