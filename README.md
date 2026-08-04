
# Home-Lab-SIEM
A Home Lab focused on detecting threats and logging detections in ways that can be easily analyzed

I will post more results based things at the top, down below will be a documentation of the whole process 




# Documenting the process
This is where I will be documenting the progresss I make on this project to better understand the process. This should allow for anyone (including myself) looking at this to view how I progress
and deal with problems whent they occur. I will update this page whenever progress is made.


## Downloading VMWare and the VMs
I downloaded VMWare on my home pc to have a fresh virtualization environment for this lab.
For the VMs I have an Ubuntu server to act as the Wazuh (Open Source SIEM software) server where all alerts on the network will be forwarded to. I have a kali machine to act as the attacker where the simulated attacks will be launched from. I then  also have a windows 10 system to act as the target of the Kali machines attacks. The windows machine will enroll as a Wazuh client and forward logs of the attacks being done on it to the Ubunutu server.

<img width="400" height="320" alt="image" src="https://github.com/user-attachments/assets/4505fc3f-ef7f-498b-b3c5-b4f9230553af" />

(Note: I disabled the windows machine's firewall as it was blocking the VM's from ICMP messages from getting through)

## Setting up the Wazuh server
I started by setting up the ubuntu server as a Wazuh indexer. The indexer is the place where alerts generated from the server are stored. Since I am doing this all on one server/node the ubuntu server will be acting as the indexer and the server for this lab.

I followed this useful guide on Wazuh's website to set up the indexer:
[Wazuh Indexer Setup](https://documentation.wazuh.com/current/installation-guide/wazuh-indexer/step-by-step.html)

I tested that the indexer is working and got these outputs which means that the indexer should be all set
<img width="661" height="290" alt="image" src="https://github.com/user-attachments/assets/bdec605d-23ac-4d07-a29f-a72c16c963f5" />
<img width="809" height="96" alt="image" src="https://github.com/user-attachments/assets/6ce536ac-f76c-43af-8e66-a77f539f0b48" />

I then set up the server which will analyze information from the agents and report anything to the indexer. (Server and Indexer are both on the same ubuntu server) 

I again used the useful step-by-step guide on Wazuh's website to set up the server:
[Wazuh Server Setup](https://documentation.wazuh.com/current/installation-guide/wazuh-server/step-by-step.html)

The final step for the server is to install the dashboard which acts like a web server which can be accessed from other computers to get a UI for the functions of overseeing the Wazuh SOC services.
I was having some issues with disk space on the on my VM, so that is something to watch out for.

[Wazuh DashBoard Setup]([https://documentation.wazuh.com/current/installation-guide/wazuh-dashboard/index.html)](https://documentation.wazuh.com/current/installation-guide/wazuh-dashboard/step-by-step.html)

From a browser on another computer going to the IP address at a specified port (which was setup during configuration) will bring you to the login page.

<img width="1278" height="750" alt="Wazuh Dashboard Login Page" src="https://github.com/user-attachments/assets/e58efee8-d0c8-4e19-a46d-a6bf30ba4095" />

Entering Credentials brings us to the UI for the Wazuh dashboard

<img width="1273" height="749" alt="Wazuh Dashboard Home Page" src="https://github.com/user-attachments/assets/af69606a-3358-4b9e-b35c-9c0115ee52fe" />

As you can see there are currently no agents so my next step will be enrolling the Windoow's VM as an agent.


