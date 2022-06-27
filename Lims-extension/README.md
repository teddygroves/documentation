This is the backend for LIMS - Laboratory Information Management System
 
## RESPONSIBILITY
- Project leader: Lea Mette Madsen Sommer, lemad@biosustain.dtu.dk
- LIMS Administrator: Ester Milesi, esterm@biosustain.dtu.dk
- Code: Karina Reimer-Hansen, kreimer@biosustain.dtu.dk, Eren Yagdian, ereyag@biosustain.dtu.dk
- Documentation: Karina Reimer-Hansen, kreimer@biosustain.dtu.dk
 
### TECHNOLOGY USED
- Python 3
- Jenkins
- Docker
- PostgreSQL
 
#### PYTHON 3
Python 3 is an object-oriented programming language that the project is written in.
FLask is also used in the project, Flask is a micro web framework written in Python. It is classified as a microframework because it does not require particular tools or libraries.
 
### JENKINS
Jenkins is an open source automation server. It helps automate the parts of software development related to building, testing, and deploying, facilitating continuous integration and continuous delivery.
 
#### DOCKER
Docker is an open source containerization platform.
It enables developers to package applications into containers.
With Docker, you can ensure that the functionality of your applications can be executed in any environment. This advantage arises because all applications and their dependencies are brought together in a Docker execution container.
 
We have 5 linux containers running for this project.
 
lims-extensions_worker               
lims-extensions_web          
PostgreSQL                  
Redis            
Productservice
 
A Docker-Container is a standard software unit that stores a code and all its dependencies. This makes the application run quickly and reliably on a wide variety of computing environments. A Docker container represents a lightweight standalone executable software package that contains everything needed to run an application code runtime: Program code, RunTime engines, System tools, System libraries, Settings
 
This containerised software always runs the same on Linux, Mac and Windows-based systems, regardless of infrastructure. Docker containers isolate the software from the environment and ensure that it works consistently despite differences in operating systems.

#### PostgreSQL
**some text missing**

### LIMS workflow environment **I moved this down so that the order is the same as in the bullet list above**
 
We have 3 environments that is also setup with Benchling
- Test is run locally and relate to the Benchling test environment
- Staging is a copy of the production, where we run the final test before new code is pushed to production. We also have a Benchling staging environment attached.
- Production is here where we show our finished solution
 
The code itself is restricted access, for sequrity reasons.
 
