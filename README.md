# HR-Analysis-Dashboard
An interactive Power BI Human Resources Analytics Dashboard featuring dynamic toggle views for workforce demographics and salary/compensation insights.
📊 Human Resources Dashboard — Power BI

An interactive Power BI dashboard built to analyze employee data across departments, business units, salary, satisfaction, and performance metrics. The report contains two dedicated pages — Employee Overview and Salary Analysis — with cross-filtering slicers for deep-dive analysis.


🖼️ Dashboard Preview

Employee View Salary View
<img width="1366" height="768" alt="Employee" src="https://github.com/user-attachments/assets/cba7b598-5b9a-435e-be76-cff97eab75b2" />
              <img width="1366" height="768" alt="Salary" src="https://github.com/user-attachments/assets/8dd3d098-39f5-4a91-9e70-258f6724ab42" />
📁 Dataset


File: Human_Resources.csv
Records: 3,520 employees
Columns: Department, Groups, Job Type, Marital Status, Age, Business Unit, Hire Date, Employee Type, Sick Days, Balance Days, Years in Current Role, Years Since Last Promotion, Education, Job Involvement, Job Satisfaction, Performance Rating, Relationship Satisfaction, Work-Life Balance, Gender, Salary, Job Classification



🧩 Page 1: Employee Overview

Gives a complete snapshot of workforce composition and well-being.

KPI Cards


Total Employees (Count of Emp. Type) — 3,520
Total Salary — 335M
Total Sick Days — 23K
Total Balance Days — 44K


Visuals


Donut Chart — By Job Type (Full Time / Part Time)
Donut Chart — By Gender
Donut Chart — By Marital Status
Donut Chart — By Education
Donut Chart — By Current Role (Years in role)
Donut Chart — By Last Promotion
Clustered Bar Chart — Sum of Sick Days & Balance Days by Business Unit
Clustered Bar Chart — Sum of Sick Days & Balance Days by Department


Slicers/Filters


Performance Rating
Relationship Satisfaction
Job Satisfaction
Gender
Business Unit (button-style: Houston, New York City, Los Angeles, Seattle)
Job Type



💰 Page 2: Salary Analysis

Focused view on compensation trends across the organization.

KPI Cards


Average Salary — 94.65K
Total Salary Cost — 80M (filtered view)
Avg Job Satisfaction Score — 2.52


Visuals


Donut Chart — By Gender
Donut Chart — By Marital Status
Donut Chart — By Job Type
Donut Chart — By Education
Donut Chart — By Current Role
Donut Chart — By Last Promotion


Slicers/Filters


Business Unit (button-style)
Age Group (30–39, 40–49, 50+, Under 30)
Job Type
Performance Rating
Relationship Satisfaction
Job Satisfaction



🧮 Key DAX Measures Used

daxTotal Employees = COUNTROWS('Human Resources')

Active Employees = 
CALCULATE(COUNTROWS('Human Resources'), 'Human Resources'[Emp.Type] = "Active")

Average Salary = AVERAGE('Human Resources'[Salary])

Total Salary Cost = SUM('Human Resources'[Salary])

Avg Job Satisfaction Score = 
AVERAGEX(
    'Human Resources',
    SWITCH('Human Resources'[Job Satisfaction], "Low", 1, "Medium", 2, "High", 3, "Very High", 4)
)

Age Group = 
SWITCH(
    TRUE(),
    'Human Resources'[Age] < 30, "Under 30",
    'Human Resources'[Age] < 40, "30-39",
    'Human Resources'[Age] < 50, "40-49",
    "50+"
)


🎨 Design


Theme: Light neutral background (#F3F1EC) with dark purple header accent
Color Palette: Navy, Teal, Gold/Mustard, Black — consistent across all charts
Navigation: Page-based tabs (Employee / Salary) with synced slicers for cross-report filtering



🛠️ Tools Used


Power BI Desktop — Data modeling, DAX, and visualization
Power Query — Data cleaning and transformation
DAX — Custom measures and calculated columns



📌 Key Insights


Gender distribution is nearly balanced (~50/50) across the workforce
Salary and satisfaction scores vary meaningfully across departments and business units
Sick day and balance day trends highlight departments that may need attention
Promotion and tenure patterns show even distribution across the "Years since last promotion" buckets



🚀 How to Use


Clone this repository
Open HR_Dashboard.pbix in Power BI Desktop
Use the slicers to filter by Business Unit, Job Type, Performance Rating, etc.
Switch between Employee and Salary pages using the tabs at the bottom
