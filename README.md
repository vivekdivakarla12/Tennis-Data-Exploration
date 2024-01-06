## Tennis Data Exploration, part 1

### Introduction
This data is from TennisAbstract's Jeff Sackmann, who has match data for every ATP match since 1968. I took the 2023 match data csv, and loaded it into Tableau to make these visualizations. I have added a few new statistics, as well as a matchID for every match in the dataset. 
- First Serve Dominance Rating -> First serve points won% from the match winner minus the first serve points won% from the loser of the match.
- Aces per game -> Aces over how many matches the player played
- Second Serve Delta -> Second serve points won% from the match winner minus the second serve points won% from the loser of the match.
  
### First Serve Statistics
The first statistic I chose to make was a "first serve dominance rating". This statistic shows the first serve points won% from the match winner minus the first serve points won% from the loser of the match. The idea is to see how much better the winner was on first serve than the loser. The graph below shows the statistics from all 65 wins of Carlos Alcaraz's season. Alcaraz is the world #2 and a great player, but his wins this season came in a variety of ways. He had some dominant performances, including a 6-0 6-2 win over Facundo Bagnis where he won 81% of his first serves, compared to 34% for Bagnis. On the contrary, he had seven matches where he was able to win despite his opponent winning a higher percentage of their first serves, meaning he was able to deliver performances in crucial moments, and isn't completely reliant on his first serve like other players. 

<img width="1263" alt="Screenshot 2023-12-22 at 6 41 28 PM" src="https://github.com/vivekdivakarla12/Tennis-Data-Exploration/assets/11672096/f6d91cce-cb5e-4615-8c5b-362629d83060">

### ATP Player Ranking by Date

When looking at the end of the 2023 tennis season, it is interesting to view how the rankings have shifted from the beginning of the year to the end of the year. I selected three players who took massive leaps to the top 40, to further understand how they jumped and try to predict who can have this success in 2024. 
- First is the great story of Christopher Eubanks. Eubanks was a college player at Georgia Tech, but his pro career was in a rut, as he hovered around the rankings of 120-140. He had a successful end of 2022, reaching 2 challenger finals that could signal big things to come. When looking at his game, it is incredibly aggressive, which leads to higher peaks but also less consistency. However, in the ATP tour rankings, as long as the peaks are high, you will have a lot of success, as the big tournaments reap major point gains. The first breakthrough was in the Miami Masters, where he reached the quarterfinals from qualifying, breaking the top 100 for the first time and reaching a career high of 75. Once a player reaches the top 100, they are now able to enter more ATP events directly, leading to opportunities for more points. His next massive breakthrough came in the grass season, which suits his serve. Eubanks won Mallorca, a 250 tournament, and then reached the quarterfinals of Wimbledon. He beat a few top players on this run and moved into the tour's top 30, meaning he will be seeded at slams. Eubanks' story showcases that it is never too late to have a breakthrough in tennis, and you only need a few opportunities to skyrocket up the ranks.
- Another player who advanced this year was Arthur Fils, who is just 18. Fils was a top ranked junior, and was the runner up in the junior French Open in 2021. Being from France, he was able to receive wild card opportunities in French events, giving him experience against top players and chances to receive many ranking points. He took advantage in a great way, reaching back to back semifinals in Montpelier and Marseille, and winning his first ever tournament in Lyon. One aspect that is missing from this data is matches from the challenger tour, which features players who are lower ranked and give out less points. Winning matches in the challenger tour is key for improving your ranking to enter ATP events. Fils utilized this, as he won a challenger tournament and reached another final early in the year, and used the momentum to lead his charge into the ATP events, where he finished the year in the top 40.
- Finally, Nicolas Jarry was able to rebuild his ranking well this season. Jarry was provisionally banned for doping in 2020, taking his ranking down from #38 to unranked. Once you are unranked, you have to completely build yourself back up, only with a few opportunities for wild cards. By the end of 2022, Jarry was back to #162, allowing him to play in qualifying rounds. Since his career high was in the top 40, he clearly has the level to be at ATP events, and showed it in the beginning of this year. He was qualifying for events with ease, and got back to the winners circle in his home tournament in Santiago. Although it took a few years, Jarry was able to showcase his level once again, and even surpassed his previous career high.
  
