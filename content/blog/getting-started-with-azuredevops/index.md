---
title: "Getting Started With AzureDevOps"
date: 2019-09-18T21:15:03Z
draft: false
author: "Steve Borosh"
slug: "getting-started-with-azuredevops"
canonicalURL: "https://rvrsh3ll.github.io/blog/getting-started-with-azuredevops/"
medium_url: "https://medium.com/@rvrsh3ll/getting-started-with-azuredevops-8bf0bf089bc3"
tags:
  - "azure"
  - "devops"
  - "github"
---
### Getting Started With Azure DevOps

**Introduction**

Recently, I set out to find a simple solution to manage the building of all my offensive C# tools in a central location. The main goal I had for this project was to find a solution that didn’t require a ton of infrastructure to setup. I quickly came across the Azure DevOps platform. It didn’t take long for me to build a pipeline from my GitHub repository and compile my first binary.

This blog is intended to be a quick walk-through on how to setup your first C# build pipeline on Azure DevOps. In this tutorial, I am using the free tier. For more pricing options see <https://azure.microsoft.com/en-us/pricing/details/devops/azure-devops-services/>

**Building Your First Project**

Getting started is as easy as authenticating with your GitHub account. You don’t need a GitHub account though, as you may opt to store your code in an Azure repository. Once you’ve authenticated, click the “New project” button to create your first project.

![](1-9rg6Iz0I23TjFEa3i6XweQ.png)

Enter the details of your new project and select whether you want it public or private. You can still invite people to the project if it is private.

![](1-ZR-b9JNGPvJbHNEOkiYruQ.png)

After you create your project, you’ll be presented with your overview page. On this page, you can link to a wiki or readme, display project stats and invite members to your team.

![](1-p7oOdLTbPc_u0ZbAolTURw.png)

In the “About this project” section, you may use the pencil icon to edit details of the project.

![](1-dhSSHkhO4CPjtug_1ZOYrw.png)

The “About” radio button choices must be present prior to editing the description. In my case, I created a simple wiki page.

![](1-0yZy5WCku873vBKZwS3hOw.png)

Now, you’re all set to start your first pipeline. Navigate to the pipeline section and click “New Pipeline”.

![](1-ayMwAUi27fRXSsC0acHi0Q.png)

The next page is where you have the option of manually modifying your pipeline with YAML files. Or, you may choose the simple route and select “Use classic editor” at the bottom of the page. In my examples, I’ll be using the classic editor.

![](1-ChpROmrHR8TnC7Lct70mTw.png)

Now, you have the option to select where your code resides. In this instance, I’ll choose a GitHub repository from my account.

![](1-JlsPd2Np53iL6dRdrSYB3w.png)

Simply search for and select the repository where the code is.

![](1-eMgeSFX8Oi5FVAXCsJv9PQ.png)![](1-A6mmVlsBw_3-XJY-6UqMog.png)

Next, select your template. I’m using the “.NET Desktop” template.

![](1-JXbTQMhOvYRorQMjm6I8Gw.png)

The nice part about the classic method is that it fills in the Agent tasks for you. However, it defaults to an Agent specification of Visual Studio 2017. You may want to change that to “windows-2019” on the right-hand side of the menu. Select “Save & Queue” to save your settings and begin the build process.

![](1-gnJdy7g6bixTmga5YBr6OA.png)

If you want your builds to execute anytime a change is committed to the selected branch, select the “Triggers” tab and check the “Enable continuous integration” box.

![](1-IJEIRqqjc32zmX47Y8gFmg.png)

After saving, you’ll receive one final prompt before building. Review your settings, add a save comment and then click “save and run”.

![](1-9EfAcfhnQ6achlc7B6t75Q.png)

Your Pipeline will display a blue spinning circle as the agent queues and runs the job. If it fails, you’ll see a red “x”. When it succeeds, a green check mark will appear. Click on the build to see the results.

![](1-7FxiW7cb2XfUpi0XgqFqGA.png)

Here we see that our build completed in 54 seconds and 1 artifact was created. Artifacts are your completed project builds. Click on the “published” link.

![](1-GvTLcRtFz9vJ5aTqpGLwZw.png)

Select each drop-down until you reach your compiled binary as shown.

![](1-bmVJ6vjXo4AQdks1raFCpA.png)

You may click the binary and choose to download it to your local system. I am not currently aware of a method to select all pipelines and download every binary in one package using the free tier of the Azure DevOps service.

**Conclusion**

In this blog post, I covered the basics of using Azure DevOps pipelines to build your .NET tools in a central location. The ability to invite people to your projects is a great way to easily share builds within your team. The ability to collaborate, test, perform continuous integration and build your tools in one easy-to-use platform makes Azure DevOps a great option to try.
