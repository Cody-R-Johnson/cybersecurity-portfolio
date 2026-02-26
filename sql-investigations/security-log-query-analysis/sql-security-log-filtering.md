# SQL Query Filtering for Security Log Analysis

## Project Overview

This project demonstrates the application of SQL filtering techniques to investigate security-related events within an organization's employee database and authentication logs.

The objective was to use structured SQL queries with filtering operators to identify suspicious login attempts, investigate potential security incidents, and analyze employee access patterns across departments and locations.

This work reflects practical database investigation skills essential for security analysts working with SIEM platforms, log analysis tools, and security information databases.

---

## Environment

- **Database Management System:** MariaDB shell
- **Database:** `organization`
- **Primary Tables:**
  - `log_in_attempts` (authentication logs)
  - `employees` (employee information and department data)

---

## Investigation Objectives

The security team required targeted queries to:

1. Investigate failed login attempts after business hours
2. Identify suspicious login activity on specific dates
3. Filter login attempts originating outside of Mexico
4. Retrieve employee information by department
5. Analyze employee distribution by office location

Each objective required precise SQL filtering using operators such as `WHERE`, `AND`, `OR`, `NOT`, `LIKE`, and wildcard patterns.

---

## SQL Investigation Queries

### 1. Retrieve After-Hours Failed Login Attempts

**Objective:** Identify failed login attempts that occurred after business hours (after 18:00).

**Security Context:** After-hours login failures may indicate unauthorized access attempts or compromised credentials.

**Query:**
```sql
SELECT * 
FROM log_in_attempts 
WHERE login_time > '18:00' AND success = 0;
```

**Filters Applied:**
- `login_time > '18:00'` – Filters for login attempts after 6:00 PM
- `success = 0` – Filters for failed attempts only

**Result:** Returns all failed login attempts outside normal business hours for further investigation.

---

### 2. Retrieve Login Attempts on Specific Dates

**Objective:** Investigate all login activity on 2022-05-09 and the day before (2022-05-08).

**Security Context:** A suspicious event was reported on 2022-05-09, requiring analysis of login patterns on that date and the preceding day to establish a timeline.

**Query:**
```sql
SELECT * 
FROM log_in_attempts 
WHERE login_date = '2022-05-09' OR login_date = '2022-05-08';
```

**Filters Applied:**
- `login_date = '2022-05-09'` – Target date
- `OR login_date = '2022-05-08'` – Preceding date
- `OR` operator used to capture both dates

**Result:** Returns all login activity across two days to identify suspicious patterns.

---

### 3. Retrieve Login Attempts Outside of Mexico

**Objective:** Filter login attempts that did not originate from Mexico.

**Security Context:** The organization detected suspicious activity and needed to focus on login attempts originating outside of Mexico.

**Query:**
```sql
SELECT * 
FROM log_in_attempts 
WHERE NOT country LIKE 'MEX%';
```

**Filters Applied:**
- `NOT` operator excludes results matching the pattern
- `LIKE 'MEX%'` uses wildcard pattern matching
  - `MEX%` matches both 'MEX' and 'MEXICO'
  - `%` wildcard represents any number of characters

**Result:** Returns all login attempts from countries other than Mexico.

---

### 4. Retrieve Employees in Marketing (East Building)

**Objective:** Identify all employees in the Marketing department located in office spaces within the East building.

**Security Context:** Security team needs to update security configurations for all Marketing employees in the East building offices.

**Query:**
```sql
SELECT * 
FROM employees 
WHERE department = 'Marketing' AND office LIKE 'East%';
```

**Filters Applied:**
- `department = 'Marketing'` – Filters for Marketing department
- `office LIKE 'East%'` – Matches any office starting with "East"
  - Includes East-170, East-320, etc.

**Result:** Returns all Marketing employees in East building office locations.

---

### 5. Retrieve Employees in Finance or Sales

**Objective:** Identify employees in the Finance or Sales departments.

**Security Context:** Security team needs to implement updated security policies for Finance and Sales departments.

**Query:**
```sql
SELECT * 
FROM employees 
WHERE department = 'Finance' OR department = 'Sales';
```

**Filters Applied:**
- `department = 'Finance'` – Filters Finance employees
- `OR department = 'Sales'` – Includes Sales employees
- `OR` operator combines both conditions

**Result:** Returns all employees in Finance or Sales departments.

---

### 6. Retrieve All Employees Not in IT

**Objective:** Identify employees who are not part of the Information Technology department.

**Security Context:** Security update applies to all departments except IT.

**Query:**
```sql
SELECT * 
FROM employees 
WHERE NOT department = 'Information Technology';
```

**Filters Applied:**
- `NOT department = 'Information Technology'` – Excludes IT employees

**Result:** Returns all employees outside the IT department.

---

## SQL Operators and Techniques Demonstrated

| Operator/Technique | Purpose | Example Use |
|-------------------|---------|-------------|
| `WHERE` | Filter rows based on conditions | Baseline filtering |
| `AND` | Combine multiple conditions (all must be true) | After-hours AND failed logins |
| `OR` | Match any of multiple conditions | Date range or department filtering |
| `NOT` | Exclude specific conditions | Exclude specific countries or departments |
| `LIKE` | Pattern matching with wildcards | Match country codes, office locations |
| `%` wildcard | Represents any sequence of characters | 'East%', 'MEX%' |
| `>` comparison | Greater than (used for time/date filtering) | login_time > '18:00' |
| `=` comparison | Exact match | department = 'Marketing' |

---

## Security Analysis Use Cases

These SQL filtering techniques support:

- **Incident Response:** Rapidly query logs during active investigations
- **Threat Hunting:** Identify anomalous login patterns
- **Compliance Auditing:** Generate reports on access by department/location
- **Insider Threat Detection:** Monitor after-hours activity
- **Access Control Reviews:** Identify users by role/location for policy enforcement

---

## Skills Demonstrated

- SQL query construction
- Database filtering and pattern matching
- Security log analysis
- Incident investigation methodology
- Logical operator application (`AND`, `OR`, `NOT`)
- Wildcard pattern matching
- Data retrieval for security operations
- Technical documentation

---

## Key Takeaways

SQL remains a foundational skill for security analysts working with structured data sources. The ability to construct precise queries with filtering logic enables:

- Rapid incident triage
- Targeted threat investigation
- Efficient access control reviews
- Data-driven security decision-making

These techniques translate directly to SIEM platforms (Splunk, Sentinel, Chronicle) and database-backed security tools.

---

## Portfolio Note

This project reflects practical SQL investigation skills aligned with security analyst and SOC analyst responsibilities. The queries demonstrate structured thinking, attention to filtering logic, and the ability to translate security requirements into database operations.
