# ESET_UNOFFICIAL_TOOLS
There is a library of unofficial tools for ESET applications

First what should need to be done it's a fact that ESET have a lot of good applications and procedures in their own Company Brand but for some reasons for typical daily management operations there is a shortage that stop and froze the operations. In this case I have put there a repository of my own application for Windows Servers and Windows Endpoint systems that might be for some of You unpriceset.

For first run I put application created in PowerShell and complied with free application for create powerscript to .msi format.
In case of this application - You can remotley administrate an uninstall of ESET Menagement Agent via Active Directory. That might be helpfull when:
  - You loss your connection betwen ESET Protect Console and ESET Agent in Windows OS.
  - You need to reinstall Agent in Your network (ESET Protect tools are in this case powerless).

If You need to use this Application on Windows Server's envoirement - there is no nessesery to change anything else options.
If You need to use this Appliacation on Windows Endpoint (10/11) - there is a case of indywidual configuration of Active Directory security options that should be changed before this operation.

In bout cases - Application sholuld be shared in folder in network, from where Computers have persmissions to read (no nessesery for full access to write). Then useing GPO Policy and .msi Uninstaller - You should send aplliction to all Your hosts in network and after "gpupdate /force" command - ESET should be uninstall from PC's. After that procedure - recerse manula of ESET should send a new Agent installation to those PC'a and in the end - Yours new PC's should be online in Your ESET Protect Console.

This is an instruction for disable UAC using Group Policy:

Group Policy Management Console – gpmc.msc (use google for search instruction: "How to Disable User Account Control with Group Policy" or use Your own knowladge).

And the last one - this is an instuction for create a GPO to ESET Remote AD deployment:
  [KB6864] Deploy the ESET Management Agent using a Group Policy Object (Windows)

Procedure:
1. Undeploy any other GPO for ESET Management Agent deployment (if there was created earlier)
2. Use "gpupdate /force" command at AD Server.
3. Turn off in GPMC UAC settings.
4. Put into shared localization a .msi file from this repository.
5. Create a GPO to use this .msi application
6. Use "gpupdate /force" command at AD Server.
7. Wait until all Computers in Your network download a new Policy and use .msi application. Chceck if You have any option in a few PC's that did the work done.
8. Create a new GPO ESET Management Agent installation application and .INI file.
9. Put those two new files to a shared location.
10. Create a new GPO Policy according to KB6864 ESET Official Instruction

If You do the job good, a .msi Installation files should connect Your's PC from now int a new ESET Protect WebConsole.

If You have any questions or something from this instruction doesnt work good or You have ANY ideas or question - feel free to ask!
Glad if it help :)
