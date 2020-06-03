This page serves to inform users about specific error details.
When the error message is not clear enough, then this is the place to put an indepth story about it.


## E56D89C5-8760-4503-839C-F695092C79BF
The normal schema of GitLab is:
gitlab.com/owner/project
gitlab.com/group/project

but when a user gives an URL to a group like:
gitlab.com/group/subgroup
it still resolves with the API but it does not give data back(as expected)

But also when you create a project on GitLab it gives something along the lines of:
get started with GitLab make your first commit.

and if you haven't done that then the API cannot get any information.
referring to the not instantiated part.
