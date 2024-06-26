# In-Depth Exploration of Mongodb Queries

## MongoDB Compass
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
- **_projection()_** method only works with **_find()_** method. To use field filtering with **_findOne()_** method we need to use the first filtering method.
- All data or query parameter must be in **_JSON_** format
- MongoDB Operators
    - **_Whenever we use an operator an extra bracket is used_** ```{<field>: {$eq: <value>}}```
    - Operators
        - $eq --> Equal
        - $ne --> Not equal
        - $gt --> Grater than
        - $gte --> Grater than equal
        - $lt --> Less than
        - $lte --> Less than equal
        - $in --> give all matching data matching in an array
        - $nin --> give all un-matching data matching in an array
- **_sort()_** method is used to sort search results
    - **_sort(<field>: 1)_** --> _field: on which field the sort will apply_ and _1: ascending order_
- To combine multiple condition, use comma (,) between two condition inside operator curly bracket **{}**
    - implicit AND
    - ```db.test.find({gender: "Female", age: { $gte: 18, $lte: 30 }}).sort({age: 1})```
    - ```tsx
        db.test.find(
    {
        gender: "Female",
        age: { $nin: [18, 20, 22, 24, 26, 28, 30] },
        interests: {$in: ["Cooking", "Gaming"]}
    }, {age: 1, gender: 1, interests: 1})
    .sort({age: 1})
    ```
