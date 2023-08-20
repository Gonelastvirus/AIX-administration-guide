# AIX-administration-guide


## SMITToolToaddcreateuserandloginviassh

**Command:** smitmkuser

Gotosecurityandusers.Addusernamemaxlengthmustbe 8 characterslong.


PressEnterandpressF3tocancel.Nowcheckbycommand **“whoami”.** Switchtorootuser.
command:passwdsubesh
Thiswillsetthepasswordforusersubesh.

Logindirectlyintotheserverwithuser“subesh”viaSSH.

WelcometoAIXserver


## SetupLocalrepoandinstallyumpackagemanageronRHEL

Gettheisofileontherootdirectory.Createdirectory/media/RHEL-disc
**Command:** root@lastvirus/]#mkdir/media/RHEL-disc
Copytheisofilefromrootto/media/RHEL-disc

Mounttheisofile:
**Command:** mount-oloop/root/rhel-baseos-9.1-ppc64le-dvd.iso/media/RHEL_disc/


Copythemedia.repotoyum.repos.d
**Command:** cp/media/rhel_iso/media.repo/etc/yum.repos.d/

Addconfigurationviavimeditor.

Ifnoerrorsarereturned,thefollowingcanbeusedtoupdate:
**Command:** yumupdate
**Command:** yumrepolist


## LogicalVolumeManagementusingSMIT

Listphysicalvolume:
**Command:** lspv

### CreateVolumegroup:

**Command:** smitvg

Setvolumegroupname


```
● PhysicalpartitionsizeinMegaBytes.PressEscand 4 andselectpartitionsize.
● SetPhysicalvolumename.Forexamplehdisk0,hdisk
```
### CreatelogicalvolumeusingSMT
**Command:** smitlv
SelectAddLogicalvolutionoption

PressEscand 4 ,selectoneoftheexistingvolumegroupsormanuallyset.

```
● Afterthisitwillaskforalogicalvolumename.SettheLVnamemanually.
● Numberoflogicalpartitions.Example 1 is 1 gb.Ifyouhavea10gbharddiskandyouset
thenumberoflogicalpartitionsto 1 i.e. 1 gbforeachfilesystemthenyoucanhave 10
filesystems.
● Setlogicalvolumetype.PressEscand 4 andchoosejfs2.Itislikeext4.
```
ConfirmLVexistonLVgroup
#lsvg-lvolumn_groupname
Example:lsvg-ldatavg


### CreateaFilesystemtoaccesslogicalvolume

**Command:** smitfs
SelectAddchange/showfilesystem.

```
● SelectEnhancedfilesystem.
● SelectAddanEnhanceJFSonpreviouslydefinedlv.
```
● SetLvname,pressEscand4.Choosethepreviouslydefinedlvname.
● NowsetMountpoint.Forexample/testfs
● SetMountAutomaticallyatsystemrestart?, toyes
Nowmountthe/testfs
**Command:** /testfs


## ShowFilesystem.

**Command:** df-g

### ListPhysicalvolume

## UnderstandingPartitiononAIX

Letusconsideranemptylandwhichisyourphysicalharddisk.Supposeyouboughttheland
andassignyournameonitwhichisbasicallyyourvolumegroup.Onthatlandyoulayoutyour
house design, some spacewill be bedroom, bathroom and hall etcwhichis basicallyyour
Logicalvolume(LV).NowyouassignthefilesystemtothoseLogicalvolumes(LV).


## RemoveLVandFSfromthevolumegroup

Unmountfirst.Makesureyouarenotinthatfilesystem.Sogoonrootfirst.
**Command:** unmountfs_name
Example:unmount/testfs
**Command:** rmfs/testfs
Nowourlogicalvolumeandfilesystemgotdeleted.

## RemoveVolumegroups

Showdisk
#lspv
**Command:** reducevg-d-fvolume_group_namephysical_disk_name
Example:#reducevg-d-fdatavghdisk
Flags:
-d:device
-f:forcefully

## RemovePhysicalvolume(Disk)

Basicallydeletehdisk1,hdisk0etc
**Command:** #rmdev-Rdlhdisk
Rmdev:removedevice.
Flags:
● -Rflag:Recursiveremoval.Thisflagisusedtoremovethespecifieddeviceandallits
dependentdevices.Itwillremoveanychilddevicesthatareattachedtothedevicebeing
removed.
● -dflag:DeletesthedevicefromtheODM(ObjectDataManager)database.
● -lflag:Specifiesthatthedevicetoberemovedisidentifiedbyitslogicalname.


## BasicAIXCommand

#oslevel-s:Thisconfirmswearerunning AIXversion7.2orsomethingelse.
#uname-awecanseeserverisAIX,namegivenisAIX
#uptime:uptimeshowshowlongthesystemhasbeenup.Howmanyusershasloggedin.

**StopandStartservices.**


