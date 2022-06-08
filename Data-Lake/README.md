# DATA-LAKE project
A data lake is a scalable data storage and analytics service.
 
## Responsibility
- project leader: Lea Mette Madsen Sommer, lemad@biosustain.dtu.dk
 
- code for proteomics: Eren Yagdian, ereyag@biosustain.dtu.dk
- code for NGS: Eren Yagdian, ereyag@biosustain.dtu.dk
- code for datalake-sync: Thomas Meltofte Erikesen, thoeri@biosustain.dtu.dk
- code for datalake-sync-mv: Thomas Meltofte Erikesen, thoeri@biosustain.dtu.dk
 
- Pipeline data regenerate for proteomics: Tune wulff, tuwu@biosustain.dtu.dk and Ding He, dinghe@biosustain.dtu.dk
- Pipeline data for NGS: Vijayalakshmi Kandasamy, vijkan@biosustain.dtu.dk and Ding He, dinghe@biosustain.dtu.dk
- Metabolomics: Tune Wulff, tuwu@biosustain.dtu.dk
- Pipeline data for metabolomics: Ding He, dinghe@biosustain.dtu.dk and Tune Wulff, tuwu@biosustain.dtu.dk
- NGS lab: Vijayalakshmi Kandasamy, vijkan@biosustain.dtu.dk
- External data providers: none know
 
- Documentation: Karina Reimer-Hansen, kreimer@biosustain.dtu.dk
 
# Technology use
- python 3
- Azure
- Docker
- SQL
 
### Python3
Python3 is the programming language that the project is written in.
 
### Azure
Azure is a cloud computing service operated by Microsoft for application management via Microsoft-managed data centers.
 
### Docker
Docker is an open source containerization platform.
It enables developers to package applications into containers.
We use Docker for the MV environment.
 
### SQL
SQL stands for Structured Query Language.
SQL lets you access and manipulate databases.
 
##  We are converting our projects from SQL to Postgresql
reasons for this is that we have had experience,
that the banking-team sometimes made naming changes to their Post Sql database tables.
 
This gives os mapping conflicts in our SQL database.
To solve this we want to convert our SQL database to a Postgresql database
so that we have one to one database relations with Benchling.
 
## How the data-lake works
The Data lake get it data from 3 different data providers
- Analytical Core
- NGS lab
- External data providers
When the data is put into the data-lake we process it into tables and organize it in the data warehouse.
 
(you can also find a data-lake.png in this folder that will show you a diagram of the data-lake struktur)
 
## data-lake folder structure
- proteomics
- ngs
- meta
 
### datalake-sync overview
In the data-lake repositories you will find a folder called datalake-sync (data-lake/data lake-sync)
 
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
 
### datalake-sync-vm
 
In the data-lake repositories you will find a folder called datalake-sync-mv (data-lake/data lake-sync-mv)
 
This folder contains configuration files and scripts for setting up the VM used to sync files to the data lake, along with other tasks.
 

