## Database

| Model class   | Attribute | Type | Description                                 |                           |
| ---------------------- | --------------- | ------ | ------------------------------------------------------- | ------------------------------------ |
| **User**    | Id                      | Integer | Identification string                                | Auto-generated |
|             | Name                    | String   | The full name of the user                            |                |
|             | Email                   | String   | The e-mailaddress of the user                        |                |
|             | IdentityId              | String   | The id of the user provided by the identity provider |                |
|             | Services | LinkedService[] | The services linked to the account of the user |                |
| **Linked Service** | Service | String | The service that the link is for (For example:  FHICT GitLab) | |
|  | RefreshToken | String | The refresh token of the user for communicating with the service API | |
| **Project** | Id                      | Integer | Identification string                                | Auto-generated |
|             | Name                    | String   | The name of the project                              |                |
|             | Description             | String   | A description of the project                      |                |
| | ShortDescription | String | A short description of the project | |
|             | Uri                     | String   | The URI of the project                               |                |
| | UserId | Integer | The id of the user who added the project | |
|             | Contributors            | String[] | The contributors of the project                      |                |

