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
