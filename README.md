# Code First Migrations
Open PackageManger and run the following commands to create and update database objects.
```bash
add-migration InitalSchema
add-migration MoreStuff
add-migration MoreStuff -force (to overwrite last migration)

update-database (apply migrations to current version)
```

## Seeding the database
Create a new empty migration and add code to populate tables.  Run update-database to aply the migration:
```bash
public override void Up()
{
    Sql("INSERT INTO MEmbershipTypes (...) VALUES (..)");
}
        
public override void Down()
{
    Sql("DELETE MembershipTypes");
}
```

# LINQ Extention Mehods
Method for querying a simple item or list of items:
```csharp
var movies = _context.Movies.Where(m => m.GenreId == 1);
var movie = _context.Movies.Single(m => m.Id == 1);
var movie = _context.Movies.SingleOrDefaultItem( m => m.Id == 1);
var movies = _context.Movies.ToList();
```
# Eager Loading
To load derived classes referenced in the intial entity.
```csharp
var movies = _context.Movies.Include(m => m.Genre);
```

# Restart Migrations
To reset from beginning (new database), perform the following steps:
1. Save data population migration scripts or other manual scripts
2. Delete the Migrations folder
3. Rebuild Solution
4. Clean Solution
5. Run the following command from the Package Manager console
```bash
Enable-Migrations
Add-Migration Initial
Update-Database
```
6. Restore and run population migrations
