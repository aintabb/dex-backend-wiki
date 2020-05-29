## C1 Context

The diagram below contains the context of Digital Excellence.

There are 2 types of users:

- **Users** are people who view and manage projects on Digital Excellence.
- **Administrators** are internal users that have authorization to manage Digital Excellence.

Digital Excellence uses an external identity provider. This identity provider allows users to sign in using their existing Fontys-account. Unlike other users, administrators are authenticated using an internal account on the Identity Server.

Digital Excellence uses information (projects) from multiple external sources (For example: GitLab, GitHub, etc.)

![alt text](../wiki/images/architecture/C1.png "C1 Context")





## C2 Containers

The diagram below gives a more in-depth look at Digital Excellence. The application uses multiple containers that together make up the entire application. These containers are:

- The **front end** is a user interface where the user can view and manage projects.
- The **web server** is a container that serves the front end.
- The **API back end** is the back end that handles all requests to view and manage projects.
- The **Identity Server** is the back end that handles all requests to authenticate and authorize users.
- The **databases** are containers that are responsible for storing data (For example: projects, users, etc.). The data is stored and retrieved by the API back end and the identity back end.

![alt text](../wiki/images/architecture/C2.png "C2 Containers")





## C3 Components

The diagram below contains a more in-depth look at the API back end of Digital Excellence.

- The API back end contains 3 layers:
  - The UI layer contains controllers which handle requests:
    - The **user controller** handles requests for managing and retrieving users.
    - The **project controller** handles requests for managing and retrieving projects.
    - The **search controller** handles requests for searching projects.
  - The logic layer contains services which handle application logic:
    - The **user service** manages users.
    - The **project service** manages projects (both local and external).
    - The **search service** handles the logic for searching projects (both local and external).
- The data access layer contains repositories for storing data and a manager to retrieve information and search external sources:
  - The **user repository** stores and retrieves users.
    - The **project repository** stores and retrieves projects.
    - The **sources manager** retrieves and searches projects in external sources (For example: GitLab, GitHub, etc.)

![alt text](../wiki/images/architecture/C3.png "C3 Components")