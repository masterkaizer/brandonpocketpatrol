##  Brandon  j sellam packet cops
### here some explanations
1. public/index.html - lading page fr you app
   In this file, we are loading the index.js and db.js
    Also, we are checking for service worker script (service-worker.js)

2. public/service-worker.js - 
   This will serve the service worker functionality like install, activate service worker, etc
3. index.js - main frontend script file where we will have all frontend 
            code logic like 
                 add/delete a transaction
                 here one request will go to server (http://localhost:3000/api/transaction)
                 if we can connect to the server, then it will save data in MongoDB
                 if we r unable to connect to the server, then data will be stored as offline .below  code will serve the purpose.
                 (// fetch failed, so save in indexed DB
                 saveRecord(transaction);)
4. db.js - This file is used to check if we are back online so that all offline data will be pushed to MongoDB.

   // listen for app coming back online
   window.addEventListener("online", checkDatabase);

Backend code(Node.js)

server.js  - main start with a file where we will import all dependency modules.
             DB connection setup
             load model
             configure routes
router/api.js - here, we have two post API, and one gets API handlers to save the data and get the data from the transaction collection object.
models/transaction.js - our collection object schema where we will store the budget transactions.
