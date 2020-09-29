## Endpoints of API Back end

| Controller             | Endpoint        | Method | Required Role/Scope | Description                          |
| ---------------------- | --------------- | ------ | ------------------------------------------------------- | ------------------------------------ |
| **User Controller**    | /api/User | GET| Role.RegisteredUser| Get user information |
|| /api/User     | POST| Scopes.UserWrite|Create user account|
|| /api/User/{id}| GET | Scopes.UserRead |Get user information|
|| /api/User/{id}| PUT | Scopes.UserWrite|Update user account |
|| /api/User/{id}| Delete | Scopes.UserWrite| Delete user account |
| **Project Controller** | /api/Project   | GET    | None | Get all projects|
|| /api/Project| POST   | Role.RegisteredUser| Create new project|
|| /api/Project/{id}   | GET| None | Get project information|
|| /api/Project/{id}   | PUT| Scope.ProjectWrite or User that added the project | Update project|
|| /api/Project/{id}   | DELETE | Scope.ProjectWrite or User that added the project | Delete project|
|| /api/Project/wizard?sourceUrl={url} | GET | Role.RegisteredUser| Get information from external sources|
| **Search Controller**| /api/search/internal/{query}| GET| None| Search for projects in the Digital Excellence database |
|| /search/external/{query} | GET | None | Search for projects in the FHICT GitLab**Not implemented yet** |
| **Embed Controller** | /api/Embed | GET    | Scope.EmbedRead| Get all embedded projects|
|| /api/Embed | POST| Scopes.EmbedWrite or User that added the project|Create embedded project|
|| /api/Embed/{guid}| GET | None |Get project inside the embedded project|
|| /api/Embed/{guid}| DELETE | Scopes.EmbedWrite or User that added the project|Delete embedded project |
| **Highlight Controller** | /api/Highlight   | GET    | None | Get all highlights|
|| /api/Highlight| POST| Scopes.HighlightWrite |Create highlight|
|| /api/Highlight/{highlightId}| GET | None |Get highlight|
|| /api/Highlight/{highlightId}| PUT | Scopes.HighlightWrite|Update highlight|
|| /api/Highlight/{highlightId}| DELETE | Scopes.HighlightWrite|Delete highlight|
| **Role Controller** | /api/Role/Roles | GET    | Scope.RoleRead | Get all roles|
|| /api/Role/Scopes| GET    | Scope.RoleRead| Get all scopes|
|| /api/Role/{roleId} | GET    | Scope.RoleRead | Get Role information|
|| /api/Role/{roleId}| PUT | Scope.RoleWrite |Update role|
|| /api/Role/{roleId}| DELETE| Scope.RoleWrite|Delete role|
|| /api/Role| POST | Scope.RoleWrite|Create role|
|| /api/Role/SetRole| PUT | Scope.RoleWrite|Update role of user|
| **File Controller** | /api/File | GET    | Role.RegisteredUser | Get all files|
|| /api/File| POST  | Role.RegisteredUser| Upload / Create file|
|| /api/File/{fileId} | GET    | None | Get single file|
|| /api/File/{fileId} | DELETE | Role.RegisteredUser (only owner) | Delete file |



