# Project 1:  Benchmarking and Analysis of Network Functions

### Overview 
 
This project is a part of Master's curriculum. More details about the project can be found [here](https://en.cs.uni-paderborn.de/cn/teaching/theses-student-projects/student-project-groups-completed/ba). Network Function Virtualization (NFV) is a concept of making the network functions more flexible and manageable. Network functions such as proxy, load balancer etc. can be installed using container technology to meet the user demands. Such network functions are called Virtual Network Functions (VNFs).The main objective of the project is to The collected dataset and publish it to make it available for the research communities since there are very limited VNF performance profiles available. I was a part of benchmarking and analysis team where I was more inclined towards analysis of the data.  I worked on 2 network services namely Traefik and mitmproxy. However, here I give a brief overview and analysis of Traefik.

Traefik is an open-source Edge router that acts as a load balancer and a reverse proxy for TCP and HTTP-based applications and it can be configured automatically as well as manually. Traefik integrates easily with every major cluster technology such as Docker. I concentrated on configuring traefik as a load balancer and it is installed as an Ubuntu-based docker image to balance the incoming load among web servers. This experiment is also extended for the first time to use multiple connection points in tng-bench at the output. The experiment has been run under two different scenarios to compare the performance of VNF under various circumstances.


### Key outcomes

<ol>
<li> Created docker images for network services </li>
<li> Benchmarked the network services under various scenarios using a benchmarking tool called Tango-bench </li>
<li> Collected datasets which are then used for extensive exploratory data analysis </li>
<li> Analysed trends and patterns against different network services of same category for e.g. how do different load balancers such as NGINX, HAproxy, Traefik compare against        each other in terms of response time, handling requests per second etc.? </li>
<li> Extended the analysis to perform predictive analytics using Linear regression, random forest, SVM </li>
</ol>

### Analysis

##### Correlation matrix of traefik

Correlation helps in identifying the relationship between the variables. Having a more positive values indicates that the parameters are highly correlated and vice versa.

![](/benchmarking_and_performanceProfiling_of_Networkfunctions/correlation_traefik.jpg)

##### Comparison of traefik with other load balancers

![](/benchmarking_and_performanceProfiling_of_Networkfunctions/mean_time.jpg)

######  Observation: 
It is the time taken to respond to a request for service.  Having the least response time indicates better performance of a load balancers. According to the plot, the response time of NGINX is the least among others which means that it gives the quickest response for a request. This could be due to default caching in NGINX which other load balancers does not have. Traefik takes more time to respond to a request. A general trend is seen for all the load balancers - as the CPU bandwidth increases the mean time per request decreases.

##### Predictions

The predominant aim of using prediction models is to predict the required physical resources for a network service. Various regression techniques such as linear, random forest, SVM are tested.

![](/benchmarking_and_performanceProfiling_of_Networkfunctions/Linear_regression.jpg) ![](/benchmarking_and_performanceProfiling_of_Networkfunctions/Random_forest.jpg)
![](/benchmarking_and_performanceProfiling_of_Networkfunctions/SVM.jpg)

#### Comparing the prediction models

MSE, RMSE, MAE are error metrics which are used to compare the accuracy of the prediction models. According to the results, random forest performed better on the collected data set and very less prone to errors as compared to other prediction models. I concluded that random forest performs best for the collected data set of traefik and it can be used to predict the required resources. However, there is always room for improvement. There could be other models which may perform better than random forest.

![](/benchmarking_and_performanceProfiling_of_Networkfunctions/comparison.jpg)


# Project 2:  Classification: Loan eligibility prediction using Logistic regression and deploying the ML model using Flask on localhost

### Objective

To automatically analyze the loan application and approve or disapprove it based on the details. The main reason why I wanted to attempt this project is to learn how a ML model can be deployed. I have build several ML models, trained them and compared various metrics but I have never really put them to real use. So, in this project I wanted to explore how ML model can be deployed for an end user.
The dataset was obtained from [kaggle](https://www.kaggle.com/altruistdelhite04/loan-prediction-problem-dataset).

### Steps
* Preprocessed data to handle missing values
* Exploratory data anlysis to find correlating variables
* More than 12 independent variables such as education, marital status, gender, applicant income etc. and 1 target variable Loan status (to approve or not)
* I have chosen 3 only feautures [Education, Marital status, gender] to train the model
* Most of the feautures were categorical (Yes/No, Male/Female, Graduate/Non-graduate) -> hence, I encoded them as binary 0/1
* Logistic regression was used to train the ML model since its a classification problem.
* About 80% accuracy was obtained from the model
* The model was them deployed on localhost:5000 using Flask and simple HTML/CSS for template -> Reference: [Kdnuggets](https://www.kdnuggets.com/2019/10/easily-deploy-machine-learning-models-using-flask.html)
* The below picture shows final result of the deployment 
                                                                 
   ![](/loan_prediction/deployment.PNG)
   

# Project 3: Sentiment Analysis: Classifying amazon reviews using Logistic regression and Random forest classification

## Overview

This is a sentiment analysis project to classify amazon food reviews by customers into positive, negative and neutral.
The dataset is from [kaggle](https://www.kaggle.com/laowingkin/amazon-fine-food-review-sentiment-analysis).

### Steps
* I used wordcloud to perform analysis the data
* Assigned sentiment score based on ratings

    | Rating      | Sentiment         | Implication |
    | ------------- |:-------------:| -----:|
    | less than 3     | -1 | negative |
    | = 3     | 0      |   neutral |
    | greater than 3 | +1      |    positive |

* Handled missing data and dropped punctuations
* Converted text into vectors using CountVectorizer(sklearn)
* Since its a classification problem, logistic regression is used to classify into positive, negative or neutral sentiment
* Logistic regression and random forect achieved an accuracy of 87% and 91% respectively.

# Project 4: Linear regression to predict the price of a house

* Created a model to predict the sales price of a house based on total square feet
* The dataset is obtained from [kaggle](https://www.kaggle.com/c/house-prices-advanced-regression-techniques)
* Peprocessed the data and performed exploratory data analysis to find the infuencing variables
* Linear regression did not perform the best
   - Achieved an explained variance score (EVS) of less than 60%
   - indicates that other variables may influence sales price and not just total square feet
      ![](/images/LinearReg.jpg)

   
