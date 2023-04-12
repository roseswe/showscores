# Pacemaker ShowScores for SLES12 and SLES15

This program tries to show the scores each pacemaker resource has on cluster members (nodes).
Original idea and script for older pacemaker versions (1.x) was done around 2009 by Dominik Klein.
In the sub-directory **SLES11** you will find a slightly enhanced and adapted version that runs **only on SLES11** pacemaker clusters.

In SLES12 and SLES15 commands and their output changed, so a new simplified showscores was _invented_!  :sparkles:

See also the SUSE TID <https://www.suse.com/support/kb/doc/?id=000019442>  (no default-resource-stickiness)

NOTE: This program should not be limited to two node clusters all other scripts I am aware of!

## Requirements

This `showscores` version will not run under SLES11 because there the standard (G)AWK version is too old (GNU AWK 3.1.8) to support multidimensional arrays (please use instead the `showscores` version found in the SLES11 sub-directory).

It will run under SLES12SP5 = GNU AWK 4.1.8 (API: 1.0), SLES15SP2 = GNU AWK 4.1.0 (API: 1.0) and SLES15SP3/SP4 = GNU AWK 4.2.1 (API: 2.0)

## Example Output SLES15, 2 node cluster

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

## Example Output, SLES15, 3 Node SAP HANA SRA cluster, read-enable setup

``` shell

rsc_defaults: resource-stickiness=Multiple attributes match name=resource-stickiness
  Value: 1000   (id=build-resource-stickiness)
  Value: 1000   (id=rsc-options-resource-stickiness)   migration-threshold=5000

##[ Resource ]#####[ Nodes ]##            hanode_02          hanode_mm          hanode_01

admin-ip                                       1000                  0                  0
cln_SAPHanaTopology_TST_HDB00                     0          -INFINITY                  0
msl_SAPHana_TST_HDB00                             2          -INFINITY                  2
rsc_SAPHanaTopology_TST_HDB000                    0          -INFINITY               1000
rsc_SAPHanaTopology_TST_HDB001                 1000          -INFINITY                  0
rsc_SAPHanaTopology_TST_HDB002                    0          -INFINITY                  0
rsc_SAPHana_TST_HDB000                            2          -INFINITY               1152
rsc_SAPHana_TST_HDB001                         1102          -INFINITY                  0
rsc_ip_TST_HDB00_master                           0          -INFINITY               3000
rsc_ip_TST_HDB00_readenabled                   3000          -INFINITY                  0

Showscore taken on node: hanode_04 at Wed Apr 12 12:13:08 CEST 2023
```

NOTE: hanode_mm is the "Majority Maker" node


<!--
vim:set fileencoding=utf8 fileformat=unix filetype=gfm tabstop=2 expandtab:
$Id: Readme.md,v 1.5 2023/04/05 11:56:03 ralph Exp $
-->
