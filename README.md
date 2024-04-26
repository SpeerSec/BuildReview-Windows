# Setup
From a PowerShell window run the following:

You might find the script fails to run even when running as an administrative PowerShell window, issue the following command;
```PowerShell
Set-ExecutionPolicy -ExecutionPolicy Bypass -Scope Process -Force
```

*Process* is used here as it will ensure that after PowerShell is closed the client's security is restored.


```PowerShell
Import-Module "C:\path\to\root\folder\BuildReview.psd1"
```

_If you git cloned to Documents:_
```PowerShell
Import-Module "$env:USERPROFILE\Documents\BuildReview-Windows\BuildReview.psd1"
```
---

Then run:

```PowerShell
New-BuildReviewCollector
```

_Old instruction:_
_You should now have a wsus cab file and a ps1 in the root of your %userprofile% folder. You need these both on the system to be audited, note the wsus cab file must be on the root of the C:\ drive; the script can be anywhere._

!! The script should now move the cab file to the root of the system drive on it's own. Just perform a quick check before running the next commands !!



Next if you are in the Documents directory:

```PowerShell
..\BuildReview.ps1
```


OR at the path output by the script.


This script will usually take 5-10 minutes depending on the OS and size of policies.

In cases where a policy is enforcing the execution policy simply run this instead;
```PowerShell
iex [System.IO.File]::ReadAllText('c:\BuildReview.ps1')
```

# Exporting Results
The HTML results and tool-output directory for each host will be saved to `C:\Results\`


# Coverage

I can update registries to check depending on the OS. I have updated the current checked registries to include Server 2019, 2022 and Windows 11.


From OneLogicalMyth:
In the meantime ensure you read the raw XML results file generated as you will see blank results for some collections/groups/checks depending on the OS. Additionally, it is recommend each reported issue is verified to ensure accuracy.

In Scope:
* Windows 2012 R2 (works best)
* Windows 2008 R2
* Windows 2022
* Windows 2019
* Windows 2016
* Windows 8.1
* Windows 11
* Windows 10
* Windows 7

Out of Scope:
* Windows 2012
* Windows 2008
* Windows Vista
* Windows 8
* Windows XP
* Windows 2000 or older
