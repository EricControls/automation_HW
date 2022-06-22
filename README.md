# Automation\_hw

Here in Machinalabs we mostly use Beckhoff products for both safety monitoring and automation projects. For our new robots, we are going to make an automated system that controls multiple components such as a hydraulic system, safety monitoring, etc. 
Please feel free to email us if you have any questions and keep in mind that Google and Youtube can help you a lot. 

## Your Job

Today we want to make the first part of this cool project which is controlling the hydraulics via the HMI interface. Beckhoff lets you simulate the whole system without any actual part and debug your work before deploying it to the setup.  
Stuff you need:
- Twincat3
- HMI add on

## Setting up

In the downloading process, you have to make a Beckhoff account. It is free and only needs your email address. 
Please download TwinCAT 3 `XAE` from the following link:
https://www.beckhoff.com/en-us/support/download-finder/software-and-tools/

After you finished the installation, download and install the TE2000 from the following link (you have two options, they are both OK):
https://www.beckhoff.com/en-us/products/automation/twincat/te1xxx-twincat-3-engineering/te2000.html

### Hint
Before you start, you can watch this 5 min tutorial:
https://www.youtube.com/watch?v=kdn2-emwvk8


## Componenets:

- pump
- hydraulic jack that is connected to the pump
- pressure sensor 
- HMI that has one button (name it run)

## E-Bus 

- first, replicate the project on the video. 
- in the solution explorer window, I/O, devices, right-click and select add a new item
- in the new window go to EtherCAT, Ethercat master 
- since it is virtual you can close the popped up window
- we are going to make out a system on this EtherCAT channel 
- now right-click on Device 1(EtherCAT), select Add new item
- add an EK1100 coupler
- connect an EL3024 to the coupler (this is our analog read)
- connect an EL2634 to the coupler (this is the relay that controls the pump)



You are all set!

## Implemetation
Now use this bus and the HMI, and build us a cool project that does the following:
- The system starts with the pump off and waiting for the user to push the button on the HMI
- When the button is pressed, the pump should turn on until we reach the 9V output from the pressure sensor. 
- We want to maintain the pressure between 8-10V so feel free to come up with logic and please explain it. 
- We should implement some safety features such as leak detection, pump malfunctioning, ...
- Now that we have the basics of the project, please make a fancy UI with more than just a button.  
- Please also create this design and let us know how you would improve this project (both hardware and software).



## Extra 
If you made it this far, let's do one extra step, let's try to stop the robot if the system lost the pressure (you should come up with a logic to determine this). As the first step,  we have to connect our Kuka robots to the project. 
Copy the provided `XML` file to the following address: `C:\TwinCAT\Config\IO\Ethercat\`. Now you can add the robot to your project the same way you added Beckhoff parts. 

In the case of failure, we want to set the first bit of io in the robot to `True`, otherwise `False`. On the Kuka side, we already programmed the robot to monitor this value during the operation


## Submission
To submit the homework, please email us the final project. 
