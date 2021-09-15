# HR11-SatelliteSim-Challenge

## Challenge Description
At Vedo Systems we build software for NASA’s manned spaceflight program. To successfully build software that drives and operates vehicles in space, we need a virtualized environment to study how the vehicle will behave from launch, to orbit operations, and through landing.  Not only does this help engineers develop and test the spacecraft, it also provides the necessary tools for training astronauts and flight controllers on the vehicle's control systems.  To accomplish this, we utilize simulations for all phases of spacecraft development from early vehicle design and analysis to flight software verification and certification for flight. This challenge is an opportunity to build a spacecraft simulation using some of the same tools we use to develop high fidelity simulations at Johnson Space Center (JSC). At Johnson Space Center we use the Trick Simulation framework to build spacecraft and space environment simulations. NASA has made Trick open source which makes it available to anyone interested in building up simulations with the same tools we use every day in our work at Vedo Systems.

## Prompt
In the Vedo Systems challenge you will develop a spacecraft simulation which starts with the spacecraft orbiting the moon, reads data from the Trick vehicle Simulation, and redners a spacecraft that shows the state of the spacecraft in real-time (thrusters firing, spacecraft rotating, etc.). You will have the spacecraft execute some simple attitude maneuvers by sending control inputs, and provide a display of the spacecraft trajectory. Bonus goals include providing a method for displaying multiple camera views and/or adding features you think will be useful for ground control to operate spacecraft around the moon.

# Spacecraft Visualizer

Challenge Requirements:

	1. Read data from the trick simulator.  
	2. Setup spacecraft to orbit moon.
	3. Render a spacecraft that shows the state of the spacecraft in real-time, i.e. thrusters firing, spacecraft rotating, etc.
	4. Provide simple attitude maneuver controls.
	5. Provide display of trajectory.

Bonuses:

	1. Provide method of seeing multiple camera views.
	2. Features you think that will be useful for ground control to send spacecraft to/around moon. 

# Getting Started

Ready Environment:
	For your convenience, we have packaged up a VM that can be used.  We highly suggets using this to get started, ask the Vedo team for info on where to find it.
	If you choose to use the VM, there is no need to follow the 'Install Trick' section.

Install Trick 
Automatic:
  WINDOWS:
    
			* Install 'Windows Subsystem for Linux' (WSL): https://docs.microsoft.com/en-us/windows/wsl/install-win10. Note that you will want to download the Ubuntu subsystem.
			* After installation, open WSL and follow the Ubuntu instructions.
      
  LINUX (Ubuntu):
    
			* Navigate to the scripts directory in the repo, i.e. "cd ${WORKSPACE_DIR}/scripts".
			* Run the install_depends script.  "./install_trick.sh ${PATH_TO_WORKSPACE}".  This will make a directory ${PATH_TO_WORKSPACE}/trick where your trick environment will be set.
			* If you want the trick binaries to be directly callable, run "echo PATH=${PATH}:${PATH_TO_WORKSPACE}/trick/bin".
			* A script called run_trick.sh should have been generated in the same directory as this README. Run that to run the sattelite simluator.

If all else fails, manually install.

    * Pull Submodules:
			git submodule init
			git submodule update

		* Make a Patch for Trick:
			cd trick
			git apply ../patches/SIM_satellite.patch

		* https://nasa.github.io/trick/documentation/install_guide/Install-Guide
		* After building trick, you need to go and build SIM_satellite.  This is found in 'trick/trick_sims/SIM_sattelite'.  In this directory, run 'trick-CP'.
		* Run by navigating to '/trick/trick_sims/SIM_sattelite' and calling 'S_main_*.exe RUN_test/input.py'.  A window should appear and after a minute or so the 'Start' button 
			should be enabled.  Click 'Start', now your trick application is running.
		* After you are finished running, click 'Freeze', then click 'Stop'.  This will stop the simulation, and you can close the window.

# Using the Simulator

While your application is responsible for providing a visualization of a spacecraft, we have provided a physics simulator using trick for your convenience.  
We are using NASA's open source simulator 'TRICK'.  Original source can be found at https://github.com/nasa/trick.

You should be mostly interested in how to use trick in general (navigating the GUI and viewing variables), as well as accessing the variable server.  From the GUI
or variable server you will be able to determine mass, dimensions, and state of the satellite in realtime.

See the README in the repo, or the following links for documentation.

	* Tutorials: https://nasa.github.io/trick/tutorial/Tutorial
	* Documenation: https://nasa.github.io/trick/documentation/Documentation-Home
	* Variable Server: https://nasa.github.io/trick/tutorial/TutVariableServer
