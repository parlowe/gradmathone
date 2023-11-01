# Taylor Swift and Travis Kelce: Modern Romance or Crafty Marketing Campaign

## Background and Motivation
On September 24th, 2023 Taylor Swift was spotted at Arrowhead stadium in Kansas City, Missouri. This was the first evidence to support relationship rumors between Taylor Swift and Chiefs Tight-End Travis Kelce since they met during her summer Era’s tour and began spending more time together. What followed was an internet storm of speculation. Swifties were turning to the NFL in droves, hoping to catch glimpses of Taylor Swift attending games. Commentators for the Chiefs began using quotes from Taylor Swift songs to describe the games, and stats have even been published to compare the performance of Kelce when Swift is and is not in attendance. 

But is this purported romance all that it is meant to be, or simply a shroud for a more sinister plot? There is ample research in the field of economics on the influence of popular culture on consumer behavior. We are all influenced to spend our money in the way that others are spending their money, from the clothes we decide to wear to the music we listen to. Studies have shown that popular culture influences our perceptions on fair price, and that this effect is compounded by social media [1] [2].

In this project I am asking the guiding question: Is the partnership between Taylor Swift and Travis Kelce legitimate, or simply a ploy to increase relative interest in their respective brands and thereby increase influence on popular culture? If this were the case, both parties would effectively be molding popular culture to create economically favorable conditions for their brands. I aim to investigate this question in the following ways: 

Aim One: Investigate changes in relative interest for each entity before Swift appearance on 9/24

Aim Two: Use regression to predict relative interest for each entity 

This project is interesting to me because I was a fan of both Taylor Swift and the NFL (though admittedly not the Chiefs) prior to their intersection. I also think it is entertaining to question popular social narratives, and apply statistical reasoning to cultural phenomena. 

## Data
While I would have liked to analyze financial or economic data for this project, this was not publicly available. Instead I used data available from Google Trends to track relative interest scores for Taylor Swift, Travis Kelce, and the Kansas City Chiefs. 

Relative interest is a normalization metric that is performed by Google to assign scores to data based on the number of searches in a given time frame. I generated relative interest scores by week from the past year (9/24/22-9/24/23) to serve as a sample of relative interest from before the 9/24 game, and relative interest scores by day for days since 9/24 (9/24/2023-10/26/2023). These gave me two datasets with 53 data points in the before sample (Figure 1), and 33 data points in the after sample (Figure 2). 

#### Figure 1: Realative Interest for All Parties by Week- Past Year
<p align="center">
  <img src="init_1.png" width="350"> </p>

#### Figure 2: Realative Interest for All Parties by Day - Since 9/24
  <p align="center">
  <img src="init_2.png" width="350">
</p>

I also wanted to examine a population that was likely to demonstrate interactions in the fanbases of Taylor Swift and Travis Kelce the most clearly. To do this, I generated relative interest scores by day for days since 9/24 (9/24/2023-10/26/2023) specifically localized to Kansas since this represents one of the states that considers the Kansas City Chiefs the home team (Figure 3). 

#### Figure 3: Realative Interest for All Parties by Day - Since 9/24 in Kansas
  <p align="center">
  <img src="init_3.png" width="350">
</p>

Finally, I gathered the dates of the games that Swift attended and categorized the dates post 9/24 according to the number of games Swift had attended (Figure 4). The intent was to use this data in regression modeling. The dates of the games attended were 9/24, 10/1, 10/12, and 10/22.

#### Figure 4: Number of Games Attended by Day Since 9/24
  <p align="center">
  <img src="init_4.png" width="350">
</p>


## Methods
To investigate hypothesis testing, a Wilcoxon Rank Sum test was performed. A null U-distribution for a 5 sample comparison of groups was constructed numerically (Figure 5).

#### Figure 5: Null U-Distribuion for 5 samples
  <p align="center">
  <img src="null_1.png" width="350">
</p>

The relative interest scores for the five weeks before 9/24 were compared to the relative interest scores in the five days after 9/24. A nonparametric test was used to complete hypothesis testing because the relative interest scores for the past year were plotted on a histogram and there was an apparent skew in the data for Travis Kelce and the Kansas City Figures (Figures 6 and 7). 

#### Figure 6: Histogram of Travis Kelce Relative Interest Scores
  <p align="center">
  <img src="init_6.png" width="350">
</p>

#### Figure 7: Histogram of Chiefs Relative Interest Scores
  <p align="center">
  <img src="init_7.png" width="350">
</p>

Since these distributions were constructed from greater than 30 observations and did not appear normal, t-testing from a t-distribution was not possible. A five sample U test was performed due to limitations in computing memory when attending to numerically construct larger null U-distributions. 

Regression analysis was performed to predict the relative interest post 9/24 for Travis Kelce and Taylor Swift. Complex regression models were constructed, regressing the popularity of the opposite figure in Kansas, the number of games Taylor Swift had attended, and the mixed effects of the two parameters. The complex regression models had the form: 

$Relative Interest = ax_1 + bx_2+ cx_1x_2 +d$

Here $x_1 =$ games Taylor Swift has attended and $x_2 =$ realtive interest of opposite party

