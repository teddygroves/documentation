This is the backend for LIMS - Laboratory Information Management System
 
## RESPONSIBILITY
- Project leader: Lea Mette Madsen Sommer, lemad@biosustain.dtu.dk
- LIMS Administrator: Ester Milesi, esterm@biosustain.dtu.dk
- code: Karina Reimer-Hansen, kreimer@biosustain.dtu.dk, Eren Yagdian, ereyag@biosustain.dtu.dk
- Documentation: Karina Reimer-Hansen, kreimer@biosustain.dtu.dk
 
### TECHNOLOGY USED
- Python 3
- jenkins
- Docker
- postgres
 
#### PYTHON 3
Python 3 is an object-oriented programming language that the project is written in.
FLask i also used in the project, Flask is a micro web framework written in Python. It is classified as a microframework because it does not require particular tools or libraries.
 
### JENKINS
Jenkins is an open source automation server. It helps automate the parts of software development related to building, testing, and deploying, facilitating continuous integration and continuous delivery.
 
### LIMS workflow environment
 
we have 3 environment that is also setup with Benchling
- test is running local on software engineer and have Benchling test environment
- staging is a copy of the production, where we run the final test before new code is pushed to production. We also have a Benchling staging environment attached.
- production is here where we show our finished solution
 
The code lays on github https://github.com/orgs/biosustain/teams/rdm under repositories is not accessible for everyone.
 
#### DOCKER
Docker is an open source containerization platform.
It enables developers to package applications into containers.
With Docker, you can ensure that the functionality of your applications can be executed in any environment. This advantage arises because all applications and their dependencies are brought together in a Docker execution container.
 
We have 5 linux containers running on this project.
 
lims-extensions_worker               
lims-extensions_web          
postgres                  
redis            
productservice
 
A Docker-Container is a standard software unit that stores a code in all its dependencies. This makes the application run quickly and reliably on a wide variety of computing environments. A Docker container represents a lightweight standalone executable software package that contains everything needed to run an application code runtime: Program code, RunTime engines, System tools, System libraries, Settings
 
This containerised software always runs the same on Linux, Mac and Windows-based systems, regardless of infrastructure. Docker containers isolate the software from the environment and ensure that it works consistently despite differences.
