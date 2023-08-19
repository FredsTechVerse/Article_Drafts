#### MONGODB

- Cluster - Several servers connected together to manage your database(s)... Yea thats right.A cluster can have multiple databases.
- Database - Simply a container for storing data usually in collections which are managed using a database management systems.
- Externalizing file storage is a good and cost effective practise as the two can scale independently.
- For my usecase , having all my projects in one cluster will be cost effective and simple to manage.

#### MONGOOSE OPERATORS

A way for us to interact with our data stored in a bucket , the database.

- Enables us to conveniently issue instructions to the db in a precise yet shorter way.
- This operators are used as key value pairs where the key is the operator and the value is the value to be used in the operation. eg `Inventory.find({"quantity": { $gt: 5000}})`
- Not to forget that the operator is preceded by a dollar sign.
- They will go a long away in aiding in precision query. Eg the pull operator manipulates the database directly while removing token.
- Be careful with the order of the operator and key!
- **_Cluster_** Its simply a group of computers that can host serveral database(s) with a limit to not the no of databases it can hold but the total number collections and space that they can take up!
