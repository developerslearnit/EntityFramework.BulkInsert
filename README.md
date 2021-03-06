# EntityFramework.BulkInsert
Updated port of EntityFramework.BulkInsert from the original version on the Codeplex site. This is not my original project, this is to keep it going and add minor updates and support.  The original was hosted on Codeplex but later taken down.  Since then the project has seen support for async IO, bug fixes, explicit transaction support and support for MySql.

# NuGet
There are several NuGet packages available:
* EntityFramework6.BulkInsert [![NuGet](https://img.shields.io/nuget/v/EntityFramework6.BulkInsert.svg?style=flat-square&label=nuget)](https://www.nuget.org/packages/EntityFramework6.BulkInsert/)

* EntityFramework6.BulkInsert.SqlServerCe [![NuGet](https://img.shields.io/nuget/v/EntityFramework6.BulkInsert.SqlServerCe.svg?style=flat-square&label=nuget)](https://www.nuget.org/packages/EntityFramework6.BulkInsert.SqlServerCe/)

* EntityFramework6.BulkInsert.MySql [![NuGet](https://img.shields.io/nuget/v/EntityFramework6.BulkInsert.MySql.svg?style=flat-square&label=nuget)](https://www.nuget.org/packages/EntityFramework6.BulkInsert.MySql/)

# Purpose
The purpose of this library is for performing Bulk Inserts using EntityFramework 6 and your existing `DbContext` instance to perform faster inserts instead of generating multiple insert statements for a collection of strongly typed objects.

# Usage

```cs
IEnumerable<Car> cars = GenerateCars();

using (var context = GetDbContext())
{
    context.BulkInsert<Car>(cars);
}
```

Async IO support is also built in:

```cs
IEnumerable<Car> cars = GenerateCars();

using (var context = GetDbContext())
{
    await context.BulkInsertAsync<Car>(cars);
}
```

This library supports Explicit and Implicit transactions either using `IDbTransaction` or `TransactionScope`

# Building
To build/compile clone this repository and build:

```
git clone https://github.com/ghost1face/EntityFramework.BulkInsert.git
```
