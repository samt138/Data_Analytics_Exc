# Analysis

## 1. What are the most in-demand skills for the top 3 most popular data roles?

To find the most in-demand skills required for the top 3 data jobs, i filtered out by which ones were the most popular 5 skills required for Data Analytics, Data Engineer, Data Scientst.
The following visualization highlight the most popular job titles and their top skills.  

```python
fig, ax = plt.subplots(len(job_titles), 1)
sns.set_theme(style='ticks')

for i, job_title in enumerate(job_titles):
    df_plot = df_skills_percent[df_skills_percent['job_title_short'] == job_title].head(5)
    #df_plot.plot(kind='barh', x='job_skills', y='skill_percent', ax=ax[i], title=job_title)
    # Modfying the plot into a seaborn
    sns.barplot(data=df_plot, x='skill_percent', y='job_skills', ax=ax[i], hue='skill_count', palette='dark:b_r')
    ax[i].set_title(job_title)
    ax[i].set_xlabel('')
    ax[i].set_ylabel('')
    ax[i].get_legend().remove()
    ax[i].set_xlim(0, 78)
```

View my Jupyter notebook for more detailed information and data modification for colorblind data:
[top_skills.ipynb](Data_project/Top_skills.ipynb)

### Results
![Visualization of Top Skills for Data Jobs](https://github.com/samt138/Data_Analytics_Exc/blob/master/Data_project/images/output.png?raw=true)

### Insights

- Python is in high demand across all three data job roles, with Data Scientist (72%) and Data Engineers (65%) being more prominent.
- For Data Analyst and Data Scientist, SQL is the most in-demand skill, with over half the job postings requiring the skill. For Data engineer, Python is the most sought after skill
- Data Engineers require more dedicated skills in cloud technology (AWS, Azure, Spark), while the other job require more proficient in general data management tools

## 2. How are in-demand skills trending for Data Analysts?
```python
sns.lineplot(data=df_plot, dashes=False, palette='tab10')
sns.set_theme(style='ticks')
sns.despine()

plt.title('Trending Top Skills of Data Analyst in the USA')
plt.ylabel('Likelhood in Job Posting')
plt.xlabel('2023')
plt.legend().remove()

for i in range(5):
    plt.text(11.2, df_plot.iloc[-1, i], df_plot.columns[i])
```
![Trending skills for Data Analyst](https://github.com/samt138/Data_Analytics_Exc/blob/master/Data_project/images/output2.png?raw=true)

Please view my detailed Jupyter notebook for more details: [skills_trend.ipynb](Data_project/Skills_trend.ipynb)

### Insights

- SQL is the most in-demand skill required throughout the year, with gradual decrease overtime
- Excel has once again become sought after skill from September
- Both Python and Tableau show relatively stable demand throught the year. 
