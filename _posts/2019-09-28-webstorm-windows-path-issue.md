---
title: "WebStorm - NodeJS Interpreter '%PATH%' Error Fix"
last_modified_at: 2019-09-26T15:26:00-08:00
comments: true
categories:
  - JetBrains
tags:
  - JetBrains
  - WebStorm
  - NodeJS
  - Windows
  - CommandPrompt
  - PowerShell
  - NPM
classes: 
  - wide
header:
  overlay_image: /assets/images/logos/jb_beam.png
  show_overlay_excerpt: false
  teaser: /assets/images/logos/webstorm_logo_300x300.png
  og_image: /assets/images/logos/webstorm_logo_300x300.png
---

The fix for the `No executable found in %PATH%` error when attempting to set the NodeJS interpreter and NPM package manager in JetBrains WebStorm.

Install Sequence:

1. Windows 10
2. ToolBox 1.15.5796
3. From ToolBox - WebStorm 2019.2.3
4. NodeJS

At this point, the `No executable found in %PATH%` error will be present when attempting to create a NodeJS project.

![image-center](/assets/images/2019-09-28-webstorm-windows-path-issue/WebStorm-NodeJS-Interpreter-Path-Not-Found.png){: .align-center}

If you've gotten to this point, there may have been an hour or two of beating your head against your fist trying to understand why the error wont go away.

- Command Prompt and PowerShell both execute `node`.
- Restarting WebStorm does not resolve the issue.
- We checked the %PATH% environment value and see the `C:\Project Files\nodejs` path present.

## The Fix

Shutdown WebStorm and then restart JetBrains ToolBox - or restart your PC.

When attempting to create a new NodeJS project, the Node interpreter and NPM package manager should now be detected.

Simple? Read on!

## Probable Cause

It appears that JetBrains applications launched through ToolBox receive the environment variables that were present when ToolBox was started. Installing any package after would not update the environment variables when applications are started and restarted via ToolBox.

See [JetBrains Support Ticket](https://intellij-support.jetbrains.com/hc/en-us/community/posts/115000684650-Windows-Terminal-PATH-is-missing-environment-variables) for more.
