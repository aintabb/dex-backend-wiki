## Database

| Model class   | Attribute | Type | Description                                 |                           |
| ---------------------- | --------------- | ------ | ------------------------------------------------------- | ------------------------------------ |
| **User**    | Id                      | String   | Identification string                                | Auto-generated |
|             | Name                    | String   | The full name of the user                            |                |
|             | Email                   | String   | The e-mailaddress of the user                        |                |
|             | IdentityId              | String   | The id of the user provided by the identity provider |                |
|             | FhictGitlabRefreshToken | String   | The FHICT GitLab API refresh token of the user       |                |
| **Project** | Id                      | String   | Identification string                                | Auto-generated |
|             | Name                    | String   | The name of the project                              |                |
|             | Description             | String   | The description of the project                       |                |
|             | Uri                     | String   | The URI of the project                               |                |
|             | Contributors            | String[] | The contributors of the project                      |                |

