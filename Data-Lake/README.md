# DATA-LAKE PROJECT
A data lake is a scalable data storage and analytics service.
Here we collect Proteomics, NGS, Metabolomics data this data com from NGS lab sevicer.  

## RESPONSIBILITY
- Project leader: Lea Mette Madsen Sommer, lemad@biosustain.dtu.dk
- Code for proteomics: Eren Yagdian, ereyag@biosustain.dtu.dk
- Code for NGS: Eren Yagdian, ereyag@biosustain.dtu.dk
- Code for datalake-sync: Thomas Meltofte Erikesen, thoeri@biosustain.dtu.dk
- Code for datalake-sync-mv: Thomas Meltofte Erikesen, thoeri@biosustain.dtu.dk
- Pipeline data regenerate for proteomics: Tune wulff, tuwu@biosustain.dtu.dk and Ding He, dinghe@biosustain.dtu.dk
- Pipeline data for NGS: Vijayalakshmi Kandasamy, vijkan@biosustain.dtu.dk and Ding He, dinghe@biosustain.dtu.dk
- Metabolomics: Tune Wulff, tuwu@biosustain.dtu.dk
- Pipeline data for metabolomics: Ding He, dinghe@biosustain.dtu.dk and Tune Wulff, tuwu@biosustain.dtu.dk
- NGS lab: Vijayalakshmi Kandasamy, vijkan@biosustain.dtu.dk
- External data providers: none know
- Documentation: Karina Reimer-Hansen, kreimer@biosustain.dtu.dk

### TECHNOLOGY USED
- python 3
- Azure
- Docker
- SQL

#### PYTHON 3
Python3 is the programming language that the project is written in.

#### AZURE
Azure is a cloud computing service operated by Microsoft for application management via Microsoft-managed data centers.

#### DOCKER
Docker is an open source containerization platform.
It enables developers to package applications into containers.
We use Docker for the MV environment.

#### SQL
SQL stands for Structured Query Language.
SQL lets you access and manipulate databases.

## HOW THE DATA-LAKE WORKS
The Data lake get it data from 3 different data providers
- Analytical Core
- NGS lab
- External data providers
When the data is put into the data-lake we process it into tables and organize it in the data warehouse.
(you can also find a data-lake.png in this folder that will show you a diagram of the data-lake struktur)

## DATA-LAKE FOLDER STRUCTURE
- Proteomics
- NGS
- Metabolomics

### DATALAKE-SYNC OVERVIEW
sync_to_azure is a script for synchronizing MiSeq/NextSeq runs to Azure
blob storage.
that given us a source folder (--main-folder) containing individual runs
in sub-folders, the script will synchronize each sub-folder to azure, verify
the integrity of remote files by comparing MD5 hashes, and optionally delete
local files if files were successfully transferred and validated (with
--remove-source).
Completed runs may be detected by checking for the existence of user-defined
files, such as "RTAComplete.txt" for MiSeq and "RunCompletionStatus.xml" for
NextSeq v2 (with --completion-flag).
In addition to synchronizing folders containing sequencing runs, the script
can optionally copy sample-sheet files located in a separate folder; for a
given run ${NAME} the sample-sheet is expected to be named ${NAME}.csv.
 
# DOCKER IMAGE
The docker image requires that the `azure-storage-azcopy` submodule has been checked out. If that is not the case, the submodule can be initialized as follows:
 
``` bash
$ git submodule update --init azure-storage-azcopy/
```
 
Note that the submodule is currently set up using an SSH URL (`git@github.com/`) and therefore requires that the user has added a public SSH on github. If this is not done, the `submodule update` command will fail with permission denied errors.
 
To build an image with a tag based on the current commit:
 
``` bash
$ make
# or
$ make build
```
 
The image can be pushed to the CFB container registry with
 
``` bash
$ make push
```
 
By default, the short form of the current commit hash will be used as the tag for the docker image. This can be overridden by setting the `TAG` variable:
 
``` bash
$ make TAG=MyTag
$ make push TAG=MyTag
```
 
**WARNING:** Please make sure that all current changes have been committed before building a docker image for deployment!
 
 
# TO MANUAL INSTALLATION USE THIS COMMAND LINES 
``` bash
$ python3 setup.py install
$ sync_to_azure -h
```
 
Optional pretty logs:
 
``` bash
$ python3 -m pip install coloredlogs
```
 
## AZCOPY
AzCopy v10 is a command-line utility that you can use to copy data to and from containers and file shares in Azure Storage accounts. 
AzCopy V10 presents easy-to-use commands that are optimized for performance.
read more on https://github.com/biosustain/azure-storage-azcopy.git

This script depends on a modified version of AzCopy that adds a 'list_md5s'
command for the bulk retrieval of MD5 hashes of uploaded:
 
``` bash
$ sudo apt-get install golang
$ git clone https://github.com/biosustain/azure-storage-azcopy.git
$ cd azure-storage-azcopy
$ git checkout list_md5s
$ go build
```
 
Place the resulting executable, 'azure-storage-azcopy', in your PATH. If 'go
build' fails while fetching dependencies, you may need to set a GOPATH:
 
``` bash
$ export GOPATH=$HOME/go
```
 
