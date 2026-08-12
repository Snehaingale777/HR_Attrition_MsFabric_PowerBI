# HR_Attrition_MsFabric_PowerBI

Tools: Microsoft Fabric (Dataflow Gen2, Lakehouse, Semantic Model), Power BI Dataset: IBM HR Employee Attrition dataset (1,470 employees) Live report:(https://github.com/Snehaingale777/Fabric/blob/main/HR-Employee-Attrition.csv)

Why I built this

Every company loses employees, and every time someone leaves it costs money to hire and train a replacement. HR teams usually know attrition is a problem but don't always know exactly where it's coming from. I wanted to build a dashboard that answers that clearly: what's the overall attrition rate, which departments are losing the most people, and does pay or age have anything to do with who leaves.

How I built it

I loaded the raw HR dataset into a Lakehouse using Dataflow Gen2. I picked this over a coding-based approach because this dashboard would eventually be used and maintained by HR, not developers, so I wanted the process to stay simple.

I added two new columns, Salary Band and Age Group, so the data groups nicely into ranges instead of showing every individual number.

I kept everything in one flat table instead of splitting it into separate fact and dimension tables. With under 2,000 rows, that extra structure wasn't needed here.

I connected the report live to the data so it updates automatically without me having to refresh it manually.

I also added security so only the right people can see certain things. I used column-level security (CLS) to hide the salary column completely from anyone who shouldn't see it — they don't even know that column exists. I also set up row-level security so each department head only sees their own team's data, not everyone else's.

What I found
Overall attrition is 16.1%, which is higher than the usual industry range of 10-15%.
Sales has the highest attrition at 20.6%, then HR at 19%. R&D is the lowest at 13.8%.
Sales Representatives leave the most out of any role, at almost 40%.
People earning under 3k leave a lot more often (28.6%) than people earning above 10k (10.4%).
People who work overtime leave about 3 times more often than people who don't.
Younger employees between 18-25 leave the most, at 35.8%.
Single employees leave more than twice as often as married employees.

So basically, the people most likely to leave are young, single, lower-paid Sales employees who work overtime a lot. If a company wanted to fix attrition, that's the group I'd focus on first.

Screenshots

https://github.com/Snehaingale777/HR_Attrition_MsFabric_PowerBI/blob/main/df_HR_s.jpg
https://github.com/Snehaingale777/HR_Attrition_MsFabric_PowerBI/blob/main/lh_HR_s.jpg
https://github.com/Snehaingale777/HR_Attrition_MsFabric_PowerBI/blob/main/HR%20semantic.jpg


What I'd improve

Right now the security setup is based on fixed roles for each department. If this grows to a lot more departments, I'd switch to a proper security table so new department heads can be added without creating a new role every time.
