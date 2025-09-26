# SQL-Job-Market-Analysis
This project analyzes job postings data using **SQL** to uncover insights about in-demand skills, salaries, and top companies.   It demonstrates how SQL can be applied to **real-world data** for decision-making and is part of my data analytics portfolio.

Company (company_id, company_name, industry, location)
Job_Posting (job_id, company_id, job_title, job_type, salary, posted_date)
Skill (skill_id, skill_name)
Job_Skill (job_id, skill_id)  -- bridge table for many-to-many relation
Applicant (applicant_id, name, applied_job_id, application_date)


erDiagram
    COMPANY ||--o{ JOB_POSTING : offers
    JOB_POSTING ||--o{ JOB_SKILL : requires
    SKILL ||--o{ JOB_SKILL : maps
    JOB_POSTING ||--o{ APPLICANT : applied_for

    COMPANY {
        int company_id PK
        string company_name
        string industry
        string location
    }

    JOB_POSTING {
        int job_id PK
        int company_id FK
        string job_title
        string job_type
        real salary
        date posted_date
    }

    SKILL {
        int skill_id PK
        string skill_name
    }

    JOB_SKILL {
        int job_id FK
        int skill_id FK
    }

    APPLICANT {
        int applicant_id PK
        string name
        int applied_job_id FK
        date application_date
    }
| job_id | job_title                 | job_type  | salary | company  |
| ------ | ------------------------- | --------- | ------ | -------- |
| 1      | Data Analyst              | Full-time | 250000 | DataTech |
| 2      | Machine Learning Engineer | Full-time | 400000 | DataTech |
| 6      | Financial Analyst         | Remote    | 300000 | FinServe |
```
SELECT c.industry, COUNT(*) AS job_count
FROM company c
JOIN job_posting j ON c.company_id = j.company_id
GROUP BY c.industry
ORDER BY job_count DESC;
