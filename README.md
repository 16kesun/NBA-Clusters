# NBA-Clusters
Clustering 2018-2019 NBA player into modern roles
ddd

# Get Data
I used selenium webdriver to scrape various tables from NBA.com. These tables include Hustle, Post, Cut, Pull-up, Catch-Shoot, and Possession

Hustle: These stats describe a players effort level. Includes deflections, contested shots, loose balls recovered.

Post, Cut, Pull-up, Catch-Shoot: These four categories represent different ways a player scores points. Catch-Shoot means you shoot the ball as soon as you have it (no dribbling). Pull-up means you dribble before you take the shot. Post means you have your back to your deffender before you shoot the ball. Cut means you make a run at the basket without the ball and the ball handler gets you the ball close to the hoop for an easy lay-up. Since these four all fall under the category of scoring, they share the same stats. Pull-up will be differentiated with "p" and catch-shoot with "cs". Stats include points, field goals attempted, field goal percentage

Possession: These stats describe what a player does with the ball. Stats include average dribbles per touch, time of possession, touches in the paint, touches near the elbow

# Data Cleaning
I filled in missing values with zeros and made numeric all the necessary stats. Some columns also had "%" in them so I removed the "%" and converted them into decimal values. Next I had to differentiate between certain post, cut, pull-up and catch-shoot stats that had the same column names. Lastly I dropped columns that appeared in all the tables (except for player name, which I will use to join my tables) such as games played and team, and joined the tables into one.

# EDA
I built a heatmap to inspect which of my feaatures are highly correlated with one another.

I looked at barplots with teams on the x-axis to determine how successful and unsuccessful teams play the game differently. For example, Golden State (highly successful) has the lowest average time of possession, while Dallas (unsucessful) has the highest average time of possesion. 

I also looked at scatterplots to determine if relationships exist between certain features. For example, a positive correlation exists between contested three point shots and deflections, indicating that effort may be an underlying factor when it comes to a player's performance in these two categories.

Lastly I looked at the age distribution of the league and looked at how age affects player performance on certain stats.

# Clustering
I used K-means clustering to group the players into new roles. I looked at an elbow plot to find the optimal amount of clusters, but it indicated two, which would not help accomplish my goal of defining modern player roles. So using domain knowledge I was able to group the players into 9 different roles, which I labeled Inside/Outside, Elite Ball Handler, Solid Big, Go-to Scorer, Bench Inside, Bench Perimeter, Shooter, High Effort, and Benchwarmer.

Inside/Outside: Players who are comfortable with scoring close to the rim as well as far away (Aaron Gordon, Andrew Wiggins, Brandon Ingram).

Elite Ball Handler: Players who usually play away from the basket and average high possession stats. Also able to score effectively (Donnovan Mitchell, Mike Conley, Kyle Lowry)

Solid Big: Players who play close to the basket, average high post-up and cut frequencies (Andre Drummond, Clint Capella, Deandre Jordan).

Go-to Scorer: Essentially the biggest stars in the league, able to create their own shots and average high possession stats (Lebron James, Kevin Durant, Kyrie Irving).

Bench Inside: Includes developing and declining big men. Majority of their points come from cutting and catch-shoot. (Semi Ojeleye, Jarret Allen, Tyson Chandler).

Bench Perimeter: Developing and declining players who play away from the basket. These players do not post up nor do they make cuts and average a relatively high time of possession when compared with the other groups (Markelle Fultz, Isaiah Thomas, Jodie Meeks).

High Effort: Players who average high effort metrics such as deflections and contested shots (Andre Iquodala, Caris Lavert, Avery Bradley).

Benchwarmer: Players who barely play over ten minutes per game and average a low number of starts. Lowest performing group for the majority of features (Jimmer Ferdette, Greg Monroe, Ryan Anderson).

# Cluster Analysis
First I created a bar chart showing the performance of my clusters when it comes to standard stats (Points, Assists, Rebounds, Blocks, Steals, Three pointers).

I also made radar charts for each cluster using time of possession, cut points, pull-up points, catch-shoot points, and post points to look at the scoring tendencies of the groups. By examining these figures I was able to conclude that big man play was being phased out of the league. Looking at the Bench Inside cluster, we can see that these players tend to favor the catch-shoot method of scoring. In fact, the traditional weapons for big men (cutting and posting) tend to be the least popular method accross all clusters, while catch-shoot (indicative of perimeter play) is the most popular method.

Lastly I created two functions, one where you input a player and the function returns the cluster the player belongs in and another where you input a team and the function returns the players on that team, the cluster of each player, and a count plot for each cluster for that team.
