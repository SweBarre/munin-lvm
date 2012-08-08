# vg_
** vg_ - Wildcard-plugin to monitor lvm2 volume groups and the logival volumes in that group. **

Configuration
[vg_*]
user root

This is a wildcard plugin. To monitor a volume group , link
vg_<volume group name> to this file. E.g.

  ln -s /usr/share/munin/plugins/vg_ /etc/munin/plugins/vg_local

...will monitor the volume group named local.

# lvthin_
lvthin_ - Wildcard-plugin to monitor lvm2 thin pools and
thin provisioned logical volumes.


The plugin may need to run as root to get volume groupe and
logical volume information

  [lvthin_*]
      user root

The plugin needs to binaries from the lvm tools, lvs and vgs
It will use the lvs and vgs found in default PATH, if you need
to change this you need to configure this:

  [lvthin_*]
     env.LVS /sbin/lvs
     env.VGS /sbin/vgs

Default warning and critical  will be set if the thin pool is 
cunsumed over 80% used AND more then 100% is provisioned to
logical volumes.
This could be changed by setting the enviroment variable
use_warning to the following three valuse
 no     : No warnings or critical values on the thin pool
          will be set
 yes    : always use warning and critical values on pool
          consumption
 over   : (default) only use warning and critical if
          the pool is over provisioned

  [lvthin_*]
      env.use_warning over

The default value for warning is 80
the default value for critical is 95
To set warning and critical levels do like this:

  [lvthin_*]
      env.warning 80
      env.critical 95
