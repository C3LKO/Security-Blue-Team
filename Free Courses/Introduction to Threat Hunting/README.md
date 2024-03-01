Search a system using these IOCs to find evidence of various files and malware that is hiding.​

Learn how to use IOCs to search an entire system for any evidence of them, allowing you to identify suspicious or malicious files used values such as strings, MD5 hashes, file names, file size, and more.​

You will be given a system image, which you must load as a virtual machine, and use techniques to generate IOCs from two malware samples, and then search the system to find all other copies of the malware that are hidden deep inside.

---

- Mandiant IOC Collector
- MD5 Hashing
- SHA-1 Hashing
- Strings
- File Properties
- Mandiant Redline
- Virtual Machines


> <img width="400" src="https://github.com/C3LKO/Security-Blue-Team/blob/main/Assets/Introduction%20to%20Threat%20Hunting-course.jpg"> <br>



Introduction
A proactive approach of looking for malicious activity should be taken within a network despite the absence of any specific alerts.
Threat hunting is advanced position that requires knowledge of both blue teaming and red teaming skills. 
Download the zip file for the challenge. 
Make sure to install the necessary software using the link provided by Security Blue Team.
Below is the message we got from Matt:
 
> <img width="400" src="https://github.com/C3LKO/Security-Blue-Team/blob/main/Assets/threat%20hunting.jpg"> <br>

Gathering Information
Get the MD5 and SHA256 hash values of the malware with Ppowershell terminal. 
Run the following commands to get the MD5 and SHA256 hashes of the malware:
Get-FileHash -algorithm md5 “filename.extension”
Get-FileHash “filename.extension”

Launch Redline then go to IOC Search Collector and navigate to the folder location of the IOCs.

Select Edit your script > Disk > put a check mark on Show Advanced Parameters > put a check mark on File Enumeration > paste the exact path of the location of the IOCs on the Path field. On the lower part of the pop-up window, select Include Directories, MD5, SHA256, Strings and Include Files.

Click Ok to go back to the previous screen. Under the Save Your Collector To field, enter the location of the folder where you want Redline to post the results. Click Ok to proceed.

Wait for Redline to finish and then navigate to the folder location where Redline posted the results.
Open an admin powershell terminal and navigate to the location. Run the RunRedlineAudit.bat script.
This will create a new folder called Sessions in the same location as the previously run script. We will be using .mans file to view the results of the scan.
Now go back to Redline and select Open Previous Analysis. Navigate to the location of the .mans file.

On the new window, select IOC Reports below and click on the only entry showing at the top of the screen.

Click on the two reports to view the results. We can now use the information on the screen to answer the questions.

Questions:

1.	How many pieces of malware were detected using IOCs generated from the two samples?
- Answer: 4
2. What is the file name beginning with \”w\”? (including extension)
- Answer: wallpaperHD.exe
3. Is there malware in the location “/DaveS/Pictures”? (True or False)
- Answer: True
4. Which MD5 hash appears in two different files?
- Answer: 0c4374d72e166f15acdfe44e9398d026

