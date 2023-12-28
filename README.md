# ESET_UNOFFICIAL_TOOLS
There is a library of unofficial tools for ESET Protect (On-Prem / Cloud) Applications.

First thing what should need to be selected it is a fact that ESET have a lot of good applications and procedures in their own Company Brand but for some reasons for typical daily management operations there is a shortage that might froze the operations that should need to be done fast. In that case I have put here a repository of my own application for Windows Servers and Windows Endpoint systems that might be for some of You unpriceset. Called it like that also it is to large because more value it is on procedure and a fact that application is ready to use accross the code-lenght.

This .msi file is nothing more that it is created in PowerShell script, with was compiled to .msi format that should go over Active Directory Policy Group Management console.
In case of that You can remotely administer (uninstall) a ESET Menagement Agent via Your AD Domain Server. That might be helpfull when:
  - You loss your connection between ESET Protect Console and ESET Management Agent in OS Windows;
  - You need to reinstall ESET Management Agent in Your network (when ESET Protect tools via Protect WebConsole or ESET Deployment Tool are in this case powerless).

If You need to use this Application on Windows Server's environment - there is no nessesery to change anything else (just put this App into GPO and let is do the job).
If You need to use this Appliacation on Windows Endpoint OS (like a Win10 or Win11) or if You GPO Policy are much restrictive - there is a case of individual configuration of Active Directory security options that should be changed before this operation start (I have put a instruction about that point lower in this readme instruction).

In both cases - Application sholuld be shared in folder in network, from where Computers have permissions to read (no necessary for full access to write). Useing GPO Policy settings and .msi Uninstaller Applicatio - You should send signal to all Your PC-hosts in network (for faster deployment try to use "gpupdate /force" command) that ESET Management Agent should be uninstalled from it. After that procedure - according to ESET manual, You should send a new ESET Management Agent installation file. In the end - Your's PC's should be online in Your new ESET Protect Console again. Remember that .msi file doesn't overwrite each other. Procedure in this case is importand to do it good and reconect Your's hosts back again into Protect Console.

OK, but first that should neet to be done, it is instruction for disable User Account Control (UAC) using Group Policy:

  -> Group Policy Management Console – run "gpmc.msc" and use google for search instruction: "How to Disable User Account Control with Group Policy" or use Your own knowladge.

Second TIP but not the last one - is good to know and understand the instuction for create a GPO to ESET Remote AD deployment:
  -> I will send You to a Official "KB6864" that have a name "Deploy the ESET Management Agent using a Group Policy Object (Windows)". You might find it on ESET webpages or useing the google search engine.

So if You have all that tide - let's start:

Procedure:
1. Undeploy any other GPO for ESET Management Agent deployment (if there was created earlier);
2. Use "gpupdate /force" command at Your AD Server;
3. Turn off for this operation in GPMC.msc an UAC settings;
4. Put into shared space a .msi file from this repository;
5. Create a new GPO to use this .msi application (according to KB6864 created by ESET);
6. Use "gpupdate /force" command again at Your AD Server;
7. Wait until all Computers in Your network download a new GPO Policy with .msi application. Check if You have that option on few PC's that it is working done;
8. In Your ESET Protect WebConsole create a new ESET Management Agent installation application (You should have two files: an .msi and .ini - according to ESET KB6864);
9. Put those two new files into a shared space in your network;
10. Create a new GPO Policy for ESET according to KB6864 ESET Official Instruction;
11. Use "gpupdate /force" command again and wait until a PC's start connectiong again into Yours ESET Protect WebConsole;
12. If You do the job good, a procedure and files should connect Your's PC from now into a new ESET Protect WebConsole again (or first time depends of situation You read this manual).

If You have any questions or something from this instruction doesn't work good or You have ANY futer ideas - feel free to ask!
Glad if it will help You :)
