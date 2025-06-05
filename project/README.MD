# The Analysis
##  1. What are the most crucial skills to learn for data science, data analytic and data enginner in germany?
to identify the most demanded skills for the 3 data roles. I filtered out the dataset by the top 3 most popular data roles and analyze the top 5 most demanded skills for those roles. this project highlights the most popular job titles and their top skills, showing which skills job applicant must focus on depending on the roles.

inside my notebook here are the detailed steps of my analysis: [2_skills_demand_Germany.ipynb](./2_skills_demand_Germany.ipynb)

### Data Visualization
```python
fig, ax = plt.subplots(len(job_titles), 1, figsize=(8, 6))

for i, job_title in enumerate(job_titles):
    df_plot = df_skills_percent[df_skills_percent["job_title_short"] == job_title].head(5)
    
    
    df_plot.plot(kind="barh", x="job_skills", y="skill_percent", ax=ax[i], legend=False, color='skyblue')
    sns.barplot(data=df_plot, x="skill_percent", y="job_skills", ax=ax[i], hue="skill_count", palette="YlOrRd", dodge=False)
    for n, v in enumerate(df_plot["skill_percent"]):
        ax[i].text(v + 1, n, f"{v:.0f}%", va="center")
    
    ax[i].set_xticks([])
plt.show()
```
    
    




![alt text](image.png)
    
### Summary
- We can see here that python is either second or the first most important skills in demand. this shows that pyhton is a versatile skills that every data roles needs prominently for data scientist at (79%).
- sql is also in high demand in germany data jobs aswell. We can see from the data that sql top the data analyst skills demand at (56%). and for data engineer and data scientist it ranks second after python respectively at (57%), (41%)
- data engineer demanded specialized skills like aws, azure and spark compared to the other two roles who are expected to have a good data management skills

## 2. skills trend for data analyst role in germany
inside my notebook here are the detailed steps: [4_skills_trend_Germany](./4_skills_trend_Germany.ipynb)

### Data Visualization
```python
df_plot = df_da_ger_percent.iloc[:, :5]
sns.lineplot(data=df_plot, dashes=False, palette="tab10")

from matplotlib.ticker import PercentFormatter
ax = plt.gca()
ax.yaxis.set_major_formatter(PercentFormatter(decimals=0))

for i in range(5):
    plt.text(11.2, df_plot.iloc[-1, i], df_plot.columns[i])
plt.show()
```

![alt text](image-1.png)

### Summary
The graph shows that sql is the the skill that most likely be in demand for data analyst job in germany appearing in job post above (60%) of the time of Followed by python that appeared in job post above (40%) of the time. As for the rest of the skills, their appearance on job post varies a lot. Power Bi for example have their demand dropped at the end of the year, as for tableau it's demand surge on april but then dropped at the end of the year.

### 3. Salary analysis for job roles in germany
### Data Visualization
```python
sns.boxplot(data=df_ger_top5, x="salary_year_avg", y="job_title_short", )
ticks_x = plt.FuncFormatter(lambda y, pos:f"${int(y/1000)}K")
plt.gca().xaxis.set_major_formatter(ticks_x)
plt.show()
```
![alt text](image-2.png)
### Summary
The box plot provides insights into the salary distribution for the top five data roles. It is evident that Machine Learning Engineers and Data Scientists are among the most lucrative positions. Machine Learning Engineers have a wide salary range, from approximately $50K to $240K, with a median around $135K. This suggests they are highly sought after for their diverse skill sets, and employers are willing to offer competitive compensation. Data Scientists have a slightly narrower salary range, between $60K and $200K, also with a median near $135K, indicating strong demand and rewarding pay for their expertise.

Senior Data Engineers follow closely, with salaries ranging from $70K to $170K, and a comparable median. Data Engineers earn between $50K and $200K, with an average around $120K, reflecting solid but relatively lower compensation, typically associated with mid-level roles. On the lower end of the spectrum, Data Analysts have the most modest salaries, generally ranging from $45K to $180K, with a median around $95K. Although there are a few outliers earning over $200K, this is not representative of the typical pay for the role.

Overall, the data indicates that roles requiring advanced technical specialization and modeling capabilities, such as Machine Learning Engineer and Data Scientist, command higher salaries in the data industry.











