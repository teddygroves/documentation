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

#### DOCKER
Docker is an open source containerization platform.
It enables developers to package applications into containers.
we have 4 containers running 1 for the worker, 1 web, 1 for postgres database and 1 for redis image. 