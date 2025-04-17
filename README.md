# Big-Bash-Fantasy-AI
 
This is my project repository for my Big Bash AI Fantasy Team first season.

## AI Team Performance Metrics
- Total Score: 6485
- Best Round Score: 1147 (Round 2)
- Final Team Value: $1,891,800

- Overall Rank: 11398 - 20.15%
- Best Round Rank: 398 - 0.007% (Round 2)

## AI Team Build
### Data Collection & Manipulation
- Extracted ball by ball BBL data from Cricsheet (https://cricsheet.org/downloads/) for each game in BBL01 to BBL13 which was stored in a single CSV file. Special thank you and shout out to Stephen Rushe of Cricsheet for creating this amazing dataset, which I have leveraged primarily for this project!

- Venue clean up

### Response Variable and Explanatory Feature Creation
- Response Variable
- Previous Season/s Player Features
- Dealing with new players

### Model Build
- Train & Test Split
- Model Pipeline
- Model objects considered
- Hyperparameter tuning

### Model Scoring Process
- Overall scoring process
- Process to extract & create the during tournament model features  

### Optimisation
- Optimisation set up
- Objective function
- Constraints

## Round by Round Tournament Overview

### <ins>Round 1</ins>
- Round Score: 736
- Round Rank: 27350 (20.15%)
- AI Captain: Beau Webster (132 points - 17.9%)

- Selected Team

![](images/Gameweek%20Performance/Round%201%20-%20Team.png)

- Match Up Result
![](images/Gameweek%20Performance/Round%201%20-%20Match%20Up.png)


### <ins>Round 2</ins>
- AI Trades

| Traded In  | Fantasy Points | Traded Out |
|------------|----------------|------------|
| :---       |     :---:      |       ---: |
| L.Pope     | 156            | J.Clarke   |
| H.Thornton | 106            | B.Couch    |
| P.Walter   | 44             | C.Lynn     |

- Trades In: 
1. L.Pope (156 points)
2. H.Thornton (106 points)
3. P.Walter (44 points)

- Trades Out:
1. C.Lynn 
2. B.Couch
3. J.Clarke

- Round Score: 1147
- Round Rank: 398 (0.70%)
- AI Captain: Matt Short (230 points - 20.05%)

- Selected Team

![](images/Gameweek%20Performance/Round%202%20-%20Team.png)

- Match Up Result
![](images/Gameweek%20Performance/Round%202%20-%20Match%20Up.png)

### <ins>Round 3</ins>
- Trades In: 
- Trades Out:
- Round Score: 818
- Round Rank: 15821 (27.91%)
- AI Captain: Jack Edwards (24 points - 2.93%)

- Selected Team

![](images/Gameweek%20Performance/Round%203%20-%20Team.png)

- Match Up Result
![](images/Gameweek%20Performance/Round%203%20-%20Match%20Up.png)

### <ins>Round 4</ins>
- Trades In: 
- Trades Out:
- Round Score: 765
- Round Rank: 8872 (15.65%)
- AI Captain: Jamie Overton (142 points - 18.56%)

- Selected Team

![](images/Gameweek%20Performance/Round%204%20-%20Team.png)

- Match Up Result
![](images/Gameweek%20Performance/Round%204%20-%20Match%20Up.png)

### <ins>Round 5</ins>
- Trades In: 
- Trades Out:
- Round Score: 364
- Round Rank: 29750 (52.47%)
- AI Captain: Henry Thornton (54 points - 14.83%)

- Selected Team

![](images/Gameweek%20Performance/Round%205%20-%20Team.png)

- Match Up Result
![](images/Gameweek%20Performance/Round%205%20-%20Match%20Up.png)

### <ins>Round 6</ins>
- Trades In: 
- Trades Out:
- Round Score: 666
- Round Rank: 7221 (12.74%)
- AI Captain: Wes Agar (48 points - 7.21%)

- Selected Team

![](images/Gameweek%20Performance/Round%206%20-%20Team.png)

- Match Up Result
![](images/Gameweek%20Performance/Round%206%20-%20Match%20Up.png)

### <ins>Round 7</ins>
- Trades In: 
- Trades Out:
- Round Score: 533
- Round Rank: 37537 (66.21%)
- AI Captain: Will Sunderland (90 points - 16.89%)

- Selected Team

![](images/Gameweek%20Performance/Round%207%20-%20Team.png)

- Match Up Result
![](images/Gameweek%20Performance/Round%207%20-%20Match%20Up.png)

### <ins>Round 8</ins>
- Trades In: 
- Trades Out:
- Round Score: 802
- Round Rank: 16789 (29.61%)
- AI Captain: Peter Hatzoglou (22 points - 2.74%)

- Select Team

![](images/Gameweek%20Performance/Round%208%20-%20Team.png)

- Match Up Result
![](images/Gameweek%20Performance/Round%208%20-%20Match%20Up.png)

### <ins>Round 9</ins>
- Trades In: 
- Trades Out:
- Round Score: 654
- Round Rank: 22340 (39.40%)
- AI Captain: Nathan Ellis (178 points - 27.22%)

- Select Team

![](images/Gameweek%20Performance/Round%209%20-%20Team.png)

- Match Up Result
![](images/Gameweek%20Performance/Round%209%20-%20Match%20Up.png)

## AI Team Next Season Future Improvements

### Feature Creation
- Actual cricket stats: Create features to capture previous season BBL total season runs, batting average, total wickets, economy etc.
- Power Surge: Build Bowlers Power Surge dataset and create new related bowler features
- Fielding Points: Improved methodology for the fielding points proxy or even individual past season fielding features leveraging webscraping of cricinfo scorecards.
- Pre Tournament other domestic tournament records: Currently new players to the competition, either young players or international signings can not be differentiated due to no past season records. Other domestic tournaments can be used as a proxy to help differentiate players. 
- Fix multi game average variables: This variables should be populated as null if the player has not played the required amount of games. (e.g. 3 game average, player must have player 3 games)
- T stat/ Sharpe Ratio: T stat/ Sharpe Ratio transformation of features to capture both expected value, variance and number of data (way to capture player stability)
- Sub Player Feature: Develop feature which penalises players who have played a minor proportion of the team's total games.
- Bowling and Batting Position: Currently model is scored on the current game position of the player, but feature should be created as a ratio similar to the scoring of the feature.
- Improve Scoring Process: Reduce daily manual scoring process during BBL season by leveraging webscraping to automate the data capturing process from Cricinfo and BBL Supercoach App


### Modelling
- Separate Batting & Bowling Fantasy Points Model: The current approach of modelling the overall player's fantasy points had average performance and was hard to predict even when leveraging both prior season and current season features. This can be improved by building two models, one which predicts the players bowling fantasy points and the second which predicts the players batting fantasy points.
- Pricing Model: Create a model to predict the change in player price based on current and previous GW points features. This is essential for the full season trade optimisation.
- Interval Estimation: As player performance and BBL fantasy points have a very high variance, point estimation modelling techniques may not be capturing entire story, especially when players will only be in the team for a few rounds. Therefore interval estimation of player points paired with simulation techniques could lead to a more consistent team selection.
- Bayesian Modelling: Currently two sub-models are used, the pre tournament model which predicts the players points using past season features and a during tournament model which leverages both past season and current season previous games features to predict the player points. This could be capture better and more accurately leveraging the prior and posterior aspects of bayesian modelling techniques.     

### Strategy (via Optimisation)
- Add constraint to consider 2x points for captain
- 
- Full Season Trade Optimisation:
- Bench Trick: Incorporating Bench Trick and trying to utilise more than the allocated 12 starting players.



