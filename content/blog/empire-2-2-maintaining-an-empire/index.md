---
title: "Empire 2.2 — Maintaining an Empire"
date: 2017-10-12T17:18:57Z
draft: false
author: "Steve Borosh"
slug: "empire-2-2-maintaining-an-empire"
canonicalURL: "https://rvrsh3ll.github.io/blog/empire-2-2-maintaining-an-empire/"
medium_url: "https://medium.com/rvrsh3ll/empire-2-2-maintaining-an-empire-2f7d0329b294"
publication: "rvrsh3ll"
tags:
  - "empire"
---
### Maintaining an Empire

All great empires require maintenance. As we move towards the next major release (Empire 3.0), we continue to receive great support from the Empire community. From git issues to pull requests, the improvements keep flooding in. The core developers of Empire could not appreciate this more! We are certainly grateful for the support of such a great community.

![support.jpg](0-kuri8kcbmBpP-PWH.jpeg)

This blog post will actually cover some of the fixes and improvements from 2.1 and 2.2 releases as we did not release a blog post for the 2.1 release. Many of these fixes or improvements came from the community and we certainly don’t take credit for them all, nor do we have the ability to cover all the fixes and improvements that were submitted. This blog covers some of the notable improvements that we have time to cover. For a full list of changes, please see the [changelog](https://github.com/EmpireProject/Empire/blob/master/changelog).

#### Obfuscated Empire

Empire 2.1 introduced “Obfuscated Empire”, a modification to the code base from [@cobbr](https://github.com/cobbr). This represents a significant change for Empire. While, we don’t want to play the game of “whack-a-mole” with antivirus vendors, we certainly want to push defenders and blue teams to be on the lookout for obfuscated code from adversaries. Obfuscated empire can be used to help defenders work on their detection mechanisms for this type of attack. We highly suggest you try this option out and read more on obfuscated empire at <https://cobbr.io/ObfuscatedEmpire.html>

#### Added backgrounding for downloads

[@Xorrior](https://github.com/xorrior) modified the PowerShell agent to allow for background downloads. It involves using the same logic used in background job execution. Download tasks are sent to a PowerShell runspace in a newly created AppDomain. During each tasking cycle, the target file is appropriately chunked and then a single chunk is sent to the pipeline for retrieval. That file data is retrieved at the end of tasking cycle and sent back to the server. Agents will no longer be tied up for the duration of a large file download. This logic has not been added to the python agent but will be in the future.

#### Add TokenManipulation UAC Bypass module

This was certainly one of my “[@rvrsh3ll](https://twitter.com/rvrsh3ll)” favorites. The original research was done by James Forshaw ([@tiraniddo](https://twitter.com/tiraniddo)) and then weaponized by Ruben Boonen ([@fuzzysec](https://twitter.com/fuzzysec)). Researcher and Empire dev, Matt Nelson ([@enigma0x3](https://twitter.com/enigma0x3)) released a PowerShell [script](https://github.com/enigma0x3/Misc-PowerShell-Stuff/blob/master/Invoke-TokenDuplication.ps1) at DerbyCon 2017 showing how UAC is basically dead, by duplicating tokens to run code in an elevated context regardless of UAC setting. This was huge! Of course we had to have this in Empire so, a few questions to Matt and we had a modified version ready to go for Empire usage. Now, Empire has a stable BypassUAC module that is all in-memory and will be usable for quite some time. See module: privesc/bypassuac_tokenmanipulation

#### Added ‘SandboxMode’ to evade Apple Sandbox protection on applescript

[@dchrastil](https://github.com/dchrastil) found a novel method using osascript to pop a credential prompt from within the Office sandbox. This option greatly enhances capabilities for post-phishing in a MacOS setting. See module: collection/osx/prompt

#### Add EternalBlue module

Community member [@e0x70i](https://github.com/e0x70i) graced us with a port of the metasploit EternalBlue module in the Empire 2.1 release. See module: exploitation/exploit_eternalblue

#### SSL Intermediate Certificates to support Domain Fronting

A mod from [@dchrastil](https://github.com/dchrastil),[@h1ghtopfade](https://twitter.com/h1ghtopfade), and John McLeod. This modification allows for intermediate SSL certificates while setting up a listener over SSL. This was accomplished by splitting the empire.pem (cert + key) into two separate files (empire_chain.pem, empire_priv.key).

#### REST API Fixes

Huge thanks for the continuing support of the REST api from @[byt3bl33d3r](https://github.com/byt3bl33d3r)!

#### Conclusion

![d314_death_star_wall_cling.jpg](0-3YzAEoEni14272k0.jpeg)

While we continue to move forward to our next major release, there’s a few things we are certainly striving to add, such as multiplayer Empire, SOCKS proxy through the agent, internal c2 comms channels such as UDP or SMB and much more. Please join the Empire on [slack](http://adaptiveempire.herokuapp.com/) today! [Get Empire 2.2](https://github.com/EmpireProject/Empire/tree/master)
