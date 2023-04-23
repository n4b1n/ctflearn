## Basic Injection

See if you can leak the whole database using what you know about SQL Injections.

---

### SQL Injection
SQL Injection is a type of security exploit in which an attacker adds malicious SQL code to a web form input box to gain access to resources or make changes to data.

on this challenge, the webapp was accepting user inputs without sanitizing. When we input data and click on submit, the following SQL query was being executed:
	
	SELECT * FROM webfour.webfour where name = '$input'
	
as you can see the $input is directly added to the sql query without sanitizing.

if we input 'sam':
	
	SELECT * FROM webfour.webfour where name = 'sam'
	
this will show the data related to user sam.
	
we can add ' to the end of our input to close the string and add our payload after that:
		`sam' or '1' = '1`
		
the following sql query will be called to end: 
	
	SELECT * FROM webfour.webfour where name = 'sam' or '1' = '1'
	
this will output all data of other users too. because 1=1 is always true.
	
learn more about sql here: 
[portswigger](https://portswigger.net/web-security/sql-injection)
[owasp](https://owasp.org/www-community/attacks/SQL_Injection)
[wikipedia](https://en.wikipedia.org/wiki/SQL_injection)

Solved: 2023-04-23