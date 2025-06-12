EF Core is powerful, but it doesn’t protect you from common mistakes. And I see these all the time:  
  
- Calling ToList() too early and breaking query composition  
- Not using AsNoTracking() for read-heavy scenarios  
- Lazy loading inside loops, causing N+1 problems  
- Using Include() everywhere, even when not needed  
- Not projecting only the required columns with Select()  
- Registering DbContext as Singleton (don't do this)  
- Missing indexes in the database  
- Not reviewing the generated SQL  
- Treating EF Core like an ORM black box
