# A Basketball tool to predict the player position
This project is the sequel of the recomandation tool that I built and I'm trying to provide more tools that can be helpful to a Basketball General Manager. In this project I create a classification model that can predict the position of a Basketball player. I started with a small data set and the target value was separated into the five main Basketball positions, I used the K nearest neighbor neighbor algorithm but my model was to simply and it was totally overfit. So, I used a bigger data set and I divided the target column in three parts Guards, Forwards and Centers aiming to achieve better results. Let’s start with an Exploratory Data Analysis and some thoughts that could be helpful for the Machine learning part. 

## EDA
The new data set was a lot bigger than the previous one, more than 25000 rows and 52 columns. I forced to drop some rows because I had many incomplete columns but my data set was still big.
The next step was to examine the correlation between the features and drop features that was the same such as, FGA, FG etc and low correlated features. 
