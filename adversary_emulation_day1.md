


## Details to Include in Emulation Plan
- How can we emulate the technique? What tools do we need? What tools do we have that can be leveraged?
- What controls could potentially stop the technique? What controls are currently in place?
- How could we possible detect the technique?
- Add template fields to document detection & success of technique emulation

## Executing a Purple Team Exercise Pg. 46
Assemble red and blue teams and run through the following steps:
1) Present the adversary and the specific TTP that will be emulated (Red)
2) Discuss the expected controls that are in place to prevent success execution or detect the TTP (Blue)
3) Emulate the TTP (Red)
4) Find evidence of successful execution of the TTP (Blue)
5) Present evidence execution of the TTP (Blue)
6) Document results of the TTP (joint effort)
7) Implement short-term fixes that are identified. Example: a change to an existing detection rule/use case (Blue)
8) Document any longer term actions. Example: a change to configuration or a new log source to configure/on-board in the SIEM (Blue)

## VECTR pg. 47
VECTR (https://vectr.io)is a tool developed by Security Risk Advisors that facilitates tracking of your red and blue testing activities to measure detection and prevention capabilities across different attack scenarios. VECTR allows blue and red teams to track both progress and vectors of performed attacks, effectively reaching the purple team's goal through intel sharing.

## SIGMA pg. 62
A project developed by Florian Roth, it provides a generic, vendor neutral, rule format that can be used to describe suspicious or malicious behavior. Most SIGMA rules are also mapped to MITRE's ATT&CK framework. As part of the project, several "converters" have been written that allow you to convert the SIGMA rules to certain technologies. Splunk supports sigma rules. https://github.com/Neo23x0/sigma

One of the benefits of SIGMA is field mapping. Field mapping allows you to convert SIGMA fields to your local implementations.

## Jupyter Notebooks pg. 72
A document accessible through the web. Allows users to start "sessions" which allow input (code) and output (code results) to be saved. You can also add notes that document how the code works, what additional analysis needs to be done manually on the output. 

A great intro to the Jupyter Threat Hunting notebooks with a threat hunting use case http://threathunterplaybook.com/tutorials/jupyter/introduction/html


# Assessing Detection Coverage

## Sysmon Event Types pg. 85

Endpoint Detection Superpowers on the cheap pg. 86
https://medium.com/@olafhartong/endpoint-detection-superpowers-on-the-cheap-part-1-e9c28201ac47

## Event Tracing for Windows (ETW) pg. 87
- kernel-level tracing facility that lets you log kernel or application-defined events to a log file. Can consume the events in real time or from a log file and use them to debug an application or to determine where performance issues are occurring in the application

ETW architecture is divided in three main components:
- *Controller* allows us to start or stop tracing sessions. They also enable providers. Example: logmax.exe
- *Providers* provide the events that are being traced. Ex: Microsoft-Windows-Security-Auditing
- *Consumers* consume the events that are being traced. Ex: Event Viewer


## Rule Based Detection
- A better approach to detecting badness would be to create rules that detect techniques rather than the tool
- Sysmon event ID 8 (CreateRemoteThread): look for target lsass.exe and assess who is attempting to interact with lsass.exe
- Sysmon event ID 10 (ProcessAccess): look for target lsass.exe and asses who is attempting to interact with lsass.exe

## Anomaly-Based Detection: Introducing EE-Outliers pg. 111
- EE-Outliers is a frmework to detect outliers in events stored in an Elasticsearch cluster. The framework was developed for the purpose of detecting anomalies in security events.
- Uses statistical models that are easily defined by the user in a config file. In case the models detect an outlier, the relevant Elasticsearch events are enriched with additional outlier fields. These fields can then be dashboarded and visualized using the tools of your choice.
