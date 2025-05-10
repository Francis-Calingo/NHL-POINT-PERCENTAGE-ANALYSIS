# PROJECT OVERVIEW: NHL Point Percentage Analysis (with Python)

# 

# Table of Contents
* [Introduction](#introduction)
* [Code and Setup](#code-and-setup)
* [Data Cleaning and Preprocessing](#data-cleaning-and-preprocessing)
* [Time-Series Analysis](#time-series-analysis)
* [Further Analysis](#further-analysis)
* [Discussion](#discussion)
* [Credits and Acknowledgements](#credits-and-acknowledgements)

---
  
# Introduction

This project analyzes the point percentages of Stanley Cup winners, finalists, and regular season champions across NHL history, using season-by-season trends and 5-year rolling averages. The goal is to uncover long-term patterns in elite team performance and explore how regular-season dominance correlates with playoff success. This project seeks to explore the following questions:

* How closely do regular season champions align with Stanley Cup winners?

* Do Cup-winning teams show consistent performance patterns across decades?

* Have these relationships changed with different eras of the NHL?

[<b>Back to Table of Contents</b>](#table-of-contents)

---

# Code and Setup
  <ul>
    <li><b>IDEs Used:</b> Google Colab, Jupyter Notebook</li>
    <li><b>Python Version:</b> 3.10.12</li>
    <li><b>Libraries and Packages:</b> pandas, plotly.express, matplotlib, Dash</li>
  </ul>

If you'd like to fork or run this locally:

```bash
git clone https://github.com/Francis-Calingo/NHL-POINT-PERCENTAGE-ANALYSIS.git
cd NHL-POINT-PERCENTAGE-ANALYSIS
```

To install the necessary Python libraries and packages:
```bash
pip install -r requirements.txt
```

[<b>Back to Table of Contents</b>](#table-of-contents)

---

# Web Scraping
  <ul>
    <li><b>Stanley Cup Champions:</b> https://records.nhl.com/awards/stanley-cup/winners/li>
    <li><b>Regular Season Team Statistics:</b> https://www.nhl.com/standings/2024-04-18/league</li>
  </ul>

[<b>Back to Table of Contents</b>](#table-of-contents)

---

# Data Cleaning and Preprocessing

The csv file containing the data has **672 entries (168 records x 4 fields).**
**Head (first 5 rows) and tail (last 5 rows) of the csv:**

| YEAR | TEAM | POINTS % | TYPE |
|----|----|----|----|
|1968|Montreal Canadiens|0.635|WINNER|
|1969|Montreal Canadiens|0.678|WINNER|
|1970|Boston Bruins|0.651|WINNER|
|1971|Montreal Canadiens|	0.622|WINNER|
|1972|Boston Bruins|0.763|WINNER|
|----|----|----|----|
|2019|Tampa Bay Lightning|0.780|REGULAR SEASON CHAMPION|
|2020|Boston Bruins|0.713|REGULAR SEASON CHAMPION|
|2021|Colorado Avalanche|0.732|REGULAR SEASON CHAMPION|
|2022|Florida Panthers|	0.744|REGULAR SEASON CHAMPION|
|2023|Boston Bruins|0.823|REGULAR SEASON CHAMPION|

After loading this csv into a Jupyter Notebook, na rows were dropped. Three rows should correspond to 2005, as there was a lockout that cancelled the entire 2004-05 season.

```python
New_df=df.dropna() #Remove the data for 2005. It should drop 3 rows.
New_df
```

[<b>Back to Table of Contents</b>](#table-of-contents)

---

# Time-Series Analysis

<p>The plot demonstrates that regular season performances peaked in the 1970s, declined over time in the mid-90s, before slowly climbing up and mostly stabilizing somewhere in the middle (although the historic performances of the 2018-19 Tampa Bay Lightning and the 2022-23 Boston Bruins teams help the regular season champion trendline almost creep up to its previous historic highs). </p>

![newplot](https://github.com/user-attachments/assets/88db03af-247f-4e42-ab18-3c2b370e0ace)

Code snippet:

```python
app = Dash(__name__)

Scatter_Plot = px.scatter(New_df, x='YEAR', y="POINTS %", color="TYPE", trendline="rolling", trendline_options=dict(window=5),
                title="Win Percentage of NHL Cup Finalists and Regular Season Champions. with 5-Year Rolling Average",
                hover_name="TEAM", width=1200, height=800)

app.layout = html.Div(children=[
    html.H1(children='Hello Dash'),

    html.Div(children='''
        Dash: A web application framework for your data.
    '''),

    dcc.Graph(
        id='example-graph',
        figure=Scatter_Plot
    )
])

if __name__ == '__main__':
    app.run(debug=True)
```

Facet_col visualization of the three trend lines:

<img width="896" alt="image" src="https://github.com/user-attachments/assets/3533b896-2d07-40c1-9fa6-cb156807692a" />

Code snippet:

```python
Scatter_Plot2 = px.scatter(New_df, x='YEAR', y="POINTS %", color="TYPE", trendline="rolling", trendline_options=dict(window=5),
                title="Win Percentage of NHL Cup Finalists and Regular Season Champions. with 5-Year Rolling Average",
                facet_col="TYPE", hover_name="TEAM", width=1200, height=800) #Using facet_col to make it easier to vizualise the three trendlines.
Scatter_Plot2
```

[<b>Back to Table of Contents</b>](#table-of-contents)

---

# Further Analysis

<p> This plot demonstrate that not only has it become rarer for the NHL regular season champion to win the Stanley Cup in the same season, but it's becoming more common for teams that did not finish very close to the regular season champions in points to win the Stanley Cup. This shows that the league has become more competitive and betting on certain top teams is not as certain as it was in the past.</p>

<img width="668" alt="image" src="https://github.com/user-attachments/assets/382514ee-afea-4625-a9b2-0c5031ec9ce0" />

[<b>Back to Table of Contents</b>](#table-of-contents)

---

# Discussion

<p> Despite the increasingly competitive nature of the league (as demonstrated by the time-series plot showing that, in general, both the Stanley Cup finalists and regular season champions are not performing as well in the regular season and the playoffs, respectively, as their 1970s counterparts), it appears that, more often than not, when it comes to the Stanley Cup finals, the team with a higher regular season point total will more than likely win the Stanley Cup over their opponent. Here is what that entails for different relevant parties:</p>

* **For hockey analysts**: Consider performance consistency and opponent strength rather than point totals alone when predicting playoff outcomes.

* **For teams**: Regular season perfomance no longer guarantees playoff success as much as it did in prior eras, especially in the age of the salary cap. Coaches must consider other factors in their playoff matchups besides suface comparisons of regular season performance. For example, facing the same opponent sparsely during the regular season is much different from facing them at least 4 consecutive times.

* **For the sports betting industry**: Utilizing the trend lines, as well as understanding that, more often than not, NHL teams that finish with the higher point percentage will win the Cup than their opponent in the Finals, will help adjust their odds calculations accordingly.

[<b>Back to Table of Contents</b>](#table-of-contents)
</details>

---

# Credits and Acknowledgements

"Linear and Non-Linear Trendlines in Python". Plotly, https://plotly.com/python/linear-fits/. 

[<b>Back to Table of Contents</b>](#table-of-contents)
