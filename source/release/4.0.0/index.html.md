---
title: OVirt 4.0.0 Release Notes
category: documentation
authors: rafaelmartins
---

# oVirt 4.0.0 Release Notes

The oVirt Project is pleased to announce the availability of oVirt 4.0.0 beta1 release as of May 19th, 2016.

oVirt is an open source alternative to VMware™ vSphere™, and provides an awesome KVM management interface for multi-node virtualization. This release is available now for Red Hat Enterprise Linux 7.2, CentOS Linux 7.2 (or similar).

This is pre-release software. Please take a look at our [community page](http://www.ovirt.org/community/) to know how to ask questions and interact with developers and users. All issues or bugs should be reported via the [Red Hat Bugzilla](https://bugzilla.redhat.com/). The oVirt Project makes no guarantees as to its suitability or usefulness. This pre-release should not to be used in production, and it is not feature complete.

To find out more about features which were added in previous oVirt releases,
check out the [previous versions release notes](http://www.ovirt.org/develop/release-management/releases/).
For a general overview of oVirt, read [the Quick Start Guide](Quick_Start_Guide)
and the [about oVirt](about oVirt) page.

## Install / Upgrade from previous versions

### Fedora / CentOS / RHEL

## BETA RELEASE

In order to install oVirt 4.0.0 Alpha Release you will need to enable oVirt 4.0.0 beta1 release repository.

In order to install it on a clean system, you need to install

`# yum localinstall `[`http://plain.resources.ovirt.org/pub/ovirt-4.0_beta1/rpm/el7/noarch/ovirt-release40.rpm`](http://plain.resources.ovirt.org/pub/ovirt-4.0_beta1/rpm/el7/noarch/ovirt-release40.rpm)

To test oVirt 4.0.0 beta1 release, you should read our [Quick Start Guide](Quick Start Guide).

### oVirt Hosted Engine

If you're going to install oVirt as Hosted Engine on a clean system please follow [Hosted_Engine_Howto#Fresh_Install](Hosted_Engine_Howto#Fresh_Install) guide.

If you're upgrading an existing Hosted Engine setup, please follow [Hosted_Engine_Howto#Upgrade_Hosted_Engine](Hosted_Engine_Howto#Upgrade_Hosted_Engine) guide.

## What's New in 4.0.0?

### Enhancement

#### oVirt Engine

 - [BZ 1037844](https://bugzilla.redhat.com/1037844) <b>[RFE][AAA] Allow the user to change an expired password as a part of the User Portal login process</b><br>Previously if the user password has expired they needed to be set on the ldap server. Now there is a new capability added to the ldap and jdbc extensions to enable changing passwords from the front end in a new change password screen.
 - [BZ 1054070](https://bugzilla.redhat.com/1054070) <b>[RFE] add ability to cold restart of a VM when it run by Run Once and reboots</b><br>
 - [BZ 1060791](https://bugzilla.redhat.com/1060791) <b>[RFE] Cleanup, remove IP information guest_info section from VM resource</b><br>
 - [BZ 1083661](https://bugzilla.redhat.com/1083661) <b>[RFE] display cluster compatibility version for host</b><br>'Cluster Compatibility Version' field, which shows cluster version supported by the host, were added into Hosts view, General Tab, Info subtab
 - [BZ 1092744](https://bugzilla.redhat.com/1092744) <b>[RFE][AAA] Introduce uniform login services</b><br>A single sign on module has been added that authenticates the user once and allows access to webadmin and userportal. Signing off from one portal closes the session on SSO and the user is logged out of all portals.
 - [BZ 1110577](https://bugzilla.redhat.com/1110577) <b>[RFE] introduce Italian</b><br>
 - [BZ 1121653](https://bugzilla.redhat.com/1121653) <b>[RFE] "Open in full screen" checkbox should be controlled by a global setting in "rhevm-config"</b><br>Feature: Configure default for Console's Open In Fullscreen<br><br>Reason: Open In Fullscreen default behavior shall be configurable by user.<br><br>Result: Using engine-config, the user can set weather the console's window is going to be open in full screen by default. <br>The value can be set independently for Administrtion Portal, Basic User portal, Extended User Portal.<br>Console retrieved via REST shares setting with the Administration Portal.<br><br>Default can be set via engine-config by setting FullScreenWebadminDefault, FullScreenUserportalBasicDefault, FullScreenUserportalExtendedDefault options.
 - [BZ 1138139](https://bugzilla.redhat.com/1138139) <b>[RFE][ImportDomain] Adding a button to import floating and unregistered disks</b><br>Feature: Register unregistered floating disks through the GUI.<br><br>Reason: Since floating disks are not part of any VM/Template, the user can't register floating disks explicitly from the GUI but only from the REST.<br><br>Result: Added a subtab in the GUI called "Import Disk" which support the ability toe register a floating disk into the setup.<br><br>A storage domain also supports a functionality called "Scan Disks" which scans the Storage Domain for unregistered floating disks that are not reflected in the setup.<br>This can be much helpful for managing underline copies of disks from an external Storage Domain.
 - [BZ 1150239](https://bugzilla.redhat.com/1150239) <b>[RFE] [pre-4.0] Model memory volumes as disks in the database/backend</b><br>
 - [BZ 1172390](https://bugzilla.redhat.com/1172390) <b>[RFE] GUI should have a field/column chooser in the UI</b><br>Data tables in WebAdmin UI now support "column control" context menu, triggered by right-clicking the table header area.<br><br>This context menu allows controlling visibility and position of individual columns. This is useful for users who don't need to see all columns or want to re-order columns to their liking.
 - [BZ 1176217](https://bugzilla.redhat.com/1176217) <b>[RFE] Rename "Edit" button in Storage Domains tab to "Manage Domain"</b><br>
 - [BZ 1194989](https://bugzilla.redhat.com/1194989) <b>[RFE] Provide option to remove / replace base template while template sub-version exists</b><br>Feature: <br><br>Previously it was only possible to remove base template if there were to template sub-version based on it.<br><br>These patches allows to remove a base template even if there are some template sub-version based on it. The sub-version with lowest version number become the next base template for all other sub-version. Version number are not touched. I.e. Version number of base template no longer needs to be 1.
 - [BZ 1197449](https://bugzilla.redhat.com/1197449) <b>[RFE] add source_ip to the sessions table</b><br>New column 'Source IP' was added into Active Users Sessions view, to be able to identify client host from which users connects to engine
 - [BZ 1199933](https://bugzilla.redhat.com/1199933) <b>[RFE] Add Fencing of Ilo3/4 via ssh fencing to RHEV-M</b><br>Feature: Add Fencing of Ilo3/4 via ssh fencing<br><br>Reason: Customer requirement <br><br>Result: Fencing of Ilo3/4 via ssh is supported
 - [BZ 1205641](https://bugzilla.redhat.com/1205641) <b>[RFE][HC] - Monitor if self-heal is ongoing on a gluster volume</b><br>Feature: Monitor Self-Heal for gluster volumes.<br><br>Reason: For a replicate volume, the engine should monitor if self-heal is ongoing on a volume. There should be an indication in the UI for self-heal activity.<br><br>Result: Ovirt will monitor the unsycned entries(which needs healing) in all the replicate  volumes. Unsynced entries will be shown in the bricks sub per brick with expected time to heal the entries. There will be a warning icon added to the volume and bricks status column when there is a unsynced entry.
 - [BZ 1208860](https://bugzilla.redhat.com/1208860) <b>Template versions have non-unique name in Disk tab</b><br>Feature: The Disk Tab displays template version along with its name.<br><br>Reason: There was confusion in listing of template disks, since just the name of a template was displayed.<br><br>Result: Improved user experience. User can simply decide which template version the disk belongs to.
 - [BZ 1213309](https://bugzilla.redhat.com/1213309) <b>[RFE][HC] - Support replace brick from UI</b><br>
 - [BZ 1216888](https://bugzilla.redhat.com/1216888) <b>[RFE] engine-backup should not depend on the engine</b><br>
 - [BZ 1218674](https://bugzilla.redhat.com/1218674) <b>[RFE][TEXT] - During restore alert user that objects might be missing in the system afterwards.</b><br>
 - [BZ 1223732](https://bugzilla.redhat.com/1223732) <b>[RFE] Add authz provider column for user session management</b><br>Feature: User session management.<br><br>Reason: There was no authz information for users in session management table, so we were not able to distinguish between two users with the same name from two different profiles (domains).<br><br>Result: In session management table, users can now see authz provider name where users belongs.
 - [BZ 1234394](https://bugzilla.redhat.com/1234394) <b>[RFE] VM Pools allow stateful VMs</b><br>
 - [BZ 1240954](https://bugzilla.redhat.com/1240954) <b>[RFE][webadmin-portal] Cannot override template's name when importing an image as template from glance</b><br>It is now possible to specify a custom name for the template when importing a Glance disk through the Web Admin portal.
 - [BZ 1250102](https://bugzilla.redhat.com/1250102) <b>[RFE] - Show user/group icons in search results for users</b><br>
 - [BZ 1252426](https://bugzilla.redhat.com/1252426) <b>[RFE] Migration improvements (convergence, bandwidth utilization)</b><br>\* Tab 'Resilience policy' in Cluster dialogs was renamed to 'Migration'. The content of the tab remains part of 'Migration' dialog.
 - [BZ 1253710](https://bugzilla.redhat.com/1253710) <b>[RFE] Add template methods to work with Cloud-Init/Sysprep settings through RHEVM API</b><br>Cloud-init and sysprep are now can be added via REST API
 - [BZ 1255474](https://bugzilla.redhat.com/1255474) <b>[RFE][SCALE] traffic shaping on ovirtmgmt interface</b><br>
 - [BZ 1264767](https://bugzilla.redhat.com/1264767) <b>[RFE] Enforce a specific(latest) spice client version</b><br>Feature: enforce minimal version of remote-viewer <br><br>Enforces the minimal version of remote-viewer to versions:<br>windows: 2.0-128<br>rhel7: 2.0-6<br>rhel6: 2.0-14<br><br>If the remote-viewer is older than the specified one, remote-viewer will show a link to documentation describing how to update.
 - [BZ 1267508](https://bugzilla.redhat.com/1267508) <b>[RFE] Replace python-cheetah with python-jinja2 within ovirt-engine</b><br>Replaced python-cheetah with python-jinja2 as template-engine for services configuration files, as python-cheetah didn't receive updates since 2012 and is not available on RHEL 7.2.
 - [BZ 1271698](https://bugzilla.redhat.com/1271698) <b>Change terminology from "virtual machine disk" to "virtual disk"</b><br>
 - [BZ 1271988](https://bugzilla.redhat.com/1271988) <b>[RFE] Add support for qcow2 disks, adding the ability to choose qcow2 disk format when creating a VM from template.</b><br>Feature: When creating a Vm from a template, the user is able to choose the Volume Format of the disks : either Raw or QCOW2.<br><br>Reason: The user wants to be able to specify the volume format of the disks when creating a template based VM.<br><br>Result: When creating a Vm from a template, the user is able to choose the Volume Format of the disks : either Raw or QCOW2.<br>The Allocation Policy is now hidden.<br>If the Template Provisioning is Thin, the volume format of the disks will be marked as QCOW2 and the user won't be able to change it.<br>If the Template Provisioning is Clone, the user will be able to choose the volume format (QCOW2 or Raw)
 - [BZ 1273025](https://bugzilla.redhat.com/1273025) <b>User portal's permission tab offers to add permissions which cannot be added</b><br>Feature: User portal lists only roles which can be actually assigned.<br><br>Reason: All roles were displayed causing user's confusion.<br><br>Result: Improved user experience.
 - [BZ 1273041](https://bugzilla.redhat.com/1273041) <b>[RFE] extend Permission tab with list of 'My groups'</b><br>The add permissions dialog now has a new radio button "My Groups" which lists the currently logged in user's groups. The user can use this option to grant permissions to other users in his group.
 - [BZ 1273399](https://bugzilla.redhat.com/1273399) <b>[RFE] Support for reporting Docker containers active on the Virtual Machine</b><br>
 - [BZ 1275182](https://bugzilla.redhat.com/1275182) <b>[RFE]Email notification when the number of LVs in SD are reaching/more than 300</b><br>Previously, when the number of LVs in a storage domain reached the recommended maximum, we logged it and a message was shown in the events pane.<br>Now, one can register to the event notifier and get an email when it happens.
 - [BZ 1277495](https://bugzilla.redhat.com/1277495) <b>remove the pre-3.6 setupnetworks api</b><br>
 - [BZ 1277569](https://bugzilla.redhat.com/1277569) <b>[RFE] Atomic guest OS support</b><br>
 - [BZ 1279398](https://bugzilla.redhat.com/1279398) <b>[RFE] [admin portal] Sort ISOs from ISO domain in lists in natural (version) sort order</b><br>Feature: Sort ISO domain files while taking into consideration version numbers.<br><br>Reason: Up until now, the files were ordered alphabetically, i.e a file named RHEV_3.5.10.iso used to come before a file named RHEV_3.5.5.iso.<br>This feature sorts the files alphabetically, but while taking into consideration the version numbers.<br><br>Result: A file named RHEV_3.5.10.iso will come after a file named RHEV_3.5.5.iso and not before it.
 - [BZ 1281666](https://bugzilla.redhat.com/1281666) <b>[RFE] Engine should warn admin about bad 802.3ad status</b><br>
 - [BZ 1284903](https://bugzilla.redhat.com/1284903) <b>[RFE] Command Infrastructure - support flows</b><br>
 - [BZ 1285446](https://bugzilla.redhat.com/1285446) <b>Random sub-template of given name is used to create VM Pool via REST</b><br>Feature: The latest template version is used within VM creation via REST when just the template name (or Blank) is provided.<br><br>Reason: Prior this enhancement, the template version had to be specified in the REST create VM command explicitly or a random version was selected otherwise.<br><br>Result: The user can rely on default template version selection when creating VM via REST.
 - [BZ 1290737](https://bugzilla.redhat.com/1290737) <b>[AAA] add credentials modify sequence</b><br>
 - [BZ 1302657](https://bugzilla.redhat.com/1302657) <b>[RFE] Switch from vnc/cirrus to vnc/vga</b><br>Feature: Default VNC graphics is VGA in 4.0<br><br>Imported VMs with VNC/Cirrus and originating in previous compatibility versions are automatically upgraded to VNC/VGA.<br><br>The user can still switch the VNC graphics to Cirrus if needed.<br><br>No matter of this change, the QXL shall be preffered as default graphics if the guest OS supports it.
 - [BZ 1304346](https://bugzilla.redhat.com/1304346) <b>[RFE] Prepare a method to compute (guess) the required memory for starting a VM</b><br>
 - [BZ 1308350](https://bugzilla.redhat.com/1308350) <b>[SCALE] Improve GetDeviceList verb call through the REST API to work in scale.</b><br>Adding support for skipping the LUN status check in the REST API.<br>Checking the status of the LUN is a heavyweight operation and this data is not always needed by the user.<br><br>The default is `true` for backward compatibility.<br>The parameter `report_status` is available both on getting the list of a host storages or a specific host storage.<br>
 - [BZ 1308861](https://bugzilla.redhat.com/1308861) <b>[RFE] Indicate which host is running the HE VM</b><br>
 - [BZ 1310804](https://bugzilla.redhat.com/1310804) <b>[RFE] Override instance type on VmPools in Python-SDK</b><br>Feature: add instance type support for REST API for vm pools<br><br>Reason: It can be set in webadmin/userportal but it was missing from the REST API and from the SDKs<br><br>Result: Now it is possible to set the instance type also from the REST API/SDKs
 - [BZ 1313295](https://bugzilla.redhat.com/1313295) <b>[RFE] noVNC: Include VM name in the web page title instead of "noVNC" title.</b><br>Feature: Include VM name into the title of both noVNC and SPICE HTML5 windows.<br><br>Reason: Since the noVNC always had a title "noVNC", it was hard to know which VM is this console connected to. The same goes for the SPICE HTML5 window which had a title "Spice Javascript Client".<br><br>Result: The title of the noVNC window is now: <br>\<vm name\> - noVNC<br>The title of the SPICE HTML5 window is now: <br>\<vm name\> - Spice Javascript Client
 - [BZ 1314375](https://bugzilla.redhat.com/1314375) <b>[RFE] - Provide external network partners API</b><br>
 - [BZ 1316077](https://bugzilla.redhat.com/1316077) <b>[RFE] Mention the vcenter hierarchy at Data Center option when import guest from vmware in rhevm</b><br>There is an '?' (question mark) near the data-center field that explain that folder can be in data-center as well:<br>e.g:<br>mydatacenter<br>or<br>mydatacenter/myfolder
 - [BZ 1317434](https://bugzilla.redhat.com/1317434) <b>[RFE] Implement live merge of auto-generated snapshot and backing file after live storage migration</b><br>
 - [BZ 1318580](https://bugzilla.redhat.com/1318580) <b>[RFE] restore: ensure that 3.6 backup can be restored on clean 4.0</b><br>Feature: Allow engine-backup of version 4.0 to restore backups taken on 3.6.<br><br>Reason: engine 4.0 does not support el6. Users that want to upgrade from 3.6 on el6 to 4.0 on el7 have to do this by backing up the engine on 3.6/el6 and restore on 4.0/el7.<br><br>Result: Using this flow, it's possible to migrate a 3.6/el6 setup to 4.0/el7:<br>
 - [BZ 1318665](https://bugzilla.redhat.com/1318665) <b>[RFE] - make DWH required for engine.</b><br>
 - [BZ 1318746](https://bugzilla.redhat.com/1318746) <b>[RFE] Sessions tab: improve usability</b><br>New fields have been added to session tab in webadmin to show the client ip address, the session start time and the session last access time.
 - [BZ 1322940](https://bugzilla.redhat.com/1322940) <b>[RFE] AAA - Make Kerberos work with Java Authentication Framework</b><br>Feature: <br><br>Reason: Provide a way how to configure gssapi using ticket cache for authz pool.<br><br>Result: We added new security domain called 'oVirtKerbAAA' into JBoss configuration.<br>
 - [BZ 1327012](https://bugzilla.redhat.com/1327012) <b>[RFE] Remove dwh_datacenter_history_view from engine db</b><br>
 - [BZ 1328805](https://bugzilla.redhat.com/1328805) <b>[RFE] Add option to run DWH in a "minimal" mode for collecting data for the dashboards</b><br>

#### VDSM

 - [BZ 1182092](https://bugzilla.redhat.com/1182092) <b>[RFE] Make plug-able API for supervdsm</b><br>
 - [BZ 1252426](https://bugzilla.redhat.com/1252426) <b>[RFE] Migration improvements (convergence, bandwidth utilization)</b><br>\* Tab 'Resilience policy' in Cluster dialogs was renamed to 'Migration'. The content of the tab remains part of 'Migration' dialog.
 - [BZ 1270581](https://bugzilla.redhat.com/1270581) <b>[RFE] Hostdev_passthrough: support SCSI FC tape device</b><br>
 - [BZ 1273399](https://bugzilla.redhat.com/1273399) <b>[RFE] Support for reporting Docker containers active on the Virtual Machine</b><br>
 - [BZ 1281666](https://bugzilla.redhat.com/1281666) <b>[RFE] Engine should warn admin about bad 802.3ad status</b><br>
 - [BZ 1298120](https://bugzilla.redhat.com/1298120) <b>[RFE] Support for hooks in the guest agent</b><br>
 - [BZ 1304509](https://bugzilla.redhat.com/1304509) <b>[RFE] consume NetworkManager-defined interfaces</b><br>
 - [BZ 1324375](https://bugzilla.redhat.com/1324375) <b>[RFE] Use 10s timeout for boot menu</b><br>Boot menu timeout was increased to 10 seconds. This should make the boot menu more accessible when pause mode is not enabled.
 - [BZ 1334745](https://bugzilla.redhat.com/1334745) <b>[RFE] Add hook to handle FCOE storages</b><br>

#### oVirt Hosted Engine Setup

 - [BZ 1228641](https://bugzilla.redhat.com/1228641) <b>[RFE] Switch from XML-RPC to JSON-RPC API for HE setup</b><br>
 - [BZ 1324921](https://bugzilla.redhat.com/1324921) <b>[RFE] hosted-engine should have a flag to check whether the engine is deployed</b><br>hosted-engine should have a flag to check whether the engine is deployed<br>

#### oVirt Engine DWH

 - [BZ 1285788](https://bugzilla.redhat.com/1285788) <b>[RFE] Enable logging of dwh ETL process in debug mode</b><br>Feature: We added a DEBUG mode for logging of Sampling, Hourly and Daily jobs time.<br><br>In order to start DEBUG mode, you should add a conf file and set `DWH_AGGREGATION_DEBUG=true`. <br><br>Reason: In order to debug the Sampling, Hourly and Daily jobs.<br><br>Result: The ovirt-engine-dwhd.log will include the start and wnd of each job.<br><br>This is usually for qa only.
 - [BZ 1302598](https://bugzilla.redhat.com/1302598) <b>[RFE] Add to ovirt_engine_history views that simplifies users usage of dwh views</b><br>Feature: Added for each time period (sample/hourly/daily) views that join the configuration views with statistics views of the entities it relates to, like network interface and disks.<br><br>Reason: In order to simplify the use of views for the users.<br><br>Result: 3 new views for vms and 3 new views for hosts.
 - [BZ 1302611](https://bugzilla.redhat.com/1302611) <b>[RFE] - Upgrade the Talend to latest version that supports OpenJDK 1.8.</b><br>
 - [BZ 1318665](https://bugzilla.redhat.com/1318665) <b>[RFE] - make DWH required for engine.</b><br>
 - [BZ 1324440](https://bugzilla.redhat.com/1324440) <b>[RFE] Add log message with the Application Settings</b><br>Feature: A log message with the dwh application settings, that can be updated by the user, was added to the log file.<br>The log is added each time the dwh is started.<br><br>Reason: Add better way to debug and monitor the dwh settings. <br>
 - [BZ 1328805](https://bugzilla.redhat.com/1328805) <b>[RFE] Add option to run DWH in a "minimal" mode for collecting data for the dashboards</b><br>

#### oVirt vmconsole

 - [BZ 1328854](https://bugzilla.redhat.com/1328854) <b>[RFE] provide alphabetic order when displaying available vm consoles</b><br>

#### oVirt Log collector

 - [BZ 1294984](https://bugzilla.redhat.com/1294984) <b>[RFE][TEXT] - add warning when running log collector without filters.</b><br>

#### oVirt Engine SDK Ruby

 - [BZ 1291365](https://bugzilla.redhat.com/1291365) <b>[RFE] Create a Ruby SDK for the oVirt API</b><br>Ruby SDK for the oVirt API is now available<br>

#### oVirt Host Deploy

 - [BZ 1200469](https://bugzilla.redhat.com/1200469) <b>[RFE] add support for hosted-engine deployment on additional hosts</b><br>Feature: support for hosted-engine deployment on additional hosts has been added to ovirt-host-deploy<br><br>Reason: to ease hosted-engine additional node deployment<br><br>Result: ovirt-engine can now use ovirt-host-deploy for deploying hosted engine additional nodes

#### OTOPI

 - [BZ 1216888](https://bugzilla.redhat.com/1216888) <b>[RFE] engine-backup should not depend on the engine</b><br>

### Deprecated Functionality

#### oVirt Engine

 - [BZ 1236976](https://bugzilla.redhat.com/1236976) <b>[RFE] UIPlugins should not use restapi http session</b><br>The UI code is now aligned with Engine SSO infra, dropping reliance on REST webapp's HTTP session mechanism in favor of using SSO token.<br><br>This impacts (and potentially breaks) all UI plugins as the "RestApiSessionAcquired" callback is now removed.<br><br>From now on, UI plugins should use the newly introduced "api.ssoToken" function when authenticating Engine (e.g. REST API) requests:<br><br>  var xhr = new XMLHttpRequest();<br>  xhr.open('GET', 'http://example.com/ovirt-engine/api');<br>  xhr.setRequestHeader('Authorization', 'Bearer ' + api.ssoToken());<br>  xhr.setRequestHeader('Accept', 'application/json');<br>  xhr.addEventListener('load', function () {<br>    // response loaded OK, parse JSON data<br>    var data = JSON.parse(this.responseText);<br>  });<br>  xhr.send();<br><br>Note that UI plugins no longer need to use session-specific request headers like "Prefer:persistent-auth" and "JSESSIONID:xxx", which simplifies their code.
 - [BZ 1282798](https://bugzilla.redhat.com/1282798) <b>Drop All-in-One support</b><br>All-In-One setup support has been dropped in favor of Hosted Engine.
 - [BZ 1316560](https://bugzilla.redhat.com/1316560) <b>[RFE] remove the plugin support for spice connection</b><br>Spice plugin is not supported since 4.0.<br>The 'Native' spice connection is suggested as a replacement.<br><br>If 'Plugin' is set as the default for Spice connections by user (via engine-config), it is automatically switched to 'Native' by calling engine-setup on upgrade.
 - [BZ 1320515](https://bugzilla.redhat.com/1320515) <b>Remove deprecated api/vms/<id>/move</b><br>The API of /vms/<vmid>/move has been removed, after been deprecated since 3.1

#### oVirt Engine DWH

 - [BZ 1300328](https://bugzilla.redhat.com/1300328) <b>[RFE] Remove collection of data centers statistics</b><br>Deprecated functionality should describe removed or no longer supported features.<br><br>Data centers statistics tables only included status, which is not really meaningful. <br>We removed these tables, views and collection.
 - [BZ 1323605](https://bugzilla.redhat.com/1323605) <b>[RFE] Remove collection from dwh_disk_vm_map_history_view</b><br>Deprecated functionality should describe removed or no longer supported features.<br><br>The collection from engine view `dwh_disk_vm_map_history_view` was replaced by collection from `dwh_vm_device_history_view` on version 3.1.<br><br>This collection was not remove for legacy compatibility.<br><br>In 4.0 legacy compatibility will be for 3.6 only.<br><br>- Removed collection of `disks_vm_map`.<br>- Deleted `disks_vm_map` table from history db.<br>- Deleted `dwh_vm_disk_configuration_history_view` from engine db.

#### oVirt Host Deploy

 - [BZ 1314790](https://bugzilla.redhat.com/1314790) <b>Drop ovirt-host-deploy-offline</b><br>ovirt-host-deploy-offline won't be available anymore in 4.0

### Release Note

#### oVirt Engine

 - [BZ 1285432](https://bugzilla.redhat.com/1285432) <b>[RFE] Expose global alert messages via UI plugin API</b><br>New UI plugin API function `showAlert` has been added, allowing UI plugins to show "global" alert boxes in top center part of the WebAdmin UI.<br><br>This can be useful when a UI plugin wants to inform the user about some important event. The `showAlert` function supports different alert types (danger, warning, success, info) as well as optional auto-hide after given time period.

## Bug fixes

### oVirt Engine

 - [BZ 994403](https://bugzilla.redhat.com/994403) <b>All options “Create Snapshot“ during VM “In Preview” status, should be grayed out</b><br>
 - [BZ 1057009](https://bugzilla.redhat.com/1057009) <b>Taking a memory snapshot should alert the user that the VM will be paused for creation duration.</b><br>
 - [BZ 1148514](https://bugzilla.redhat.com/1148514) <b>Engine may kill session that is still in use</b><br>
 - [BZ 1167698](https://bugzilla.redhat.com/1167698) <b>[SetupNetworks]> Unmanaged network on host NIC should prevent attaching new networks to this NIC, until unmanaged network is removed</b><br>
 - [BZ 1183741](https://bugzilla.redhat.com/1183741) <b>User Portal: "Simple" user: Too much vertical space between top-banner and content in case the "Basic | Extended" bar is hidden</b><br>
 - [BZ 1187752](https://bugzilla.redhat.com/1187752) <b>Hypervisor CPU family and name mismatch between API and webUI</b><br>
 - [BZ 1191514](https://bugzilla.redhat.com/1191514) <b>Missing storage related VDSM error codes</b><br>
 - [BZ 1197808](https://bugzilla.redhat.com/1197808) <b>Unable to remove VM previewing a snapshot</b><br>
 - [BZ 1201482](https://bugzilla.redhat.com/1201482) <b>Storage QoS is not applying on a Live VM/disk</b><br>
 - [BZ 1215727](https://bugzilla.redhat.com/1215727) <b>Whenever an exception is thrown in the front end code, unrelated parts of the GUI tend to stop working (e.g. 'new' and 'import' buttons under Networks tab)</b><br>
 - [BZ 1219383](https://bugzilla.redhat.com/1219383) <b>[MAC pool] limit range to 2^31 addresses</b><br>
 - [BZ 1221163](https://bugzilla.redhat.com/1221163) <b>[TEXT][REST] Wrong error is thrown when attempting an update command on a detached storage domain</b><br>
 - [BZ 1221189](https://bugzilla.redhat.com/1221189) <b>Add warning when adding external FCP lun to VM although it is part of existing storage domain</b><br>
 - [BZ 1226767](https://bugzilla.redhat.com/1226767) <b>New Virtual Machine window-> CPU Shares & CPU Pinning Topology should not be greyed out when usable</b><br>
 - [BZ 1229743](https://bugzilla.redhat.com/1229743) <b>New host info is cleared after disabling use of Host Foreman provider</b><br>
 - [BZ 1246886](https://bugzilla.redhat.com/1246886) <b>Remove vm-pool fails if vms are running</b><br>
 - [BZ 1253440](https://bugzilla.redhat.com/1253440) <b>RadioButton "Specific" in New VM dialog > Hosts is not controlled by its label</b><br>
 - [BZ 1254654](https://bugzilla.redhat.com/1254654) <b>[F23] ovirt-log-collector fails to build on fedora >= 23</b><br>
 - [BZ 1256683](https://bugzilla.redhat.com/1256683) <b>UI not show all "Run on" hosts under vm general tab</b><br>
 - [BZ 1259620](https://bugzilla.redhat.com/1259620) <b>Missing Cpu.setType api</b><br>
 - [BZ 1260732](https://bugzilla.redhat.com/1260732) <b>[BACKWARDS COMPATIBILITY CLEANUP] Remove support for pinning VM to only one CPU</b><br>
 - [BZ 1261335](https://bugzilla.redhat.com/1261335) <b>[engine-setup][text] The error for a missing update in the sql performing the validation should be fixed.</b><br>
 - [BZ 1261795](https://bugzilla.redhat.com/1261795) <b>A minor typo found during translation "Cannot ${action} ${type}. At most one VLAN-untagged Logical Network is allowed on a NIC (optionally in conjunction with several VLAN Logical Networks). The following Network Interfaces violate that : ${NETWORK_INTERF</b><br>
 - [BZ 1261951](https://bugzilla.redhat.com/1261951) <b>Improve error message when OVF cannot be parsed from export domain</b><br>
 - [BZ 1267228](https://bugzilla.redhat.com/1267228) <b>Asynchronous frontend validation of icons</b><br>
 - [BZ 1267259](https://bugzilla.redhat.com/1267259) <b>New/Edit Cluster dialog ui is inconsistent</b><br>
 - [BZ 1267910](https://bugzilla.redhat.com/1267910) <b>PSQLException when insert value to audit log if input string is too long</b><br>
 - [BZ 1268216](https://bugzilla.redhat.com/1268216) <b>Query count grows linear with vm count for /api/vms endpoint</b><br>
 - [BZ 1268224](https://bugzilla.redhat.com/1268224) <b>Query count grows linear with host count for /api/hosts endpoint</b><br>
 - [BZ 1268949](https://bugzilla.redhat.com/1268949) <b>Wrong error message while changing template of vm</b><br>
 - [BZ 1269413](https://bugzilla.redhat.com/1269413) <b>running master on FC22 server.log shows several warnings about java modules.</b><br>
 - [BZ 1269953](https://bugzilla.redhat.com/1269953) <b>Console Client Resources page - cannot scroll</b><br>
 - [BZ 1271094](https://bugzilla.redhat.com/1271094) <b>[Host QoS] - Updating second network with host QoS when it attached to host NIC with another network that is out-of-sync, considered as synced</b><br>
 - [BZ 1271220](https://bugzilla.redhat.com/1271220) <b>[REST] [Host network QoS] It's possible to configure weighted share and rate limit on the network to be bigger than the max value configured on engine</b><br>
 - [BZ 1273094](https://bugzilla.redhat.com/1273094) <b>4.0: can't remove vm template - the disks are removed and the template stays locked</b><br>
 - [BZ 1273447](https://bugzilla.redhat.com/1273447) <b>After a command is finished tasks are not cleared and stay in executing status</b><br>
 - [BZ 1273932](https://bugzilla.redhat.com/1273932) <b>RestAPI returns 500 instead of 400 when sending invalid JSON</b><br>
 - [BZ 1273970](https://bugzilla.redhat.com/1273970) <b>Automation of UI tests needs way to check status of VM in userportal</b><br>
 - [BZ 1274220](https://bugzilla.redhat.com/1274220) <b>Setup can't be canceled using Ctrl + C when setting Local ISO domain path</b><br>
 - [BZ 1274338](https://bugzilla.redhat.com/1274338) <b>Upgrade WildFly to 8.2.1</b><br>
 - [BZ 1275719](https://bugzilla.redhat.com/1275719) <b>remove ie8, ie9 permutations from GWT compilations</b><br>
 - [BZ 1275747](https://bugzilla.redhat.com/1275747) <b>Cancel migration VDSErrorException  Failed to DestroyVDS on destination host</b><br>
 - [BZ 1277209](https://bugzilla.redhat.com/1277209) <b>Double click on split table checkbox column shouldn't initiate item move</b><br>
 - [BZ 1277496](https://bugzilla.redhat.com/1277496) <b>remove oldest network api (3.0? — preceding existence of setsupnetworks) and internal usage thereof</b><br>
 - [BZ 1277667](https://bugzilla.redhat.com/1277667) <b>ISO domain can't be created</b><br>
 - [BZ 1278738](https://bugzilla.redhat.com/1278738) <b>The "virtio_scsi" element isn't populated when a VM is requested</b><br>
 - [BZ 1279589](https://bugzilla.redhat.com/1279589) <b>Incorrect type usage of extension api</b><br>
 - [BZ 1279771](https://bugzilla.redhat.com/1279771) <b>[Host QoS] - Updating/changing value/s on the Host QoS entity via DC while a network that using this entity and attached to server doesn't invoke sync</b><br>
 - [BZ 1280358](https://bugzilla.redhat.com/1280358) <b>Disk Alias and Description maximum size isn't restricted to max size</b><br>
 - [BZ 1282218](https://bugzilla.redhat.com/1282218) <b>After detaching VMs from pool the number of pre started VMs in pool isn't changed</b><br>
 - [BZ 1283151](https://bugzilla.redhat.com/1283151) <b>external VMs are not added when storage is not configured</b><br>
 - [BZ 1283499](https://bugzilla.redhat.com/1283499) <b>Impossible to POST key value using REST API</b><br>
 - [BZ 1285390](https://bugzilla.redhat.com/1285390) <b>REST error message suggests description but there is none</b><br>
 - [BZ 1286752](https://bugzilla.redhat.com/1286752) <b>Inconsistent use of placeholders in login form</b><br>
 - [BZ 1286810](https://bugzilla.redhat.com/1286810) <b>Log out from userportal doesn't work for non-admins</b><br>
 - [BZ 1288089](https://bugzilla.redhat.com/1288089) <b>[events] "untranslated" VM_MIGRATION_TO_SERVER_FAILED event for subscription</b><br>
 - [BZ 1293881](https://bugzilla.redhat.com/1293881) <b>Host installation fails with "java.lang.Integer cannot be cast to java.lang.String"</b><br>
 - [BZ 1293944](https://bugzilla.redhat.com/1293944) <b>Log common locking management actions</b><br>
 - [BZ 1295779](https://bugzilla.redhat.com/1295779) <b>Untranslated job name for vm-logon and CloneVm</b><br>
 - [BZ 1296127](https://bugzilla.redhat.com/1296127) <b>string showing number of cores of VM in basictab in 3.6 is harder to read than in 3.5</b><br>
 - [BZ 1296520](https://bugzilla.redhat.com/1296520) <b>[engine-backup] Misleading error msg when log parameter is not passed</b><br>
 - [BZ 1297689](https://bugzilla.redhat.com/1297689) <b>No error message is shown on getDevicelist failure when adding a new FC storage domain</b><br>
 - [BZ 1299233](https://bugzilla.redhat.com/1299233) <b>NPE when importing image as template from glance</b><br>
 - [BZ 1301031](https://bugzilla.redhat.com/1301031) <b>[events] Strange reason when putting host to maintenance - No reason was returned for this operation failure. See logs for further details.</b><br>
 - [BZ 1302034](https://bugzilla.redhat.com/1302034) <b>It's possible to remove inherited permissions from Everyone's group</b><br>
 - [BZ 1302236](https://bugzilla.redhat.com/1302236) <b>Uncaught exception occurred. in the UI while choosing CPU Architecture as 'undefined' in the New Cluster dialog</b><br>
 - [BZ 1302667](https://bugzilla.redhat.com/1302667) <b>[FC23] engine-setup fails to configure nfs</b><br>
 - [BZ 1302780](https://bugzilla.redhat.com/1302780) <b>Can't clone vm from template as thin copy to an imported domain with a copy of the template disk</b><br>
 - [BZ 1303346](https://bugzilla.redhat.com/1303346) <b>XSD value object requires at least 1 occurrence of datum but doesnt always have it in nic statistics</b><br>
 - [BZ 1303694](https://bugzilla.redhat.com/1303694) <b>bad string in error message when testing external provider without permissions</b><br>
 - [BZ 1304653](https://bugzilla.redhat.com/1304653) <b>ACTION_TYPE_FAILED_VM_SNAPSHOT_TYPE_NOT_ALLOWED message isn't i18n comptaible</b><br>
 - [BZ 1305343](https://bugzilla.redhat.com/1305343) <b>Irrelevant warnings are logged when attaching an export domain to a dc</b><br>
 - [BZ 1305600](https://bugzilla.redhat.com/1305600) <b>Setting vm ticket using REST doesn't report error</b><br>
 - [BZ 1305900](https://bugzilla.redhat.com/1305900) <b>use different bus for cdrom when q35 chipset is used</b><br>
 - [BZ 1306743](https://bugzilla.redhat.com/1306743) <b>Live Merge does not update the database properly upon failure</b><br>
 - [BZ 1308478](https://bugzilla.redhat.com/1308478) <b>[SCALE] Create new VM in webadmin portal shows only spinning ring.</b><br>
 - [BZ 1308563](https://bugzilla.redhat.com/1308563) <b>Adding a host with a name that is already in use returns a Bad Request (code 400)</b><br>
 - [BZ 1310426](https://bugzilla.redhat.com/1310426) <b>VmPool related jobs are stuck in job and steps tables in DB when several consecutive actions are called</b><br>
 - [BZ 1310642](https://bugzilla.redhat.com/1310642) <b>Provide more details in the Events/Tasks tab message when importing an image as template from an external provider</b><br>
 - [BZ 1310705](https://bugzilla.redhat.com/1310705) <b>Problem when configuring ovirt-engine with dockerc plugin enabled</b><br>
 - [BZ 1310837](https://bugzilla.redhat.com/1310837) <b>oVirt cannot be accessed through IPv6 address</b><br>
 - [BZ 1317279](https://bugzilla.redhat.com/1317279) <b>iscsi login fails in v3</b><br>
 - [BZ 1317581](https://bugzilla.redhat.com/1317581) <b>Neutron | missing REST-API to import networks from neutron external provider</b><br>
 - [BZ 1317947](https://bugzilla.redhat.com/1317947) <b>engine-setup should default to not create NFS ISO domain</b><br>
 - [BZ 1318666](https://bugzilla.redhat.com/1318666) <b>Remove VM fails with HTTP400 - bad request</b><br>
 - [BZ 1320964](https://bugzilla.redhat.com/1320964) <b>REST API: Can't set quota for DC (in v3 compatibility mode at least) - "No enum constant org.ovirt.engine.api.model.QuotaModeType.disabled"</b><br>
 - [BZ 1321452](https://bugzilla.redhat.com/1321452) <b>[REST API] storage_manager object/tag is missing in host details</b><br>
 - [BZ 1322019](https://bugzilla.redhat.com/1322019) <b>Admin user reported as "admin@internal@internal-authz"</b><br>
 - [BZ 1322435](https://bugzilla.redhat.com/1322435) <b>Radio buttons in Install host dialog are not clickable when window is too narrow</b><br>
 - [BZ 1322515](https://bugzilla.redhat.com/1322515) <b>The "Default" cluster doesn't have Display and Migration networks set out of the box</b><br>
 - [BZ 1322923](https://bugzilla.redhat.com/1322923) <b>java.lang.IllegalArgumentException: No type specified for option: 'encrypt_options' in /api/capabilities</b><br>
 - [BZ 1322947](https://bugzilla.redhat.com/1322947) <b>Management network can't be moved to other host NIC</b><br>
 - [BZ 1323201](https://bugzilla.redhat.com/1323201) <b>[migration 3.6 el6 - 3.6 el7] Failed to execute stage 'Setup validation': Firewall manager iptables is not available</b><br>
 - [BZ 1323484](https://bugzilla.redhat.com/1323484) <b>oVirt welcome page locale selector is broken</b><br>
 - [BZ 1323631](https://bugzilla.redhat.com/1323631) <b>Closing a connection should not require 'filter' header.</b><br>
 - [BZ 1323826](https://bugzilla.redhat.com/1323826) <b>engine-setup stage 'Setup validation' takes too long to complete</b><br>
 - [BZ 1325699](https://bugzilla.redhat.com/1325699) <b>Remove dwh_disk_vm_map_history_view from engine db</b><br>
 - [BZ 1325785](https://bugzilla.redhat.com/1325785) <b>permissions on Database Object don't allow  "add direct LUN" to virtual machine.</b><br>
 - [BZ 1325938](https://bugzilla.redhat.com/1325938) <b>VM stay in 'powering down' after stopping VM</b><br>
 - [BZ 1325978](https://bugzilla.redhat.com/1325978) <b>Not possible to change the boot protocol from static ip to dhcp via ui</b><br>
 - [BZ 1326003](https://bugzilla.redhat.com/1326003) <b>Can't update direct lun using the API</b><br>
 - [BZ 1326578](https://bugzilla.redhat.com/1326578) <b>Email notification can't be configured in engine. "Operation Canceled Error while executing action: A Request to the Server failed with the following Status Code: 500"</b><br>
 - [BZ 1328011](https://bugzilla.redhat.com/1328011) <b>Engine: internal admin cannot migrate VM (permission issue)</b><br>
 - [BZ 1328404](https://bugzilla.redhat.com/1328404) <b>[REST-API] refresh host capabilities not working</b><br>
 - [BZ 1328463](https://bugzilla.redhat.com/1328463) <b>creating a new vm from templates tab overrides template's initialization parameters</b><br>
 - [BZ 1328737](https://bugzilla.redhat.com/1328737) <b>Editing a sub attribute of vm/template initialization attr via API overrides all other sub_attributes</b><br>
 - [BZ 1329383](https://bugzilla.redhat.com/1329383) <b>engine-backup message are not helpful</b><br>
 - [BZ 1329906](https://bugzilla.redhat.com/1329906) <b>Storage domain ownership of LUN not displayed.</b><br>
 - [BZ 1330168](https://bugzilla.redhat.com/1330168) <b>[Admin Portal] not able to get admin portal login screen after ovirt-engine-rename</b><br>
 - [BZ 1331079](https://bugzilla.redhat.com/1331079) <b>Migrating icon keeps floating when scrolling</b><br>
 - [BZ 1331939](https://bugzilla.redhat.com/1331939) <b>A minor typo found during translation</b><br>
 - [BZ 1331940](https://bugzilla.redhat.com/1331940) <b>"VmWare" should be changed to "VMware"</b><br>
 - [BZ 1332039](https://bugzilla.redhat.com/1332039) <b>VM can be "down" and "migrating" at the same time</b><br>
 - [BZ 1332239](https://bugzilla.redhat.com/1332239) <b>[REST-API] rsdl: wrong parameter name under copy disk template action</b><br>
 - [BZ 1332960](https://bugzilla.redhat.com/1332960) <b>Detach a vm's disk using the API will remove the disk permanently</b><br>
 - [BZ 1332986](https://bugzilla.redhat.com/1332986) <b>Snapshot operation names changed from <op_name>_snapshot to <op_name>snapshot</b><br>
 - [BZ 1333340](https://bugzilla.redhat.com/1333340) <b>[REST API V3] when calling GET on vm the boot sequence will always be set to 'hd'</b><br>
 - [BZ 1333354](https://bugzilla.redhat.com/1333354) <b>[REST API V3] Adding a vm with custom_properties fails via api version 3</b><br>
 - [BZ 1334096](https://bugzilla.redhat.com/1334096) <b>REST API: Search cluster request returns empty result (v3)</b><br>
 - [BZ 1334098](https://bugzilla.redhat.com/1334098) <b>Scheduling policy doesnt get updated in REST (v3)</b><br>
 - [BZ 1335186](https://bugzilla.redhat.com/1335186) <b>hosted-engine vm and storage domain not displayed in the admin web ui</b><br>
 - [BZ 1335199](https://bugzilla.redhat.com/1335199) <b>home page has link to reports, but reports won't be in 4.0</b><br>
 - [BZ 1335464](https://bugzilla.redhat.com/1335464) <b>import domain fails using the sdk</b><br>
 - [BZ 1336405](https://bugzilla.redhat.com/1336405) <b>Failed to import template from export domain with 'General command validation failure.'</b><br>

### VDSM

 - [BZ 912390](https://bugzilla.redhat.com/912390) <b>vdsm: race between create and destory of VM leaves VM running on host while engine thinks its down.</b><br>
 - [BZ 1189200](https://bugzilla.redhat.com/1189200) <b>traceback in ioprocess while restarting VDSM</b><br>
 - [BZ 1201482](https://bugzilla.redhat.com/1201482) <b>Storage QoS is not applying on a Live VM/disk</b><br>
 - [BZ 1234328](https://bugzilla.redhat.com/1234328) <b>SR-IOV --> add support for Hotplug/unplug of VFs</b><br>
 - [BZ 1261056](https://bugzilla.redhat.com/1261056) <b>Place bonding-defaults.json outside of /var/lib/vdsm</b><br>
 - [BZ 1269175](https://bugzilla.redhat.com/1269175) <b>nic removed from bond can not be bound to another bond</b><br>
 - [BZ 1270220](https://bugzilla.redhat.com/1270220) <b>SPM is not tolerant for very slow NFS file deletes</b><br>
 - [BZ 1274670](https://bugzilla.redhat.com/1274670) <b>VM migration doesn't work with current VDSM master</b><br>
 - [BZ 1278414](https://bugzilla.redhat.com/1278414) <b>drop requirement of 'umask' argument on cpopen</b><br>
 - [BZ 1283278](https://bugzilla.redhat.com/1283278) <b>Add dependency when fix for bug 1283116 (7.2.z) is in ([abrt] qemu-img: get_block_status(): qemu-img killed by SIGABRT)</b><br>
 - [BZ 1300640](https://bugzilla.redhat.com/1300640) <b>spec: require python-six >= 1.9</b><br>
 - [BZ 1305338](https://bugzilla.redhat.com/1305338) <b>Issue with vdsm-hook-vmfex-dev-4.16.33-1 - "InvalidatedWeakRef"</b><br>
 - [BZ 1309884](https://bugzilla.redhat.com/1309884) <b>In RHEL7, VDSM is no longer calling _destroyVmForceful() if SIGTERM fails</b><br>
 - [BZ 1314705](https://bugzilla.redhat.com/1314705) <b>[ovirt-node] Can't register node to engine through TUI</b><br>
 - [BZ 1318550](https://bugzilla.redhat.com/1318550) <b>Vm.status() causes crash of MoM GuestManager</b><br>
 - [BZ 1319987](https://bugzilla.redhat.com/1319987) <b>Storage activities are failing with error "Image is not a legal chain"</b><br>
 - [BZ 1320281](https://bugzilla.redhat.com/1320281) <b>Vdsm is missing arch specific dependencies</b><br>
 - [BZ 1321325](https://bugzilla.redhat.com/1321325) <b>stompTests.StompTests test_echo(4096, False) ERROR</b><br>
 - [BZ 1323782](https://bugzilla.redhat.com/1323782) <b>vdsm-restore-network leaves inconsistent RunningConfig after a failed restoration</b><br>
 - [BZ 1323969](https://bugzilla.redhat.com/1323969) <b>race on recovery prevents events to be delivered</b><br>
 - [BZ 1333627](https://bugzilla.redhat.com/1333627) <b>Growing backing file length in qcow2 header causes 'Backing file name too long' error.</b><br>

### oVirt Hosted Engine Setup

 - [BZ 1156060](https://bugzilla.redhat.com/1156060) <b>[text] engine admin password prompt consistency</b><br>
 - [BZ 1186388](https://bugzilla.redhat.com/1186388) <b>[TEXT][HE] Ask user to choose an existing cluster during installation</b><br>
 - [BZ 1221176](https://bugzilla.redhat.com/1221176) <b>hosted-engine accepts FQDNs with underscore while the engine correctly fails on that</b><br>
 - [BZ 1259266](https://bugzilla.redhat.com/1259266) <b>engine_api.hosts.add fails if called passing reboot_after_installation optional parameter</b><br>
 - [BZ 1298592](https://bugzilla.redhat.com/1298592) <b>Deploy of the second host failed if I have root password of the first host under answer file</b><br>
 - [BZ 1306573](https://bugzilla.redhat.com/1306573) <b>hosted engine appliance deployment fails with insufficient information.</b><br>
 - [BZ 1316094](https://bugzilla.redhat.com/1316094) <b>[HE] VDSM API - netinfo.CachingNetInfo doesn't exist anymore</b><br>
 - [BZ 1318652](https://bugzilla.redhat.com/1318652) <b>hosted-engine deploy failure: 'module' object has no attribute 'Ssh'</b><br>
 - [BZ 1321381](https://bugzilla.redhat.com/1321381) <b>hosted-engine-setup trusts also the system defined CA certs while the oVirt python SDK ignores them</b><br>
 - [BZ 1332927](https://bugzilla.redhat.com/1332927) <b>The hosted engine deploy via appliance failed on the engine-setup stage</b><br>

### oVirt Engine DWH

 - [BZ 1301962](https://bugzilla.redhat.com/1301962) <b>engine-setup fails with: Internal error: cannot import name dialog</b><br>
 - [BZ 1311149](https://bugzilla.redhat.com/1311149) <b>change vds_groups in etl to cluster</b><br>
 - [BZ 1312638](https://bugzilla.redhat.com/1312638) <b>Remove DWH views that will not be supported anymore</b><br>
 - [BZ 1321517](https://bugzilla.redhat.com/1321517) <b>RHEV DWH database growing excessively</b><br>
 - [BZ 1328769](https://bugzilla.redhat.com/1328769) <b>[nightly 4.0] setup-engine Failed to execute stage 'Misc configuration' because of DWH scripts</b><br>
 - [BZ 1328860](https://bugzilla.redhat.com/1328860) <b>[dwh] engine-cleanup on separate dwh machine does not reset dwh_history_timekeeping</b><br>

### oVirt vmconsole

 - [BZ 1330503](https://bugzilla.redhat.com/1330503) <b>ovirt-vmconsole-1.0.2 fails make distcheck</b><br>

### oVirt Log collector

 - [BZ 1254654](https://bugzilla.redhat.com/1254654) <b>[F23] ovirt-log-collector fails to build on fedora >= 23</b><br>

### oVirt Image Uploader

 - [BZ 1104661](https://bugzilla.redhat.com/1104661) <b>zero returncode on error</b><br>
 - [BZ 1264424](https://bugzilla.redhat.com/1264424) <b>change ovirt-engine api endpoint</b><br>

### oVirt ISO Uploader

 - [BZ 1264542](https://bugzilla.redhat.com/1264542) <b>change ovirt-engine api endpoint</b><br>

### oVirt Host Deploy

 - [BZ 1279434](https://bugzilla.redhat.com/1279434) <b>ovirt-vmconsole-host-sshd service is not started automatically at boot</b><br>
 - [BZ 1320059](https://bugzilla.redhat.com/1320059) <b>vdsm _reconfigure should be called before _start</b><br>

### oVirt Live

 - [BZ 1282799](https://bugzilla.redhat.com/1282799) <b>Import all-in-one plugins from ovirt-engine into ovirt-live</b><br>
 - [BZ 1316029](https://bugzilla.redhat.com/1316029) <b>vdsm - caps/machinetype API changes broke setup</b><br>

### OTOPI

 - [BZ 1316908](https://bugzilla.redhat.com/1316908) <b>hosted-engine --deploy fails when you have i18n chars in /root/.ssh/authorized_keys</b><br>
