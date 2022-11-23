**Automates MDS SAN Zoning with Intersight Cloud Orchestrator [ICO]**

This workflow automates the tasks required to zone a new host to an MDS based SAN fabric [A/B].
It leverages Intersight Cloud Orchestrator [ICO] and tasks that invoke web API requests to the MDS.
The included tasks can be used to build additional workflows e.g. add storage targets [wwpn or device-alias] to host zone.

Use as is or modify to your needs.  Test in a lab environment before using in production.

Included data types:
Fibre Channel Device WWPN

Included tasks:
Get MDS Active Zoneset Name
Add MDS Device Alias
Add Zone to MDS
Add MDS Zone to Zoneset
Activate MDS Zoneset
Commit MDS Zone Database
Copy MDS Running to Startup

To execute the workflow, the MDS Switches must be connected to Intersight by adding them as a target.
https://intersight.com/help/saas/getting_started/claim_targets#minimum_permissions_for_targets

The required inputs are: Zone Name, MDS Fabric A, VSAN Fabric A, WWPN Fabric A, MDS Fabric B, VSAN Fabric B and WWPN Fabric B.
Upon execution the workflow will create new device-alias based on the inputted host wwpns and use these device-alias as the zone member type.

<img width="913" alt="Screen Shot 2022-11-23 at 8 57 37 AM" src="https://user-images.githubusercontent.com/22679823/203569569-929218c5-6e02-464e-ad19-2ab5c8fe0df0.png">

During execution the workflow will gather the active zoneset name for the given VSAN ID.  This requires an active zoneset to be present and also ensures the new zone is added to the active zoneset and database.  This assumes enhanced zoning mode [recommended] is enabled for the given VSAN ID.

<img width="1514" alt="Screen Shot 2022-11-23 at 8 58 56 AM" src="https://user-images.githubusercontent.com/22679823/203569618-35dbfd33-47ad-4ca8-8bf7-47427e9f2422.png">
