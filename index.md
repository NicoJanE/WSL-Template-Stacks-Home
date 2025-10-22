---
layout: default_c
RefPages:
 
--- 
 
<br>

<span style="font-size: 36px; font-weight: 550;">W</span><span style="font-size: 24px; font-weight: 500;">elcome the WSL-TS site</span> <span style="color: #409EFF; font-style: italic; font-size:17px;"> — WSL Template Stack</span>

WSL Template Stacks provide pre-configured development environments for Windows developers who want to leverage the Windows Subsystem for Linux (WSL) for cross-platform development. Each WSL Template Stack is tailored for specific development scenarios and includes a complete development environment with all necessary tools, dependencies, and a working template project for specific programming languages and frameworks.

<div class="nje-info-box">
📚 <strong>Direct Links</strong><br>
 <a href="https://nicojane.github.io/WSL-Template-Stacks-Home//index#2-the-available-stacks"> 🔶 The Available Stack Components</a>
</div>

<div class="nje-info-box">
📚 <strong>Background information</strong><br>
 <a href="https://gist.github.com/NicoJanE/34719538ba72e72df4cb451f9001d368"> 🔶 WSL Questions & Answers</a>
</div>

<br>

## What's Included

WSL Template Stacks are containerized development environments that combine:

- **Pre-configured WSL distribution** with specific programming language toolchains
- **Complete development toolset** including compilers, package managers, and utilities
- **Ready-to-use template projects** demonstrating best practices and architecture
- **Integrated development environment** with VS Code as the default editor

##  Quick Setup Process

1. **Prerequisites**: Ensure WSL 2 is installed and enabled on your Windows system
2. **Download**: Obtain the appropriate template stack for your technology
3. **Execute**: Run the provided setup script to create your development environment
4. **Develop**: Open the generated project in VS Code and start coding

## Who & Why

<details>
  <summary style="font-size: 1.17em; font-weight: 600; margin-top: 0.1em; margin-bottom: 0.2em;"> &#9654; Target Audience
  </summary>

- **Windows developers** wanting to use Linux development tools
- **Teams** requiring consistent development environments
- **Developers** starting new projects and wanting to skip initial setup
- **Students and educators** needing quick access to configured development environments
- **Anyone** who values rapid setup and clean, isolated development environments

</details>

<details>
  <summary style="font-size: 1.17em; font-weight: 600; margin-top: 0.1em; margin-bottom: 0.2em;"> &#9654; Key benefits
  </summary>

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

</details>

<hr>

# The available stacks

This section provides an overview of the different **WSL Template development stacks** and their documentation. These stacks are designed for developers and include template projects with instructions for use on both **Windows and Linux**. Most stacks support Visual Studio Code, and some also support Visual Studio 2022 (all editions).
Select one of the options below to view the related project page.

## WSL Development stacks

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


## WSL OS Related
The following repository contains instructions for setting up specific WSL OS distributions. 
<br><br>
<span class="nje-ident" style="--nje-number-of-spaces: 4px;"></span> 
➡️ [WSL with Full Desktop GUI](https://github.com/NicoJanE/WSL-OS-With-GUI-Desktop)  
<small><span class="nje-ident" style="--nje-number-of-spaces: 22px;"/> </small>
<small> - WSL with **Mate** full Desktop(Default). Uses X11 Forward to the host (Note: WSLg does not support full desktop) </small> <br>

##  A note about using X11 instead of WSLg (graphical output)

The default graphical output of WSL is known to be limited. The following instructions show you can use the faster X11 method instead, Refer to the linked document for [details](https://nicojane.github.io/WSL-Template-Stacks-Home/howto_wsl_using_x11)

 