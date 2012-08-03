# vg_
** vg_ - Wildcard-plugin to monitor lvm2 volume groups and the logival volumes in that group. **

This plugin does not require configuration.

This is a wildcard plugin. To monitor a volume group , link
vg_<volume group name> to this file. E.g.

  ln -s /usr/share/munin/plugins/vg_ /etc/munin/plugins/vg_local

...will monitor the volume group named local.
