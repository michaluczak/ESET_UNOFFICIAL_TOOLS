# ESET_UNOFFICIAL_TOOLS
There is a library of unofficial tools for ESET applications

First what should need to be done it's a fact that ESET have a lot of good applications and procedures in their own Company Brand but for some reasons for typical daily management operations there is a lag that stop and froze the operations. In this case I have put there a repository of my own application for Windows Servers and Windows Endpoint systems that might be for some of You unpriceset.

For first run I put application created in PowerShell and complied with free application for create powerscript to .msi format.
In case of this application - You can remotley administrate an uninstall of ESET Menagement Agent via Active Directory. That might be helpfull when:
  - You loss your connection betwen ESET Protect Console and ESET Agent in Windows OS.
  - You need to reinstall Agent in Your network (ESET Protect tools are in this case powerless).

If You need to use this Application on Windows Server's envoirement - there is no nessesery to change anything else options.
If You need to use this Appliacation on Windows Endpoint (10/11) - there is a case of indywidual configuration of Active Directory security options that should be changed before this operation.

In bout cases - Application sholuld be shared in folder in network, from where Computers have persmissions to read (no nessesery for full access to write). Then useing GPO Policy and .msi Uninstaller - You should send aplliction to all Your hosts in network and after "gpupdate /force" command - ESET should be uninstall from PC's. After that procedure - recerse manula of ESET should send a new Agent installation to those PC'a and in the end - Yours new PC's should be online in Your ESET Protect Console.
