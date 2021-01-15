---
title: Guide for Conducting an ANSYS Fluent Simulation – From Start to Finish
categories:
- Fluent
- ANSYS
feature_image: "https://www.lss.ovgu.de/lss_media/Downloads/Forschung/Medizinsche+Str%C3%B6mungen/Medizinsche+Str%C3%B6mungen+3-height-333-width-593-p-1982.png"

---

<center>
<script src="https://gumroad.com/js/gumroad.js"></script>
<a class="gumroad-button" href="https://gum.co/ANSYSFluentTut" target="_blank">Obtain the files for the below tutorial by clicking here, pay what you want! $0, $5, etc </a>
</center>


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

    Username: myFIU username
       a. Ex: amirza
    Password: myFIU password
        a. If you forget your myFIU password reset your password here
          https://login.fiu.edu/account/recovery/ 
    Second Password: DUO Mobile six-digit code
        a. Open up the DUO Mobile application on your phone, the code shown is the one 
             that should be used here.

{% include figure.html image="\assets\imgs\Fluent_Tut\Slide5.jpg" caption="" width="800" height="360" %}

- ### Accessing Computer

  -  ##### Visit https://remoteaccess.labstats.com/fiu.cec

  -  ##### Select any computer clicking the "Connect" button

  -  ##### Download the associated connection file, run it, and press Connect

  -  ##### Select "More Choices" and "Use a Different Account"

  -  ##### Your login info is the same as if you were on a lab PC at FIU but with a slight difference in the username:

     Username: EICAD\yournovellusername

     Password: yournovellpassword

        ​	If you forget your Novell password, reset your password here 

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

  - ##### Right click the geometry node and select Import Geometry → Browse and locate the location of the CAD file oyu wish to import.

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
---------------------------------------------------------------------------

## Producing an Adequate Mesh for Simulation

- ### Select the Mesh node under the Project Tree to the left
- ### Set the following settings under Defaults
  - ##### Physics Preference: CFD
  - ##### Solver Preference: Fluent
  - ##### Element Order: Quadratic
- ### Set the following settings under Sizing
  - ##### Capture Curvature: Yes
  - ##### Capture Proximity: Yes 
- ### Set the following settings under Inflation
  - ##### Use Automatic Inflation: All Faces in Chosen Named Selection
  - ##### Named Selection: Wall
- ### Under the "Mesh" ribbon tab, left click the "Generate" button
- ### If you look under Statistics you can see the number of Nodes/Elements used to Mesh your model, here are my values:
  - ##### Nodes: 1,118,749
  - ##### Elements: 564, 504

{% include figure.html image="\assets\imgs\Fluent_Tut\Slide14.jpg" caption="" width="800" height="360" %}
{% include figure.html image="\assets\imgs\Fluent_Tut\Slide15.jpg" caption=" Finalized Mesh" width="800" height="360" %}

---------------------------------------------------------------------------

## Setting Up Simulation
- ### Fluent Launcher
  - ##### From Workbench double click the Setup node
  - ##### Fluent Launcher should appear, ensure the following settings:
    - ###### Double Precision: Checkmarked
    - ###### Solver Processes: Put the number of cores your PC has (Default is 1)
    - ###### Solver GPGPUs per Machine: Put the number of GPUs your PC has (Default is 0 or None)

{% include figure.html image="\assets\imgs\Fluent_Tut\Slide17.jpg" caption="" width="800" height="360" %}

{% include figure.html image="\assets\imgs\Fluent_Tut\Slide18.jpg" caption="Fluent Startup Screen" width="800" height="360" %}

- ### General
  - ##### Scale
    - ##### Click Scale... and set "View Length Unit In" to mm
  - ##### Check:
    - ###### Click Check and look at the console window for any warnings or errors.
      - If there are any issues, they would be mesh related, try to adjust mesh options or Google the particular problem.
  - ##### Time
    - ##### You can select for a Steady-State or Transient simulation, for this example we shall go with Transient.

{% include figure.html image="\assets\imgs\Fluent_Tut\Slide19.jpg" caption="" width="800" height="360" %}

- ### Model
  - ###### Double click "Viscous" and ensure that it is set to SST k-omega

{% include figure.html image="\assets\imgs\Fluent_Tut\Slide20.jpg" caption="" width="800" height="360" %}

- ### Materials
  - ###### Under Material → Fluid → Air, double click Air
  - ###### Edit name to blood
  - ###### Set Density to 1060 kg/m<sup>3</sup>
  - ###### Set Viscosity to 0.0033 kg/m-s
  - ###### Click "Change/Create" to make this new blood fluid

{% include figure.html image="\assets\imgs\Fluent_Tut\Slide21.jpg" caption="" width="800" height="360" %}

