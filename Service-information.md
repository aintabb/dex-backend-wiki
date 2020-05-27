# Information
## .ConfigureAwait(false)
Why do we use configure await?

For the short answer:

It improves performance by avoiding unnecessary thread static access,
but more important it avoids deadlocks.

Long Answer:

https://devblogs.microsoft.com/dotnet/configureawait-faq/