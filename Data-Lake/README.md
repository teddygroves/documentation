# DATA-LAKE PROJECT
A data lake is a scalable data storage and analytics service.
Here we will collect all the unstructured data that is generated at DTU Biosustain. Currently this includes: Proteomics data from Analytical Core and MiSeq and NextSeq data from the NGS lab.
 
**RESPONSIBILITY**
- Project leader: Lea Mette Madsen Sommer, lemad@biosustain.dtu.dk
- Code for proteomics: Eren Yagdian, ereyag@biosustain.dtu.dk
- Code for NGS: Eren Yagdian, ereyag@biosustain.dtu.dk
- Code for datalake-sync: Thomas Meltofte Erikesen, thoeri@biosustain.dtu.dk
- Code for datalake-sync-vm: Thomas Meltofte Erikesen, thoeri@biosustain.dtu.dk
- Pipeline data for proteomics: Tune wulff, tuwu@biosustain.dtu.dk and Ding He, dinghe@biosustain.dtu.dk
- Pipeline data for NGS: Vijayalakshmi Kandasamy, vijkan@biosustain.dtu.dk and Ding He, dinghe@biosustain.dtu.dk
- Metabolomics: Tune Wulff, tuwu@biosustain.dtu.dk
- Pipeline data for metabolomics: Ding He, dinghe@biosustain.dtu.dk and Tune Wulff, tuwu@biosustain.dtu.dk
- NGS lab: Vijayalakshmi Kandasamy, vijkan@biosustain.dtu.dk
- External data providers: none know
- Documentation: Karina Reimer-Hansen, kreimer@biosustain.dtu.dk
 
### TECHNOLOGY USED
- Python 3
- Azure
- Docker
- SQL
 
#### PYTHON 3
Python 3 is an object-oriented programming language that the project is written in.
 
#### AZURE
Azure is a cloud computing service operated by Microsoft for application management via Microsoft-managed data centers.
Here we host the Blob storage containers.
Blob storage is a feature in Microsoft Azure that lets us store unstructured data in Microsoft's cloud platform. This data can be accessed from anywhere in the world and can include any kind of data type you want. Blobs are grouped into "containers" and user access is set on the blob level.
 
#### DOCKER
Docker is an open source containerization platform.
It enables developers to package applications into containers.
We use Docker for the VM environment.
 
#### SQL
SQL stands for Structured Query Language.
SQL lets you access and manipulate SQL-databases.
 
## HOW THE DATA-LAKE WORKS
The Data lake gets its data from different data providers
- Analytical Core
- NGS lab

the Data lake repo contains mutible diff projects repos  

the data-lake virtual machine reads, writes and processed to the data-lake.
NGS data comming from the MiSeq that is processed and a result table is loaded into the DWH
(you can also find a data-lake.png in this folder that will show you a diagram of the data-lake struktur)
 
## DATA-LAKE PIPELINES
- Proteomics
- NGS nextseq
- NGS miseq
- Nanopore **is next**
- targeted-Metabolomics **is next**
- Untargeted-Metabolomics **is next**
 
### DATALAKE-SYNC OVERVIEW

sync_to_azure is a script for synchronizing MiSeq and NextSeq that runs in the Azure
blob storage. (Blob storage is optimized for storing massive amounts of unstructured data.)
the sync_to_azure script given us a source folder (--main-folder) containing individual runs
in sub-folders, the script will synchronize each sub-folder to azure, verify
the integrity of remote files by comparing MD5 hashes, and optionally delete
local files if files were successfully transferred and validated (with
--remove-source).
 
## AZCOPY
The project is depend on AZCOPY,
AzCopy v10 is a command-line utility that you can use to copy data to and from containers and file shares in Azure Storage accounts.
AzCopy V10 presents easy-to-use commands that are optimized for performance.
read more on https://github.com/biosustain/azure-storage-azcopy.git
 
# LOGGING
By default the script will write all output to STDOUT, but the --log-file
option may be used to save a copy to a given file. In addition, if the
--log-recipient and --smth-\* options are set, the log will be emailed to
the specified recipients if any errors occur.
 
# datalake-sync-vm
In the data-lake repositories you will find a folder called datalake-sync-vm (data-lake/data lake-sync-vm)
This folder contains configuration files and scripts for setting up the VM used to sync files to the data lake.
 
## BUILDING AND PUSHING CONFIG FILES AND DOCKER IMAGES
Makefile has a set of rules to determine which parts of a program need to be recompiled, and issues commands to recompile them. Makefile is a way of automating software building procedures and other complex tasks with dependencies. Makefile contains: dependency rules, macros and suffix(or implicit) rules.
The `Makefile` included in this directory automates building, tagging, and pushing of docker images used by the VM. In addition,
the makefile generates updated wrapper scripts that invoke the current version of the images and rsyncs these to the VM.
 

