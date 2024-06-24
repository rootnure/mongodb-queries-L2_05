# In-Depth Exploration of Mongodb Queries

- MongoDB Compass
    - query in cli
        - ```show dbs``` to view all database directory in MongoDB Compass
        - ```use <db_directory>``` to use an database directory or create a new one if db_directory doesn't exists
        - ```db.createCollection("db_collection_name")``` to create a database collection within a db_directory
        - ```db.getCollection("db_collection_name").insertOne( <data_to_insert> )``` insert a single data to db_collection
        - ```db.getCollection("db_collection_name").insertMany( <data1_to_insert>, <data2_to_insert>, ... , <data999_to_insert )``` insert many data at once to db_collection
        - ```db.getCollection("db_collection_name").find( <field_to_find> )``` get all matching data from db_collection
        - ```db.getCollection("db_collection_name").findOne( <field_to_find> )``` get the first matching data from db_collection
    - Field filtering
        - ```db.getCollection("db_collection_name").find( <field_to_find>, <only_needed_field> )``` get all matching data from db_collection with limited field(s)
        - ```db.getCollection("db_collection_name").find( <field_to_find> ).project( <only_needed_field> )``` get all matching data from db_collection with limited field(s)
        - ```db.getCollection("db_collection_name").find( <field_to_find>, <only_needed_field> )``` get all matching data from db_collection with limited field(s)
        - **_projection()_** method only works with **_find()_** method. Field filtering using **_project()_** method cannot be used with **_findOne()_** method
    - all data or query parameter must be in **_JSON_** format
