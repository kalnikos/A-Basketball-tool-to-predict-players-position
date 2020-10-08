# A Basketball tool to predict the player position
This project is the sequel of the recomandation tool that I built and I'm trying to provide more tools that can be helpful to a Basketball General Manager. In this project I create a classification model that can predict the position of a Basketball player. I started with a small data set and the target value was separated into the five main Basketball positions, I used the K nearest neighbor algorithm but my model was to simply and it was totally overfit. So, I used a bigger data set and I divided the target column in three parts Guards, Forwards and Centers aiming to achieve better results. Let’s start with an Exploratory Data Analysis and some thoughts that could be helpful for the Machine learning part. 

## EDA
The new data set was bigger than the previous one, more than 25000 rows and 52 columns. I forced to drop some rows because I had many incomplete columns but my data set was still big.
The next step was to examine the correlation between the features and drop those that was the same such as, FGA, FG etc and low correlated features. 

![cor_matrix](https://user-images.githubusercontent.com/66875726/95019270-0a5cfc00-066d-11eb-99eb-0a77474abfbf.png)

Reading the Matrix I had some doubts about how the model can be able to recognise the forward position. Definitely, the center has the rebound and the block attribute, the guards the assist, turnovers and 3pa but which feature could distinguish the forwards. In order to find a unique feature I tried to visualize the three positions and compare the mean value of every feature. The feature that made the forwards to stand out was the VORP (Value Over Replacement Player).

![VORP](https://user-images.githubusercontent.com/66875726/95019722-b3a4f180-066f-11eb-8a78-5d1ed5da383d.png)

I also used one more feature selection technique, the Univariate feature selection aiming to determine the relationship of the features with the target variable.

In addition, I realised that my target value had unbalanced observations and I used the resample method to balance them. After this procedure the total rows were 11000.  

Finally, I used a dimension reduction method, the Principal Component Analysis in order to visualize the data and identify clusters.  

![PCA](https://user-images.githubusercontent.com/66875726/95027556-262ec500-06a2-11eb-92f8-89399c9fc902.png)

less than 60% the dataset’s variance ratio lies along the first two components. I received a better Variance Ratio adding one more component. Below is a 3D graph with 68% Variance Ratio  

![newplot (4) (1)](https://user-images.githubusercontent.com/66875726/95482277-9c7b4200-0996-11eb-8993-0395492cebf6.png)