- ### Boundary Conditions
  - ###### Inlet - By default it is assumed to be a velocity condition, you have 3 options for how to set it
    - Constant -  This uses a constant inlet velocity for the entirety of the simulation, a simple example would be 0.1 m/s.
    - Expression -  This lets you write a more complex expression to put at the inlet condition.
      - Ex:  IF(t<0.333[s],0.1[m/s]*sin(9.424*t/1[s]) ,0[m/s])
       
      - This is an IF statement that says “If the simulation time is less than 0.  333 seconds have the inlet velocity be defined by 0.1[m/s]*sin(9.424*t/1[s]) otherwise (meaning the time is greater than 0.333 seconds) let the velocity be 0 [m/s]
    - Custom - This lets you prescribe your unique inlet condition that cannot be easily defined with an expression, such as from a text or CSV file.
      - A custom inlet velocity condition can be written to a text file with the following format:


              ((profilename transient n periodic)
              (time
              1 
              2
              3
              )
              (vel
              10
              20
              30
              )
              )


        - Profilename - General name for the profile, can be anything.
        - Transient - Tell Fluent this is a transient profile
        - N - Number of points, in the above example 3
        - Periodic -  Marker for if the waveform is periodic, can be either 0 or 1 for yes or no.
      - Once the profile has been made and saved as a text file go to File → Read → Profile
      - Set File Types to All
      - Locate the text file and click OK
      - Go to the Inlet boundary condition velocity box and there should now be an option to select the profile you just read as the input with the name of “profilename vel”, ex: “Inlet_Velocity vel”

{% include figure.html image="\assets\imgs\Fluent_Tut\Slide22.jpg" caption="Constant" width="800" height="360" %}
{% include figure.html image="\assets\imgs\Fluent_Tut\Slide23.jpg" caption="Expression" width="800" height="360" %}
{% include figure.html image="\assets\imgs\Fluent_Tut\Slide24.jpg" caption="Profile Text Format" width="800" height="360" %}
{% include figure.html image="\assets\imgs\Fluent_Tut\Slide25.jpg" caption="Importing Profile" width="800" height="360" %}
{% include figure.html image="\assets\imgs\Fluent_Tut\Slide26.jpg" caption="Selecting Profile" width="800" height="360" %}


  - ###### Outlet - Ensure "Guage Pressure (pascal)" is set to 0
  - ###### Wall -  Ensure "Wall Motion" is set to "Stationary Wall" 

{% include figure.html image="\assets\imgs\Fluent_Tut\Slide27.jpg" caption="" width="800" height="360" %}

- ### Methods
  - ###### Scheme - Simple
  - ###### Pressure - Second Order
  - ###### Momentum -  Second ORder Upwind 
  - ###### Turbulent Kinetic Energy -  Second Order Upwind
  - ###### Specific Dissipation Rate -  Second Order Upwind
  - ###### Transient Formulation - Second Order Implicit 

- ### Monitor
  - ###### Residuals
    - Set all equation's absolute criteria for convergence to 1e-6, by default they should be set to 0.001.

{% include figure.html image="\assets\imgs\Fluent_Tut\Slide27.jpg" caption="" width="800" height="360" %}

- ### Run Calculation
  - ###### Click Check Case and make sure a box saying “No recommendations to make at this time” shows up, if not address the suggestions given to you for a better simulation.
  - ###### Time Advancement
    - Type - Fixed
    - Parameters
      - Number of Time Steps - 10
      - Time Step Size(s) - 0.1
        - Note: a x b = total time, so 10 x 0.1 =  1 second of simulation time with 10 "snap shots" of data in between.
      - Max Iterations / Time Step - 40
  - ###### Solution Processing
    - Statistics
      - Checkmark "Data Sampling for Time Statistics"
      - Sampling Interval - 1
    - Data File Quantities
      - Under additional quantities you can select additional quantities to track in your simulation. An example would be “Mean Wall Shear Stress” to track the accumulating average of WSS on all surfaces of your model.

{% include figure.html image="\assets\imgs\Fluent_Tut\Slide30.jpg" caption="" width="800" height="360" %}

- ### Initialization
  - ###### Initializaiton Methods - Hybrid Initialization
  - ###### Select Initialize and check console for an output similar to this

               
                Initialize using the hybrid initialization method.

                Checking case topology... 
                -This case has both inlets & outlets 
                -Pressure information is not available at the boundaries.
                Case will be initialized with constant pressure

                  iter		scalar-0

                  1		1.000000e+00
                  2		2.476617e-04
                  3		4.185013e-05
                  4		1.750290e-05
                  5		4.053254e-06
                  6		1.225216e-06
                  7		3.535340e-07
                  8		1.098154e-07
                  9		3.394697e-08
                  10		1.149003e-08

                Hybrid initialization is done.
               
{% include figure.html image="\assets\imgs\Fluent_Tut\Slide29.jpg" caption="" width="800" height="360" %}

- ### Calculation Activities
  - ###### Autosave (Every Time Steps)
    - Set "Save File Every" to 1 Time Steps
    - Check "Data File Quantities", everything that is selected will be saved for Post-Processing. 

{% include figure.html image="\assets\imgs\Fluent_Tut\Slide31.jpg" caption="" width="800" height="360" %}

