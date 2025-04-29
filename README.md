![](images/readme/project%20banner.png)

## Welcome
This is my project repository for my first iteration of my Big Bash League (BBL) AI Fantasy Team. By leveraging the ball by ball data of each match from the previous ten BBL seasons, I created two machine learning models and an bespoke optimisation process to select my initial 12 player squad prior to the start of the tournament and to identify the optimal player trades for each of the 9 rounds during the season.

## AI Team Performance

![](images/Gameweek%20Performance/Final%20Summary.png)

**Best Round Rank: 398 - 0.007% (Round 2)**

## AI Team Build
### Data Collection & Manipulation
- **Raw Data:** Extracted ball by ball BBL data from Cricsheet (https://cricsheet.org/downloads/) for each game in BBL01 to BBL13 which was stored in a single CSV file. Special thank you and shout out to Stephen Rushe of Cricsheet for creating this amazing dataset, which I have leveraged primarily for this project!

- **Venue Name Clean Up:** As the raw data includes over 13 seasons of BBL matches, the names of many venues have changed over the years. To build accurate venue trends, the collection of names for each venue was grouped and relabelled to a standard name.

- **Null & Missing Data:** Many rows in the data had some of the columns missing values or nulls. This was mainly tackled by overriding these fields as 0, which is appropriate as most variables lower limit is 0. 

### Response Variable and Explanatory Feature Creation
- **Response Variable:** Number of Fantasy Points (Bowling + Batting) the player will get in the game. As the raw data did not include individual fielding statistics, these points were added separately in the optimisation.
- **Explanatory Features Considered:** 
1. Player's previous season/s fantasy points summary statistics (up to 3 seasons prior)
2. Venue of game
3. Opposition team
4. Venue x Opposition interaction
5. Home Ground flag
6. Player's current season fantasy points summary statistics   
Team Rank
7. Opposition team rank
8. Player's overs bowled and batting position

### Model Build
- **Modelling Data Split:** 80% of the data randomly allocated for training set and remaining 20% for testing set. 
- **Model Pipeline:** Allows the user to select which variables to consider in the model, EDA between response variable and explanatory features, model builder loop and model performance metrics.
- **Model objects considered:** Linear Regression, Decision Trees, Random Forest, Gradient Boosting Machine & Explainable Boosting Machine.
- **Hyperparameter tuning:** For the machine learning model objects, unique hp grids were used to optimise the models, leveraging a 5 fold cross validation process on the training data to identify the best parameters. 
- **Model Performance Metrics:** MAE, MAPE, RMSE, R2 & Actual vs Expected plots to assess the overall model predictive power. Variable feature importance was used to assess most impactful features.

### Model Scoring Process
- **Overall process:** The scoring process first extracts the latest round's actual data for every player to rebuild the dataset used to create the model. Then the latest performance data is fed into the model to predict the expected fantasy points for every active player's remaining games. This process creates a final dataframe which has the 10 expected fantasy points predictions per player for each game in the season. 

### Optimisation
- **Optimisation set up:** Extract the final player scoring dataset and join additional fantasy features required for optimisation constraints e.g. player price. The dataset is then sliced and aggregated up to a player level, only considering the upcoming few rounds based on how many future rounds are selected. 
- **Objective Function:** Maximise the amount of fantasy points
- **Optimisation Constraints:** 
1. Number of players in the team = 12
2. Number of players from previous round team >= 9
3. Number of available players = 12
4. Number of wicketkeepers >= 1
5. Number of batters >= 6
6. Number of bowlers >= 5
7. Team Budget < current round budget

## Tournament Overview

### <ins>Round 1</ins>
- Round Score: 736
- Round Rank: 27350 (48.24%)
- AI Captain: Beau Webster (132 points - 17.93%)

**Selected Team**

![](images/Gameweek%20Performance/Round%201%20-%20Team.png)

**Match Up Result**
![](images/Gameweek%20Performance/Round%201%20-%20Match%20Up.png)


### <ins>Round 2</ins>
**AI Team Round Trades**

| Traded In  | Fantasy Points | Traded Out |
| :---       |     :---:      | :---       |
| L.Pope     | 156            | J.Clarke   |
| H.Thornton | 106            | B.Couch    |
| P.Walter   | 44             | C.Lynn     |

- Round Score: 1147
- Round Rank: 398 (0.70%)
- AI Captain: Matt Short (230 points - 20.05%)

**Selected Team**

![](images/Gameweek%20Performance/Round%202%20-%20Team.png)

**Match Up Result**
![](images/Gameweek%20Performance/Round%202%20-%20Match%20Up.png)

### <ins>Round 3</ins>
**AI Team Round Trades**

| Traded In  | Fantasy Points | Traded Out    |
| :---       |     :---:      | :---          |
| J.Edwards  | 24             | J.Behrendorff |
| H.Kerr     | 104            | H.Cartwright  |
| M.Stoinis  | 51             | B.Webster     |

- Round Score: 818
- Round Rank: 15821 (27.91%)
- AI Captain: Jack Edwards (24 points - 2.93%)

**Selected Team**

![](images/Gameweek%20Performance/Round%203%20-%20Team.png)

**Match Up Result**
![](images/Gameweek%20Performance/Round%203%20-%20Match%20Up.png)

### <ins>Round 4</ins>
**AI Team Round Trades**

| Traded In    | Fantasy Points | Traded Out |
| :---         |     :---:      | :---       |
| J.Brown      | 128            | T.Curran   |
| F.O'Niell    | 16             | M.Short    |
| W.Sutherland | 66             | P.Walter   |

- Round Score: 765
- Round Rank: 8872 (15.65%)
- AI Captain: Jamie Overton (142 points - 18.56%)

**Selected Team**

![](images/Gameweek%20Performance/Round%204%20-%20Team.png)

**Match Up Result**
![](images/Gameweek%20Performance/Round%204%20-%20Match%20Up.png)

### <ins>Round 5</ins>
**AI Team Round Trades**

| Traded In  | Fantasy Points | Traded Out  |
| :---       |     :---:      | :---        |
| W.Agar     | 4              | B.Dhawshuis |
| S.Billings | 13             | H.Kerr      |
| L.Ferguson | 8              | S.Konstas   |
| *D.Sams*   | *15*           | *F.O'Niell* |

- Round Score: 364
- Round Rank: 29750 (52.47%)
- AI Captain: Henry Thornton (54 points - 14.83%)

**Selected Team**

![](images/Gameweek%20Performance/Round%205%20-%20Team.png)

**Match Up Result**
![](images/Gameweek%20Performance/Round%205%20-%20Match%20Up.png)

### <ins>Round 6</ins>
**AI Team Round Trades**

| Traded In  | Fantasy Points | Traded Out   |
| :---       |     :---:      | :---         |
| C.Green    | 10             | L.Pope       |
| S.Johnson  | 81             | J.Overton    |
| G.Sandhu   | 19             | D.Sams       |
| *D.Warner* | *70*           | *H.Thornton* |

- Round Score: 666
- Round Rank: 7221 (12.74%)
- AI Captain: Wes Agar (48 points - 7.21%)

**Selected Team**

![](images/Gameweek%20Performance/Round%206%20-%20Team.png)

**Match Up Result**
![](images/Gameweek%20Performance/Round%206%20-%20Match%20Up.png)

### <ins>Round 7</ins>
**AI Team Round Trades**

| Traded In   | Fantasy Points | Traded Out   |
| :---        |     :---:      | :---         |
| P.Hatzoglu  | 14             | L.Ferguson   |
| C.Jordan    | 48             | G.Sandhu     |
| B.McDermott | 0              | M.Stoinis    |

- Round Score: 533
- Round Rank: 37537 (66.21%)
- AI Captain: Will Sunderland (90 points - 16.89%)

**Selected Team**

![](images/Gameweek%20Performance/Round%207%20-%20Team.png)

- Match Up Result
![](images/Gameweek%20Performance/Round%207%20-%20Match%20Up.png)

### <ins>Round 8</ins>
**AI Team Round Trades**

| Traded In  | Fantasy Points | Traded Out   |
| :---       |     :---:      | :---         |
| N.Ellis    | 143            | W.Agar       |
| M.Owen     | 219            | G.McDermott  |
| B.Stanlake | 13             | P.Siddle     |

- Round Score: 802
- Round Rank: 16789 (29.61%)
- AI Captain: Peter Hatzoglou (22 points - 2.74%)

**Selected Team**

![](images/Gameweek%20Performance/Round%208%20-%20Team.png)

- Match Up Result
![](images/Gameweek%20Performance/Round%208%20-%20Match%20Up.png)

### <ins>Round 9</ins>

**AI Team Round Trades**

| Traded In  | Fantasy Points | Traded Out   |
| :---       |     :---:      | :---         |
| J.Clarke   | 0              | C.Green      |
| M.Neser    | 42             | B.Stanlake   |
| T.Rogers   | 30             | D.Warner     |

- Round Score: 654
- Round Rank: 22340 (39.40%)
- AI Captain: Nathan Ellis (178 points - 27.22%)

**Selected Team**

![](images/Gameweek%20Performance/Round%209%20-%20Team.png)

**Match Up Result**
![](images/Gameweek%20Performance/Round%209%20-%20Match%20Up.png)

## AI Team Next Season Improvements

### Feature Creation
- **Actual cricket stats:** Create features to capture previous season BBL total season runs, batting average, total wickets, economy etc.
- **Power Surge:** Build Bowlers Power Surge dataset and create new related bowler features
- **Fielding Points:** Improved methodology for the fielding points proxy or even individual past season fielding features leveraging webscraping of cricinfo scorecards.
- **Pre Tournament other domestic tournament records:** Currently new players to the competition, either young players or international signings can not be differentiated due to no past season records. Other domestic tournaments can be used as a proxy to help differentiate players. 
- **Fix multi game average variables:** This variables should be populated as null if the player has not played the required amount of games. (e.g. 3 game average, player must have player 3 games)
- **T stat/ Sharpe Ratio:** T stat/ Sharpe Ratio transformation of features to capture both expected value, variance and number of data (way to capture player stability)
- **Sub Player Feature:** Develop feature which penalises players who have played a minor proportion of the team's total games.
- **Bowling and Batting Position:** Currently model is scored on the current game position of the player, but feature should be created as a ratio similar to the scoring of the feature.
- **Improve Scoring Process:** Reduce daily manual scoring process during BBL season by leveraging webscraping to automate the data capturing process from Cricinfo and BBL Supercoach App


### Modelling
- **Separate Batting & Bowling Fantasy Points Model:** The current approach of modelling the overall player's fantasy points had average performance and was hard to predict even when leveraging both prior season and current season features. This can be improved by building two models, one which predicts the players bowling fantasy points and the second which predicts the players batting fantasy points.
- **Interval Estimation:** As player performance and BBL fantasy points have a very high variance, point estimation modelling techniques may not be capturing entire story, especially when players will only be in the team for a few rounds. Therefore interval estimation of player points paired with simulation techniques could lead to a more consistent team selection.
- **Bayesian Modelling:** Currently two sub-models are used, the pre tournament model which predicts the players points using past season features and a during tournament model which leverages both past season and current season previous games features to predict the player points. This could be capture better and more accurately leveraging the prior and posterior aspects of bayesian modelling techniques.
- **Pricing Model:** Create a model to predict the change in player price based on current and previous GW points features. This is essential for the full season trade optimisation.
- **Likelihood of selection model:** Create a model or approach to identify the likelihood of a player being selected for their team. This is essential for the full season trade optimisation.    

### Strategy (via Optimisation)
- **More tailored fantasy optimisation:** Build additional constraints to capture nuance fantasy point scoring e.g. 2x points for captain, vice captaincy trick, bench player trick.
- **Full Season Trade Optimisation:** This season the optimiser suggested the best trades for the upcoming 2/3 rounds which is based of my prior fantasy knowledge. By utilising a full season trade optimisation process, every round the remaining tournament will be simulated and the most optimal trades will be identified by considering future round trades as well.



