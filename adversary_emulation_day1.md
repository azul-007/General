


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

