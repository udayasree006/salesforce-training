Day 5 – Introduction to Apex and Database Operations
Overview

Today’s learning focused on understanding Apex programming in Salesforce and how it is used to build custom business logic, automate operations, and interact with Salesforce databases using SOQL and SOSL queries.

1. Introduction to Apex
What is Apex?

Apex is a strongly typed, object-oriented programming language developed by Salesforce. It runs directly on the Salesforce Platform and is mainly used to implement custom backend logic and automation.

Apex allows developers to:

Create custom business processes
Perform database operations
Automate tasks
Build integrations with external applications
Handle complex validations and calculations
Basic Apex Example
Account acc = new Account(Name='ABC Technologies');
insert acc;

The above code creates a new Account record and inserts it into Salesforce.

2. Key Concepts Learned
DML Operations

DML (Data Manipulation Language) operations are used in Apex to interact with Salesforce records.

Common DML Statements
Operation	Purpose
insert	Adds new records
update	Modifies existing records
delete	Removes records
upsert	Inserts or updates records
undelete	Restores deleted records
Example
Contact con = new Contact(
    FirstName='John',
    LastName='Smith'
);

insert con;
3. SOQL (Salesforce Object Query Language)

SOQL is used to retrieve records from Salesforce objects.

Example Query
List<Account> accList =
[
    SELECT Id, Name
    FROM Account
];

This query retrieves Account IDs and Names from Salesforce.

Filtering Records
SELECT Name
FROM Contact
WHERE LastName='Smith'

This query returns contacts whose last name is Smith.

4. SOSL (Salesforce Object Search Language)

SOSL is used to search text across multiple Salesforce objects.

Example
FIND 'Smith'
IN ALL FIELDS
RETURNING Contact(Name), Lead(Name)

This searches for the word “Smith” across Contact and Lead records.

5. Difference Between SOQL and SOSL
SOQL	SOSL
Searches one object at a time	Searches multiple objects
Used to retrieve records	Used for text searching
Similar to SQL	Similar to search engines
Exact matches	Keyword-based matches
6. Flow vs Apex
Flow	Apex
No-code/Low-code automation	Programming language
Drag-and-drop builder	Requires coding
Best for simple automation	Best for advanced logic
Faster development	More customization
Limited flexibility	Highly scalable
7. Configuration vs Coding
Configuration	Coding
Uses clicks instead of code	Uses programming logic
Easier to maintain	Requires developer skills
Suitable for standard tasks	Suitable for complex requirements
Faster implementation	More flexibility
8. Real-Time Use Cases of Apex
Student Attendance System

Apex can calculate attendance percentages automatically and identify students below the required attendance criteria.

Fee Management Automation

Apex can:

Check due dates
Send automatic reminders
Update payment status
Placement Eligibility Processing

Apex can evaluate:

CGPA
Attendance
Skills

and determine placement eligibility automatically.

9. Integrated College Management System Design
CRM Usage

Salesforce CRM can manage:

Students
Faculty
Courses
Attendance
Fees
Placements
Objects Used
Standard Objects
Account
Contact
Custom Objects
Student__c
Course__c
Attendance__c
Fee__c
Placement__c
10. Relationships Between Objects
Parent Object	Relationship	Child Object
Student	Enrolled In	Course
Student	Has	Attendance
Student	Pays	Fee
Student	Gets	Placement
11. Validation Rules

Validation rules help maintain accurate data.

Examples
Student ID should not be empty
Attendance percentage cannot exceed 100
Fee amount must be greater than zero
Phone numbers must contain valid digits
12. Flow Automation Examples

Flows can automate:

Admission confirmation emails
Fee reminders
Attendance updates
Leave approval processes
13. Apex Use Cases

Apex is preferred when:

Complex calculations are required
Large data processing is needed
External system integrations are involved
Advanced automation is required
14. Pseudocode Examples
Attendance Calculation
START
Input total classes
Input attended classes
Calculate attendance percentage

IF percentage < 75
   Mark as detained
ELSE
   Mark as eligible
END
Fee Reminder Process
START
Check payment due date

IF payment pending
   Send reminder email
ELSE
   Update status
END
Placement Eligibility
START
Check CGPA
Check attendance

IF CGPA > 7 AND attendance > 75
   Eligible for placement
ELSE
   Not eligible
END
15. Challenges Faced and Solution

During SOSL implementation, a DML exception occurred because an existing Flow named:

“Check New Lead for Matching Account”

was failing while creating Lead records.

Error
CANNOT_EXECUTE_FLOW_TRIGGER
Probably Limit Exceeded or 0 recipients
Solution

The issue was resolved by temporarily deactivating the failing Flow from:

Setup → Flows → Check New Lead for Matching Account → Deactivate

After deactivating the Flow, the Apex challenge executed successfully.

16. Reflection

Today’s session provided practical understanding of how Salesforce handles:

Data operations using Apex
Database querying using SOQL
Text searching using SOSL
Automation through Flows
Backend business logic implementation

I understood how Apex becomes essential when business requirements become more advanced and cannot be handled only through declarative tools.

Conclusion

Apex is a powerful backend programming language in Salesforce that enables developers to build scalable enterprise applications, automate complex business processes, and integrate Salesforce with external systems efficiently.

The combination of Apex, SOQL, SOSL, Flows, and CRM architecture provides a complete ecosystem for enterprise application development.

screenshots:
<img width="1906" height="919" alt="Screenshot 2026-05-13 183149" src="https://github.com/user-attachments/assets/c6328e2e-ec07-4102-9892-13c672658751" />
<img width="1919" height="921" alt="Screenshot 2026-05-13 183221" src="https://github.com/user-attachments/assets/bfebde72-9101-4bd9-8152-cc79e0a3d691" />