#shutdown-F-r:RestartingAIXServer.Flags:-FmeansForcefully,-rflag:Thisflaginstructs
thesystemtorestartautomaticallyaftershuttingdown.

### MonitorSystemPerformancewithTOPAS


## WhatDoesitmeanwhentheloadaverageis444?

Whentheloadaverageisdisplayedas"4 4 4,"itmeansthatonaverage,therearefourprocesses
activelyusingorwaitingfortheCPUduringeachofthethreetimeintervals.Thissuggestsa
moderatetohighlevelofCPUutilization.

Tounderstandwhetheraloadaverageof 4 ishighorlow,youneedtoconsiderthenumberof
CPUcoresavailableonthesystem.IfthesystemhasfourorfewerCPUcores,aloadaverageof
4 would indicatethattheCPUisfullyutilizedorevenoverloaded.Ontheotherhand,ifthe
systemhasmorethanfourCPUcores,aloadaverageof 4 mightstillindicateareasonablelevel
ofCPUusage,dependingonthespecificworkloadandsystemcapabilities.

Insummary,aloadaverageof 444 meansthat,onaverage,therearefourprocessesactively
usingorwaitingfortheCPUduringthelast1,5,and 15 minutes.Itsuggestsmoderatetohigh
CPUutilization,butthesignificanceofthisvaluedependsonthenumberofCPUcoresavailable
onthesystemandthespecificworkloadbeingprocessed.


## InstallSuperuserdo(SUDO)onAIX

Mounttheisoorextractthe.tar.gzfileintothepath.
**Command:**
loopmount -i ESD-Toolbox_for_Linux_Apps_Common_7.1-7.3_122022_LCD4107737.iso -o
"-Vudfs-oro"-m/mnt


## visudoandUserPrivilege

**Command:** visudo
Getintothesudoersfilewithvieditor.

subeshALL=(ALL)ALL
● "ALL":Thefirst"ALL"inthiscontextreferstoallthehostsorsystems.Itmeansthatthe
specifiedruleappliestoallhostsorsystems.
● "(ALL)":Thesecond"ALL"representsallusers.Itindicatesthattheuser"subesh"can
runcommandsasanyuser.
● "ALL":Thefinal"ALL"signifiesthattheuser"subesh"canrunanycommand.


## RootAssign“subesh”UserRolestochangeotherUsersPassword

Gotopath/etc/security/roles
Command:vi/etc/security/roles
YouwillseeissowithrolesDomainAdmin,SecPolicy,SysConfig.
Copyit.

Now seerolesassigntousersubesh.
Command:lsuser-fsubesh|greproles
Makesureyouareinroot.Permissionallowedtoroottoassignroles.
Nowchangeuserroles.
Command:chuserroles=DomainAdmin,SecPolicy,SysConfigsubesh


Nowseetherolesassignedornot.
Command:lsuser-fsubesh|greproles

Stillyouareallowedtochangeotherusers'passwords.
Command:swroleSecPolicy
Swrolemeansswitchtorolespecified.
Makesuretoswitchuserfromroottosubesh.

Removeroles


Isso:InformationSystem SecurityOfficer.AnISSOisresponsibleforcreatingandassigning
rolesandisthereforethemostpowerfulroleonthesystem.SomeISSOresponsibilitiesinclude:

```
● Establishingandmaintainingsecuritypolicy
● Settingpasswordsforusers
● Networkconfiguration
● Deviceadministration
```
Moredetails:https://www.ibm.com/docs/en/aix/7.2?topic=roles-predefined


## ConfigureNFSinAI

ChecktherunningNFSservices.
**Command:** lssrc-a|grepnfs
Activatethenfsserviceiftheyareinactiveorindifferentstates.


Createthedirectoryyouwannashare.

Checkifitiscreatedornot.

Createfiletext.txt

Checkif/etc/exportsisontheserverornot.Ifnotthencreateit.

Add/directory-rwor-roaccess=ip:ip.Noportisneeded.NFShasitsownport.


Serversideisdone.
Ontheclientside.Installnfs
**Command:** sudoaptinstallnfs-common


## ConfiguringSecureShell(SSH)forAIX

Open the /etc/ssh/sshd_config file on the AIX server where you want to install Network
Manager.
Ensurethatthefilecontainsthefollowingline:
UseLoginyes

1. Saveandclosethefile.
2. YoucannowuseSSHtoaccesstheserverandinstallNetworkManager.


## errptCommand

Generatesareportofloggederrors.
**Flags:**

**-a:** Displays information about errors in the error log file in detailed format. If used in
conjunctionwiththe-tflag,alltheinformationfromthetemplatefileisdisplayed.

