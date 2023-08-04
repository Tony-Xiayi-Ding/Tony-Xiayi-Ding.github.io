---
layout: post
title: All-NBA Teams Selection Prediction
subtitle: Excerpt from project report
gh-repo: daattali/beautiful-jekyll
cover-img: /assets/img/NBA.jpg
thumbnail-img: /assets/img/NBA.jpg
share-img: /assets/img/NBA.jpg
tags: [R, Machine Learning, NBA]
comments: true
---


Every year, there are more than 450 basketball players that play in a single NBA season, but only 15 of them would get selected into the All-NBA teams for that specific season. As a huge NBA fan, it makes me wonder what makes these 15 players stand out from all the NBA players. As a result, this project will be trying to locate the top features of an NBA player that are indicative of All-NBA teams selection, and to what extent can I predict the selection of All-NBA team using the players’ statistics?

**FYI:**
- **Please click this [link](https://tony-xiayi-ding.github.io/BST260-Final-Project/) to read all the other sections (Introduction, Results, and Conclusion) of this project.**

## Dataset

A total of two datasets were used in this project, namely *Seasons_Stats.csv* and *All.NBA.1984-2018.csv*. These two datasets were all originally parsed from a website called [Basketball Reference](https://www.basketball-reference.com/).

- The Seasons_Stats.csv file can be accessed through this [link](https://www.kaggle.com/datasets/drgilermo/nba-players-stats?select=Seasons_Stats.csv). This dataset contains players’ game statistics from year 1950 to 2017, and each column represents an attribute of that player. These attributes include basic statistics such as games played (G) and total points scored in that season (PTS) as well as the more advanced metrics such as Win Shares (WS), which is an estimate of the number of wins contributed by that player.

- The All.NBA.1984-2018.csv file can be accessed through this [link](https://www.kaggle.com/code/kerneler/starter-all-nba-players-1984-2018-e8f3592a-1/data?select=All.NBA.1984-2018.csv). This dataset contains all the players that are selected to be in All-NBA teams starting from the 1984-1985 season to the 2016-2017 season. One thing to note is that before the 1988-1989 season, only 2 teams of All-NBA teams were selected each year; and starting from the 1988-1989 season, a total of 3 teams of All-NBA teams were selected each year.

## Conclusion and Discussion

The top three most important features derived from the logistic regression model were *Games*, *ShootingPercentage*, and *BoxPlusMinus*; while the top three most important features derived from the random forest model were *EfficiencyRating*, *BoxPlusMinus*, and *Points*. Although the two groups of top three most important features did not overlap much(the only overlapping variable is BoxPlusMinus), they still were very similar to each other. To illustrate, the variable *ShootingPercentage* has very close ties to the variable *EfficiencyRating* in that a player who shoots well would have a higher PER value than a player who has a low shooting percentage. Additionally, a player who’s able to earn a lot of game time is usually the same player who can help his team score, which explains why the variable *Game* and the variable *Points* are present. Consequently, we can conclude that: **a player who is great at scoring points while also maintaining a high efficiency rating and a high Box Plus/Minus will have a significantly higher chance of being selected into the All-NBA teams.**

If I had more time to dig deeper into this research question, I would try to scrape the web for the 2018-2022 NBA season data and test my models’ performances on them after training them on all the data that I used in this project. In addition, I would also consider using upsampling or downsampling techniques, such as SMOTE, to balance the skewed training set. Moreover, I would also try to separate my analysis for the All-NBA selections to Centers, Forwards, and Guards since in reality, any All-NBA team is always composed of 2 Guards, 2 Forwards, and 1 Center. Lastly, since the 3 All-NBA teams each year are ranked (i.e. the 1st team is better than the 2nd team, and the 2nd team is better than the 3rd team), maybe I can factor this perspective into consideration in the future by giving relatively more weights to the players that make it onto the 1st team comparing to those who were on the 2nd/3rd team.



## References

Basketball-Reference. *Glossary*. Basketball-Reference. Retrieved November 28, 2022, from https://www.basketball-reference.com/about/glossary.html

Goldstein, O. (2018, April 27). *NBA players stats since 1950*. Kaggle. Retrieved November 28, 2022, from https://www.kaggle.com/datasets/drgilermo/nba-players-stats?select=Seasons_Stats.csv

Kerneler, K. (2018, September 2). *Starter: All NBA players 1984-2018 e8f3592a-1*. Kaggle. Retrieved November 28, 2022, from https://www.kaggle.com/code/kerneler/starter-all-nba-players-1984-2018-e8f3592a-1/data?select=All.NBA.1984-2018.csv





