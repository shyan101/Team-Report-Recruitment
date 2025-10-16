# Team-Report-Recruitment

POWER BI DATA VISUALIZATION and ANALYSIS

<img width="914" height="454" alt="Screenshot 2025-10-15 234047" src="https://github.com/user-attachments/assets/3eae203d-91ae-4faf-89c8-4b0a87e7f5f7" />


<img width="1307" height="738" alt="Screenshot 2025-10-16 000541" src="https://github.com/user-attachments/assets/68b01052-014d-46f9-b121-6823a76d9e7b" />


********************************  *****************  ****************  *****************
ANALYSIS thru USING PYTHON LIB: MATPLOTLIB,SEABORN

1) 
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






