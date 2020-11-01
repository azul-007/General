**Arrays**
```Powershell
$colorPicker = @('blue', 'white','yellow','black')
```
**Reading arrays**
```powershell
$colorPicker[0]
$colorPicker[1]
$colorPicker[2]
$colorPicker[3]
```

**Modifying Array Elements**
```powershell
$colorPicker[3] = 'white'
```

**Adding Elements to an Array**
```powershell
$colorPicker += 'orange'
$colorPicker += @('pink','cyan')
```

**ArraysLists**
```powershell
$colorPicker = [System.Collections.ArrayList]@('blue','white','yellow','black')
$colorPicker.Add('gray')
$colorPicker.Remove('gray')
```

**Hashtables**
```powershell
$users = @{
abertram = 'Adam Bertram' raquelcer = 'Raquel Cerillo' zheng21 = 'Justin Zheng'

$users['abertram']

$users.abertram
```

**View properties of a hashtable**
```powershell
Select-Object -InputObject $yourobject -Property *
```

**Adding and Modifying Hashtable Items**
```powershell
$users.Add('natice', 'Natalie Ice')
$users['phrigo'] = 'Phil Rigo'
```
**Removing Items from a Hashtable**
```powershell
$users.Remove('natice')
```

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
