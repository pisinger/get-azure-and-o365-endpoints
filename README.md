# get-azure-and-o365-endpoints

**☝Tested with PowerShell 7 only:**

> <https://docs.microsoft.com/en-us/powershell/scripting/install/installing-powershell-on-windows?view=powershell-7.2/>

> <https://aka.ms/powershell-release?tag=stable/>

---

**Get-O365EndpointsPerCategory:**
This script connects to O365 endpoints RestAPI and keeping an offline version to run the script more efficient and to avoid making same requests to query for same data much often. In addition, you can use the script also to tack for changes within last time delta. For this simply use the `$ChangesWithinLastNumOfDays` param to query for changes.

**Get-AzureEndpoints:**
This script downloads "AzureServiceTags" json file and parsing it into csv to get a single subnets per row view. The script always checks for local csv copy and using it for filtering (checking script execution folder). So simply re-run the script to apply filters you are interested in.
