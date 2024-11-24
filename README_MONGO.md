``` javascript

// 1. Switch to the database MCA2022 (it will be created if it doesn't exist)
use MCA2022

// 2. Insert documents into the Employee collection
// Insert a single document
db.Employee.insertOne({
    emp_id: 101,
    emp_fname: "John",
    emp_lname: "Doe",
    dept: "IT",
    sal: 50000
})

// Insert multiple documents
db.Employee.insertMany([
    { emp_id: 102, emp_fname: "Jane", emp_lname: "Smith", dept: "HR", sal: 60000 },
    { emp_id: 103, emp_fname: "Mike", emp_lname: "Brown", dept: "Finance", sal: 45000 },
    { emp_id: 104, emp_fname: "Susan", emp_lname: "Lee", dept: "IT", sal: 70000 }
])

// 3. Insert documents into the Customer collection
// Insert a single document
db.Customer.insertOne({
    cust_id: 201,
    cust_fname: "Alice",
    cust_lname: "Johnson",
    contact_no: "1234567890",
    address: "New York"
})

// Insert multiple documents
db.Customer.insertMany([
    { cust_id: 202, cust_fname: "Bob", cust_lname: "Williams", contact_no: "0987654321", address: "San Francisco" },
    { cust_id: 203, cust_fname: "Charlie", cust_lname: "Brown", contact_no: "1122334455", address: "Chicago" }
])

// 4. Find an employee by ID (e.g., emp_id: 102)
db.Employee.find({ emp_id: 102 })

// 5. Find a customer by ID (e.g., cust_id: 201)
db.Customer.find({ cust_id: 201 })

// 6. Update the salary of an employee (e.g., emp_id: 103)
db.Employee.updateOne(
    { emp_id: 103 },               // Find employee with emp_id = 103
    { $set: { sal: 48000 } }       // Set the new salary to 48000
)

// 7. Delete a customer document (e.g., cust_id: 203)
db.Customer.deleteOne({ cust_id: 203 })

// 8. Create an index on the 'sal' field in the Employee collection
db.Employee.createIndex({ sal: 1 })

// 9. Get a list of indexes in the Employee collection
db.Employee.getIndexes()

// 10. Drop the index on the 'sal' field
db.Employee.dropIndex("sal_1")

// 11. Sort employees by salary in descending order
db.Employee.find().sort({ sal: -1 })


```
