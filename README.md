 # EDR Home Lab: Attack and Defense
 
 ## Project: 
This lab is dedicated to simulating a real cyber attack and endpoint detection and response. Utilizing Eric Capuano's guide online, I will be using cloud hosted virtual machines to simulate the threat & victim machines. The attacking linux machine will utilize 'Sliver' as a C2 framework to attack a Windows endpoint machine, which will be running 'LimaCharlie' as an EDR solution.

Eric Capuano's guide: https://blog.ecapuano.com/p/so-you-want-to-be-a-soc-analyst-20

#


## Setup
The first step to the lab is setting up a LimaCharlie EDR for the victim machine (Windows) and installing a sensor that will import sysmon logs. The attacking machine (Linux) will use Sliver which is pre installed to attack the victim machine.
