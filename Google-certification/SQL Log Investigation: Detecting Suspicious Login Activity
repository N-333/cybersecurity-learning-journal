SQL Log Investigation: Detecting Suspicious Login Activity
Project Overview

This project demonstrates how SQL can be used to analyze authentication logs and employee records in order to identify potential security threats. By querying a MariaDB database containing login activity and employee information, suspicious login patterns such as failed attempts after business hours, unusual login dates, and foreign login sources were investigated.

The objective of this project was to simulate how a Security Analyst or SOC Analyst might use SQL queries to investigate suspicious activity within an organization's system logs.

Scenario

The organization's security team noticed unusual login behavior and requested an investigation of authentication logs stored in a database. The goals of the investigation were to:

Identify failed login attempts after business hours

Investigate login activity during suspicious dates

Detect login attempts originating outside Mexico

Retrieve employee information for system update operations

SQL queries were used to filter and analyze relevant data from the database.

Tools and Technologies

MariaDB

SQL

Database log analysis

Command Line Interface

Database Tables Used
1. log_in_attempts

Contains authentication log records.

Important columns:

login_time

login_date

country

success

2. employees

Contains employee and department information.

Important columns:

username

department

office

Investigation Steps
1. Identify Failed Login Attempts After Business Hours

Business hours end at 18:00. Failed login attempts occurring after this time may indicate brute-force attacks or unauthorized access attempts.

SQL Query
SELECT *
FROM log_in_attempts
WHERE login_time > '18:00' AND success = 0;
Result

39 failed login attempts occurred after business hours.

Security Insight

Multiple failed logins after office hours may indicate:

Brute force password attempts

Credential stuffing

Unauthorized access attempts during low monitoring periods

2. Investigate Login Attempts on Suspicious Dates

The security team requested investigation of login activity on May 8 and May 9, 2022.

SQL Query
SELECT *
FROM log_in_attempts
WHERE login_date = '2022-05-08' OR login_date = '2022-05-09';
Result

75 login attempts occurred during this time window.

Security Insight

Concentrated login activity within a short time frame could indicate:

Coordinated login attempts

Credential testing

Suspicious access attempts targeting specific accounts

3. Identify Login Attempts Originating Outside Mexico

To detect foreign access attempts, login records not originating from Mexico were filtered.

SQL Query
SELECT *
FROM log_in_attempts
WHERE NOT country LIKE 'MEX%';
Result

144 login attempts originated outside Mexico.

Security Insight

Foreign login attempts may indicate:

Compromised accounts

Unauthorized remote access

VPN usage masking true attacker location

4. Retrieve Marketing Department Employees in East Offices

The IT team required employee information to update machines belonging to Marketing department staff located in the East building.

SQL Query
SELECT *
FROM employees
WHERE department = 'Marketing' AND office LIKE 'East%';
Result

The first employee returned by the query was jclark.

5. Retrieve Employees in Finance or Sales Departments

A system update was required for employees in both Finance and Sales departments.

SQL Query
SELECT *
FROM employees
WHERE department = 'Finance' OR department = 'Sales';
Result

The first Sales department employee returned was sgilmore.

6. Identify Employees Not in the IT Department

Updates had already been applied to Information Technology department machines. Employees outside this department needed to be identified.

SQL Query
SELECT *
FROM employees
WHERE NOT department = 'Information Technology';
Result

161 employees were identified outside the IT department.

Key Findings

The investigation revealed several notable patterns:

39 failed login attempts occurred after business hours.

75 login attempts occurred during the suspicious date range.

144 login attempts originated outside Mexico.

These patterns may indicate:

Potential brute force login attempts

Unusual authentication behavior

Possible foreign access attempts

Further investigation with additional monitoring tools or SIEM systems would be recommended.

Skills Demonstrated

This project demonstrates the following cybersecurity and technical skills:

SQL query development

Log analysis

Authentication log investigation

Security data filtering

Pattern detection in login activity

Database investigation techniques

Conclusion

This project demonstrated how SQL can be used to analyze authentication logs and employee records during a security investigation. By applying logical operators such as AND, OR, and NOT, relevant security events were identified within the database.

These techniques are commonly used by Security Analysts and SOC teams when investigating suspicious activity within large datasets of authentication logs.
