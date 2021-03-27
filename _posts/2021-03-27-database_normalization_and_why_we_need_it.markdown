---
layout: post
title:      "Database normalization and why we need it!"
date:       2021-03-27 06:10:23 +0000
permalink:  database_normalization_and_why_we_need_it
---


Database normalization is the method of arranging the database's attributes to minimize or eradicate data duplication (having the same data in multiple locations).

Data redundancy creates problems. Since the same data is replicated in several locations, data replication increases the database's size unnecessarily. During insert, remove, and upgrade operations, inconsistency issues may arise. To understand these issues, let us take an example of an Employee table.

| EmployeeID 	| Name  	| Department 	| Manager 	| Office_tel 	|
|------------	|-------	|------------	|---------	|------------	|
| 1          	| John  	| HR         	| Ron     	| 12345      	|
| 2          	| Shawn 	| HR         	| Ron     	| 12345      	|
| 3          	| Brad  	| HR         	| Ron     	| 12345      	|


As we can see, the department, manager, and office telephone number are repeated. This repetition of data is called data redundancy. 

**Insertion anomaly**

If we want to insert thousands of employees with the same department and manager, they will eat up extra memory, and there will be redundant data. This is an insertion anomaly.

**Update anomaly**

What will happen if the manager changes? All the records of employees have to be updated. And if we mistakenly miss updating any of the data, then there will be data inconsistency. 

**Deletion anomaly**

If we delete the employees' information, we all also lose all the department and manager information. 


