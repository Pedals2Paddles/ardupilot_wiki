.. _3DR_Solo:

================
3DR Solo
================

**DRAFT DRAFT DRAFT DRAFT DRAFT DRAFT DRAFT DRAFT DRAFT DRAFT DRAFT DRAFT**

This article details using Arducopter version 3.5 and higher a 3DR Solo

Overview
========

The 3DR Solo contains, among many things, a Pixhawk 2 flight controller. It comes
with a heavily customized branch of Arducopter 3.3 compiled specifically for the
Solo. When you do the initial pre-flight update, part of that update is this Solo 
branch of Arducopter. It is installed on the Pixhawk, and has all the neccessary
default parameters and customizations baked into it. It is essentially transparent
to the user, taking place behind the curtains.  Since 3DR is no longer in the
consumer UAS business, this branch of Arducopter will not be seeing any further
updates.

Since the Solo uses a Pixhawk flight controller, it is capable of running variations
of Arducopter besides the 3DR Solo branch. This article will focus on installing,
configuring, and operating Arducopter master version 3.5 or higher on a 3DR Solo.
Arducopter master continues where 3DR left off, keeping the Solo a modern, advanced,
and highly capable sUAS.

.. warning::
	This is **not** a one-click process like you may be used to from the 3DR Solo app. There
	are many steps that must be followed to ensure safe and reliable operation on the Solo.


.. warning::
	Today, Arducopter master does not contain the motor pod (ESC) fault protection code
	that is in the customized 3DR Solo branch. The protection is needed for safe and
	reliable flight when using the Solo's stock Pixhawk 2. This protection will be
	added to Arducopter master in the near future. Furthermore, the Pixhawk 2.1 "green cube"
	also rectifies the problem making it no longer a factor. Using Arducopter master on 
	a stock Solo Pixhawk 2 without the protection code is at your own risk and not recommended.
	This warning will be removed once the protection is included in Master.
	

Before you begin
================

Before beginning the upgrade to Arducopter master on your Solo, you need to complete some
requisites.

-  Complete Solo and controller in working order, paired, fully charged.
-  Solo and controller both up to date with current 3DR Solo firmware from the
   initial pre-flight update. The current 3DR firmware is 2.4.2.
-  3DR Solo app on your phone or tablet.
-  Flight tested, working properly in respects. An untested or malfunctioning
   Solo should not be used for this process. It won't fix it.
-  :ref:`Mission Planner <Mission-Planner-Home>` on your windows PC or laptop. Mission 
   Planner will connect to the Solo over your Sololink WiFI network.  Mission Planner
   will be used throughout this article to load firmware and set parameters.

   
Prepar Mission Planner
======================
If you've used Mission Planner in the past, this is probably already done. We need to make
sure Mission Planner is configured for Advanced mode. You only need to do this once.
#. Solo and controller powered on and connected to oneanother.
#. Windows PC WiFi connected to the Sololink WiFI network.
#. Open Mission Planner
#. Click the Config/Tuning button at the top.
#. Select planner on the left.
#. Towards the bottom make sure the basic/advanced dropdown is set for advanced.
   

   
Connect to Solo with Mission Planner
====================================

This step will be referenced many times throughout this article. 

#. Solo and controller powered on and connected to oneanother.
#. Windows PC WiFi connected to the Sololink WiFI network.
#. Open Mission Planner
#. In the top right corner, set the dropdown for UDP.
#. In the top right corner, click the connect button. 
   If prompted for the local port, make sure it says 14550 and click ok.
   

Save Original Solo Parameters
=============================
It is a good practice to save a copy of your original parameter file. It has no immediate purpose
or reference through this process, but it is good to have for troubleshooting should the need arise.
 
#. Connect to Solo with Mission Planner (if you are not already).
#. Click the Config/Tuning button at the top.
#. On the left, select Full Parameter List
#. On the right, click Save To File. Choose a location and save the file as “Solo Original Parameters.param”
#. On the top right, click disconnect.


Install Firmware
================
Now it's time to install the Arducopter master firmware. Version 3.5 and higher is compatible. Firmware
versions prior to 3.5 are untested and not configured to operate on a Solo. Do not use firmware prior to 3.5.
#. Open Mission Planner.
#. In the top right corner, set the dropdown for UDP. Do not connect.
#. At the top, click Initial Setup.
#. On the left, click Install Firmware.
#. Click the picture of a quadcopter labeled APM:Copter V3.5x (or higher)
#. Click yes when asked if you're sure.
#. Click no when asked if this is a Linux board.
#. If prompted for the local port, make sure it says 14550. Click ok.
#. The Solo controller will lose connection with the solo. This is ok.
#. The lights on the solo will begin blinking and changing colors. This is ok.
#. After about a minute, there will be some musical tones.
#. Power off the solo. Wait 10 seconds. Turn the solo back on.
#. The motor pod LEDs will probably all be green. This is ok.
#. The Solo and controller will reconnect to one another.
#. Congratulations, you’re on Arducopter Master! Now it’s time to configure.


Initial Configuration
=====================
These steps will configure Arducopter to operate properly on your Solo. Arducopter master
does not come with all the Solo's required parameters baked in like the original 3DR version
did. So we need to do all that, then do all the calibrations.

#. Connect to Solo with Mission Plannner.
#. Click the Config/Tuning button at the top.
#. On the left, select Full Parameter List
#. On the right, click Refresh Parms
#. On the right, click Save To File.
   Choose a location and save the file as “Solo Master Initial Parameters.param”
