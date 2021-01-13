---
title: Guide for Conducting an ANSYS Fluent Simulation – From Start to Finish
categories:
- Fluent
- ANSYS
feature_image: "https://picsum.photos/2560/600?image=872"

---

<p align=center> ~Refer to the PowerPoint for accompanying pictures for each step~ </p>

## Accessing ANSYS through FIU VPN

- ### Setting up FIU VPN

  - ##### Install AnyConnect

    - Microsoft Windows (https://network.fiu.edu/downloads/anyconnect-win.msi)
    - MAC OS X (https://network.fiu.edu/downloads/anyconnect-macos.dmg)

- ### Logging In 

  - ##### Enable TwoFactor Authentication

    1. Visit https://login.fiu.edu/enroll
    2. Log in using your myFIU username and password
    3. When prompted, enter the phone number of the device you would like to enroll in two-factor authentication (FIU number will not be accepted)
    4. Specifiy what type of device corresponds to the enrolled number
    5. When prompted enter the code you received
    6. You are now enrolled in two-factor authentication

  - ##### Open Up the app called Cisco AnyConnect Secure Mobility Client

  - ##### Type in "vpn.fiu.edu" and press the connect button

  - ##### Login follows the following format:

    1. Username: myFIU username
       a. Ex: amirza
     2. Password: myFIU password
        a. If you forget your myFIU password reset your password here
          https://login.fiu.edu/account/recovery/ 
     3. Second Password: DUO Mobile six-digit code
        a. Open up the DUO Mobile application on your phone, the code shown is the one 
             that should be used here.

{% include figure.html image="\assets\imgs\Fluent_Tut\Slide5.jpg" caption="" width="800" height="360" %}

- ### Accessing Computer

  -  ##### Visit https://remoteaccess.labstats.com/fiu.cec

  -  ##### Select any computer clicking the "Connect" button

  -  ##### Download the associated connection file, run it, and press Connect

  -  ##### Select "More Choices" and "Use a Different Account"

  -  ##### Your login info is the same as if you were on a lab PC at FIU but with a slight difference in the username:

     1. Username: EICAD\yournovellusername

     2. Password: yournovellpassword

        ​	a. If you forget your Novell password, reset your password here 

        ​		https://eic.fiu.edu/change-network-password/

   -   ##### Click the Start Menu and search up "Workbench" and double click "Workbench 2019 R2", or whichever version you see, to start up the program.

- ### Transferring Files

  -  #####  On your main computer right click and “Copy” the file or folder you wish to transfer.

  -  ##### On the lab computer right click and “Paste” wherever you want the file or folder to be.

---------------------------------------------------------------------------

## Importing Cleaned CAD Model

- ### Selecting and Dragging Workbench Components

  - ##### Drag the "Fluid Flow (Fluent)" component from the "Analysis Systems" tab from the Toolbox section found on th eleft-hand side of the window.

- ### Import CAD Model (.STEP or .SDOC)

  - ##### Right click the geometry node and select Import Geometry --> Browse and locate the location of the CAD file oyu wish to import.

  - ##### In this example the .STEP file for P0088 is used.

- ### Opening ANSYS Meshing

  - ##### Double click the "Mesh" node to open ANSYS Meshing, the geometry node should have a checkmark next to it prior to you doing this.

---------------------------------------------------------------------------