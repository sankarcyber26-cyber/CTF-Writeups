# SQL Injection

## Platform
PortSwigger Web Security Academy

## Status
Core SQL Injection practicals completed.

## Topics Practised

- SQL Injection basics
- Authentication bypass
- UNION-based SQL Injection
- Database version identification
- Table enumeration
- Column enumeration
- Database content retrieval
- Oracle-specific SQL Injection
- MySQL-specific SQL Injection

## Methodology

1. Identify the user-controlled input.
2. Test whether the input affects the SQL query.
3. Determine the UNION column count.
4. Identify reflected columns.
5. Identify the database type.
6. Enumerate tables when required.
7. Enumerate columns when required.
8. Retrieve relevant data in the authorized lab.
9. Validate the impact.
10. Document the result and remediation.

## Labs Completed

1. Retrieve Hidden Data
2. Login Bypass
3. Querying Oracle Database Version
4. Querying MySQL Database Version
5. Database Contents Enumeration
6. Oracle Database Contents Enumeration

## Key Learning

The main focus was understanding the SQL Injection methodology
instead of memorising individual payloads.

## Impact

SQL Injection can allow attackers to alter database queries,
bypass authentication, or access data that should not be exposed.

## Remediation

- Use parameterized queries / prepared statements.
- Avoid concatenating untrusted input into SQL queries.
- Apply appropriate server-side validation.
- Use least-privileged database accounts.
- Avoid exposing detailed database errors.

## Safety

All practical testing was performed in authorized training labs.
Sensitive credentials, session tokens, and other secrets are not published.
