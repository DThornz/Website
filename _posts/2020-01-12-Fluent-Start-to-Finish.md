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

{% include figure.html image="\assets\imgs\Fluent_Tut\Slide6.jpg" caption="" width="800" height="360" %}

   -   ##### Click the Start Menu and search up "Workbench" and double click "Workbench 2019 R2", or whichever version you see, to start up the program.

{% include figure.html image="\assets\imgs\Fluent_Tut\Slide7.jpg" caption="" width="800" height="360" %}

- ### Transferring Files

  -  #####  On your main computer right click and “Copy” the file or folder you wish to transfer.

  -  ##### On the lab computer right click and “Paste” wherever you want the file or folder to be.

{% include figure.html image="\assets\imgs\Fluent_Tut\Slide8.jpg" caption="" width="800" height="360" %}
---------------------------------------------------------------------------

## Importing Cleaned CAD Model

- ### Selecting and Dragging Workbench Components

  - ##### Drag the "Fluid Flow (Fluent)" component from the "Analysis Systems" tab from the Toolbox section found on th eleft-hand side of the window.

- ### Import CAD Model (.STEP or .SDOC)

  - ##### Right click the geometry node and select Import Geometry --> Browse and locate the location of the CAD file oyu wish to import.

  - ##### In this example the .STEP file for P0088 is used.

- ### Opening ANSYS Meshing

  - ##### Double click the "Mesh" node to open ANSYS Meshing, the geometry node should have a checkmark next to it prior to you doing this.

{% include figure.html image="\assets\imgs\Fluent_Tut\Slide10.jpg" caption="" width="800" height="360" %}
---------------------------------------------------------------------------

## Selecting and Assigning Faces for Boundary Conditions

- ### Moving around work window (camera controls and important selection tools)

  - ##### Scroll wheel – Zoom in/out
  - ##### Shift + Scroll Wheel - Gradual zoom in/out
  - ##### Middle click + Drag - Rotates around the point that was clicked in any direction.
  - ##### Middle click + Drag - Rotates around thiv.	Ctrl + Middle click + Drag – Move the object around the window without changing viewpointe point that was clicked in any direction.

- ### Assigning Face for Inlet

  - ##### Select the green "Face" selection option
  - ##### Left click the planar face chosen as the inlet, hold Ctrl while left clicking to select more than one face if required.
  - ##### Right click and select "Create Named Selection"
    - ###### Type in a name into the field, a suggestion is “Inlet” as ANSYS will recognize this name as an inlet boundary face and auto setup parts later in Fluent to save us time.

- ### Assigning Face(s) for Outlet

  - ##### Repeat the same steps as above but assign the name of “Outlet” instead.
  - ##### If you wish to apply a different outlet boundary condition to each face then name them separately, such as “Outlet-1”, “Outlet-2”, etc.

- ### Assigning Faces for Wall

  - ##### Press Ctrl + A to select all faces
  - ##### Press Ctrl + Left click to deselect the faces that were either Inlet or Outlet.
  - ##### Create a Named Selection as you did above but name it "Wall"

{% include figure.html image="\assets\imgs\Fluent_Tut\Slide12.jpg" caption="" width="800" height="360" %}