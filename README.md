# Job Market Insights SQL Project  

## 📌 Project Overview  
This project explores **job market dynamics** using SQL.  
We simulate a relational database containing companies, job postings, required skills, and applicants.  
Through structured SQL queries, we uncover insights about **industries, skills demand, salaries, and applicant behavior**.  

The project is designed as a **portfolio-ready case study** to showcase SQL proficiency, data analysis, and database design.  

---

## 🗂️ Database Schema  

The database consists of **5 tables**:  

- **Company** → Information about employers (industry, location).  
- **Job_Posting** → Job details (title, type, salary, posting date).  
- **Skill** → Core skills (SQL, Python, etc.).  
- **Job_Skill** → Bridge table mapping jobs to required skills.  
- **Applicant** → Candidates applying for jobs.  

📊 **Entity Relationship Diagram (ERD):**  

```mermaid
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
```
