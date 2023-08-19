### WORKING WITH ENVIROMENT VARIABLES

1. Exclude apostrophes when defining string values,they will be placed automatically when the varibale is needed
2. KEY must always be writtend in capital letters underscore separated if need be.
3. Import dotenv in the root route... After this we do not need to import it again as it will already have served its purpose of loading the enviroment variables into the process.env object. This is only done locally hence using the following code
   `if (process.env.NODE_ENV !== "production") { require("dotenv").config();}`

### TROUBLESHOOTING CONNECTION STATUS

- Connections tests are vital while debugging server crushes, They also report on server status,database connection and availability.

```js
const db = mongoose.connection;

db.on("open", function (ref) {
  connected = true;
});

db.on("connected", function (ref) {
  connected = true;
});

db.on("disconnected", function (ref) {
  connected = false;
});

db.on("close", function (ref) {
  connected = false;
});

db.on("error", function (err) {
  connected = false;
  if (err.code == "ESERVFAIL") {
  } else {
  }
});

db.on("reconnect", function (ref) {
  connected = true;
});
```


