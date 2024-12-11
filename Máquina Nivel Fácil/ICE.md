# RESOLUCIÓN DE LA MÁQUINA ICE

## TASK 1 - CONNECT

![image](https://github.com/user-attachments/assets/608d2d7f-ff67-4dba-83d8-a2d90240385f)

## TASK 2 - RECON

Once the scan completes, we'll see a number of interesting ports open on this machine. As you might have guessed, the firewall has been disabled (with the service completely shutdown), leaving very little to protect this machine. One of the more interesting ports that is open is Microsoft Remote Desktop (MSRDP). What port is this open on?

![image](https://github.com/user-attachments/assets/a577d2b5-7e40-4340-b663-c51f76349dd3)

![image](https://github.com/user-attachments/assets/3749a0a3-7ee3-420e-82c9-3514d2d88732)

What service did nmap identify as running on port 8000? (First word of this service)

![image](https://github.com/user-attachments/assets/1fae5182-681d-42e4-a800-d36c504c4abf)

![image](https://github.com/user-attachments/assets/42e36244-6f28-4600-8854-82994f997012)

What does Nmap identify as the hostname of the machine? (All caps for the answer)

![image](https://github.com/user-attachments/assets/b2a0be46-737d-42c4-95d4-f192135f7259)

![image](https://github.com/user-attachments/assets/d3b9d40b-94c6-4683-a822-05659722f36b)

## TASK 3 - GAIN ACCESS

Now that we've identified some interesting services running on our target machine, let's do a little bit of research into one of the weirder services identified: Icecast. Icecast, or well at least this version running on our target, is heavily flawed and has a high level vulnerability with a score of 7.5 (7.4 depending on where you view it). What is the Impact Score for this vulnerability? Use https://www.cvedetails.com for this question and the next.

![image](https://github.com/user-attachments/assets/284894df-8fba-4542-aa2a-01a94af37981)

![image](https://github.com/user-attachments/assets/45f664a2-f53f-4f1a-8cce-c18ac1bc7e97)

What is the CVE number for this vulnerability? This will be in the format: CVE-0000-0000

![image](https://github.com/user-attachments/assets/39eec405-453f-4d4a-b176-a3da38dd7897)

![image](https://github.com/user-attachments/assets/515572ab-5810-43fa-8e6b-02f89dddd3a9)

After Metasploit has started, let's search for our target exploit using the command 'search icecast'. What is the full path (starting with exploit) for the exploitation module? If you are not familiar with metasploit, take a look at the Metasploit module.

![image](https://github.com/user-attachments/assets/9a419f9f-fdc4-4707-8b55-54aaa220e82a)

![image](https://github.com/user-attachments/assets/3904e0d4-e9cc-445d-9c68-cf62f3f955c3)

Following selecting our module, we now have to check what options we have to set. Run the command `show options`. What is the only required setting which currently is blank?

![image](https://github.com/user-attachments/assets/0f1ce4eb-7d09-42d2-84d7-d2fa329f1e64)

![image](https://github.com/user-attachments/assets/d4d5034e-6ffe-48e7-a7e0-62c81d81fd6a)

First let's check that the LHOST option is set to our tun0 IP (which can be found on the access page). With that done, let's set that last option to our target IP. Now that we have everything ready to go, let's run our exploit using the command `exploit`

![image](https://github.com/user-attachments/assets/bcb12ebc-54dd-41e7-9af9-7b0c6137a1cc)

## TASK 4 - ESCALATE

Woohoo! We've gained a foothold into our victim machine! What's the name of the shell we have now?

![image](https://github.com/user-attachments/assets/c18ecfbd-d8d5-4e4c-832f-83ba65f1bf28)

![image](https://github.com/user-attachments/assets/c3f7b32c-31ee-46fc-82f8-fc5477f3b3c5)

What user was running that Icecast process? The commands used in this question and the next few are taken directly from the 'Metasploit' module.

![image](https://github.com/user-attachments/assets/4f97e88e-545c-4512-83cc-26f024b672d2)

![image](https://github.com/user-attachments/assets/930f789e-aed7-4be1-8be4-29f2d43a912f)

What build of Windows is the system?

![image](https://github.com/user-attachments/assets/4411506f-2438-462c-82c8-b8fb39c48396)

![image](https://github.com/user-attachments/assets/6b696784-cc1d-4409-81b1-c3c660e8d0cc)

Now that we know some of the finer details of the system we are working with, let's start escalating our privileges. First, what is the architecture of the process we're running?

![image](https://github.com/user-attachments/assets/792b5736-5c38-44e7-a876-e363d25ef183)

![image](https://github.com/user-attachments/assets/bcd24da0-48ad-4997-806d-b9292b7aeac5)

Now that we know the architecture of the process, let's perform some further recon. While this doesn't work the best on x64 machines, let's now run the following command `run post/multi/recon/local_exploit_suggester`. *This can appear to hang as it tests exploits and might take several minutes to complete*

![image](https://github.com/user-attachments/assets/0be218d8-2caa-46c5-a153-c86364b2585f)

Running the local exploit suggester will return quite a few results for potential escalation exploits. What is the full path (starting with exploit/) for the first returned exploit?

![image](https://github.com/user-attachments/assets/28612bae-ed8b-4406-bb75-262a3f0aff3f)

![image](https://github.com/user-attachments/assets/598de2dc-0046-4774-b3ad-2edfb15a98ad)

Now that we have an exploit in mind for elevating our privileges, let's background our current session using the command `background` or `CTRL + z`. Take note of what session number we have, this will likely be 1 in this case. We can list all of our active sessions using the command `sessions` when outside of the meterpreter shell.

![image](https://github.com/user-attachments/assets/74c9123b-fba6-464c-b33f-fe20a5a2016c)

Go ahead and select our previously found local exploit for use using the command `use FULL_PATH_FOR_EXPLOIT`

![image](https://github.com/user-attachments/assets/875f792d-1d12-4b13-8747-8a1262c3ce3e)

Local exploits require a session to be selected (something we can verify with the command `show options`), set this now using the command `set session SESSION_NUMBER`

![image](https://github.com/user-attachments/assets/5c6900db-be69-4121-83b6-ea51c6a26185)

Now that we've set our session number, further options will be revealed in the options menu. We'll have to set one more as our listener IP isn't correct. What is the name of this option?

![image](https://github.com/user-attachments/assets/9142158e-0c1c-4777-a958-41943bfdda00)

![image](https://github.com/user-attachments/assets/3d8c6bea-27d3-43c6-8466-48aa086156fa)

Set this option now. You might have to check your IP on the TryHackMe network using the command `ip addr`

![image](https://github.com/user-attachments/assets/d29516ed-9853-40f8-9a08-d08037b9a66a)

After we've set this last option, we can now run our privilege escalation exploit. Run this now using the command `run`. Note, this might take a few attempts and you may need to relaunch the box and exploit the service in the case that this fails. 

![image](https://github.com/user-attachments/assets/0091bd86-0be4-4405-b66b-a269e4899737)

Following completion of the privilege escalation a new session will be opened. Interact with it now using the command `sessions SESSION_NUMBER`

![image](https://github.com/user-attachments/assets/7be9f4e3-7597-4897-886f-225ba3f279b4)

We can now verify that we have expanded permissions using the command `getprivs`. What permission listed allows us to take ownership of files?

![image](https://github.com/user-attachments/assets/60e90873-6e6a-401e-8b05-0ee94b7fd345)

![image](https://github.com/user-attachments/assets/b5a49ec5-2322-40f5-aed3-0188d8a0d813)

## TASK 5 - LOOTING

Prior to further action, we need to move to a process that actually has the permissions that we need to interact with the lsass service, the service responsible for authentication within Windows. First, let's list the processes using the command `ps`. Note, we can see processes being run by NT AUTHORITY\SYSTEM as we have escalated permissions (even though our process doesn't). 

![image](https://github.com/user-attachments/assets/04a2018d-e8fc-40bc-941d-9071d413fbff)

In order to interact with lsass we need to be 'living in' a process that is the same architecture as the lsass service (x64 in the case of this machine) and a process that has the same permissions as lsass. The printer spool service happens to meet our needs perfectly for this and it'll restart if we crash it! What's the name of the printer service?

Mentioned within this question is the term 'living in' a process. Often when we take over a running program we ultimately load another shared library into the program (a dll) which includes our malicious code. From this, we can spawn a new thread that hosts our shell. 

![image](https://github.com/user-attachments/assets/2e419c59-0d16-48c9-8dce-dd0610c3b8d5)

![image](https://github.com/user-attachments/assets/48423ad0-c650-422d-a0b0-f902595c25d8)

Migrate to this process now with the command `migrate -N PROCESS_NAME`

![image](https://github.com/user-attachments/assets/d898982f-57b6-4d6b-b4d9-b99615c70c7d)

Let's check what user we are now with the command `getuid`. What user is listed?

![image](https://github.com/user-attachments/assets/9ce0761f-6cc4-415d-916b-b40b5425c17f)

![image](https://github.com/user-attachments/assets/8dedbe24-ae59-4c3e-8991-a235ef477037)

Now that we've made our way to full administrator permissions we'll set our sights on looting. Mimikatz is a rather infamous password dumping tool that is incredibly useful. Load it now using the command `load kiwi` (Kiwi is the updated version of Mimikatz)

![image](https://github.com/user-attachments/assets/22faf476-38de-429f-9cb4-58f63f4a9fa3)

Loading kiwi into our meterpreter session will expand our help menu, take a look at the newly added section of the help menu now via the command `help`. 

![image](https://github.com/user-attachments/assets/2a4d3380-c25a-47d8-b499-759cd81a17d6)

Which command allows up to retrieve all credentials?

![image](https://github.com/user-attachments/assets/e90452b1-3522-4bd0-97cf-398188d1c436)

![image](https://github.com/user-attachments/assets/788166c6-8b52-4805-9356-ec91277d4ac5)

Run this command now. What is Dark's password? Mimikatz allows us to steal this password out of memory even without the user 'Dark' logged in as there is a scheduled task that runs the Icecast as the user 'Dark'. It also helps that Windows Defender isn't running on the box ;) (Take a look again at the ps list, this box isn't in the best shape with both the firewall and defender disabled)

![image](https://github.com/user-attachments/assets/6afb3975-c90e-4009-8f0b-2223c7537e87)

![image](https://github.com/user-attachments/assets/d600a270-19ed-4798-9384-d933264cb81a)

## TASK 6 - POST-EXPLOITATION

What command allows us to dump all of the password hashes stored on the system? We won't crack the Administrative password in this case as it's pretty strong (this is intentional to avoid password spraying attempts)

![image](https://github.com/user-attachments/assets/574079b5-7a8e-4d47-904e-53d01fff44da)

![image](https://github.com/user-attachments/assets/ca961d7d-4b37-4cdf-bd50-a4b86950ac61)

While more useful when interacting with a machine being used, what command allows us to watch the remote user's desktop in real time?

![image](https://github.com/user-attachments/assets/42bb1aa8-aef2-4fad-b3b7-9885457280e3)

![image](https://github.com/user-attachments/assets/5e7e165a-cce7-40fd-a77a-168e3db8602b)

How about if we wanted to record from a microphone attached to the system?

![image](https://github.com/user-attachments/assets/974b442c-0f04-4e3f-a12f-a16a79761935)

![image](https://github.com/user-attachments/assets/eec8f827-0f44-4db7-9a95-00301a663b61)

To complicate forensics efforts we can modify timestamps of files on the system. What command allows us to do this? Don't ever do this on a pentest unless you're explicitly allowed to do so! This is not beneficial to the defending team as they try to breakdown the events of the pentest after the fact.

![image](https://github.com/user-attachments/assets/3758f253-174e-4631-b290-87a28ffc8ba8)

![image](https://github.com/user-attachments/assets/8adad0bb-cbae-40f5-a230-09fdda823926)

Mimikatz allows us to create what's called a `golden ticket`, allowing us to authenticate anywhere with ease. What command allows us to do this?

Golden ticket attacks are a function within Mimikatz which abuses a component to Kerberos (the authentication system in Windows domains), the ticket-granting ticket. In short, golden ticket attacks allow us to maintain persistence and authenticate as any user on the domain.

![image](https://github.com/user-attachments/assets/5863673e-78a5-4d1d-b1f1-5e8ca7036e68)

![image](https://github.com/user-attachments/assets/a0e60369-a1b6-4ef9-bbeb-72e3a8acda06)

One last thing to note. As we have the password for the user 'Dark' we can now authenticate to the machine and access it via remote desktop (MSRDP). As this is a workstation, we'd likely kick whatever user is signed onto it off if we connect to it, however, it's always interesting to remote into machines and view them as their users do. If this hasn't already been enabled, we can enable it via the following Metasploit module: `run post/windows/manage/enable_rdp`

![image](https://github.com/user-attachments/assets/042e6277-2af4-4453-813d-4be709a862ec)

![image](https://github.com/user-attachments/assets/ca798dd0-2544-42fe-bb0a-913e43c9a6cc)

![image](https://github.com/user-attachments/assets/a4b40c46-385a-45e9-a612-16b30b09e41e)















