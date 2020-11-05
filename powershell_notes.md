**Arrays**
```Powershell
$colorPicker = @('blue', 'white','yellow','black')
```
------------
**Reading arrays**
```powershell
$colorPicker[0]
$colorPicker[1]
$colorPicker[2]
$colorPicker[3]
```
------------
**Modifying Array Elements**
```powershell
$colorPicker[3] = 'white'
```
------------
**Adding Elements to an Array**
```powershell
$colorPicker += 'orange'
$colorPicker += @('pink','cyan')
```
------------
**ArraysLists**
```powershell
$colorPicker = [System.Collections.ArrayList]@('blue','white','yellow','black')
$colorPicker.Add('gray')
$colorPicker.Remove('gray')
```
------------
**Hashtables**
```powershell
$users = @{
abertram = 'Adam Bertram' raquelcer = 'Raquel Cerillo' zheng21 = 'Justin Zheng'
}
$users['abertram']

$users.abertram
```
------------
**View properties of a hashtable**
```powershell
Select-Object -InputObject $yourobject -Property *
```
------------
**Adding and Modifying Hashtable Items**
```powershell
$users.Add('natice', 'Natalie Ice')
$users['phrigo'] = 'Phil Rigo'
```
------------
**Removing Items from a Hashtable**
```powershell
$users.Remove('natice')
```
------------
**Creating Custom Objects**
```powershell
 Use the New-Object cmdlet to define a new object with a PSCustomObject type.
 $myFirstCustomObject = New-Object -TypeName PSCustomObject
 
You define a hashtable in which the keys are property names, and the values are property values, and then cast it as PSCustomObject.
 $myFirstCustomObject = [PSCustomObject]@{OSBuild = 'x'; OSVersion = 'y'}
 
 Check if the custom object is a PSCustomObject type.
 Get-Member -InputObject $myFirstCustomObject
 
 Access those properties.
 $myFirstCustomObject.OSBuild
 $myFirstCustomObject.OSVersion
```
------------
**Piping Objects Between Commands**
```powershell
Get-Service -Name 'wuauserv' | Start-Service
```
------------
**Piping Arrays Between Commands**
```powershell
Get-Content -Path C:\Services.txt | Get-Service
```
------------

**Looking at Parameter Binding**
```powershell
 PowerShell matches pipeline input to parameters in two ways. The first is via ByValue, which means that PowerShell
 
 will look at the type of object passed in and interpret it accordingly. Because Get-Service specifies that it accepts
 
 the Name parameter via ByValue, it will interpret any string passed to it as Name unless otherwise specified. Because
 
 parameters passed via ByValue depend on the type of input, only one parameter can be passed via ByValue.

The second way PowerShell will match a parameter from the pipeline is via ByPropertyName. In this case, PowerShell

will look at the object passed in, and if it has a property with the appropriate name (ComputerName, in this case),

then it will look at the value for that property and accept that value as the parameter. So if you wanted to pass in 

both a service name and a computer name to Get-Service, you could create a PSCustomObject and pass it in

$serviceObject = [PSCustomObject]@{Name = 'wuauserv'; ComputerName = 'SERV1'} 
$serviceObject | Get-Service
```
------------

### Writing Scripts

Executing scripts in powershell is disabled by default. The *execution policy* decides which scripts can be run. It h as four main categories

**- Restricted:** Doesn't allow you to run scripts, the default

**- AllSigned:** Allows you to run only scripts that have been cryptographically signed by a trusted party

**- RemoteSigned:** Allows you to run any script you write, and any script you download as long as it's been 
cryptographically signed by a trusted party.

**- Unrestricted:** Allows you to run any scripts

To see which execution policy your machine is currently using, run the following:

```powershell
Get-ExecutionPolicy
```

To change the exe- cution policy, use the Set-ExecutionPolicy command and pass in the policy you want. You will to 
run this command as admin. You need to perform this command only once, as the setting is saved in the registry. If you’re in a large Active Directory environment, the execution policy can also be set across many computers at once by using Group Policy.

```powershell
  Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
```

------------
