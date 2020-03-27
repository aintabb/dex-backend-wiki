## Endpoints of API Back end

| Controller             | Endpoint        | Method | Required role                                           | Description                          |
| ---------------------- | --------------- | ------ | ------------------------------------------------------- | ------------------------------------ |
| **User Controller**    | /user           | GET    | Administrator                                           | Get a list of all users              |
|                        | /user/{id}      | GET    | Administrator                                           |Get user information|
|                        | /user/my        | GET    | User                                                    | Get the currently authenticated user |
| **Project Controller** | /project/{id}   | GET    | User                                                    | Get project information              |
|                        | /project        | POST   | User                                                    | Add new project                      |
|                        | /project/{id}   | PUT    | User (The user that added the project) or administrator | Edit project information             |
|                        | /project/{id}   | DELETE | User (The user that added the project) or administrator | Delete project                       |
| **Search Controller**  | /search/internal/{query} | GET    | User                                                    | Search for projects in the Digital Excellence database |
|  | /search/external/{query} | GET | User | Search for projects in the FHICT GitLab |

