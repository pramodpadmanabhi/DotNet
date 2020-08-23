Entity Framework Fluent API is used to configure domain classes to override conventions. 
EF Fluent API is based on a Fluent API design pattern (a.k.a Fluent Interface) 
where the result is formulated by method chaining.

In Entity Framework Core, the ModelBuilder class acts as a Fluent API. 
By using it, we can configure many different things, as it provides more configuration
 options than data annotation attributes.

 Entity Framework Core Fluent API configures the following aspects of a model:

Model Configuration: Configures an EF model to database mappings. Configures the default Schema, DB functions, additional data annotation attributes and entities to be excluded from mapping.
Entity Configuration: Configures entity to table and relationships mapping e.g. PrimaryKey, AlternateKey, Index, table name, one-to-one, one-to-many, many-to-many relationships etc.
Property Configuration: Configures property to column mapping e.g. column name, default value, nullability, Foreignkey, data type, concurrency column etc.