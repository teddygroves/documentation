# DATA-LAKE project
A data lake is a scalable data storage and analytices service. 
Ours is host in Azure and there we store data that we subtract from Benchling.

# techenoology use 
pyhton3
Azure
Docker
SQL 
PostgreSQL

# python3
Python3 is programming language that the project is written in.

# Azure
Azure is a cloud computing service operated by Microsoft for application management via Microsoft-managed data centers.

# Docker 
Docker is an open source containerization platform. it enables developers to package applicatins into containers.

# SQL and PostgrSQL
SQL stands for Structured Query Language. SQL lets you access and manipulate databases. 

PostgrSQL is a more advanced version of SQL. This the database languages that Benchling use.  

##  We are converting our projects from SQL to Postsql
reasons for this is that
we have had experience, that the bancling-team sometime makes naming conventions changes to there Postsql database. 

That gives os mapping conflicts in our SQL database. 
To solve this we want to convert our SQL database to a Postsql database
so that we have one to one database relations with Benchling.

# How the data-lake works
The Data lake get it data from 3 different data providers 
- Analytical Core
- NGS lab
- External data providers



# datalake-sync overview
In the data-lake repositories you will find a folder calld datalake-sync (data-lake/datalake-sync)
sync_to_azure is a script for synchronizing MiSeq/NextSeq runs to Azure
blob storage. Given a source folder (--main-folder) containing individual runs
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