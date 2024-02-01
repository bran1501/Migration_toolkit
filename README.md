KOS
* Description *
This the NEW & IMPROVED KOS App.
Deprecated app: Knowledge Object Sync (KOS) https://splunkbase.splunk.com/app/6536.
New feature:
This app is only dedicated for the Final Migration Review. Useful Dashboards can be found here -> https://github.com/bran1501/Data-Health-Check

Using KOS you can verify if all your Knowledge Objects(KO) were moved correctly and with the same content(search,data,etc.)
This works if you are migrating from on-prem to on-prem of on-prem to the cloud
 
* Setup *
Splunk Enterprise:
Go to Manage Apps > Browse more Apps > Look for Knowledge Object Sync(KOS) and install it
 
Splunk Cloud:
Go to Manage Apps > Browse more Apps > Look for Knowledge Object Sync(KOS) and install it
 
* Help *
While this app is not formally supported, the developer can be reached at splunkbase@prudentconsulting.com. Responses are made on a best effort basis. Feedback is always welcome and appreciated!
(if you use the User Group approach, include: Learn more about splunk-usergroups slack here: https://docs.splunk.com/Documentation/Community/current/community/Chat#Join_us_on_Slack)

Details:
# Instructions
 
## Prerequisites
Before installing this app, the following needs to be addressed on-prem.
Go to the Tab *On-prem Lookups*, click on the options and the lookup will be automatically downloaded.

## Install
This app should be installed on Search Heads Only
https://docs.splunk.com/Documentation/SplunkCloud/latest/Admin/Experience Install the app. For Splunk Cloud, refer to [Install apps in your Splunk Cloud deployment](https://docs.splunk.com/Documentation/SplunkCloud/latest/Admin/SelfServiceAppInstall). For customer managed deployments, refer to the standard methods for Splunk Add-on installs as documented for a [Single Server Install](http://docs.splunk.com/Documentation/AddOns/latest/Overview/Singleserverinstall) or a [Distributed Environment Install](http://docs.splunk.com/Documentation/AddOns/latest/Overview/Distributedinstall).
 
## Configuration
Make sure you are sc_admin and share the lookups to this app only.
 
## Usage
Content Validation V2:
This Panel will make sure all titles are migrated.
src = on-prem
dest = Splunk Cloud/on-prem destination
If src=true and dest=true, this means the KO titles were migrated successfully.
Inputs:
Exclude: Click on the apps you don’t want to see populating.
Missing: By default is set up to true in order to check all missing KOs.
Content: Select if you would like to see all content(User, global and app) or just User content or any user content.
Environment: Click on the stack name(Remember to replace lookup) or setup the static value
Select the KO you would like to see(By default Savedsearches are gonna show up)

Update Validation:
Type a date and Splunk will check the updated KOs since this date.
Data Validator:
Here you can check if all buckets from on-prem were migrated.
Check the source and pre-requisites, then assign the correct name to the lookup
Useful dashboards:
Event Parser: Parse your data using the magic 8.
Data Quality: Check the sourcetypes with issues and use this dashboard to identify better and faster the main issues.
 
 
# Known Issues
See the release notes of the latest version for known issues
 
# Troubleshooting Steps
If no information is returned, make sure you renamed the lookup correctly.
If Lookup is correct, this means all content was migrated successfully.
If you make sure everything is migrated but user content is showing up, until the user logs in, this content will disappear from the search.
If you click on the panel, it will show another search that is comparing the content of the title(This would only check existing content on both environments).
 
# Upgrade
No special instructions for upgrading this app to a newer version.
 
# Help
While this app is not formally supported, the developer can be reached at christhianb@splunk.com (OR in splunk-usergroups slack, @Christhian Bran). Responses are made on a best effort basis. Feedback is always welcome and appreciated!
(if you use the User Group approach, include: Learn more about splunk-usergroups slack here: https://docs.splunk.com/Documentation/Community/current/community/Chat#Join_us_on_Slack)

