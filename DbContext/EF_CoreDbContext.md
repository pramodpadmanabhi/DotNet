Entity Framework Core DB-Context 

* DbContext - Represents a session with a database and provides API For Comunnaticating with database and provides capabilities

  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  
  * Capabilities
  
        1) Database Connections -> Opening and Maintaining Connections to the database
        2) Database Opertations -> Adding,Modifying,Deleting
        3) Change Tracking -> Detects change made to an entity and sets the EntityState of on objects.The Type of operation depends on the EntityState Value
        4) Model Building -> Responsible for setting up Conceptual Model and maps to the Database
        5) Data Mapping -> Includes Data Mapper Layer,mapping the results of SQL Queries to Entity Instances
        6) Object Caching -> When the DbContext SaveChanges method is called, a transaction is created and all pending changes are wrapped in it as a single unit of work. 
                             If an error occurs when the changes are applied to the database, they are rolled back and the database is left in an unmodified condition.
                             
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  
  * Adding Data via DbContext
  
        1) Add<TEntity>(TEntity entity)
        2) Add(object entity)
        3) AddRange(IEnumerable<objects> entities)
        4) AddRange(params object[] entities)
        5) AddAsync( args same 3rd or 4th)
        
  * Updating Data via DbContext
  
        -> Depends on whether the context is currently tracking the entity being modified or not
        -> The below Examples does not need _context.update() as author entity is already being tracked by EF_Core and changes the ENTITYSTATE to MODIFIED
          /*
              var author=_context.Authors.Find(author=>author.ID==ID);
              author.name="Pramod";
              _context.SaveChanges()  // generates update Statement
          */
        
        -> Disconnected Scenario - Entity properties are done in controller/client
           /*
              _context.Entry(author).State = EntityState.Modified;
              _context.SaveChanges();
           */ 
           
        -> DBContext Update updates automatically Changes the ENTITYSTATE to Modified if Primary key is provided, if primary key is absent 
            it is treated as insert statement and ENTITYSTATE is Added
            /*
                _context.Update(author) or _contex.UpdateRange(authors)
                _context.SaveChanges()
            /*
         
         ->DBContext Attach State sets Unchanged State if key value is not present and Added State if if key value is present,with this we can update specific property 
            so that Database Commands can be generated for that
              /*
                    var autor = new Author{
                      AuthorId=1,
                      FirstName="Pramod",
                      LastName="Padmanabhi"
                    }
                    _context.Attach(author);
                    _context.Entry(author).Property("FirstName").IsModified = true;
                    _context.SaveChanges();
              */
              
              
              
  # Change Tracker
    
  ##### Change Tracker records current state of an entity using Four Values
  * Added
  * Unchanged
  * Modified
  * Deleted
         
        


  
