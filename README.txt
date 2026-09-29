# MongoDB Interview Practice Dataset

Collections:
- users: 50
- products: 30
- orders: 120
- reviews: 120
- departments: 6
- employees: 40

Recommended database name:
mongodb_interview

Import with MongoDB Compass:
1. Create/select database `mongodb_interview`.
2. Create each collection.
3. Import the corresponding JSON file as JSON Array.

Or with mongoimport:
mongoimport --uri "<YOUR_URI>" --db mongodb_interview --collection users --file users.json --jsonArray
(and similarly for the other files)

Relationships:
- orders.userId -> users._id
- orders.items[].productId -> products._id
- reviews.userId -> users._id
- reviews.productId -> products._id
- products.supplierId is an integer supplier reference (no supplier collection intentionally; some questions ask you to work around this)
- employees.departmentId -> departments._id
- employees.managerId -> employees._id (self-reference)

Dates are ISO strings in the JSON files. If imported as strings, you can still use string comparisons for ISO timestamps, but for date operators such as $dateDiff/$dateSubtract it is better to convert them to Date in your imported collection or change the fields to BSON Date using Compass/import options.