Overall, I believe these stories showcase the way the ATP rankings work, and how players of different backgrounds are able to rise in the rankings in many different ways. These three stories are just the surface, and there are many stories of players rising and falling through the rankings.


![Screenshot 2023-12-31 at 6 50 35 PM](https://github.com/vivekdivakarla12/Tennis-Data-Exploration/assets/11672096/047a4ff7-b5da-4a81-8c10-683ad4f08f0a)

### First/Second serve statistics for top 11 players

<img width="1052" alt="Screenshot 2024-01-02 at 11 50 03 AM" src="https://github.com/vivekdivakarla12/Tennis-Data-Exploration/assets/11672096/cf1cd77c-e37d-4bd4-92dc-f03fee4e0388">

The third story I chose was examining the first and second serves of the top 11 players of 2023. I created two fields, first serve dominance rating, and second serve delta, which compare the difference in serve stats between the winning player and the losing player for a specific match. Shown in this graph is a box and whisker plot for each player's matches, where you can see the range of outcomes for each player. An interesting insight to take from this graph is that Djokovic, Medvedev, and Sinner, the #1, #3 and #4 players in the world, have the highest median first serve dominance rating, meaning they are creating the biggest differences between their first serves and their opponents. On the other side, Alcaraz and Ruud, who had two of the lowest first serve ratings, had two of the highest median second serve ratings. Especially for Ruud, who won most of his matches on clay, where a dominant first serve is not as effective, taking advantage of rallies on second serves is a key factor to win. When looking at the data quality, there are a few outliers in the dataset, as wins via retirement against injured players can inflate the stats. 


### Correlation between Features and winning tennis matches

After performing the exploratory data analysis in Tableau, I loaded the data into a Pandas dataframe in python to do further analysis. I split each row (which contained a full match) into two rows, with the first row containing the winner and his stats, and the second row containing the loser and their stats. I then created a row called 'match_won', which is a 1 or 0 on whether the player won the match or not. This made it possible to use as a target variable, and calculate correlation coefficients for the feature variables in the dataset. As seen in the graph below, the most important feature was first serve points won%, which is more important than second serve points won%. One feature that I thought would be more important is first serve in%, as if a player gets more first serves in, I believe it greatly improves their chances of holding serve, and therefore winning the match.

<img width="697" alt="Screenshot 2024-01-06 at 3 52 39 PM" src="https://github.com/vivekdivakarla12/Tennis-Data-Exploration/assets/11672096/371da59e-38d6-4545-87f6-c4109121953a">

After viewing the data for all matches, I chose to split the data into three sections, one for each major surface. I then did the same correlation calculations to understand how matches are won on Hard, Clay, and Grass. Compared to all matches, the order of importance is the same for hard courts, but the numbers are slightly different. One statistic that becomes more important is ace%, as the correlation grows from .235 to .269. While this jump may not look like much, the margins between winning and losing a tennis match can be very slim, so the small percentage differences matter. 

<img width="799" alt="Screenshot 2024-01-06 at 3 53 07 PM" src="https://github.com/vivekdivakarla12/Tennis-Data-Exploration/assets/11672096/0a35913b-4427-4aa7-a55c-3add633187c6">

CLAY

<img width="795" alt="Screenshot 2024-01-06 at 3 57 33 PM" src="https://github.com/vivekdivakarla12/Tennis-Data-Exploration/assets/11672096/02a4d6c9-0fcc-4604-84e2-bbcc380423d3">

GRASS

<img width="813" alt="Screenshot 2024-01-06 at 4 00 56 PM" src="https://github.com/vivekdivakarla12/Tennis-Data-Exploration/assets/11672096/bb727ac1-3d76-4280-8ba4-53e6e167c6df">
