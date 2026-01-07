~~~
$ cd /tmp
$ wget https://mirror.nforce.com/pub/software/raidtools/storcli/storcli-1.19.04-1.noarch.rpm
--2026-01-07 12:42:01--  https://mirror.nforce.com/pub/software/raidtools/storcli/storcli-1.19.04-1.noarch.rpm
Resolving mirror.nforce.com (mirror.nforce.com)... 46.166.191.151, 2a00:1768:6000:22:1::1
Connecting to mirror.nforce.com (mirror.nforce.com)|46.166.191.151|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4632676 (4.4M) [application/x-redhat-package-manager]
Saving to: ‘storcli-1.19.04-1.noarch.rpm’

storcli-1.19.04-1.noarch.rpm  100%[=================================================>]   4.42M  2.36MB/s    in 1.9s

2026-01-07 12:42:04 (2.36 MB/s) - ‘storcli-1.19.04-1.noarch.rpm’ saved [4632676/4632676]

$ sudo rpm -ivh storcli-1.19.04-1.noarch.rpm
[sudo] password for :
Verifying...                          ################################# [100%]
Preparing...                          ################################# [100%]
Updating / installing...
   1:storcli-1.19.04-1                ################################# [100%]
$ sudo /opt/MegaRAID/storcli/storcli64 show
Status Code = 0
Status = Success
Description = None

Number of Controllers = 1
Host Name = sharedata.kei.re.kr
Operating System  = Linux4.18.0-513.24.1.el8_9.x86_64

System Overview :
===============

--------------------------------------------------------------------
Ctl Model   Ports PDs DGs DNOpt VDs VNOpt BBU  sPR DS EHS ASOs Hlth
--------------------------------------------------------------------
  0 SAS3508     8   2   1     0   1     0 Msng On  -  Y      3 Opt
--------------------------------------------------------------------

Ctl=Controller Index|DGs=Drive groups|VDs=Virtual drives|Fld=Failed
PDs=Physical drives|DNOpt=DG NotOptimal|VNOpt=VD NotOptimal|Opt=Optimal
Msng=Missing|Dgd=Degraded|NdAtn=Need Attention|Unkwn=Unknown
sPR=Scheduled Patrol Read|DS=DimmerSwitch|EHS=Emergency Hot Spare
Y=Yes|N=No|ASOs=Advanced Software Options|BBU=Battery backup unit
Hlth=Health|Safe=Safe-mode boot


$ sudo /opt/MegaRAID/storcli/storcli64 /c0 /vall show
Controller = 0
Status = Success
Description = None


Virtual Drives :
==============

---------------------------------------------------------------
DG/VD TYPE  State Access Consist Cache Cac sCC       Size Name
---------------------------------------------------------------
0/0   RAID1 Optl  RW     Yes     RWTD  -   ON  446.102 GB
---------------------------------------------------------------

Cac=CacheCade|Rec=Recovery|OfLn=OffLine|Pdgd=Partially Degraded|dgrd=Degraded
Optl=Optimal|RO=Read Only|RW=Read Write|HD=Hidden|TRANS=TransportReady|B=Blocked|
Consist=ConsistentR=Read Ahead Always|NR=No Read Ahead|WB=WriteBack|
AWB=Always WriteBack|WT=WriteThrough|C=Cached IO|D=Direct IO|sCC=Scheduled
Check Consistency


$ sudo /opt/MegaRAID/storcli/storcli64 /c0 /eall /sall show
Controller = 0
Status = Success
Description = Show Drive Information Succeeded.


Drive Information :
=================

-----------------------------------------------------------------------------------
EID:Slt DID State DG       Size Intf Med SED PI SeSz Model                      Sp
-----------------------------------------------------------------------------------
65:0      7 Onln   0 446.102 GB SATA SSD Y   N  512B SAMSUNG MZ7L3480HCHQ-00B7C U
65:1      6 Onln   0 446.102 GB SATA SSD Y   N  512B SAMSUNG MZ7L3480HCHQ-00B7C U
-----------------------------------------------------------------------------------

EID-Enclosure Device ID|Slt-Slot No.|DID-Device ID|DG-DriveGroup
DHS-Dedicated Hot Spare|UGood-Unconfigured Good|GHS-Global Hotspare
UBad-Unconfigured Bad|Onln-Online|Offln-Offline|Intf-Interface
Med-Media Type|SED-Self Encryptive Drive|PI-Protection Info
SeSz-Sector Size|Sp-Spun|U-Up|D-Down|T-Transition|F-Foreign
UGUnsp-Unsupported|UGShld-UnConfigured shielded|HSPShld-Hotspare shielded
CFShld-Configured shielded|Cpybck-CopyBack|CBShld-Copyback Shielded


$ sudo /opt/MegaRAID/storcli/storcli64 /c0 show all | egrep -i 'bbu|cache|write'
Any Offline VD Cache Preserved = No
BBU Status = NA
BBU  = Yes
Block SSD Write Disk Cache Change = No
Support FlushWriteVerify = Yes
Support discardCacheDuringLDDelete = Yes
Support JBOD Write cache = No
Write Policy = Yes
Disk Cache Policy = Yes
Support Powersave Max With Cache = No
Support SSC WriteBack = No
Support VD Cachebypass = Yes
Support VD discardCacheDuringLDDelete = Yes
BBU = Absent
CacheVault Flash Size = NA
Current Size of CacheCade (GB) = 0
Current Size of FW Cache (MB) = 1374
Cache Flush Interval            4s
Allow Boot with Preserved Cache = Off
Write Policy = WB
Cache When BBU Bad = Off
Cached IO = Off
Max Configurable CacheCade Size(GB) = 0
PDC=PD Cache|PI=Protection Info|SED=Self Encrypting Drive|Frgn=Foreign
DG/VD TYPE  State Access Consist Cache Cac sCC       Size Name
Cac=CacheCade|Rec=Recovery|OfLn=OffLine|Pdgd=Partially Degraded|dgrd=Degraded
Optl=Optimal|RO=Read Only|RW=Read Write|HD=Hidden|TRANS=TransportReady|B=Blocked|
Consist=ConsistentR=Read Ahead Always|NR=No Read Ahead|WB=WriteBack|
AWB=Always WriteBack|WT=WriteThrough|C=Cached IO|D=Direct IO|sCC=Scheduled
~~~
