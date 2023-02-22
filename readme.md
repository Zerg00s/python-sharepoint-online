# SharePoint Onlye App + Python Authentication Tutorial

### Create a new App Principal
https://TENANT.sharepoint.com/_layouts/15/appregnew.aspx


### Grant tenant-wide permissions. See full list of permissions.
https://TENANT.-admin.sharepoint.com/_layouts/15/appinv.aspx
```
<AppPermissionRequests AllowAppOnlyPolicy="true">
	<AppPermissionRequest Scope="http://sharepoint/content/tenant" Right="FullControl" />
	<AppPermissionRequest Scope="http://sharepoint/taxonomy" Right="Write" />
</AppPermissionRequests>
```


### Grant SITE COLLECTION PERMISSIONS. See full list of permissions.
https://TENANT.sharepoint.com/sites/SITE_OF_YOUR_CHOICE/_layouts/15/appinv.aspx

XML with Permissions Requests:
```
<AppPermissionRequests AllowAppOnlyPolicy="true">
  <AppPermissionRequest Scope="http://sharepoint/content/sitecollection" Right="FullControl" />
</AppPermissionRequests>
```


## TEST CONNECTION WITH PNP POWERSHELL

```
Connect to SharePoint from PowerShell
	$appId = "CLIENT_ID"
	$appSecret = "CLIENT_SECRET"
	$url = "https://tenant.sharepoint.com"
	Connect-PnPOnline -Url $url -ClientId $appId -ClientSecret $appSecret
```


## INSTALL PYTHON AND PIP

```
sudo apt update && upgrade
sudo apt install python3 python3-pip ipython3
```


## INSTALL  Office365-REST-Python-Client 
```
pip install Office365-REST-Python-Client
```



## PYTHON FILE FOR CONNECTING TO SHAREPOINT ONLINE USING CLIENT SECRET

Read more here: https://github.com/vgrem/Office365-REST-Python-Client

**Python File contents**

```
from office365.sharepoint.client_context import ClientContext
from office365.runtime.auth.client_credential import ClientCredential

client_credentials = ClientCredential('CLIENT_ID','CLIENT_SECRET')

ctx = ClientContext('https://gocleverpointcom.sharepoint.com/sites/hubclb').with_credentials(client_credentials)
target_web = ctx.web.get().execute_query()
print(target_web.url)
```


