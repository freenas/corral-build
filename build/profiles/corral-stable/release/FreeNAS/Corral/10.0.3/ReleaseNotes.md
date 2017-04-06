## FreeNAS Corral 10.0.3 Update series

Welcome to the third minor point release of FreeNAS Corral!

Updates of note in this release (culled from the usual array of resolved tickets).

* Migration fixes (If you were holding off from ugrading to Corral or rolled back to 9.10 for any of these reasons, please give this update a try and let us know)
  * Migration of iSCSI shares from 9.10 to Corral fully works now!  
  * Migration of non-dataset (directory based) shares for nfs, afp, smb, and webdav was broken and is fixed in this update. So please retry the 9.x to Corral upgrade again.
  * While migrating a passphraseless encrypted volume from 9.x to Corral, the auto-unlock feature post first/every boot is now migrated.
  * Also fixed a few other 9->Corral migration tickets, so migration in general is much better and more robust now.
* If you had your webui bound to an ip (either you had this in 9.x or you did this on a fresh install), the webui would not come back up post a reboot (or post 9.x to Corral migration). This is now fixed.

* Active Directory ID mappings are now configurable in the CLI. New Active Directory configurations use same ID ranges as FreeNAS 9.10, thus are entirely compatible. Existing setups need manual adjustment using CLI.

  Example, assumes that directory name is `my_ad`:
  
  ```account directoryservice directories my_ad properties idmap set rid_start=20000```
  
  (20000 is the typical value of `rid_start` in FreeNAS 9.)

* Several important UI fixes for encrypted volumes management
* Fixes to Directory Services UI: Can modify search path, remove configuration
* VM VGA consoles now work with HTTPs and custom Web UI ports
* Automatic removal of expired snapshot is fixed
* Re-added netdata service for charting / viewing performance (see service CLI)
* Multiple issues related to NFSv4 and Kerberos have been fixed
* Issue with Web UI not starting after setting up custom bind IP addresses has been fixed
* Bug allowing Container ports to overlap with host ports (like 80!) has been fixed.  This may explain some of the "hey, my GUI went away!" tickets.
* Fixed bug where updating docker containers broke them.
* Fixed NFS maproot / mapall UI regression
* Fixed GUI regression in creating LAGGs
* Fixed group creation UI
* Fixed some bugs in encrypted volume unlock UI
* Additional GUI seatbelts added to yell at people more before deleting things, and to make shutdown / reboot a little harder to do accidentally.
* Fixed file downloads with firefox
* Improved performance with firefox
 
(For full list of tickets fixed, see the ChangeLog)