{% include figure.html image="\assets\imgs\Fluent_Tut\Slide32.jpg" caption="" width="800" height="360" %}

- ### Conduct Simulation
  - ###### When ready click on "Run Calculation" and the Calculate button under "Solution Advancement".

- ### Convergence Graph
  - ###### As the simulation is solving a Convergence graph should appear showing how the residuals (continuity, xyz velocities, k, and omega) are converging per iteration. A time step will be completed once all of them reach the criteria set in (g), in our case 1e-6. Once all time-steps have converged then the simulation is complete.
  - ###### It is normal for transient simulations to oscillate up and down. Continuous downward trends for convergence are generally only seen in Steady-State simulations.

{% include figure.html image="\assets\imgs\Fluent_Tut\Slide33.jpg" caption="" width="800" height="360" %}
---------------------------------------------------------------------------

## Verification
- ### Mass Conservation
  - ##### To verify if the simulation is complete numerically go to Results → Reports → Fluxes
  - ##### For options select "Mass Flow Rate"
  - ##### For boundaries select your inlet and outlet(s).
  - ##### Click compute, the result shown in "Net Results (kg/s)" should be very small, ex: 1e-6 or less.
  - ##### This ensures that all the flow that has entered the fluid domain has also left it by the end of the simulation.

{% include figure.html image="\assets\imgs\Fluent_Tut\Slide35.jpg" caption="" width="800" height="360" %}

---------------------------------------------------------------------------

## Post-Processing

{% include figure.html image="\assets\imgs\Fluent_Tut\Slide37.jpg" caption="" width="800" height="360" %}

- ### Setting Units 
  - ##### Edit → Options → Units → Custom
    - You can set the units for base units here, example:
      - Length: mm
      - Pressure: Pa
      - Velocity: cm/s
    - Click Apply and OK 


{% include figure.html image="\assets\imgs\Fluent_Tut\Slide38.jpg" caption="" width="800" height="360" %}


- ### Wall Shear Stress
  - ##### Create Contour
    - Insert → Contour → Name it what you want ex: WSS
  - ##### Contour Details
    - Click on the Contour you just created under User Locations and Plots
    - Set the following for Geometry 
      - Domain: All Domains
      - Locations: Wall
      - Variable: Wall Shear.Trnavg (This is available if you set the statistic up properly back in setup while exporting the data)
      - Range: Global
      - \# of Contours: 100
    - Set the following for Render
      - Transparency: 0.0
      - Lightning: Unmarked
      - Show Contour Lines: Unmarked
  - ##### Legend Details
    - Select Default Legend View 1
    - Set the following for Appearance
      - Size: 0.8
      - Aspect: 0.07
      - Precision: 2 Fixed
      - Value Ticks: 5

{% include figure.html image="\assets\imgs\Fluent_Tut\Slide39.jpg" caption="" width="800" height="360" %}

{% include figure.html image="\assets\imgs\Fluent_Tut\Slide41.jpg" caption="" width="800" height="360" %}

- ### Velocity Plane + Streamline
  - ##### Create Plane
    - Insert → Location → Plane → Name it what you want ex: Plane 1
  - ##### Edit Plane Details
    - Click on the Plane you just created under User Locations and Plots
    - Under Geometry set the following:
      - Method: YZ Plane
      - X: 950 [mm]
  - ##### Create Contour on Plane
    - Repeat from above but have the plotted variable be Velocity.Trnavg instead.
  - ##### Create Streamline
    - Insert → Streamline → Name it what you want ex: Streamline 1
  - ##### Edit Streamline Details
    - Click on the Streamline you just created under User Locations and Plots
    - Under Geometry set the following:
      - Type: Surface Streamline
      - Surfaces: Plane 1
      - Start From: Equally Spaces Samples
      - \# of Points: 50
      - Variable: Velocity
      - Direction: Forward and Backward
    - Under Color set the following:
      - Mode: Constant
      - Color: Black
    - Click Apply to see the streamlines on top of the contour we made above.

{% include figure.html image="\assets\imgs\Fluent_Tut\Slide42.jpg" caption="" width="800" height="360" %}
{% include figure.html image="\assets\imgs\Fluent_Tut\Slide43.jpg" caption="" width="800" height="360" %}
{% include figure.html image="\assets\imgs\Fluent_Tut\Slide44.jpg" caption="" width="800" height="360" %}

- ### Exporting Images/Videos
  - ##### File → Save Image
    - File: This is the file path for where the image will be saved
    - Format: PNG is preferred
    - Use Screen Capture: Unmarked
    - White Background: Checkmarked 
    - Enhanced Output (Smooth Edges): Checkmarked
    - Use Screen Size: Unmarked
    - Width/Height: Set this to however large you want the image; a suggestion is a large square such as 1280 x 1280.
    - Click Save to save the image to folder specified in (a)

{% include figure.html image="\assets\imgs\Fluent_Tut\Slide40.jpg" caption="" width="800" height="360" %}