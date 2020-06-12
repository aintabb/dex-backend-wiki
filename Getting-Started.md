### About
This wiki article explains the steps and tools that are necessary in order to get the backend services running.  

The backend consist of the following three services:
- API (https://localhost:5001)
- Identity Server (https://localhost:5005)
- Database

### Prerequisites
- [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
- [Docker (version 19.03.0+)](https://docs.docker.com/get-docker/)
- [Docker compose (Comes pre-installed with Docker Desktop)](https://docs.docker.com/compose/install/)

### Steps
1. Clone [this](https://github.com/DigitalExcellence/dex-backend) repository, using the following command:   
```git clone https://github.com/DigitalExcellence/dex-backend.git```
2. Browse to the folder of the repository
3. Run the command: `docker-compose up` (If you want to run it in the background: `docker-compose up -d`)
4. After a short while, the services should be running and accessible on the urls mentioned in the about section
5. When you want to stop the services from running, run the command: `docker-compose down`