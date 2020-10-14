# A Basketball tool to predict the player position
This project is the sequel of the recommendation tool that I built and I'm trying to provide more tools that can be helpful to a Basketball General Manager. In this project I create a classification model that can predict the position of a Basketball player. I started with a small data set and the target value was separated into the five main Basketball positions, I used the K Nearest Neighbor algorithm but my model was too simply and it was totally overfit. So, I used a bigger data set and I divided the target column in three parts Guards, Forwards and Centers aiming to achieve better results. Let’s start with an Exploratory Data Analysis and some thoughts that could be helpful for the Machine learning part. 

## EDA
The new data set was bigger than the previous one, more than 25000 rows and 52 columns. I was forced to drop some rows because I had many incomplete columns but my data set was still big.
The next step was to examine the correlation between the features and drop those that were the same such as, FGA, FG etc and low correlated features. 

![cor_matrix](https://user-images.githubusercontent.com/66875726/95019270-0a5cfc00-066d-11eb-99eb-0a77474abfbf.png)

Examining the Matrix I had some doubts about how the model can be able to recognise the forward position. Definitely, the center has the rebound and the block attribute, the guards the assist, turnovers and 3pa but which feature could distinguish the forwards. In order to find a unique feature I tried to visualize the three positions and compare the mean value of every feature. The feature that made the forwards stand out was the VORP (Value Over Replacement Player).

![VORP](https://user-images.githubusercontent.com/66875726/95019722-b3a4f180-066f-11eb-8a78-5d1ed5da383d.png)

I also used one more feature selection technique, the Univariate feature selection aiming to determine the relationship of the features with the target variable.

In addition, I realised that my target value had unbalanced observations and I used the resample method to balance them. After this procedure the total rows were 11000.  

Finally, I used a dimension reduction method, the Principal Component Analysis in order to visualize the data and identify clusters.  

![PCA](https://user-images.githubusercontent.com/66875726/95027556-262ec500-06a2-11eb-92f8-89399c9fc902.png)

less than 60% of the dataset’s variance ratio lies along the first two components and certainly I had lost a lot of information . I received a better Variance Ratio adding one more component. Below is a 3D graph with 68% Variance Ratio  

![newplot (4) (1)](https://user-images.githubusercontent.com/66875726/95482277-9c7b4200-0996-11eb-8993-0395492cebf6.png)


## Machine Learning

Let’s nowdive to the prediction part. As I said at the beginning I started with a small data set separated the target in five positions the model wasn’t able to classify five different positions. In order to achieve better prediction results I performed the following steps. Firstly, I exported a bigger data set, and I divided the target column to tree positions Guards, Forwards and Centers. Secondly, I picked the most relevant features based on the Univariate feature selection  technique and Lastly, I balanced the observations using the resample technique.

Initially, I trained a K Nearest Neighbor model with 3 neighbors and the model accuracy was 85%. Definitely, an impressive number considering that at my first model the accuracy was less than 60%.  Obviously, it’s necessary to compute the cross validation scores to prevent overfitting.The cross validation scores verified my concerns and I tried different K Values to overcome this issue. 

![K-nn](https://user-images.githubusercontent.com/66875726/95487170-a1db8b00-099c-11eb-8bb8-232aab467d24.png)

I picked K=14 in order to make the model more complex and prevent it from overfitting. My next step was to look at the F1 scores. My biggest concern became true, the predictions per position were Guards 81%, Forwards 67%, Centers 82%, the model was able to identify in a satisfactory level the Guards and the Centers but it had problems with the forwards position.

The next algorithm that I chose to train was a Decision Tree using the Bagging Ensemble technique. The results were the same as before, thus in order to improve the classifier I used the voting method and I achieved over than 70% at the forwards position.  

Finally, I was ready to examine the test data set, the result wasn’t unexpected the model’s accuracy was 77% and the F1 scores were 80% Guards, 68% Forwards and 83% Centers.
Although When I started developing the model my expectations were higher the result was at a satisfactory level considering the complexity of the problem. So,the question is what could I have done better in order to achieve better results. The main problem I think was at the features I haven’t had many attributes that could split better the positions, maybe features such as the player height and the dribbling time could be an improvement for this particular dataset.. 
