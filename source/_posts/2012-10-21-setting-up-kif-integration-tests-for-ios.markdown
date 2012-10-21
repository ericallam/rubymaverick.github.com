---
layout: post
title: "Setting up KIF Integration Tests for iOS"
date: 2012-10-21 12:03
comments: true
categories: [iOS, KIF, Try iOS, Testing, Xcode]
published: true
---

Square released a pretty neat Integration Testing library called [KIF](https://github.com/square/KIF) last year and we have been using it to test the challenges for our upcoming [Try iOS](http://kickstarter.codeschool.com) course on [Code School](http://www.codeschool.com/courses).  The instructions in the KIF [README](https://github.com/square/KIF/blob/master/README.md) on setting up an Xcode 4 project are missing a couple of crucial steps, and after much Googling and Stackoverflowing I finally figured out how to get it to work, so I figured I'd share the process we are using for setting up KIF projects.

I'm assuming you already have an Xcode 4 (version 4.5.1) project that you want to add KIF to. First, if you aren't already working with an Xcode workspace, you will need to create one for this project.  To do so, choose the "Save as Workspace" menu item:

![image](http://f.cl.ly/items/0j1A2b3Y132K2S2F0G1r/Resized%20Screen%202012-10-21%20at%2012.13.49%20PM.png)

You need a workspace so you can manage both your original project (in my example InstagramClone), and the KIF project we are about to add the the workspace. For more on workspaces check out [this Apple doc](http://developer.apple.com/library/ios/#featuredarticles/XcodeConcepts/Concept-Workspace.html).

Next, you'll want to download the KIF project from their [downloads page](https://github.com/square/KIF/downloads), and copy the files inside of a "Frameworks" directory under the Project Root.

![image](http://f.cl.ly/items/3Y1p0H471A381R2I0O43/Resized%20Screen%202012-10-21%20at%2012.19.56%20PM.png)

Next, go back to Xcode and command-click on empty area in the Project Navigator (⌘1), and choose "Add Files to Project":

![image](http://f.cl.ly/items/1H37001a061B460V2o0b/Resized%20Screen%202012-10-21%20at%2012.21.08%20PM.png)

Navigate and select the "KIF.xcodeproj" file under Project Root->Frameworks->KIF.  Now the Project Navigator should look like you have two projects on equal footing:

![image](http://f.cl.ly/items/1t0222422N0u3H143f0q/Resized%20Screen%202012-10-21%20at%2012.27.00%20PM.png)

This is important, at this point it should not look like the "KIF" project is under the "InstagramClone" project.

Next, select your project in the Project Navigator and you should see information about Projects and Targetings in the main content area.  Command-click on your app target and choose "Duplicate":

![image](http://f.cl.ly/items/392A1v290G1t152o1I41/Resized%20Screen%202012-10-21%20at%2012.31.19%20PM.png)

Then choose "Duplicate Only":

![image](http://f.cl.ly/items/042Y0d1D2A2b1e2u1j3x/Resized%20Screen%202012-10-21%20at%2012.32.10%20PM.png)

You should see a new target named "PROJECTNAME Copy". Select the target, press Enter, and change the name to something like "Integration Tests":

![image](http://f.cl.ly/items/3C2g0m0l0k1p3C3h332k/Resized%20Screen%202012-10-21%20at%2012.33.52%20PM.png)

With the "Integration Tests" target selected, go to the "Build Phases" panel, expand the "Link Binary With Libraries" section, and click the little "+" button.  Select the "libKif.a" binary from the list and add it:

![image](http://f.cl.ly/items/3U462R3e0H2h2O091a3N/Resized%20Screen%202012-10-21%20at%2012.37.01%20PM.png)

Still with the "Integration Tests" target selected, go to the "Build Settings" panel.  Make sure you have "All" and "Combined" selected:

![image](http://f.cl.ly/items/0U02000V1U400O1W421u/Resized%20Screen%202012-10-21%20at%2012.41.54%20PM.png)

Search for the "Header Search Paths" and edit the setting to add `$(inherited)` and `$(SRCROOT)/Frameworks/KIF`, like so:

![image](http://f.cl.ly/items/3f1c1g0G3F2F0H0P2X1O/Resized%20Screen%202012-10-21%20at%2012.44.43%20PM.png)

Search for the "Other Linker Flags" setting and edit to add these flags:

![image](http://f.cl.ly/items/0j0g2H371P2I2M3S2y1k/Resized%20Screen%202012-10-21%20at%2012.47.12%20PM.png)

Next, add the `RUN_KIF_TESTS=1` Preprocessor Macro to both the "Release" and "Debug" targets, like so:

![image](http://f.cl.ly/items/3P2U1t1e3p1r272k1a0d/Resized%20Screen%202012-10-21%20at%2012.50.08%20PM.png)

Now that we've configured the "Integration Tests" target correctly, we need to make sure that before Xcode builds the target, it also builds the KIF project.  To do this we need to do a couple of things (this is what you won't find in the instructions provided by Square).

First, we need to edit the "PROJECTNAME Copy" Xcode Scheme to tell it to build KIF.  To do that, go to "Edit Schemes" and select the "PROJECTNAME Copy" scheme.  Choose the "Build" phase.  You should see something like this:

![image](http://f.cl.ly/items/0F0q0G1H2L2d1P440u04/Resized%20Screen%202012-10-21%20at%2012.52.21%20PM.png)

Click on the little "+" button right above the "Manage Schemes" button, and Add the "KIF" target:

![image](http://f.cl.ly/items/3n2i2m260X2P442W050b/Resized%20Screen%202012-10-21%20at%2012.57.12%20PM.png)

Close the "Edit Schemes" dialog and go back to the Project Navigator.  Click and Drag the "KIF" project to under your App project.  In the dialog that appears, select both your app target and the "Integration" Tests target in the "Add to targets" section:

![image](http://f.cl.ly/items/1v2y1w3J2S3v151o1T0Y/Resized%20Screen%202012-10-21%20at%2012.59.29%20PM.png)

After clicking "Finish" your Project Navigator should look like this:

![image](http://f.cl.ly/items/0s3m3l0i0i2K0L2y3w1z/Resized%20Screen%202012-10-21%20at%2012.59.37%20PM.png).

Now you should be able to follow the rest of Square's instructions for adding the Controller, Scenario, and Step files to test your app in the "Example" section of their [README](https://github.com/square/KIF/blob/master/README.md)