**-j** **_ErrorID_** **[,** **_ErrorID_** **]:** Includes only the error-log entries specified by the _ErrorID_ (error
identifier)variable.The _ErrorID_ variablescanbeseparatedbya,(comma),orenclosedin""
(doublequotationmarks)andseparatedbya,(comma),oraspacecharacter.Whencombined
withthe-tflag,entriesareprocessedfromtheerror-templaterepository.(Otherwiseentriesare
processedfromtheerror-logrepository.)

Hereontheoutputyoucansee “C”meansclassand“h”meanshardware.

AlsoonTimestampletssay0614034923,itislike 06 meansmonth(june) 14 means(june14)

0349 mean3:49timeand 23 means2023.



## ConnectCiscoSwitchorRouterviaConsoleCable
1. Youneedaserialcable.Rj45toRS232orRJ45toUSB.
2. PluginthemaleRJ45toCISCOswitchandanotherUSBmalesidetoyourlaptop.
Nowyoucanuseaminicomtoolorputtytocommunicatewithaswitch.Ifyouareawindow
user,Puttyisthebestoption.YouwillautomaticallygetselectedwiththeCOMportandchoose
theconnectiontypetoserialthistime.Notsshortelnetoranyotheroption.

Nextyoucanuseminicom.
**Command:** minicom-s


Inthesetupmenu,gotothe"Serialportsetup"optionandconfiguretheserialportsettingsto
matchthesettingsofthenetworkdevice.Thismayincludethebaudrate,databits,stopbits,and
parity.Youcancheckthedocumentationofthedevicetoseewhichsettingsareneeded.

pressAtoenterintotheserialportoption.Savethesettingsandexitthesetupmenu.


You shouldnowbein theminicomterminalwindow,youwillbe connectedtothedevice's
command-lineinterface.Youcannowentercommandstoconfigurethedevice.


## ConfigureNTPserverandClient

VerifythatyouhaveasuitableNTPserver.Enter:
**Command:** lssrc-lsxntpd
Gotontpconfifile
**Command:** vi/etc/ntp.conf
Add:
server127.127.1.0
Doublecheckthat"broadcastclient"iscommentedout.
#stopsrc-sxntpd
#startsrc-sxntpd

**Onclientside:**
Verifythatyouhaveaserversuitableforsynchronization.Enter:
**Command:** ntpdate-dip.address.of.server

Specifyyour **xntp** serverin **/etc/ntp.conf** ,enter:
Command:vi/etc/ntp.conf

(Commentoutthe"broadcastclient"lineandadd **serverip.address.of.serverprefer** .)

Leavethe **driftfile** and **tracefile** attheirdefaults.

Verifythattheclientissynched.
**Command:** lssrc-lsxntpd
Confirmbycommand‘date’.
**NOTE:** SyspeershoulddisplaytheIPaddressornameofyour **xntp** server.Thisprocessmay
takeupto 12 minutes.


## BackuprootvgbycreatingLVonVIOS

UploadAIXupdatefileonAIXserver(testserver1).Path:/tmp/

CreateLVusing **command:** smitlvonVIOS.

NowwehavetomapthatlvtoAIXserver.Serverwillreaditashdisk.
Checkthepartitionidoftestserver1.Noteitsvhostid,e.g.vhost1

Nowmapthelvusing **command:** mkdev-vdevbklv-vadaptervhost1.


Nowcheckpvontestserver1with **command:** lspv

Hereyoucanseewehavehdisk1.

CheckAIXisbootfromwhichdisk.
**Command:** bootlist-mnormal-o
Wegotitfromhdisk0whichisbasicallyourOGrootvg.

Nowwehavetotakebackupofrootvgonhdisk1.
**Command:** alt_disk_copy-dhdisk1

Nowoncommand **lspv** wewillget **altinst_rootvg.** whichbasicallymeansithasbeenclone.

#lspv#Systembootedfromhdisk0.
hdisk0 00f62177fc932e26 rootvg active
hdisk1 00f6217735697d2a altinst_rootvg

Toswitchbetweenthefirstandsecondinstancesoftheoperatingsystem,simplychangetheboot
orderandrebootthesystem.Thesystemwillbootfromthisdisk,whichisfirstonthebootlist.

#lspv#Systemstartedfromaclone(hdisk1).
hdisk0 00f62177fc932e26 old_rootvg
hdisk1 00f6217735697d2a rootvg active

Whenyouboottheoperatingsystemfromthediskthatcontainsitsoriginalversion,thevolume
groupnameswillchangebacktorootvgandaltinst_rootvg:

#lsvg
rootvg
Altinst_rootvg

Simplyforthisyouneedtorestartconsoleandinsmsmenuselectdiskandchoosediskhdsik1
orhdsik0 andchoosenormalmodethenyougo.


Nowwehavepatchesfileon/tmpsowecdthereandrunsmittyupdate_all

Afterupdatingwegotproblemonjavaversion.Basicallywefailedonupdatingjavaversion.
Howdowefindit?



