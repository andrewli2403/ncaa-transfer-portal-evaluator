# ncaa-transfer-portal-evaluator
Evaluating NCAA Division 1 Men's Basketball players. The goal was to analyze potential transfer portal players that possess the skills and fits the mold of a 3 and D player. Extra spacing and shooting gravtiy creates easier offensive possessions while defensive ability along with height tends to allow teams to be more versatile defensively.

# Model
<img src="plots/model.png" width = 800>

<figcaption align = "center"><b>Top 5 Players in Red.</b></figcaption>

The model looks at 3 key factors: 3 point rating, defensive adjusted rating (DAR), and height.

$3PT Rating = (3 Point Percentage * (3Pointer Attempted/Minutes Played)) * (1 + (.0075 * Minutes Per Game))$ from [Bill Goldblatt](http://www.82games.com/Adjusting.htm).
$Defensive Adjusted Rating = .5 * Defensive Rating + .5 * Defensive Win Shares + Strength of Schedule$.

# Data Collection
Utilized available 2022 transfer players from [Verbal Commits](https://www.verbalcommits.com/transfers/2022) and accessed corrresponding statistics for each player via [Sports Reference](https://www.sports-reference.com/cbb/). Here is my former teammate and 2022 transfer [Anthony Yu](https://www.sports-reference.com/cbb/players/anthony-yu-1.html)!

# Data Processing

Based on Goldblatt's decision to eliminate NBA Players who average less than 11 minutes per game, I eliminated college players who played less than 9 miuntes per game, proportional to Goldblatt. Players with 0 3 Pointers Made or Attempted were also eliminated.

The 3PT Rating was heavily right skewed, so to counter act this, a logarithmic transformation was applied to mimic a normal distribution.
<p align="middle">
  <img src="plots/3ptratingplot.png" width="500" />
  <img src="plots/3ptratinglogplot.png" width="500" /> 
</p>

The top 5 players based on: $total zscore = zscore(log(3PT Rating)) + zscore(Defensive Adjusted Rating) + zscore(height)$ were plotted in red. These players are indicated as having the highest 3 and D potential.


