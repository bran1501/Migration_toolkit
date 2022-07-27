# Knowledge Objects Sync(KOS)

Content Validation V2:

This Panel will make sure all titles are migrated.

src = on-prem

dest = Splunk Cloud

If src=true and dest=true, this means the KO titles was migrated successfully.

Inputs:

Exclude: Click on the apps you don’t want to see populating.

Missing: By default is set up to true in order to check all missing KOs.

Content: Select if you would like to see all content(User, global and app) or just User content or any user content.

Environment: Click on the stack name(Remember to replace $lookup$)



Select the KO you would like to see(By default Savedsearches are gonna show up)

If no information is returned, make sure you renamed the lookup correctly.

If Lookup is correct, this means all content was migrated successfully

If you made sure everything is migrated but user content is showing up, until the user logs in, this content will disappear from the search.

If you click on the panel, it will show another search that is comparing the content of the title(This would only check existing content on both environments.



Update Validation:

Type and date and Splunk will check the updated KOs since this date.



Data Validator:

Here you can check if all buckets from on-prem were migrated.

Check the source and pre-requisites, then assign the correct name to the lookup

Useful dashboards:

Event Parser: Parse your data using the magic 8.

Data Quality: Check the sourcetypes with issues and use this dashboard to identify better and faster the main issues.

PRE-REQUISITES:
RUN ON-PREM:
ANY QUESTIONS REACH OUT TO CHRISTHIANB@SPLUNK.COM

This is an example:

Stack Name: cloud-test

Run On-Prem:
| rest splunk_server=local /servicesNS/-/-/data/ui/views | fields eai:acl.sharing, eai:acl.app, disabled, label, title, eai:acl.owner eai:data updated
-> LOOKUP: cloud-test_all_dashboards.csv

| rest splunk_server=local /servicesNS/-/-/saved/searches | fields eai:acl.app title is_scheduled eai:acl.owner eai:acl.sharing search updated
-> LOOKUP: cloud-test_all_saved_searches_src.csv

| rest splunk_server=local /servicesNS/-/-/data/props/extractions | fields title eai:acl.app, eai:acl.owner,eai:acl.sharing author attribute value updated
-> LOOKUP: cloud-test_all_field_extraction_src.csv

| rest splunk_server=local servicesNS/-/-/saved/eventtypes | fields eai:acl.app,eai:acl.owner,eai:acl.sharing,search,tags,title, updated
-> LOOKUP: cloud-test_all_eventtypes_src.csv

| rest splunk_server=local /servicesNS/-/-/search/tags | fields title updated
-> LOOKUP: cloud-test_all_tags.csv

| rest splunk_server=local /servicesNS/-/-/datamodel/model | fields title eai:acl.app, eai:acl.owner,eai:acl.sharing,updated
-> LOOKUP: cloud-test_all_datamodel_src.csv

| rest splunk_Server=local /servicesNS/-/-/data/lookup-table-files | fields title eai:acl.app, eai:acl.owner,eai:acl.sharing,updated
-> LOOKUP: cloud-test_all_lookup_src.csv

| rest splunk_server=local /servicesNS/-/-/configs/conf-macros | fields title eai:acl.app eai:acl.owner eai:acl.sharing definition args disabled updated
-> LOOKOUP: cloud-test_all_macros_src.csv

| rest splunk_server=local /servicesNS/-/-/apps/local | fields label title
-> LOOKUP: cloud-test_all_apps_src.csv

| rest splunk_server=local /servicesNS/-/-/authentication/users | fields email realname title type
-> LOOKUP: cloud-test_all_users_src.csv

Upload all this lookups using the above naming convention. DO NOT CREATE LOOKUP DEFINITIONS

Make sure the Lookups have the proper permissions to be seen by the App.

