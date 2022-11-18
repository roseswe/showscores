# Pacemaker ShowScores for SLES12 and SLES15

This program tries to show the scores each pacemaker resource has on cluster members (nodes).
Original idea and script for older pacemaker versions (1.x) was done around 2009 by Dominik Klein.
In the sub-directory **SLES11** you will find a slightly enhanced and adapted version that runs **only on SLES11** pacemaker clusters.

In SLES12 and SLES15 commands and their output changed, so a new simplified showscores was _invented_!  :sparkles:

See also the SUSE TID <https://www.suse.com/support/kb/doc/?id=000019442>  (no default-resource-stickiness)

## Requirements

This `showscores` version will not run under SLES11 because there the standard (G)AWK version is too old (GNU AWK 3.1.8) to support multidimensional arrays (please use instead the `showscores` version found in the SLES11 subdirectory).

It will run under SLES12SP5 = GNU AWK 4.1.8 (API: 1.0), SLES15SP2 = GNU AWK 4.1.0 (API: 1.0) and SLES15SP3 = GNU AWK 4.2.1 (API: 2.0)

## Example Output SLES15

``` shell
$ ./showscores
rsc_defaults: resource-stickiness=123   migration-threshold=5

## [ Resource ]#####[ Nodes -> ]##          sap12ha1           sap12ha2

admin-ip                                          0                123
c-clvm                                            0                  0
c-p_mail2sysadmin                                 0                  0
clee0                                             0                123
clem1                                           123                  0
dlm0                                              0                246
dlm1                                            246                  0
g-clvm0                                           0                  0
g-clvm1                                           0                  0
g-mariadb                                         0                  0
mariadb-ip                                      123                  0
p_mail2sysadmin0                                  0                123
p_mail2sysadmin1                                123                  0
p_mydummy                                       123                  0
prm_fs1                                           0                  0
prm_mariadb                                       0                  0
prm_vg1                                   -INFINITY          -INFINITY
stonith-sbd                                     123                  0
```

<!--
vim:set fileencoding=utf8 fileformat=unix filetype=gfm tabstop=2 expandtab:
$Id: Readme.md,v 1.4 2022/11/17 21:19:46 ralph Exp $
-->
