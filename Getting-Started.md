# About
This wiki article explains the steps and tools that are necessary in order to get the backend services running.  

The backend consist of the following three services:
- API (https://localhost:5001)
- Identity Server (https://localhost:5005)
- Database


## Setup with docker
### Prerequisites
- [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
- [Docker (version 19.03.0+)](https://docs.docker.com/get-docker/)
- [Docker compose (Comes pre-installed with Docker Desktop)](https://docs.docker.com/compose/install/)

### Steps
1. Clone [this](https://github.com/DigitalExcellence/dex-backend) repository, using the following command:   
```git clone https://github.com/DigitalExcellence/dex-backend.git```
2. Browse to the folder of the repository
3. Run the command: `docker-compose up` (If you want to run it in the background: `docker-compose up -d`) (if you need to rebuild the images use: `docker-compose up --build`)
4. After a short while, the services should be running and accessible on the urls mentioned in the about section
5. When you visit the urls for the first time, you should trust the certificate
6. When you want to stop the services from running, run the command: `docker-compose down`

## Setup with Visual Studio
### Prerequisites
- [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
- [Visual Studio]

### Steps
1. Clone backend repository
2. Open solution 
3. Right click -> Set as startup projects: Choose "Multiple startup projects" and select action 'Start' for 1_API and 6_IdentityServer 

### Tips
After launch: check if database is created by using SQL Server Object Explorer.
To check if API is working:
1. Use https://localhost:5001/index.html and click on Authorize.
2. Select Scopes: 'dex-api'
3. Use user: 'bob' password: 'bob' to authorize.
4. Click one of the API requests and check for response.

## Postman setup
### Prerequisites
- [Postman]

### Steps
1. Import both environment & collection .json files from backend repository in Postman.
2. Make sure 'SSL certificate verification' setting in Postman is disabled.
3. Collection: 'Digital-Excellence-API' should be under collections in the left panel. Environment 'Local' should be available in the top right corner of Postman.