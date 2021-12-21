# Get-O365EndpointsPerCategory

This script connects to `M365 Endpoints RestAPI` and keeping an offline version to run the script more efficient and to avoid making same requests to query for same data much often.

The "offline" version of the json file is stored in script execution folder - so the RestAPI will only be queried when this file is older than 1 day, otherwise the existing copy is used.

In addition, you can use the script also to tack for changes within last time delta. For this simply use the `$ChangesWithinLastNumOfDays` param to query for changes.

> <https://aka.ms/o365ips/>

---

**Specific switches/params:**

```txt
[switch]$HttpOnly = filtering for 80/443 tcp endpoints only
[int]$ChangesWithinLastNumOfDays = query for changes within last x days
```

**Examples:**

```powershell
.\Get-O365EndpointsPerCategory.ps1 -Service Skype -Category Any -Required $True -HttpOnly
.\Get-O365EndpointsPerCategory.ps1 -Service Skype -Category Optimize
.\Get-O365EndpointsPerCategory.ps1 -Service Skype -Category OptimizeAllow -IPsOnly
.\Get-O365EndpointsPerCategory.ps1 -Service Skype -Category OptimizeAllow -IPsOnly -IPVersion IPv4
.\Get-O365EndpointsPerCategory.ps1 -Service Skype -Category OptimizeAllow -URLsOnly
.\Get-O365EndpointsPerCategory.ps1 -Service Exchange -Category Allow -IPversion IPv6 -Required $True
.\Get-O365EndpointsPerCategory.ps1 -Service Any -Category Optimize
.\Get-O365EndpointsPerCategory.ps1 -Category Optimize -IPVersion IPv4
.\Get-O365EndpointsPerCategory.ps1 -Category OptimizeAllow -URLsOnly
.\Get-O365EndpointsPerCategory.ps1 -Service Any -Category Allow -Required $True -IPVersion IPv6
.\Get-O365EndpointsPerCategory.ps1 -Service Common -Category Allow -Required $True -IPversion IPv4
.\Get-O365EndpointsPerCategory.ps1 -SearchURL office.net | ft
```

**Examples for tracking changes:**

```powershell
.\Get-O365EndpointsPerCategory.ps1 -ChangesWithinLastNumOfDays 60 | ft
.\Get-O365EndpointsPerCategory.ps1 -ChangesWithinLastNumOfDays 180  | where serviceArea -like *skype* | ft
(.\Get-O365EndpointsPerCategory.ps1 -ChangesWithinLastNumOfDays 180 | where impact -like *remove*).urls | select -Unique
(.\Get-O365EndpointsPerCategory.ps1 -ChangesWithinLastNumOfDays 180 | where impact -like *add*).urls | select -Unique
(.\Get-O365EndpointsPerCategory.ps1 -ChangesWithinLastNumOfDays 360 | where impact -like *add*).ips | select -Unique
```
