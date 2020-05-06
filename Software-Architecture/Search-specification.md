In-depth specification of the search controller

During the proof-of-concept, we will split this controller into two controllers

/search/internal/{query}

/search/external/{query}

This is done due to loading times of Gitlab.
By splitting these controllers the frontend is able to show the projects in Digital Excellence while showing a loading icon when waiting for the Gitlab projects to load.

The internal controller will search through the registered projects in Digital Excellence itself. This search will be done based on the title and description.

It is possible to apply pagination by using ?page={PAGE}&amountOnPage={AMOUNT} as the query string.

To apply sorting, the query parameters sortBy and sortDirection can be used. (For example: ?sortBy=name&sortDirection=asc)

To apply filters, the query parameter for the specific filter can be added to the query. (For example: ?highlighted=true)


The external controller will be hardwired into FHICT GitLab.
After the proof-of-concept, the external controller will search through the registered services instead of being hardwired.



Both controllers will use the same class as the return result.

| SearchResults | Type           | Description                        |
| ------------- | -------------- | ---------------------------------- |
| Results       | SearchResult[] | The search results                 |
| Query         | String         | The search query                   |
| Count         | Integer        | The amount of results on this page |
| TotalCount    | Integer        | The total amount of results        |
| Page          | Integer        | The page                           |
| TotalPages    | Integer        | The amount of pages                |



| SearchResult | Type | Description |
| ------ | ------ | ------ |
| Id | Integer | The id of the project |
| Name | String | The name of the project |
| ShortDescription | String | The short description of the project |
| Created | DateTime | The date and time that the project was created |
| Updated | DateTime | The date and time that the project was last updated |

![Class_Diagram2](uploads/e17bc012e3fa941b748b0bfb96f90264/Class_Diagram2.jpg)
