
# Home-Lab-SIEM
A Home Lab focused on detecting threats and logging detections in ways that can be easily analyzed

I will post more results based things at the top, down below will be a documentation of the whole process 




# Documenting the process
This is where I will be documenting the progresss I make on this project to better understand the process. This should allow for anyone (including myself) looking at this to view how I progress
and deal with problems whent they occur. I will update this page whenever progress is made.


## Downloading VMWare and the VMs
I downloaded VMWare on my home pc to have a fresh virtualization environment for this lab.
For the VMs I have an Ubuntu server to act as the Wazuh (Open Source SIEM software) server where all alerts on the network will be forwarded to. I have a kali machine to act as the attacker where the simulated attacks will be launched from. I then  also have a windows 10 system to act as the target of the Kali machines attacks. The windows machine will enroll as a Wazuh client and forward logs of the attacks being done on it to the Ubunutu server.
<img width="800" height="800" alt="image" src="https://github.com/user-attachments/assets/433ed701-dc04-4063-947e-30ed9107b48d" /> 






