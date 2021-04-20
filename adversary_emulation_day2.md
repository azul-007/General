## How are Payloads Being Delivered? pg. 13

- Malicious email attachments or webpages through phishing
- Abusing a flaw in the external internet perimeter
- Inserting infected removable media
- Compromise third parties in the supply chain and abuse trust relationships

## Modern Credential Phishing Attacks - Oauth Attacks

The MDSec O365 tolkit allows penetration testers/red teamers to perform Authentication Token phishing in order to employ a variety of attack techniques.
Some of the exploitation scenarios supported by the tool include:

- Outlook keyworded extraction
- OneDrive/SharePoint Keyworded Extraction
- Outlook Rules Creation
- Word Document Macro Backdooring
https://wwww.mdsec.co.uk/2019/07/introducing-the-office-365-attack-toolkit


## Getting an Initial Foothold - Key detectoin strategies pg. 14

A key detection focus is the analysis of process execution events. In order to get such visibility, defenders need to typically deploy an agent on
workstations/servers to obtain this visibility

EDR (Endpoint Detection & Response) tools are often the tool of choice for such visibility. The following lists some of the key things to look out for:

- parent-child relations
- command-line arguments
- image (dll) load
- remote threads (typical process injection)


## Getting an Initial Foothold Examples og. 15,16

Refer to the public SIGMA repository by Florian Roth for additional details: https://github.com/Neo23x0/sigma

## Anti-Malware Scanning Interface (AMSI) pg.18

The Antimalware Scan Interace is a generic interface standard that allows applications and services to integrate with any antimalware product present on a machine. 
It is able to interact with other vendor technology.

## AMSI Functions pg. 21

- AmsiInitialize - intializes the AMSI AIP
- AmsiOpenSession/AmisCloseSession - opens/closes a scanning session
- AmsiScanBuffer - scans a buffer of content for malware and returns an entry of the AMSI_RESULT structure
- AmsiScanString - scans a specific string for malware and returns an entry of the AMSI_RESULT structure
- AmsiResultIsMalware - this is a callback function that contains logic based on AMSI_RESULT of either AmsiScanBuffer or AmsiScanString
- AmsiUnintialize - cleans up and closes AMSI

## AMSI Bypass Strategies: 
- Patching AmsiScanBuffer pg. 22
- RASTAMOUSE AMSI BYPASS pg.23
- Patching AmsiContext pg. 25
- Amsi.Fail pg. 28

## Office Macro Obfuscation Techniques

VBA code stored into Office documents is stored in several forms: source code (CompressedSourceCode) and compiled code (PerformanceCache). AV products are known to scan only one or the other.

- Removing the compiled VBA code from an Office document is called *VBA purging*. Purged documents can execute without any problem: Office will generate the required compiled-code on the fly.
- Remove the VBA source code from an Office document is called *VBA stomping*. Stomped documents can execute provided that they target the same version of Office. If a different version of Office is used to open the document, Office will try to compile the missing VBA source code and will not execute the compiled code.


## Application Execution Control Bypass Techniques pg. 38

- Strategy 1: Leverage AppLocker default rules. They are focused on preventing exectution of new executables that are downloaded by end-users. The default rules thus focus on preventing execution from user-writable locations.
- Strategy 2: Leverage built-in Windows binaries. Windows requires a number of its core executables to continue operating/running, hence AppLocker allows a variety of Windows-native commands to be executed by everyone.

## Get Current AppLocker Configuration pg. 39
- Enumerate the currently active AppLocker policy by running the following PowerShell cmdlet:
  - *Get-AppLockerPolicy -Effective -Xml | Set-Content ('c:\temp\curr.xml')
  - This will export the current AppLocker bypass in a raw XML dump format save the file

## Bypass Strategy 1: Leverage Applocker Default Rules 1 pg. 40
- Abuse the default AppLocker rules:
  - Everyone is allowed to run all files located in the Program Files folder
  - Everyone is allowed to run all filed located in the Windows folder
  - Admins are allowed to run all files

## Bypass Strategy 2: Leverage Applocker Default Rules 2 pg. 41
- Oddvar Moe maintains a list of folders that are writeable by default by normal users in "C:\Windows"
  - https://github.com/api0cradle/UltimateAppLockerByPassList/blob/master/Generic-AppLockerbypasses.md
- Leverage Built in Windows Commands
  - installutil.exe
  - regasm.exe
  - regsvcs.exe 

## Bypass Strategy 2: Microsoft.Workflow.Compiler.exe 1 pg. 47
- A second approach to bypassing AppLocker is to leverage the Microsoft.Workflow.Compiler.exe binary located at C:\Windows\Microsoft\.NET\Framework64\v4.0.3019\Microsoft.Workflow.Compiler.exe. 
- Using this binary it is possible to execute uncompiled source code on a system and as such effectively bypass applocker.
- The compiler requires two input files: An XML file containing a serialized CompilerInput object and file path to which the utility can write its output.

## Zooming in on Windows Internals
### Operating System Rings
