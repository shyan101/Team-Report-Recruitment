# Team-Report-Recruitment

POWER BI DATA VISUALIZATION and ANALYSIS

<img width="914" height="454" alt="Screenshot 2025-10-15 234047" src="https://github.com/user-attachments/assets/3eae203d-91ae-4faf-89c8-4b0a87e7f5f7" />


<img width="1307" height="738" alt="Screenshot 2025-10-16 000541" src="https://github.com/user-attachments/assets/68b01052-014d-46f9-b121-6823a76d9e7b" />


********************************  *****************  ****************  *****************
ANALYSIS thru USING PYTHON connecting SQL
LIB: MATPLOTLIB,SEABORN

Connect to MySQL
conn = mysql.connector.connect(
    host="Paste hete your host name",
    user="user name",
    password="your sql paswrd",
    database="recruitment_db" // this is data base name made in MySQ
    
1) ******* Jobs per Department  **********
import matplotlib.pyplot as plt
import seaborn as sns

dept_counts = jobs_df['department'].value_counts()

plt.figure(figsize=(8,5))
sns.barplot(x=dept_counts.index, y=dept_counts.values)
plt.title("Number of Jobs by Department")
plt.xlabel("Department")
plt.ylabel("Number of Jobs")
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()

<img width="800" height="500" alt="Figure_1" src="https://github.com/user-attachments/assets/1b6ad006-e5cf-4c4b-940b-0b9abb12e4c8" />


2) ****** Recruiter Experience Distribution  ***********
   
import mysql.connector
import matplotlib.pyplot as plt
import seaborn as sns
import pandas as pd

jobs_df = pd.read_sql("SELECT * FROM jobs", conn)

recruiters_df = pd.read_sql("SELECT * FROM recruiters", conn)

plt.figure(figsize=(6,4))
sns.histplot(recruiters_df['experience_years'], bins=10, kde=True)
plt.title("Distribution of Recruiter Experience (Years)")
plt.xlabel("Experience (Years)")
plt.ylabel("Count")
plt.show()

<img width="600" height="400" alt="Figure_2" src="https://github.com/user-attachments/assets/581ab8a4-1e00-453c-8667-429403fd17a3" />

3) ******  Average Applications per Job *************

applications_df = pd.read_sql("SELECT * FROM applications", conn)

# Count applications per job
apps_per_job = applications_df.groupby('job_id').size().reset_index(name='application_count')

plt.figure(figsize=(8,5))
sns.histplot(apps_per_job['application_count'], bins=10, kde=True)
plt.title("Applications Received per Job")
plt.xlabel("Number of Applications")
plt.ylabel("Frequency")
plt.show()



<img width="800" height="500" alt="Figure_3" src="https://github.com/user-attachments/assets/fbb960e9-060b-404a-b0c5-05a3bcb01fae" />

4)  ******  Time to Fill a Job    *************

jobs_df['date_posted'] = pd.to_datetime(jobs_df['date_posted'])
jobs_df['date_closed'] = pd.to_datetime(jobs_df['date_closed'])
jobs_df['days_to_fill'] = (jobs_df['date_closed'] - jobs_df['date_posted']).dt.days

plt.figure(figsize=(8,5))
sns.boxplot(x=jobs_df['days_to_fill'])
plt.title("Distribution of Job Filling Time")
plt.xlabel("Days to Fill")
plt.show()

<img width="800" height="500" alt="Figure_6" src="https://github.com/user-attachments/assets/27f9b4ef-6db7-45cf-a635-ce7af6c54a00" />




