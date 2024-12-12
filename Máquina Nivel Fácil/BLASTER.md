# RESOLUCIÓN DE LA MÁQUINA BLASTER

## TASK 1 - MISSION START

![image](https://github.com/user-attachments/assets/0bb6ce38-1c8b-47d8-af5b-a1792c5bbefd)

## TASK 2 - ACTIVATE FORWARD SCANNERS AND LAUNCH PROTON TORPEDOES 

How many ports are open on our target system?

![image](https://github.com/user-attachments/assets/30725067-8359-4431-b276-7f797d3b9c6e)

![image](https://github.com/user-attachments/assets/b1540a93-0171-4ed5-ba68-d9e8de232a66)

Looks like there's a web server running, what is the title of the page we discover when browsing to it?

![image](https://github.com/user-attachments/assets/d4907b7c-f52d-46c3-ab60-db57037034c5)

![image](https://github.com/user-attachments/assets/1cc3da5c-a728-46b4-aa42-3db38880c24e)

Interesting, let's see if there's anything else on this web server by fuzzing it. What hidden directory do we discover?

![image](https://github.com/user-attachments/assets/bd6a19de-bd2c-4e7c-8fb3-d97268d091ff)

![image](https://github.com/user-attachments/assets/2eb52fbc-1712-4f10-a058-8efb221a1dcb)

Navigate to our discovered hidden directory, what potential username do we discover?

![image](https://github.com/user-attachments/assets/9669d2ea-eebd-4e9b-8482-d847e7593cac)

![image](https://github.com/user-attachments/assets/fd658a48-8e95-4428-9f95-3cdde32985c5)

Crawling through the posts, it seems like our user has had some difficulties logging in recently. What possible password do we discover?

![image](https://github.com/user-attachments/assets/76f65ab4-f766-4c6e-8ce8-049f819f72d9)

![image](https://github.com/user-attachments/assets/d9203ac2-0c2b-4e6a-bc79-e16856396ccb)

Log into the machine via Microsoft Remote Desktop (MSRDP) and read user.txt. What are it's contents?

![image](https://github.com/user-attachments/assets/286f2d4c-9799-4875-ad6a-2509e147462e)

![image](https://github.com/user-attachments/assets/e085a3d3-e4e0-4840-8558-5fc3e37056c3)

![image](https://github.com/user-attachments/assets/3d7ea991-3a43-4335-a6f2-67f1b0a9b569)

## TASK 3 - BREACHING THE CONTROL ROOM 

When enumerating a machine, it's often useful to look at what the user was last doing. Look around the machine and see if you can find the CVE which was researched on this server. What CVE was it?

![image](https://github.com/user-attachments/assets/19ee9b73-fb9d-474f-a59e-05479d419b6c)

![image](https://github.com/user-attachments/assets/277ccb14-d0f1-4fe9-ab9a-2909c107eada)

Looks like an executable file is necessary for exploitation of this vulnerability and the user didn't really clean up very well after testing it. What is the name of this executable?

![image](https://github.com/user-attachments/assets/5a01c7de-73f2-49e4-a1e8-897ffd4963f0)

![image](https://github.com/user-attachments/assets/91f8f055-5cea-4efe-b27b-a3e06f911252)

Ctrl + s and i show that: 

![image](https://github.com/user-attachments/assets/7ca00f8c-e18c-47d3-b061-386d31345202)

Now that we've spawned a terminal, let's go ahead and run the command 'whoami'. What is the output of running this?

![image](https://github.com/user-attachments/assets/8f9985e7-882b-42be-b9bd-e8171e9813a2)

![image](https://github.com/user-attachments/assets/c6597034-68e5-40f3-84ba-781e17c8af33)

Now that we've confirmed that we have an elevated prompt, read the contents of root.txt on the Administrator's desktop. What are the contents? Keep your terminal up after exploitation so we can use it in task four!

![image](https://github.com/user-attachments/assets/9bca1a9a-6944-450a-8725-4cb3de0e411d)

![image](https://github.com/user-attachments/assets/3b338a95-dcc0-4a90-9f07-62a881661c7f)

## TASK 4 - ADOPTION INTO THE COLLECTIVE

Return to your attacker machine for this next bit. Since we know our victim machine is running Windows Defender, let's go ahead and try a different method of payload delivery! For this, we'll be using the script web delivery exploit within Metasploit. Launch Metasploit now and select 'exploit/multi/script/web_delivery' for use.

![image](https://github.com/user-attachments/assets/084e21fe-9396-470c-90ba-19abd0925274)

![image](https://github.com/user-attachments/assets/17ce9094-daf1-4a13-aa3f-2e9f736b114e)

First, let's set the target to PSH (PowerShell). Which target number is PSH?

![image](https://github.com/user-attachments/assets/33b26900-b40e-4d44-a14c-f98a39d29b93)

![image](https://github.com/user-attachments/assets/6652cc8d-b0b3-409d-b773-ec78d56246e7)

After setting your payload, set your lhost and lport accordingly such that you know which port the MSF web server is going to run on and that it'll be running on the TryHackMe network.

![image](https://github.com/user-attachments/assets/e8422ae7-4dfc-41ca-bf8e-184219b9c095)

Finally, let's set our payload. In this case, we'll be using a simple reverse HTTP payload. Do this now with the command: 'set payload windows/meterpreter/reverse_http'. Following this, launch the attack as a job with the command 'run -j'.

![image](https://github.com/user-attachments/assets/b075312b-e6fe-405e-add8-bf7140a7b99c)

Return to the terminal we spawned with our exploit. In this terminal, paste the command output by Metasploit after the job was launched. In this case, I've found it particularly helpful to host a simple python web server (python3 -m http.server) and host the command in a text file as copy and paste between the machines won't always work. Once you've run this command, return to our attacker machine and note that our reverse shell has spawned. 

![image](https://github.com/user-attachments/assets/0905f04e-bd6f-4a5f-ba2e-fc386aa34904)

Last but certainly not least, let's look at persistence mechanisms via Metasploit. What command can we run in our meterpreter console to setup persistence which automatically starts when the system boots? Don't include anything beyond the base command and the option for boot startup. 

![image](https://github.com/user-attachments/assets/7fdaa8b0-b965-496a-a9cc-895605c46d3d)

![image](https://github.com/user-attachments/assets/1882e559-ccf1-498a-9205-92a7caaa5c16)






