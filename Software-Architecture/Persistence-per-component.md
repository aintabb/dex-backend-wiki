## Database

| Model class   | Attribute | Type | Description                                 |                           |
| ---------------------- | --------------- | ------ | ------------------------------------------------------- | ------------------------------------ |
| **User**    | Id| Integer | Identification integer| Auto-generated |
|| Name| String| The full name of the user||
|| Role| Role| The security role of the user||
|| Email| String| The e-mailaddress of the user||
|| IdentityId| String| The id of the user provided by the identity provider ||
|| Projects | Project[] | The projects linked to the account of the user ||
|| Services | LinkedService[] | The services linked to the account of the user ||
|| ProfileUrl| string| the url to the profile id||
|| IsPublic| boolean| the flag to see if the user wants to show their email address on the projects||
|**RoleScope**|Id|Integer|Identification number|Auto-generated|
|| Scope| string| The name of the rolescope||
|**Role**|Id|Integer|Identification number|Auto-generated|
|| Name| string| The name of the role||
|| Scopes| RoleScope[]| the linked scopes to the role||
| **Linked Service** | Service | String | The service that the link is for (For example:  FHICT GitLab) | |
|  | RefreshToken | String | The refresh token of the user for communicating with the service API | |
| **Project** | Id| Integer | Identification string| Auto-generated |
|| Name| String   | The name of the project||
|| Description| String   | A description of the project||
|| ShortDescription | String | A short description of the project | |
|| Uri| String| The URI of the project||
|| UserId | Integer | The id of the user who added the project | |
|| Contributors| Collaborator[] | The contributors of the project||
|| Created | DateTime | The date and time that the project was created | |
|| Updated| DateTime | The date and time that the project was last updated | |
| **Highlight** | Id| Integer | Identification number| Auto-generated |
|| ProjectId| Integer| The Id of the project||
|| StartDate| DateTime? | The date and time that the highlight could be visible| |
|| EndDate| DateTime? | The date and time that the highlight is not visible anymore | |
| **EmbeddedProject** | Id| Integer | Identification number| Auto-generated |
|| UserId| Integer| The Id of the user that created this embedded project||
|| ProjectId| Integer| The Id of the project||
|| Guid| Guid   | The unique identifier of the embedded project||
|**Collaborator**|Id|Integer|Identification number|Auto-generated|
|| FullName| string| The name of the collaborator||
|| Role| string| The role this person played in the project||
|| ProjectId| Integer| The Id of the project||
