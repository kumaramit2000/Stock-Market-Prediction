# Stock-predection
## Abstract
Stock market prediction is the act of trying to determine the future value of a company stock or other financial instrument traded on an exchange. The successful prediction of a stock's future price could yield significant profit. The efficient-market hypothesis suggests that stock prices reflect all currently available information and any price changes that are not based on newly revealed information thus are inherently unpredictable. Others disagree and those with this viewpoint possess myriad methods and technologies which purportedly allow them to gain future price. With the advent of the digital computer, stock market prediction has since moved into the technological realm. The most prominent technique involves the use of artificial neural networks. ANNs can be thought of as mathematical function approximators. The most common form of ANN in use for stock market prediction is the feed forward network utilizing the backward propagation of errors algorithm to update the network weights. These networks are commonly referred to as Backpropagation networks. Also in recent year there is a significant improvement in SVM (Support vector machine Algorithm) implementation for stock prediction. Another form of ANN that is more appropriate for stock prediction is the time recurrent neural network (RNN) or time delay neural network (TDNN). One of the modified version of RNN is LSTM which memorize history data for prediction. Keeping this details in mind in this project I tried to predict stock trend. Also to the result includes conclusion for what algorithm performs well compare to the other two.

## Approach
Our approach to for this project consist of major steps:

1. Dataset creation
2. Implementation of algorithm
3. Result and analysis

## 1.	Dataset creation :
For data collection I used yahoo finance. Yahoo Finance is a database with stock prices for various companies. Most of the companies I chose were in the sector of technology. Ex. Apple, Google, Yahoo, Microsoft etc. I collected data from January 2010 to December 2016. The stock market took a toll during 2007-2008 financial crisis. This time around, companies went in loss and stock data of companies completely unpredictable. Training our model using this data would cause our model to be less accurate because of a lack of trend during the crisis period. So I avoided data that can result into uncertain behavior

The data set contains stock data of the following companies:

*   Yahoo
*   Microsoft
*   Apple
*   Google
*   Lenovo
*   Intel
*   HP
*   Amazon
*   Oracle

For our problem I kept technology and software services as a sector. For that sector I tried to predict trend and behavior of stock.
These are all listed on the same index Nasdaq. The stock data obtained from yahoo contains the following parameters:

*   Date
*   Open
*   High
*   Low
*   Close
*   Adj Close
*   Volume

I took the daily closing values of each of the stock as the stock value for a day.

**Other parameters calculated for input dataset:**
Basic assumption in stock market is that stock momentum, increase or decrease will depend on how given stock was doing in past. Also, the stock price for given company will also depend on how market is doing and how given sector is doing. Keeping these three things in mind I calculated 5 attributes as listed below.

*   Index_Momentum
*   Index_Volatility
*   Sector_Momentum
*   Stock_Momentum
*   Stock_Price_Volatility
*   Output

**Momentum:** If price of stock or index in higher than yesterday then momentum for given day is +1 as there is an increase in price else it’s -1.

**Volatility:** Represents how big or small change in stock /index closing values. Try to capture fluctuation in market. For given day Volatility is calculated using difference between yesterday's closing value - today’s closing value divide by yesterday’s closing value.

**Index_Momentum:** Calculated based on market performance for last 5 days. It’s an average of 5 days index momentum.
Index_Volatility: Calculated as average of last 5 days Volatility for index.

**Sector_Momentum:** Calculated based on sector performance for last 5 days. It’s an average of 5 days index value for all technology company shares.

**Stock_Momentum:** Calculated as average for last 5 days momentum for given company momentum

**Stock_Price_Volatility:** Calculated as average of last 5 days for given stock.

For all attributes I kept 5 days as to capture market behavior. In future I will try change this for 10, 15 days and see if there is any improvement in accuracy. Once I calculated this attributes for each company I consolidated all dataset and created final input dataset.

**Output:** If closing stock price for a stock today day is more than yesterday’s closing stock price for the same stock, then the corresponding output is denoted by 1 else it is denoted as 0.

Hence. one record of our input data set had the following 6 dimensions:

*   Stock Price
*   Index_Momentum
*   Index_Volatility
*   Sector_Momentum
*   Stock_Momentum
*   Stock_Price_Volatility
*   Output

Data set consisted of these 6 dimensions for each of the stocks. I.E. each day has 9 records, one record for each company stock. The total number of rows for our input data set are around 15800.

## 2. Algorithms :

### a) Back Propagation:
Back Propagation Algorithm can be used for both Classification and Regression problem. Here, Stock Price Prediction is a Classification problem. I have Implemented Back Propagation algorithm for stock price prediction using Numpy and Pandas lib. Back propagation, an abbreviation for "backward propagation of errors", is a common supervised learning method of training artificial neural networks used in conjunction with an optimization method such as gradient descent. The gradient descent method calculates the gradient of a loss function with respect to all the weights in the 	network. Back propagation calculates the gradient of the error of the network regarding the network's modifiable weights. This gradient is used in a simple stochastic gradient descent algorithm to find weights that minimize the error.

Back Propagation is a multilayer feed forward network. A Multilayer feedforward neural network is a network that consists of input layer, one or more than one hidden layer and one output layer. A neural network that has no hidden layer is called 	a Perceptron. In Back Propagation the input layer is connected to the hidden layer by interconnection weights and hidden layer is connected to the output layer by interconnection weights. The increase in number of layers results in the computational complexity of the neural network. As a result, the time taken for convergence and to minimize the error may be very high


## 3. Result and analysis :

To make sure that one algorithms has a consistent performance and it performs better than other I tried to run same algorithm multiple times. Each algorithm was implemented 30 times and for each time prediction accuracy is calculated on test data. For each run different training and testing dataset is used. Find below accuracy results for each algorithm.

**Backpropagation Result:**
For 30 runs of Backpropagation algorithm I got around 65.38 mean accuracy with standard deviation of 2.40. As you can see Backpropagation performs well compared to SVM but it has huge fluctuation in accuracy so that might cause issue when I want steady accuracy.
![BackPropagation Run](Images/Backpropagation%20Run.jpeg)

T-0.95(58) = +- 1.701

T test value for 95% accuracy for 30 epoch run was in range of +-1.701 (If the value for each pair is under that range that means chances of getting improvement is 0.05% with those pair algorithms). As you can see backpropagation and SVM implementation T result falls under that range I can say that chances of getting better result from backpropagation compare to SVM is very less as there is big variations for each run in backpropagation.

## Conclusion:

In this project, I have demonstrated a machine learning approach to predict stock market trend using different neural networks. Result shows how I can use history data to predict stock movement with reasonable accuracy. For this implementation, I would like to conclude that if I incorporate all the factors that affect stock performance and feed them to neural network with proper data preprocessing and filtering, after training the network I will be able to have a model which can predict stock momentum very accurately and this can result into better stock forecasting and profit for financial firms.