#. On the right, click reset to default
#. At the warning prompt, click yes.
#. Mission Planner and the solo controller will disconnect. This is ok.
#. After the beeps, power off the solo and power it back on again.
#. The solo and controller will reconnect to oneanother shortly. Wait for this to continue.
#. Connect to Solo with Mission Planner.
#. At the top, click Config/Tuning.
#. On the right, use the dropdown to select "Solo Master"
#. On the right, click "Load Presaved"
#. Several boxes of parameters will light up green on the list. This is ok.
#. On the right, click Write Parameters.
#. Wait about 30 seconds until the boxes are no longer green.
#. On the top right, click disconnect.
#. Power off the solo. Wait 10 seconds. Power the solo back on.
#. Shortly after the beeps and music, the solo and controller will reconnect with oneanother.
#. Connect with the 3DR Solo app to do a level calibration.
   You should do this on an actual level surface. The more level, the better the AHRS trim will be.
   This is always the case, not just because we’re installing master.
#. Power off the solo. Time to go outside for a compass calibration.
#. Use the 3DR Solo app to do a compass calibration. This must be done outdoors, in a clear area
   away from buildings, vehicles, fences, cement with rebar, etc. This is critical and this is
   always the case, not just because we’re installing master.
#. Close the app once the compass calibration is successful.
#. Power off the Solo, wait 10 seconds, Power the Solo back on.
#. Shortly after the beeps and music, the solo and controller will reconnect with oneanother.
#. Connect to Solo with Mission Planner.
#. Click the Config/Tuning button at the top.
#. On the left, select Full Parameter List
#. On the right, click Save To File.  Choose a location and save the file
   as “Solo Master Complete Parameters.param”
#. Done!

First Flight
============
Congradulations. You're ready to make your first flight using Arducopter master on the Solo.  It is
recommended that your first flight be conducted at a location and time that allows you to test some
basic functions and safety systems.


Solo/Solex App Settings
-----------------------
You will need to go through all the settings in the 3DR Solo App (and the Solex app if you use that too)
to verify and update sliders, options, and settings. Hot items to set include in this sweep include
but are certainly not limited to:
- RTH altitude
- RTH/RTM* & Rewind
- Maximum altitude
- A/B Buttons
- Advanced Flight Modes
- Cycle the speed sliders between turtle and rabbit, then pick a setting.
- GoPo settings

.. warning::
	There is a known bug in the Android 3DR Solo App affecting Return to Me (RTM). It will not use
	the mobile device GPS location no matter what you set the device location settings for. **Do not
	under any circumstances use Return to Me (RTM) in the Android 3DR Solo App**. This is applies
	regardless of running Arducopter master or the Solo branch. This bug is not a factor in the Apple
	3DR Solo app or the Solex app.  It is only in the Android 3DR Solo App.

Go Airborne
-----------
- Take off and verify the Solo flies stable and predicatably. 
- Test all axes... pitch, roll, yaw, climbs, decents, and even all at once.
- Test the flight modes you have on the A & B buttons
- Make sure you are getting a good GPS lock
- Make sure the distance, altitude, speed, modes, and GPS data displayed on the app
  and controller are correct and as you expect to see.
- Let the battery run down to the failsafe while hovering safely nearby. Observe its
  behavior and verify it appropriately executed the RTH/RTM procedure.



Noteworthy Arducopter Parameters
================================
There are over 700 parameters in Arducopter master. For everyday use of the Solo just as you did before,
you still do not need to worry about any of them. They're all pre-set for you in the above processes and
by way of defaults.  However, there are some advanced use cases that may require changing some parameters.
In addition to that, there are many parameters that the Solo requires to be set a certain way. Changing
them (on purpose or by accident) can adversely effect operation.  They key parameters for advanced users
are detailed below.

-	:ref:`FS_THR_ENABLE <FS_THR_ENABLE>` controls how the Solo respond to a loss of signal from the controller.
	0 = No failsafe. This should not be used.
	1 = (Default) RTH/RTM will initiate if GPS available. If no GPS, Solo will land.
	2 = Continue with Smart Shot or auto mission. Otherwise RTH/RTM if GPS available. If no GPS, Solo will land.
	3 = Land, no RTH/RTM. This is useful for indoor flying.

-	:ref:`FS_BATT_ENABLE <FS_BATT_ENABLE>` controls the low battery failsafe options.
	0 = No failsafe. This should not be used unless the use case contraindicates it.
	1 = Land immediately, no RTH/RTM. Useful for indoors.
	2 = (Default) RTH/RTM

-	:ref:`FS_BATT_VOLTAGE <FS_BATT_VOLTAGE>` is the low battery voltage threshold. When the battery drops
	below this point, the low battery beeper sounds and it will do what you have ``FS_BATT_ENABLE`` set for.
	This value is expressed in volts. The default is 14.0. You can adjust this higher or lower depending on
	use case and preference.  Setting it for 0 will disable votlage based alarms and failsafes.

-	:ref:`FS_BATT_MAH <FS_BATT_MAH>` is the battery capacity remaining threshold expressed in milliamphours (MAH).
	When the battery remaining capacity drops below this point, the low battery beeper sounds and it wil do what
	you have ``FS_BATT_ENABLE`` set for. The default is 520. On the solo, that is on average about 1.5 minutes
	of flying time remaining. You can adjust this up or down to fit your preference and use case. Setting it
	for 0 will disable capacity remaining based alarms and failsafes.

-	:ref:`WP_YAW_BEHAVIOR <WP_YAW_BEHAVIOR>` the yaw behavior in auto missions and RTH/RTM.
	0 = No change. The Solo's yaw will keep pointing in the same direction unless you change it.
	1 = Face the next waypoint regardless of direction of flight.
	2 = Face the next waypoint except in RTH/RTM.
	3 = Face forward along the GPS course.

-	







