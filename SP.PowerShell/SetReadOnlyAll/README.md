# Change all permissions to read-only.

This solution will change all permissions to read only. The script will start at the site level and change all site permissions to Read. If the site is inheriting permissions from its parent site, it will break permission inheritance and set the new site permissions to Read. It will then find any lists (excluding hidden lists) and set any list and list item permissions to Read.

# Configuration
You must download 4 files (_Apply-ReadOnlySites.ps1_, _SPListItemHelper.dll_, _Microsoft.SharePoint.Client.dll_, _Microsoft.SharePoint.Client.Runtime.dll_) and place them all into the same folder on your computer. The _SPListItemHelper_ folder is not required.

# Syntax Examples

1. Set the site at the SPRootSite and all subsites to read only.
```
.\Apply-ReadOnlySites.ps1 -SPRootSite "https://tenant.sharepoint.com/sites/siteurl" -Recursive
```

2. Set the site at the SPRootSite and ignore subsites.
```
.\Apply-ReadOnlySites.ps1 -SPRootSite "https://tenant.sharepoint.com/sites/siteurl"
```

3. Process all subsite trees, but ignore the currest site
```
Get-PnPSubWeb | ForEach-Object { .\Apply-ReadOnlySites.ps1 -SPRootSite $_.Url -Recursive }
```