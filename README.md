# get-azure-and-o365-endpoints

**Get-O365EndpointsPerCategory:**
This script connects to O365 endpoints RestAPI and keeping an offline version to run the script more efficient and to avoid making same requests to query for same data much often.

**Get-AzureEndpoints:**
This script downloads "AzureServiceTags" json file and parsing it into csv to get a single subnets per row view. The script always checks for local csv copy and using it for filtering (checking script execution folder). So simply re-run the script to apply filters you are interested in.
