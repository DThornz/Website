---
title: Guide for Conducting an ANSYS Fluent Simulation – From Start to Finish
categories:
- Fluent
- ANSYS
feature_image: "https://picsum.photos/2560/600?image=872"
---

~Refer to the PowerPoint for accompanying pictures for each step~

1. Accessing ANSYS through FIU VPN
  1. Setting up FIU VPN
    1. Install AnyConnect
      1. Microsoft Windows (https://network.fiu.edu/downloads/anyconnect-win.msi)
      2. MAC OS X (https://network.fiu.edu/downloads/anyconnect-macos.dmg)
  2. Logging in
    1. Enable TwoFactor Authentication
      1. Visit login.fiu.edu/enroll
      2. Log in using your myFIU username and password
      3. When prompted, enter the phone number of the device you would like to enroll in two-factor authentication (FIU numbers will not be accepted).
      4. Specify what type of device corresponds to the enrolled number
      5. When prompted, enter the code you received
      6. You are now enrolled in two-factor authentication
    2. Open up the app called Cisco AnyConnect Secure Mobility Client
    3. Type in &quot;vpn.fiu.edu&quot; and press the connect button.
    4. Login follows the following format:
      1. Username: myFIU username
        1. Ex: amirza
      2. Password: myFIU password
        1. If you forget your myFIU password reset your password here [https://login.fiu.edu/account/recovery/](https://login.fiu.edu/account/recovery/)
      3. Second Password: DUO Mobile six-digit code
        1. Open up the DUO Mobile application on your phone, the code shown is the one that should be used here.
  3. Accessing Computer
    1. Visit [https://remoteaccess.labstats.com/fiu-cec](https://remoteaccess.labstats.com/fiu-cec)
    2. Select any computer by clicking the &quot;Connect&quot; button
    3. Download the associated connection file, run it, and press Connect
    4. Select &quot;More Choices&quot; and &quot;Use a Different Account&quot;.
    5. Your login info is the same as if you were on a lab PC at FIU but with a slight difference in the username:
      1. Username: EICAD\yournovellusername
      2. Password: yournovellpassword
        1. If you forget your Novell password reset your password here [https://eic.fiu.edu/change-network-password/](https://eic.fiu.edu/change-network-password/)
    6. Click the Start Menu and search up &quot;Workbench&quot; and double click &quot;Workbench 2019 R2&quot;, or whichever version you see, to startup the program.
  4. Transferring Files
    1. On your main computer right click and &quot;Copy&quot; the file or folder you wish to transfer.
    2. On the lab computer right click and &quot;Paste&quot; wherever you want the file or folder to be.
2. Importing cleaned CAD model
  1. Selecting and Dragging Workbench components
    1. Drag the &quot;Fluid Flow (Fluent)&quot; component from the &quot;Analysis Systems&quot; tab from the Toolbox section found on the left-hand side of the window.
  2. Import CAD model (.STEP or .SDOC)
    1. Right click the geometry node and select Import Geometry  Browse and locate the location of the CAD file you wish to import.
    2. In this example the .STEP file for P0088 is used.
  3. Opening ANSYS Meshing
    1. Double click the &quot;Mesh&quot; node to open ANSYS Meshing, the geometry node should have a checkmark next to it prior to you doing this.
3. Selecting and assigning faces for boundary conditions
  1. Moving around work window (camera controls and important selection tools)
    1. Scroll wheel – Zoom in/out
    2. Shift + Scroll Wheel - Gradual zoom in/out
    3. Middle click + Drag - Rotates around the point that was clicked in any direction.
    4. Ctrl + Middle click + Drag – Move the object around the window without changing viewpoint
  2. Assigning face for inlet
    1. Select the green &quot;Face&quot; selection option
    2. Left click the planar face chosen as the inlet, hold Ctrl while left clicking to select more than one face if required.
    3. Right click and select &quot;Created Named Selection&quot;
      1. Type in a name into the field, a suggestion is &quot;Inlet&quot; as ANSYS will recognize this name as an inlet boundary face and auto setup parts later in Fluent to save us time.
  3. Assigning faces for outlet
    1. Repeat the same steps as for (b) above but assign the name of &quot;Outlet&quot; instead.
    2. If you wish to apply a different outlet boundary condition to each face then name them separately, such as &quot;Outlet-1&quot;, &quot;Outlet-2&quot;, etc.
  4. Assigning faces for wall
    1. Press Ctrl + A to select all faces
    2. Press Ctrl + Left click to deselect the faces that were either Inlet or Outlet.
    3. Created a Named selection as you did in (b) but name it &quot;Wall&quot;
4. Producing an adequate mesh for simulationG
  1. Select the Mesh node under the Project tree to the left
  2. Set the following settings under Defaults
    1. Physics Preference: CFD
    2. Solver Preference: Fluent
    3. Element Order: Quadratic
  3. Set the following settings under Sizing
    1. Capture Curvature: Yes
    2. Capture Proximity: Yes
  4. Set the following settings under Inflation
    1. Use Automatic Inflation: All Faces in Chosen Named Selection
    2. Named Selection: Wall
  5. Under the &quot;Mesh&quot; ribbon tab, left click the &quot;Generate&quot; button
  6. As a reference you if you look under Statistics you can see the number of Nodes/Elements used to Mesh your model, here are my values:
    1. Nodes: 1,118,749
    2. Elements: 564,504
5. Setting up simulation
  1. Fluent Launcher
    1. From Workbench double click the Setup node
    2. Fluent Launcher should appear, ensure the following settings:
      1. Double Precision: Check Marked
      2. Solver Processes: Put the number of cores you have on your PC (Default is 1)
      3. Solver GPGPUs per Machine: Put the number of GPUs you have on your PC (Default is 0 or None)
  2. General
    1. Scale
      1. Click Scale… and set &quot;View Length Unit In&quot; to mm
    2. Check
      1. Click Check and look at the console window for any warnings or errors.
        1. If there are issues, they would be mesh related, try to adjust mesh options or Google the particular problem, otherwise contact Dr. Ramaswamy.
    3. Time
      1. You can select for a Steady-State or Transient simulation, for this example we shall go with Transient.
  3. Model
    1. Double click &quot;Viscous&quot; and ensure that it is set to SST k-omega.
  4. Materials
    1. Under Material  Fluid  Air, double click Air.
    2. Edit name to blood
    3. Set Density to 1060 kg/m3
    4. Set Viscosity to 0.0033 kg/m-s
    5. Click &quot;Change/Create&quot; to make this new blood fluid
  5. Boundary Conditions
    1. Inlet – By default it is assumed to be a velocity condition, you have 3 options for how to set it.
      1. Constant – This uses a constant inlet velocity for the entirety of the simulation, a simple example would be 0.1 m/s.
      2. Expression – This lets you write a more complex expression to put at the inlet condition.
        1. Ex: IF(t\&lt;0.333[s],0.1[m/s]\*sin(9.424\*t/1[s]) ,0[m/s])
        2. This is an IF statement that says &quot;If the simulation time is less than 0.333 seconds have the inlet velocity be defined by 0.1[m/s]\*sin(9.424\*t/1[s]) otherwise (meaning the time is greater than 0.333 seconds) let the velocity be 0 [m/s]
      3. Custom – This lets you prescribe your unique inlet condition that cannot be easily defined with an expression, such as from a text or CSV file.
        1. A custom inlet velocity condition can be written to a text file with the following format:


          1. Profilename – General name for the profile, can be anything
          2. Transient - Tell Fluent this is a transient profile
          3. N – Number of points, in the example 3
          4. Periodic – Marker for if the waveform is periodic, can be either 0 or 1 for yes or no.
        1. Once the profile has been made and saved as a text file go to File  Read  Profile
        2. Set File Types to All
        3. Locate the text file and click OK
        4. Go to the Inlet boundary condition velocity box and there should now be an option to select the profile you just read as the input with the name of &quot;profilename vel&quot;, ex: &quot;Inlet\_Velocity vel&quot;
    1. Outlet – Ensure Gauge Pressure (pascal) is set to 0.
    2. Wall – Ensure &quot;Wall Motion&quot; is set to &quot;Stationary Wall&quot;
  6. Methods
    1. Scheme – Simple
    2. Pressure - Second Order
    3. Momentum - Second Order Upwind
    4. Turbulent Kinetic Energy - Second Order Upwind
    5. Specific Dissipation Rate - Second Order Upwind
    6. Transient Formulation - Second Order Implicit
  7. Monitor
    1. Residuals
      1. Set all equation&#39;s absolute criteria for convergence to 1e-6, be default they should be set to 0.001.
  8. Run Calculation
    1. Click Check Case and make sure a box saying &quot;No recommendations to make at this time&quot; shows up, if not address the suggestions given to you for a better simulation.
    2. Time Advancement
      1. Type – Fixed
      2. Parameters
        1. Number of Time Steps – 10
        2. Time Step Size (s) – 0.1
          1. Note: a\*b = total time, so 10\*0.1 = 1 second of simulation time with 10 &quot;snap shots&quot; of data in between.
        3. Max Iterations / Time Step – 40
    3. Solution Processing
      1. Statistics
        1. Checkmark &quot;Data Sampling for Time Statistics&quot;
        2. Sampling Interval – 1
      2. Data File Quantities
        1. Under additional quantities you can select additional quantities to track in your simulation. An example would be &quot;Mean Wall Shear Stress&quot; to track the accumulating average of WSS on all surfaces of your model.
    4. Initialization
      1. Initialization Methods – Hybrid Initialization
      2. Select Initialize and check console for an output similar to this

Initialize using the hybrid initialization method.

Checking case topology...

-This case has both inlets &amp; outlets

-Pressure information is not available at the boundaries.

Case will be initialized with constant pressure

iter scalar-0

1 1.000000e+00

2 2.476617e-04

3 4.185013e-05

4 1.750290e-05

5 4.053254e-06

6 1.225216e-06

7 3.535340e-07

8 1.098154e-07

9 3.394697e-08

10 1.149003e-08

Hybrid initialization is done.

  5. Calculation Activities
    1. Autosave (Every Time Steps)
      1. Set &quot;Save Data File Every&quot; to 1 Time Steps
      2. Check &quot;Data File Quantities&quot;, everything that is selected will be saved for Post-Processing.
  6. Conduct Simulation
    1. When ready click on &quot;Run Calculation&quot; and the Calculate button under &quot;Solution Advancement&quot;.
  7. Convergence Graph
    1. As the simulation is solving a Convergence graph should appear showing how the residuals (continuity, xyz velocities, k, and omega) are converging per iteration. A time step will be completed once all of them reach the criteria set in (g), in our case 1e-6. Once all time-steps have converged then the simulation is complete.
    2. It is normal for transient simulations to oscillate up and down. Continuous downward trends for convergence are generally only seen in Steady-State simulations.
9. Verification
  1. Mass Conservation
    1. To verify if the simulation is complete numerically go to Results  Reports  Fluxes
    2. For options select &quot;Mass Flow Rate&quot;
    3. For boundaries select your inlet and outlet(s).
    4. Click compute, the result show in &quot;Net Results (kg/s)&quot; should be very small, ex: 1e-6 or less.
    5. This ensures that all the flow that has entered the fluid domain has also left it by the end of the simulation.
10. Post – Processing
  1. Setting Units
    1. Edit  Options  Units  Custom
      1. You can set the units for base units here, example:
        1. Length: mm
        2. Pressure: Pa
        3. Velocity: cm/s
      2. Click Apply and OK
  2. Wall Shear Stress
    1. Create Contour
      1. Insert  Contour  Name it what you want ex: WSS
    2. Contour Details
      1. Click on the Contour you just created under User Locations and Plots
      2. Set the following for Geometry
        1. Domain: All Domains
        2. Locations: Wall
        3. Variable: Wall Shear.Trnavg (This is available if you set the statistics up properly back in setup and while exporting the data)
        4. Range: Global
        5. (# of Contours): 100
      3. Set the following for Render
        1. Transparency: 0.0
        2. Lightning: Unmarked
        3. Show Contour Lines: Unmarked
    3. Legend Details
      1. Select Default Legend View 1
      2. Set the following for Appearance
        1. Size: 0.8
        2. Aspect: 0.07
        3. Precision: 2 Fixed
        4. Value Ticks: 5
  3. Velocity Plane + Streamline
    1. Create Plane
      1. Insert  Location  Plane  Name it what you want ex: Plane 1
    2. Edit Plane Details
      1. Click on the Plane you just created under User Locations and Plots
      2. Under Geometry set the following:
        1. Method: YZ Plane
        2. X: 950 [mm]
    3. Create Contour on Plane
      1. Repeat (bi) and (bii) from above but have the plotted variable be Velocity.Trnavg instead.
    4. Create Streamline
      1. Insert  Streamline  Name it what you want ex: Streamline 1
    5. Edit Streamline Details
      1. Click on the Streamline you just created under User Locations and Plots
      2. Under Geometry set the following:
        1. Type: Surface Streamline
        2. Surfaces: Plane 1
        3. Start From: Equally Spaced Samples
        4. # of Points: 50
        5. Variable: Velocity
        6. Direction: Forward and Backward
      3. Under Color set the following:
        1. Mode: Constant
        2. Color: Black
      4. Click Apply to see the streamlines on top of the contour we made in (iii)
  4. Exporting Images/Videos
    1. Create Image
      1. File  Save Image
        1. File: This is the file path for where the image will be saved
        2. Format: PNG is preferred
        3. Use Screen Capture: Unmarked
        4. White Background: Check marked
        5. Enhanced Output (Smooth Edges): Check marked
        6. Use Screen Size: Unmarked
        7. Width/Height: Set this to however large you want the image; a suggestion is a large square such as 1280 x 1280.
        8. Click Save to save the image to the folder specified in (a)