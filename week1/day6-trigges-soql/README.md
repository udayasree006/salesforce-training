# Day 6 - SOQL, SOSL, DML & Apex Triggers

## 1. What is SOQL?

SOQL (Salesforce Object Query Language) is used to retrieve data from Salesforce objects. It is similar to SQL but designed specifically for Salesforce.

SOQL helps developers:
1. Retrieve Salesforce records
2. Filter data using conditions
3. Access related objects
4. Perform aggregate operations
5. Build dynamic applications

Example:
```sql
SELECT Id, Name FROM Account
```

---

# 2. What is SOSL?

SOSL (Salesforce Object Search Language) is used to search text across multiple Salesforce objects simultaneously.

SOSL is useful when:
- Exact object is unknown
- Searching across multiple records
- Performing keyword-based searches

Example:
```sql
FIND {john} IN ALL FIELDS RETURNING Contact(FirstName, LastName)
```

---

# 3. Difference Between SOQL and SOSL

| SOQL | SOSL |
|------|------|
| Searches one object at a time | Searches multiple objects |
| Similar to SQL SELECT | Similar to text search |
| Returns detailed records | Returns search results |
| Used for structured queries | Used for keyword searches |
| Best for exact data retrieval | Best for global searches |

### Example
- SOQL: Retrieve all Accounts from Hyderabad
- SOSL: Search the keyword “Joseph” across Contacts and Accounts

---

# 4. Efficient Queries

Efficient queries improve Salesforce performance and help avoid governor limits.

## Best Practices
- Use indexed fields
- Avoid wildcard searches
- Use selective WHERE conditions
- Avoid queries inside loops
- Use bulk processing

### Indexed Fields Examples
- Id
- Name
- OwnerId
- CreatedDate
- External ID fields

---

# 5. DML Operations

DML (Data Manipulation Language) is used to modify Salesforce records.

## DML Statements

| Statement | Purpose |
|-----------|---------|
| insert | Add new records |
| update | Modify records |
| upsert | Insert or update |
| delete | Remove records |
| undelete | Restore deleted records |
| merge | Merge records |

### Example
```apex
Account acc = new Account(Name='ABC Company');
insert acc;
```

---

# 6. Apex Triggers

Apex Triggers execute automatically before or after database events.

Triggers are used for:
- Validation
- Automation
- Related record creation
- Preventing invalid operations
- Complex business logic

---

## Trigger Events

| Event |
|------|
| before insert |
| before update |
| before delete |
| after insert |
| after update |
| after delete |
| after undelete |

---

## Example Trigger

```apex
trigger HelloWorldTrigger on Account (before insert) {

    for(Account a : Trigger.new) {

        a.Description = 'New Account Created';
    }
}
```

---

# 7. Bulk Apex Triggers

Bulk triggers process multiple records efficiently.

## Bulkification Best Practices
- Use collections
- Avoid SOQL inside loops
- Avoid DML inside loops
- Use bulk DML operations
- Process Trigger.new records together

---

## Bulk Trigger Example

```apex
trigger ClosedOpportunityTrigger on Opportunity (after insert, after update) {

    List<Task> taskList = new List<Task>();

    for(Opportunity opp : Trigger.new) {

        if(opp.StageName == 'Closed Won') {

            Task t = new Task();

            t.Subject = 'Follow Up Test Task';

            t.WhatId = opp.Id;

            taskList.add(t);
        }
    }

    if(taskList.size() > 0) {

        insert taskList;
    }
}
```

---

# 8. Real Examples Where Triggers Are Used

## Example 1: Follow-Up Task Creation
Automatically create tasks when opportunities are marked Closed Won.

## Example 2: Attendance Management
Update attendance records automatically after student updates.

## Example 3: Fee Reminder System
Send reminders when fee payment due dates are near.

## Example 4: Placement Eligibility
Check student CGPA and attendance before placement registration.

---

# 9. Pseudocode Examples

## Example 1: Opportunity Follow-Up

```text
START
Check opportunity stage
IF stage = Closed Won
   Create follow-up task
END
```

---

## Example 2: Attendance Validation

```text
START
Calculate attendance percentage
IF percentage < 75
   Mark student detained
ELSE
   Mark student eligible
END
```

---

## Example 3: Fee Payment Reminder

```text
START
Check fee due date
IF payment pending
   Send reminder
ELSE
   Update status
END
```

---

# 10. Reflection

SOQL, SOSL, DML, and Apex Triggers are important components of Salesforce development.

They help developers:
- Retrieve and manage data efficiently
- Automate business processes
- Build scalable enterprise applications
- Handle large data volumes
- Implement advanced logic and integrations

Bulkified triggers improve performance and ensure applications work efficiently within Salesforce governor limits.

---

# Conclusion

Salesforce development combines querying, automation, and programming to build powerful enterprise solutions. SOQL and SOSL help retrieve information, DML manages records, and Apex Triggers automate complex business operations efficiently.

---

# Screenshots

<img width="1919" height="934" alt="Screenshot 2026-05-14 145840" src="https://github.com/user-attachments/assets/70a2392c-ca48-4397-ac33-52ce36d3fc60" />
<img width="1919" height="909" alt="Screenshot 2026-05-14 144150" src="https://github.com/user-attachments/assets/9854f5c4-5173-4bcf-b03a-bf226857fb45" />
