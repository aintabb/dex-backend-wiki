In-depth specification of /search/{query}

During the proof-of-concept, we will split this controller into two controllers

/search/internal/{query}

/search/external/{query}

This is done due to loading times of Gitlab.
By splitting these controllers the frontend is able to show the projects in DEX while showing a loading icon when waiting for the Gitlab projects to load.

The internal controller will search through the registered projects in DEX itself. This search will be done based on the title and description.

The external controller will be hardwired into FHICT Gitlab.
After the proof-of-concept, the external controller will search through the registered services instead of being hardwired.

Both controllers will use the same class as the return result.

| SearchResult | 
| ------ | 
| id | 
| name |
| description |
