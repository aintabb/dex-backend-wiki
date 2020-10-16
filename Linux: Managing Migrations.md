While working on Dex in a Linux enviroment, you'll be probably be using Rider-like IDEs and there will be no "Package Manager Console" to do the migration operations.

**To be able to overcome this drawback, you should follow these steps;**
* Go to this link [EF Core](https://docs.microsoft.com/en-us/ef/core/miscellaneous/cli/dotnet) and install the entity framework core tools by following the steps (*If you haven't installed dotnet core alread, go ahead and follow these steps within this link [Dotnet Core](https://docs.microsoft.com/en-us/dotnet/core/install/linux-ubuntu)*)
* After a successful installation, run this command to add a migration;
 `dotnet ef migrations add <MIGRATION_NAME> -s <STARTUP_PROJECT> -p <DB_CONTEXT_PROJECT> --context <DB_CONTEXT_PROJECT>.<CONTEXT_NAME>`           (*Here is an example command that I've used;*
 `dotnet ef migrations add AddLikesFieldToProject -s API -p Data --context Data.ApplicationDbContext`*)*
 * If you couldn't find the db contexts in your solution, run this command;
 `dotnet ef dbcontext list -p <DB_CONTEXT>`