### Arrays
```Powershell
$colorPicker = @('blue', 'white','yellow','black')
```
------------
### Reading arrays
```powershell
$colorPicker[0]
$colorPicker[1]
$colorPicker[2]
$colorPicker[3]
```
------------
### Modifying Array Elements
```powershell
$colorPicker[3] = 'white'
```
------------
### Adding Elements to an Array
```powershell
$colorPicker += 'orange'
$colorPicker += @('pink','cyan')
```
------------
### ArraysLists
```powershell
$colorPicker = [System.Collections.ArrayList]@('blue','white','yellow','black')
$colorPicker.Add('gray')
$colorPicker.Remove('gray')
```

### Select-Object
```powershell
Look at an object’s properties, use the Select-Object command and the Property parameter
Select-Object -InputObject $color -Property *
```
------------

### Get-Member cmdlet
**Look at all the methods and properties that exist on this string object, you can use the Get-Member cmdlet**
```powershell
Get-Member -InputObject $color
```

------------

### Hashtables
```powershell
$users = @{
abertram = 'Adam Bertram' raquelcer = 'Raquel Cerillo' zheng21 = 'Justin Zheng'
}
$users['abertram']

$users.abertram
```
------------
### View properties of a hashtable
```powershell
Select-Object -InputObject $yourobject -Property *
```
------------
### Adding and Modifying Hashtable Items
```powershell
$users.Add('natice', 'Natalie Ice')
$users['phrigo'] = 'Phil Rigo'
```
------------
### Removing Items from a Hashtable
```powershell
$users.Remove('natice')
```
------------
### Creating Custom Objects
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
### Piping Objects Between Commands
```powershell
Get-Service -Name 'wuauserv' | Start-Service
```
------------
### Piping Arrays Between Commands
```powershell
Get-Content -Path C:\Services.txt | Get-Service
```
------------

### Looking at Parameter Binding
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

**To change the execution policy, use the Set-ExecutionPolicy command and pass in the policy you want. You will to 
run this command as admin. You need to perform this command only once, as the setting is saved in the registry. If you’re in a large Active Directory environment, the execution policy can also be set across many computers at once by using Group Policy.**

```powershell
  Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
```
------------

### Operators
```powershell
-eq Compares two values and returns True if they are equal.
-ne Compares two values and returns True if they are not equal.
-gt Compares two values and returns True if the first is greater than the second.
-ge Compares two values and returns True if the first is greater than or equal to the second.
-lt Compares two values and returns True if the first is less than the second.
-le Compares two values and returns True if the first is less than or equal to the second.
-contains Returns True if the second value is “in” the second. You can use this to determine whether a value is inside an array.
```
------------

### Quiet Parameter
```powershell
Testing with Quiet forces a command to output True or False
Test-Connection -ComputerName onlineserver -Quiet -Count 1
```

**If you want to know whether the server was offline, use the **-not** operator **
```powershell
 -not (Test-Connection -ComputerName offlineserver -Quiet -Count 1)
```
------------

### if, else, elseif
```powershell

if (-not (Test-Connection -ComputerName $servers[0] -Quiet -Count 1)) {Write-Error -Message "The server $servers[0] is not responding!"
} elseif ($servers[0] –eq $problemServer)
Write-Error -Message "The server $servers[0] does not have the right file!"
} else {
Get-Content -Path "\\$servers[0]\c$\App_configuration.txt"
}
```
------------
### Switch Statement
```powershell
$currentServer = $servers[0]
switch ($currentServer) {
    $servers[0] {
        # Check if server is online and get content at SRV1 path.
        break
    }
    $servers[1] {
        ## Check if server is online and get content at SRV2 path.
break }
     $servers[2] {
     
     ## Check if server is online and get content at SRV3 path.
break }
```
------------

### For Loops

#### ForEach
**This method will not directly modify the original variable**
```powershell
$servers = @('SRV1','SRV2','SRV3','SRV4','SRV5')
foreach ($server in $servers) {
    $server = "new $server"
}
$servers
```

#### ForEach-Object Cmdlet
**The cmdlet also accepts a Process parameter, which should be a scriptblock containing the code you’d like to run for each element inside the input object.**
**$_ represents the current object in the pipeline.**
```powershell
$servers = @('SRV1','SRV2','SRV3','SRV4','SRV5')
ForEach-Object -InputObject $servers -Process {
    Get-Content -Path "\\$_\c$\App_configuration.txt"
}
```

#### foreach() Method
**Accepts a scriptblock parameter that should contain the code to execute each iteration. As with ForEach-Object, you use $_ to capture the current iteration’s object. This method is faster than the previous two, is great when you want to perform a task on an object-by-object basis.**
```powershell
$servers.foreach({Get-Content -Path "\\$_\c$\App_configuration.txt"})
```
------------

### For Loop
```powershell
$servers = @('SERVER1','SERVER2','SERVER3','SERVER4','SERVER5')
for ($i = 0; $i –lt $servers.Length; $i++) {
    $servers[$i] = "new $server"
}
$servers
```
------------

### While Loop
```powershell

$counter = 0
while ($counter -lt 10) {
$counter
$counter++ }
```

**Say you have a Windows server (again called $problemServer) that’s frequently going down. But there’s a file you need on it, and you don’t want to sit there testing the server every few minutes to get it. You can use a while loop to automate this process for you**
```powershell
while (Test-Connection -ComputerName $problemServer -Quiet -Count 1) {
    Get-Content -Path "\\$problemServer\c$\App_configuration.txt"
    break
}
```
------------
