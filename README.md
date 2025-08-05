 # EDR Home Lab: Attack and Defense
 
 ## Project: 
This lab is dedicated to simulating a real cyber attack and endpoint detection and response. Utilizing Eric Capuano's guide online, I will be using cloud hosted virtual machines to simulate the threat & victim machines. The attacking Linux Ubuntu machine will utilize 'Sliver' as a C2 framework to attack a Windows endpoint machine, which will be running 'LimaCharlie' as an EDR solution.

Eric Capuano's guide: https://blog.ecapuano.com/p/so-you-want-to-be-a-soc-analyst-20

#


## Setup
The first step to the lab is setting up a LimaCharlie EDR for the victim machine (Windows) and installing a sensor that will import sysmon logs. The attacking machine (Ubuntu) will use Sliver which is pre installed to attack the victim machine.
#

Windows Machine 

<img width="877" height="426" alt="sensor1" src="https://github.com/user-attachments/assets/b31d46b4-43d0-4097-b9cf-e521b06003c6" />
<img width="890" height="286" alt="artcoll" src="https://github.com/user-attachments/assets/897d6554-b84b-4504-9395-2c9688564be6" />

#
Ubuntu Machine 

<img width="642" height="446" alt="sliver" src="https://github.com/user-attachments/assets/de3f3ebd-63f7-4299-9c45-32dfd73d01f0" />

#


## The Attacks, and the Defense

The first step is to generate our C2 implant on Sliver and implant the malware into the Windows host machine. Then we can create a command and control session after the malware is executed on the endpoint.
#


<img width="746" height="212" alt="c2implant" src="https://github.com/user-attachments/assets/598cff20-a7a5-4a93-85dd-eed91107a6f2" />

#
This is a web server on the Linux VM which is serving up the location we saved our C2 implant in the previous step now downloading it on the Windows VM
<img width="1115" height="569" alt="implant" src="https://github.com/user-attachments/assets/70251339-2247-42b6-9f2f-e6ce98702243" />

<img width="888" height="146" alt="puresessions" src="https://github.com/user-attachments/assets/db938c7f-c127-4b93-b80b-cdae75b58b8c" />

#
Now we can directly interact with the C2 sessions on the Windows VM. Gathering information on the session, the user and its privileges, the working directory, connections on the system, and running processes. 

<img width="1105" height="563" alt="sessioninfo" src="https://github.com/user-attachments/assets/be3a3cbe-559b-40c1-ac48-96d1d2fa5e61" />
<img width="1116" height="167" alt="netstat" src="https://github.com/user-attachments/assets/db61e415-5c67-454a-af6f-b91259e4b02a" />
<img width="1118" height="296" alt="netstat2" src="https://github.com/user-attachments/assets/b1e49d9b-e82d-458e-863e-8c5e7f00ec45" />
<img width="1117" height="54" alt="psT" src="https://github.com/user-attachments/assets/cff67b6e-bd3b-44f9-b475-6db65b2b9234" />
<img width="1120" height="213" alt="pst2" src="https://github.com/user-attachments/assets/070e09d3-b95a-4be1-8444-361dc4d94eab" />

#
Now in our host machine we can use LimaCharlie to see the attacker's telemetry, identify the C2 implant that is not signed, and view it's network connections seeing it is active

<img width="1120" height="529" alt="limatelem" src="https://github.com/user-attachments/assets/45076ce7-e04b-4287-b73d-8513ce521000" />
<img width="1120" height="461" alt="limatelem2" src="https://github.com/user-attachments/assets/9ad1ecee-45dc-463b-a038-a1befe979b85" />
<img width="713" height="137" alt="limatelem3" src="https://github.com/user-attachments/assets/6255660e-b340-42b5-89a5-bdd79678d9af" />

#
We can also use LimaCharlie to grab the file's hash and inspect it on VirusTotal
<img width="878" height="331" alt="virust" src="https://github.com/user-attachments/assets/79c77d94-58f7-4e82-b191-96ea4533de72" />

Due to this attack being a zero day malware, VirusTotal will not detect it. But it doesn't mean it is innocent.
<img width="671" height="446" alt="virust2" src="https://github.com/user-attachments/assets/b16d6b6f-a67f-4974-9c8b-4b2e73013f56" />














