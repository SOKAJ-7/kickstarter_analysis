# kickstarter_analysis
Performing analyses on kick-starter data to uncover trends

# Kickstarting with Excel

## Overview of Project
The focus of this project was to analyse the kick-starter fundraising data of 4114 projects, comprising many different entertainment categories as well as their respective subcategories. This dataset included project information related to important dates, fundraising goals and outcomes, and country of origin. 
### Purpose
This data was used to uncover insights to assist a hypothetical client (Louise) in understanding what makes a kick-starter project successful so that she could apply these insights to her own project, a play called Fever. By using pivot tables and using Excel’s charting feature, data related to the success of theatre projects was able to be visualized relative to a project’s launch date and fundraising goal, respectively. These visualizations would be useful to Louise as she could use them to help assess the viability of her project and fundraising goals.

## Analysis and Challenges
### Analysis of Outcomes Based on Launch Date
The first part of the project was to create a line chart which could show the outcome of theatre projects based on the month that they were released. Firstly, a “Years” a column had to be created in the “Kickstarter” table so that a proper filter could be created for the line chart. This was done by using the YEAR() function on the ‘Launch Date” column. 

To create a pivot table, the updated “Kickstarter” table was selected and used as the basis for the pivot table. The “Years” and “Parent Category” fields were selected as filters, “outcomes” was set as the columns, “count of outcomes” were set as values, and the “Launch Date” were the rows of the table (Figure 1). The pivot table was then selected and used as the basis for a 2-D line chart to which a title was added.

![PTD1.png](C:\Users\jkova\OneDrive\Documents\Data Analytics Bootcamp\Classroom projects\Week 1 - Excel basics\PTD1.png))
![PTD1](https://user-images.githubusercontent.com/93050931/140625751-41e0ba55-34f6-44c8-87ca-a5d351151831.PNG)
(Figure 1)

### Analysis of Outcomes Based on Goals
The second figure that needed to be produced was a chart showing the outcomes of plays based on their fundraising goals. For this, a new sheet and table needed to be created using the COUNTIFS() function, which can count the number of cells in a range which match the provided constraints. The “Goal” column was manually inputted based on the ranges provided. The “Number of outcome” columns were filled using the general formula:

=COUNTIFS(Kickstarter!$F$2:$F$4115,"outcome",Kickstarter!$D$2:$D$4115,"< ‘upper limit", Kickstarter!$D$2:$D$4115,">= lower limit", Kickstarter!$R$2:$R$4115,"plays")

Before using this formula, the “Kickstarter” table needed to be filtered to only show results for “plays’ in the “Sub-category” column. This ensured that only the relevant projects were being counted. The “Number of projects” column was filled using SUM() on the three “Number of outcome” columns and the “Percentage of outcome” columns were filled using basic division operations using the appropriate columns. The “Percentage of outcome” columns were then summed to ensure that they equaled to 100%. The resulting table was selected and used to make a line chart. By using the “Select Data” feature for the chart, the appropriate columns could be chosen to be displayed in the chart (Figure 2). A title was then added to the chart and the legend was moved to the x-axis. No significant challenges were faced in this section of the challenge but the most likely source of error would be forgetting to filter the “Kickstarter” table to include only plays.


![Select_data.png](C:\Users\jkova\OneDrive\Documents\Data Analytics Bootcamp\Classroom projects\Week 1 - Excel basics\Select_data.png)
![Select_data](https://user-images.githubusercontent.com/93050931/140625739-88eba1bf-dffa-4338-b1da-e05f764d7d00.PNG)
(Figure 2)

### Challenges and Difficulties Encountered
When using the YEAR() function on the "Launch Date" comlumn for deliverable 1, the function did not work properly as the output was years from the early 1900’s. Through searching online excel forums, it was determined that this was likely due to an issue of cell formatting. After changing the “Launch Date” column from “dd-mm-yyyy” format to long date format, this issue was fixed.

No significant challenges were faced creating the "Outcomes Based on Goals" part of the challenge but the most likely source of error would be forgetting to filter the “Kickstarter” table to include only plays or forgetting to use the "<=" or ">=" operators on the lower or upper limits of a goal range in the COUNTIFS() formulas.


## Results
### Theatre Outcomes Based on Launch Date
When looking at the “Theatre Outcomes vs Launch Date” line chart, it is evident that kick-starter theatre projects have a higher chance of success if their launch date is in late Spring or early Summer, with the most successful months being May and June. This can be seen in the chart as the lines representing the three outcomes remain constant relative to each other throughout the year, except in May through August where the “Successful” line is much higher compared to other outcomes. A t-test could be employed to determine whether this spike is statistically significant. A possible explanation for why the spike exists is that people are more willing to go out in the summer when the weather is pleasant, and the sun is out longer. Having data related to the tickets sales of each project’s first run of showings could be useful to answer this question. 

Another interesting feature of the graph is that there are small spikes in the number of plays launched in the months of February and October, which are during periods of time where the number of plays launched tends to be lower. This may be because these months contain culturally relevant celebrations such as Valentine’s Day and Black history month in February and Halloween in October which plays could be based on. It could be useful to categorize plays by their genre and use that data to determine whether “romance” and “social critique/drama” or “Halloween-themed” and “Horror” plays are more represented in February and October compared to other months.

### Outcomes Based on Goals
One trend that is noticeable from the “Outcomes Base on Goals” chart is that plays are generally more successful if their fundraising goals are lower. This makes sense as a lower fundraising goal would most likely correspond to a lower production budget. A lower budget would then make it easier to get the project completed and then shown. The only range where this trend is untrue is for projects with goals from $35,000-$50,000. This could be because the projects included in this dataset include different production capacities for each play. For example, an independently produced play will rarely have a budget that can compete with the budget of a play produced by a theatre production company. So, what can be considered a low-budget play would be dependent on the level of production of the play. Therefore, it would be useful to include a column which could show whether a play was independently produced or produced by a known company as well as the production budget of each play. Using this data, the production budgets could be compared between independently produced plays and large company produced plays. 