# CONFIGURATION
The sync_to_azure script may be configured via command-line options,
or using a ini file via --config-file. By default, the script will look for
'azsync.cfg' in the current working directory:
 
``` toml
tenant-id =
application-id =
storage-account = cfbngsv2
container-name = nextseq01
credentials = /home/cfbngssync/config/credentials.txt
 
main-folder = /cifs/nextseq.clients.net.dtu.dk/NextSeqOutput/
samplesheet-folder = /cifs/nextseq.clients.net.dtu.dk/NextSeqSampleSheets/
completion-flag = RunCompletionStatus.xml
 
destination = NextSeqOutput
 
log-file = /home/cfbngssync/config/logs/nextseq.log
log-recipient =
azcopy-logs = /home/cfbngssync/config/logs/nextseq/
 
smtp-user = cfb-datalake-upload@win.dtu.dk
smtp-password =
smtp-host = mail.dtu.dk
smtp-port = 587
```
 
Options in the config file correspond to the options available via the command
line (see 'sync_to_azure --help'), but without the leading dashes.
 
# LOGGING
By default the script will write all output to STDOUT, but the --log-file
option may be used to save a copy to a given file. In addition, if the
--log-recipient and --smth-\* options are set, the log will be emailed to
the specified recipients if any errors occur.
 
# DEVELOPMENT
Code was formatted using [Black](https://github.com/psf/black) and checked using
[flake8](http://flake8.pycqa.org/en/latest/). Unit tests and regression tests are included and can be run using `tox`:
 
``` bash
$ cd container
$ tox
```
 
 
# datalake-sync-vm
In the data-lake repositories you will find a folder called datalake-sync-mv (data-lake/data lake-sync-mv)
This folder contains configuration files and scripts for setting up the VM used to sync files to the data lake, along with other tasks.
 
## BASIC REQUIREMENTS
The VM must have `autofs`, Docker and the Azure command-line tools (`az`) installed. In addition, `az` must be used to login using an account with access to the `cfbregistry` ACR. The `cfb_acr_reader` service principal is intended for this purpose (see below). Python modules used by `cronbeat` must either be installed globally or in a virtual environment.
 
## AUTO-MOUNTING NETWORK DRIVES
 
1. Install `autofs`:
 
``` bash
$ sudo apt-get install autofs
```
 
2. Add the following line to the end of `/etc/auto.master`:
 
```
/net /etc/auto.nfs --timeout=300
```
 
3. Add mount-points to `/etc/auto.nfs`:
 
```
MiSeqOutput          -fstype=cifs,vers=2.1,ro,credentials=/etc/creds/MiSeqOutput.txt    ://10.75.2.164/MiSeqOutput/
NextSeqOutput        -fstype=cifs,vers=2.1,ro,credentials=/etc/creds/NextSeqOutput.txt  ://10.75.2.163/NextSeqOutput/
NextSeqSampleSheets  -fstype=cifs,vers=2.1,ro,credentials=/etc/creds/NextSeqOutput.txt  ://10.75.2.163/NextSeqSampleSheets/
 
Proteomics           -fstype=cifs,vers=2.1,ro,credentials=/etc/creds/Proteomics.txt     ://CFB-pFile01.win.dtu.dk/LabData/CFB/Instrument_Data/Exploris\ 480\ FSHPNR2/Data/
```
 
 
3. Save credentials in at the locations specified in `/etc/auto.nfs`, e.g:
 
``` bash
$ cat /etc/creds/NextSeqOutput.txt
username=
password=
```
 
4. Restart autofs:
 
``` bash
$ /etc/init.d/autofs restart
```
 
Mount points should now be accessible via `/net/MiSeqOutput`, etc:
 
``` bash
$ ls /net/Proteomics/
Prot27 Prot28 Prot29 [snip]
```
 
## GRANTING ACCESS TO THE CFB DOCKER REGISTRY
 
Docker on the VM needs access to the CFB docker registry (`cfbregistry.azurecr.io`). Scripts obtain temporary access to the ACR via the `az acr login` command. For that to work, login as the `cfb_acr_reader` app using `az login` on the VM:
 
``` bash
az login --service-principal --tenant f251f123-c9ce-448e-9277-34bb285911d9 --username bf6564d4-1e66-41e3-915e-b1fa347b1c55
```
 
This stores credentials for the service principal on the VM.
 
## BUILDING AND PUSHING CONFIG FILES AND DOCKER IMAGES
 
The `Makefile` included in this directory automates building, tagging, and pushing of docker images used by the VM. In addition, the makefile generates updated wrapper scripts that invoke the current version of the images and rsyncs these to the VM.
 
In addition, the makefile will push configuration file templates to the VM. Existing configuration files are not overwritten.
 
``` bash
# Build utility files and images
make build
# Build and push utility files and images
make push
```
 
The images tagged using the short git hash for the current commit. Configuration files are currently expected to be placed in `~/config/` on the VM and utility scripts and files are expected to be placed in `~/utils`.
 
## CONFIG FILES
 
On the server side, all configuration files in `~/config` must be updated once copied there. In addition, a `~/cronbeat.ini` file must be created with a `webhook` value specified (see `cronbeat/README.md`).
 
## CRON JOBS
 
An example crontab file is included in `utils`:
 
``` bash
# replace existing crontab
$ crontab ~/utils/crontab
```