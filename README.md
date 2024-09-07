# BUILDING AN HNG HIRE DATA MODEL AND HIRING STATISTICS DASHBOARD

## Table of contents

- [About](#about)
- [Project Overview](#project-overview)
- [Business Requirements](#business-requirements)
- [Data Model Design](#data-model-design)
- [Data Loading](#data-loading)
- [Links](#links)
- [Key Insights](#key-insights)
- [Acknowledgements](#acknowledgements)


## About 
The project involves creating a data model for [HNG Hire](https://hng.tech/hire-talents), implementing it in MySQL, and building a [Power BI dashboard](https://github.com/mchenryspagg/hng-hire-data-model/blob/main/HNG%20HIRE%20DASHBOARD.pbix) to display hiring statistics.


## Project Overview
Prepare a data model for HNG Hire, implement it in MySQL, and then build a dashboard that shows hiring statistics. Show available people per stack, those in interviews, those who are hired, etc. Think through all the things that should be tracked for the model. Write some useful filters on the data.


## Business Requirements
[HNG Hire](https://hng.tech/hire-talents) aims to match talent with opportunities by helping employers find the right candidates for their roles. For this project, we need to track:
- **Candidates**: Basic details, technology stacks, status in the hiring process (available, in interview, hired, etc.)
- **Hiring Process**: Details about interviews, offers, rejections, etc.
- **Employers**: Information about companies that are hiring, the roles they are offering, etc.


## Data Model Design
 A Multi-Dimensional data model (star schema) was utilized in designing the HNG hire data model, with a hiring fact table and seven dimension tables (candidates, employers, job roles, stack, status, location, date).


### Fact Table:

**hiring**
| Column Name | Data Type | Description |
| ---------- | --------- | ----------- |
| hiring_id | Integer | Primary key |
| candidate_id | Integer | Foreign key to candidates |
| employer_id | Integer | Foreign key to employers |
| job_role_id | Integer | Foreign key to job roles |
| stack_id | Integer | Foreign key to stack |
| status_id | Integer | Foreign key to status |
| date_id | Integer | Foreign key to date |
| location_id | Integer | Foreign key to location |
| interview_score | Float | Interview score |
| years_of_experience | Integer | Years of experience of the candidate |

### Dimension Tables:

**candidates**
| Column Name | Data Type | Description |
| ---------- | --------- | ----------- |
| candidate_id | Integer | Primary key |
| full_name | Varchar | Candidate's full name |
| email | Varchar | Candidate's email address |
| phone_number | Varchar | Candidate's phone number |
| github_profile | Varchar | Candidate's GitHub profile URL |
| linkedin_profile | Varchar | Candidate's LinkedIn profile URL |
| experience_level | Varchar | Candidate's experience level (Junior, Mid, Senior, etc.) |

**employers**
| Column Name | Data Type | Description |
| ---------- | --------- | ----------- |
| employer_id | Integer | Primary key |
| company_name | Varchar | Name of the hiring company |
| industry | Varchar | Industry of the company |
| location | Varchar | Location of the company |

**job_roles**
| Column Name | Data Type | Description |
| ---------- | --------- | ----------- |
| job_role_id | Integer | Primary key |
| job_title | Varchar | Title of the job role (e.g., Data Analyst, Frontend Developer) |
| description | Text | Description of the job role |

**stack**
| Column Name | Data Type | Description |
| ---------- | --------- | ----------- |
| stack_id | Integer | Primary key |
| stack_name | Varchar | Name of the technology stack (Frontend, Backend, Mobile, etc.) |

**status**
| Column Name | Data Type | Description |
| ---------- | --------- | ----------- |
| status_id | Integer | Primary key |
| status_name | Varchar | Name of the status (Available, In Interview, Hired, Rejected) |

**location**
| Column Name | Data Type | Description |
| ---------- | --------- | ----------- |
| location_id | Integer | Primary key |
| country | Varchar | Country of the location |
| city | Varchar | City of the location |

**date**
| Column Name | Data Type | Description |
| ---------- | --------- | ----------- |
| date_id | Integer | Primary key |
| full_date | Date | Complete date (YYYY-MM-DD) |
| year | Integer | Year of the date |
| month | Integer | Month of the date |
| day | Integer | Day of the month |
| quarter | Integer | Quarter of the year |
| is_weekend | Boolean | Indicates if the date is a weekend |
| interview_date | Date | Date of the interview (if applicable) |
| hiring_date | Date | Date of hiring (if applicable) |


![image](https://github.com/user-attachments/assets/3bca7eb6-8fc3-440c-a5cc-f76b80d43ced)


## Data Loading
Dummy data was randomly created and loaded into each of the tables in the hng_hire database on MySQL

### Fact table data 
- [hiring](./hiring.xlsx)
  
### Dimension table data
- [candidates](./candidates.xlsx)
- [employers](./employers.xlsx)
- [job roles](./job_roles.xlsx)
- [stack](./stack.xlsx)
- [status](./status.xlsx)
- [location](./location.xlsx)
- [date](./date.xlsx)


## Links
- [Dashboard](https://github.com/mchenryspagg/hng-hire-data-model/blob/main/HNG%20HIRE%20DASHBOARD.pbix)
- [Report](https://drive.google.com/file/d/1nVvDgkjtzY0c_cBzW1IY0__62ETliOqH/view?usp=sharing)
- [Queries Utilized](./Queries.sql)


## Key Insights
Here are the key insights from the report:

- **Candidate Distribution**: There are a total of 6 candidates in the HNG hire pool.
- **Hiring Status**: 33% of candidates are currently being interviewed, 33% are available for a job, and 33% have been hired.
- **Role Distribution**: 1 Frontend Designer and 1 UX Designer have been hired; 1 Data Analyst and 1 DevOps Engineer are currently being interviewed.
- **Stack Representation**: Each technology stack has just 1 candidate in the HNG hire candidate pool.

![image](https://github.com/mchenryspagg/hng-hire-data-model/blob/main/DASBOARD%20PNG.png)


## Acknowledgements
This project is part 3 of three tasks required to graduate from Stage 8 at HNG 11 internship for the Data Analyst Track. Special appreciation to the organizers of the internship, and to my esteemed team members in team Bulldozer - Blessing Laweh, Adesola Ogundipe, Abena Agyemang Gyasi, Omolola Alonge - who together we made it as HNG Finalist in the data analyst track.