T-tests were used to analyze the significance of each of the fitted parameters for these terms using the Python Stats Model OLS package. Overall significance of the model was assessed using the generated F-statistic and null F-distribution comparison. P-values greater than 0.05 were considered statistically significant. 


## Results 
Hypothesis testing demonstrated no significant difference in any of the changes in relative interest before or after 9/24. The change in relative interest, the U test statistic and the p-value is reported for each party below.

Taylor Swift: +7.8, U = 9, p=0.274
Travis Kelce: +27.8, U = 5, = 0.075
Kansas City Chiefs: -3.4, U = 18, p=0.155

Since the Kansas City Chiefs experienced a decrease in relative interest, they were not included in regression analysis. 

Complex regression analysis generated significant models predicting Taylor Swift relative interest post 9/24 (Table 1), and Travis Kelce Relative interest post 9/24 (Table 2).

#### Table 1: Complex Regression Analysis Output - Predicting Taylor Swift Relative Interest
  <p align="center">
  <img src="model_1.png" width="350">
</p>

##### Table 2: Complex Regression Analysis Output - Predicting Travis Kelce Relative Interest
  <p align="center">
  <img src="model_2.png" width="350">
</p>

The only parameters found to be significant in the complex models were the relative interest of the opposite party. 

## Analysis 
From the hypothesis testing, it is clear that both Taylor Swift and Travis Kelce experienced an increase in relative interest after 9/24, but this increase was not significant. This is surprising when considering the interest increase for Travis Kelce which was 80% of his pre-9/24 interest. While this increase was close to being significant, it did not meet the threshold. This could be because a small sample size had to be used due to computational limitations, which prevented a significant finding. 

An interesting result experienced by the Kansas City Chiefs was that their relative interest decreased after 9/24. While this decrease was not significant, this decrease could be due to a shift in popular culture to prefer either individual participants in the relationship rather than the team franchise. Future analysis should be conducted to elucidate this effect. 

Complex regression analysis revealed two significant models to predict relative interest of both Taylor Swift and Travis Kelce post 9/24. When the mode parameters were examined, it was identified that the only significant predictor was the term representing the relative interest of the other entity in Kansas. 

To investigate if a better model would be generated by performing simple regression, this analysis was completed post-hoc (Table 3 and Table 4).

#### Table 1: Simple Regression Analysis Output - Predicting Taylor Swift Relative Interest
  <p align="center">
  <img src="model_3.png" width="350">
</p>

##### Table 2: Simple Regression Analysis Output - Predicting Travis Kelce Relative Interest
  <p align="center">
  <img src="model_4.png" width="350">
</p>

 While significant models were generated for both regressions, the overall significance of the models was lowered compared to the complex regressions and the r-squared term decreased. Therefore, there is a benefit to considering the number of games that Taylor Swift has attended in the regression models.

Regression analysis indicates that relative interest in Kansas of the other party is a good predictor of one party's relative interest throughout the United States. Additionally, including the number of games Taylor Swift has attended both alone and as a mixed effect increases the predictive power of the models. This indicates that the increase in relative interest experienced by both parties is helping the other party increase their own relative interest. Even more interestingly, it appears that the games that Taylor Swift is attending are having a positive (though not significant) impact on her overall relative interest, while it is negatively impacting Travis Kelce’s relative interest. 


## Conclusions and Future Directions 
Returning to the central question of this project: Is the partnership between Taylor Swift and Travis Kelce legitimate, or simply a ploy to increase relative interest in their respective brands and thereby increase influence on popular culture?

Based on the hypothesis testing in Aim One, while both parties have seen increases in their relative interest neither of the increases are significant. From Aim Two, the only significant predictor of these relative interest increases is the relative interest of the other party in Kansas. While there is indication in the regression model that attending more Chiefs games has a positive effect on Taylor Swift’s relative interest, these effects are not significant. 

While we can’t definitely answer the central question based on this research, we can say that if Taylor Swift and Travis Kelce are using their relationship to increase their influence it hasn’t been working in any significant way. However, increases that have occurred could be the result of intersecting fan-bases due to the significant predictive power of the opposite party's relative interest in Kansas. Based on these conclusions and the analysis performed, I believe that their relationship is legitimate and we aren’t at risk for spending our money less rationally on Taylor Swift merchandise or Chiefs tickets. 

Some ideas that I think would build on this insight include: 

-Conducting U-testing with larger sample sizes to see if this decreases the significance of the before and after changes. 

-Using financial or economic data that is more intimately linked to Travis Kelce or Taylor Swift to complete the analysis.

-Conducting this analysis over a longer time period to see if any increases are sustained, and among which populations. 


## References
[1] Ashok K. Lalwani, Sharon Shavitt, You Get What You Pay For? Self-Construal Influences Price-Quality Judgments, Journal of Consumer Research, Volume 40, Issue 2, 1 August 2013, Pages 255–267, https://doi.org/10.1086/670034
[2] Zahoor, S. Z., & Shah, A. M. (2023). Impact of Social Media on Users’ Complex Buying Behaviour: Analysing the Mediating Effect of Perception and Moderating Effect of Extended Social Media Usage. Management and Labour Studies, 0(0). https://doi.org/10.1177/0258042X231167315

