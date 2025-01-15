# PROJECT OVERVIEW: NHL Point Percentage Analysis (with Python)
  <ul>
    <li>Performed data visualizations (i.e., time series analysis) and analyzed playoff performances of NHL Regular season champions (President Trophy winners), as well as regular season performances of Stanley Cup finalists and winners.</li>
    <li>Scraped data from the NHL's website, collecting data from 1967 onwards (when the league expanded beyond 6 teams permanently).</li>
    <li>Imported Dash for interactivity.</li>
  </ul>
  
## Code and Resources Used
  <ul>
    <li><b>IDEs Used:</b> Google Colab, Jupyter Notebook</li>
    <li><b>Python Version:</b> 3.10.12</li>
    <li><b>Libraries and Packages:</b> pandas, plotly.express, matplotlib, Dash</li>
  </ul>
  
## Web Scraping
  <ul>
    <li><b>Stanley Cup Champions:</b> https://records.nhl.com/awards/stanley-cup/winners/li>
    <li><b>Regular Season Team Statistics:</b> https://www.nhl.com/standings/2024-04-18/league</li>
  </ul>

## Data Cleaning and Preprocessing
<ul>
    <li>Dropped na rows, which should correspond to 2005, as there was a lockout that cancelled the entire 2004-05 season.</li>
</ul>

## Time-Series Analysis

<p>The plot demonstrates that regular season performances peaked in the 1970s, declined over time in the mid-90s, before slowly climbing up and mostly stabilizing somewhere in the middle (although the historic performances of the 2018-19 Tampa Bay Lightning and the 2022-23 Boston Bruins teams help the regular season champion trendline almost creep up to its previous historic highs). </p>

![newplot](https://github.com/user-attachments/assets/88db03af-247f-4e42-ab18-3c2b370e0ace)

## Further Analysis

<p> This plot demonstrate that not only has it become rarer for the NHL regular season champion to win the Stanley Cup in the same season, but it's becoming more common for teams that did not finish very close to the regular season champions in points to win the Stanley Cup. This hsows that the league has become more competitive and betting on certain top teams is not as certain asit was in the past.</p>

<img width="668" alt="image" src="https://github.com/user-attachments/assets/382514ee-afea-4625-a9b2-0c5031ec9ce0" />

## Discussion

<p> Despite the inceasingly competitive nature of the league (as demonstrated by the time-series plot showing that, in general, both the Stanley Cup finalists and regular season champions are not performing as well in the regular season and the playoffs, respectively, as their 1970s counterparts), it appears that, more often than not, when it comes to the Stanley Cup finals, the team with a higher regular season point total will more than likely win the Stanley Cup over their opponent. Therefore, if you are placing bets at every Stanley Cup Final, you should always definitely bet on the team with the better regular season record. </p>
