# BackupPC_Snap
Simple scripts to allow BackupPC to back up LVM snapshots.

This is not really for public consumption. I just created this repository to share the code with someone else. Use at your own risk. It probably won't work for you. 

### Prerequisites

* BackupPC 3.x (should be adaptable to 4.x)
* LVM
* Perl 

### Installing

Copy the scripts to some directory and make them executable by the BackupPC user. If your BackupPC client processes do not run as root, you'll have to set up appropriate sudo privileges

### Scripts

#### snap_share

Makes an LVM snapshot of the specified BackupPC share and mounts it. Please configure the variables at the beginning of the script to suit your environment.
Run this as the *$Conf{DumpPreShareCmd}* in BackupPC. e.g. 

`/usr/local/bin/snap_share $share`   

#### unsnap_share

Unmounts and removes the LVM snapshot of the specified BackupPC share. Please configure the variables at the beginning of the scrpt to suit your environment. Run this as the *$Conf{DumpPostShareCmd}* in BackupPC, e.g.

`/usr/local/bin/unsnap_share $share`  

#### snap_rsync

Wrapper around *rsync* that translates the share name to the new snapshot mountpoint and then executes the *real* rsync. Please configure the variables at the beginning of the scrpt to suit your environment.R Please note that this takes an additional argument before the standard rsync arguments, specifically the path to *real* rsync. 

`/usr/local/bin/snap_rsync rsync_path [rsync_arguments] share_name`

Asjust your BackupPC settings to exectue rsync in this way. For example, set your *$Conf{RsyncClientPath}* to:

`/usr/local/snap_rsync /usr/bin/rsync`

### License

This code is licensed under the GNU General Public License v3.0.


