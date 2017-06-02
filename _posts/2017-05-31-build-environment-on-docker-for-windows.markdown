---
layout: post
title: "Windows Server Core Commands"
date: "2017-05-31 14:20:14 +0800"
---
#Download an installer using powershell
Start-BitsTransfer -Source http://Server01/serverdir/testfile1.txt `
-Destination C:\clientdir\testfile1.txt

e.g.
Start-BitsTransfer -Source http://chemdevinstallers.scienceaccelerated.com/VisualStudio2010SP1.zip  -Destination c:\temp\

#Extract the zip
Expand-Archive -Path Draft.Zip -DestinationPath C:\Reference

e.g.
Expand-Archive -Path .\VisualStudio2010SP1.zip -DestinationPath c:\temp\vs2010\

#Invoke the cmd after the default one exited
Ctrl+alt+delete or Ctrl+alt+end(on remote desktop)

#Restart/Shutdown Computer
Restart-Computer
Stop-Computer
