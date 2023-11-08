# HVAC-System (2022)

## Project Scope and Content
This was my first capstone project for a Computer Logic Class. The goal of this project is to design part of the controller to regulate temperature as part of the design of a thermostat. As required for all HVAC (Heating, Ventilation, and Air Conditioning) systems, the controller must be designed so that the equipment is not damaged. </br> </br>
The controller has two inputs and two outputs. The inputs are R, for Raise the temperature, and L, to Lower the temperature. These are driven by two sources. There is a sensor that monitors the temperature and compares it to the temperature specified by the user. There is also the ability of the user to manually set R or L to override the current setting. The outputs are H for Heat, to turn on the heating system when it is too cold, and C for Cool, to turn on the cooling system when it is too hot. </br> </br>

The inputs function as follows:
1. R=0, L=0 means the temperature is good.
2. R=0, L=1 means the temperature is too high.
3. R=1, L=0 means the temperature is too low.
4. R=1, L=1 is undefined. It is up to you to define how this works. </br> </br>

These are important rules which MUST be followed:
1. Rule 1: H and C may never be 1 at the same time. That is, the cooler and heater can’t be enabled simultaneously.
2. Rule 2: There MUST be 3 clocks when both H and C are 0 when switching between heating and cooling or vice versa. For example, if the inputs change from RL=10 to RL=01, there must be 3 clocks during which H is 0 and C remains 0 before C can transition to 1. These 3 clocks are a “buffer” to make sure the equipment isn’t damaged while switching from one mode to the other.
   - (The same HVAC equipment is often used to both cool and heat homes by reversing the way it operates. Switching over from cooling to heating or vice versa too quickly may seriously damage the equipment. As a result, thermostats have built in delays when switching between heating and cooling.) </br> </br>

## Stakeholders
1. **Chenoa Toledo:** This customer plans on using the cooling system more than the heating system of this HVAC system. The environment will most likely be in a geographical location where it is more hot than cold. The customer also plans on having the AC running most of the day (and keeping it on the “cool” setting for the most part). But, this customer needs to be able to save money while doing so. 
2. **Katie McFarland:** This customer prefers special features when it comes to AC designs. For example, energy saver option for when she just wants the room to be moderately cool, a timer option to be able to have the fan turn off in the middle of the night, and etc.  
3. **Dhanya Jakkula:** Customer also most likely will use the cooling system more than the heating system. She prefers her AC more simpler, though. She does not care much for the fancy features. 

_A bulk of the responses from clients mentioned wanting to keep the cooling system on for most of the time. Therefore, the proposed design keeps the AC running until someone manually holds down both input buttons to turn off the machine. This machine is mainly expected to be implemented in a common apartment household for college individuals. It’s a quick design meant for simplicity (for the user)._

## Brainstorming 

### Design 1
Assumptions: For this system, I decided that it would be best to have the R=L=1 state to be the clear/reset input. For some of the clients that I interviewed for this project, they said that even though they’d prefer to have the AC running for most of the time (primarily the cooler), it is also important for them to save money. Due to this financial limitations, a power on/off state is needed. </br> </br>
![image](https://github.com/KayeJD/HVAC-System/assets/139111295/a9f3e39b-7209-49f5-88e7-67973d13238c)

### Design 2
Assumptions: For the case in which both R and L are both one, I decided to have it be a buffer state (so the machine wouldn’t get confused if another input is clocked in while the machine is in the middle of changing states). I also decided that the three clock cycles were to be put as their own states because I thought it would limit the amount of debugging needed for the system. </br> </br>
![image](https://github.com/KayeJD/HVAC-System/assets/139111295/efa4af60-db9d-4bf0-95a3-f2ea87c5802b)

## Choosing Best Design
### Applying Criteria and Weighting
Criteria 											Weight </br>
Number of States………………………………………………………………………………………………………………..5% </br>
Understanding of Build…………………………………………………………………………………………………………25% </br>
Materials Needed………………………………………………………………………………………………………………..20% </br>
Features Included for Clients……………………………………………………………………………………………….15% </br>
Possibilities of System Failure………………………………………………………………………………………..…….35% </br>

### Explanation
I applied this weighting system to each of the designs by simply considering how much hardware (wiring) each of the designs require (Materials Needed section), counting how many used states there are for each design (# of States), the ease and/or complexities of each design (Understanding of build), how each design meets the needs/wants of the customers (Features Included for Clients), and how often I came across complications while simulating the designs in Digital (Possibilities of System Failure). I weight each of these criteria based on how important they are to the final production. For example, “Understanding of build” is of higher weight compared to the other criteria because it is much more important to be able to understand how the system works just in case there are complications with the product later due to wear and tear or other mishaps. “Possibilities of System failure” is the greatest weight out of all of the criteria because the main purpose of most engineering designs is to ensure that they are dependable and meet the needs of those who are using the system. If this one criterion is not met, then production of any engineering design is futile. 

## Choosing Design and Simulation
![image](https://github.com/KayeJD/HVAC-System/assets/139111295/39f392e9-6117-489f-801d-a9882eeec75b)

Based on the criterion, my first design is much better than the second design. I graded this design out of 5 as followed: </br>
1. Number of States (3)
   - The number of states is important to both the designers as well as the users because there is less possibility of bugs in between clock cycles/state transitions if there are less of them. But, both of my designs use 8 states. So the first design does not get any more points than the second design
2. Understanding of Build (5)
   - I understand the logic of this design much more than the second design first because the use of R=L=1 in the first design is used as a power off state. In the second design, it is used as a buffer state in which the state of the machine enters if it receives a new input during the 3 clock cycle in between changing R or L to 1. The first design is also much cleaner in terms of the 3 clock cycle transition between states. 
3. Materials Needed (3)
   - The first design does include more gates than the second design. So it does not beat it in this section of the weighting system. 
5. Features Included for Clients (4)
   - This first design would mee the needs of clients much more than the second design due to the concept that it is simply able to turn off. Clients need to save money, and the only way to do so is to save on electricity bills  not having the AC running 24/7.
6. Possibilities of System Failure (2)
   - While simulating the design in digital, it did not work properly. But, compared to the second design, the first design still was able to have less debugging necessary in order to fix it. In the second design, there are some simulations in which both the H and C would be 1, even though that state was never specified while designing the build. The first design does not have this issue


### Video Demonstration: https://drive.google.com/drive/folders/1D_dnkTNlJX_HCwcfOP6r8hLabopwt1sF?usp=sharing 

