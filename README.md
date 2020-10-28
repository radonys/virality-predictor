# Virality Predictor for CI&amp;T DeskDrop Kaggle Data

### About

The project studies the virality of articles based on attributes like title, content, and counts of likes, views, bookmarks, comments and followers based on the [CI&T DeskDrop Data](https://www.kaggle.com/gspmoreira/articles-sharing-reading-from-cit-deskdrop) available on Kaggle.

I use a combination of text mining and tabular data using TF-IDF vectors to combine text and numerical data together to feed it into a machine learning models. Further details of the project are discussed below.

### Running the Project

The project can be executed by following the steps below:

1.	Extract the ZIP folder.
2.	Open Terminal with the path set to the extracted folder.
3.	Install Python "virtualenv" by executing ```sudo pip install virtualenv``` in Terminal.
4.	Set up a Python 3 virtual environment by executing ```virtualenv -p python3 env3``` and activate it by ```source env3/bin/activate```.
5.	Once in the virtual environment, install the requirements by executing ```pip install -r requirements.txt```.
6.	Simply execute the file ```python virality_predictor.py``` to see the results.

### Project Details

#### Virality Metric

VIRALITY = 1 * VIEW + 4 * LIKE + 10 * COMMENT + 25 * FOLLOW + 100 * BOOKMARK

#### Features Considered

I conducted experiments with two sets of features to build the predictor model. The first set of features considered only the counts of the following parameters for each article: Bookmarks, Comments Created, Views, Likes, and Followers. The relationship between the above parameters and Virality was analyzed using the correlation matrix which indicated that Bookmark has the highest correlation with Virality as justified by the coefficient in the Virality formulation.

The second set of features included the above counts along with 100-feature length TF-IDF values obtained by combining title and text (title + text string concatenation) and fitting a TF-IDF vectorizer.

#### Models Used

Since the Virality metric calculation involved a linear equation with all independent variables being linear, Linear regression was used as the template model. Along with this, 3 other models were used for experimentation mainly Polynomial Regression (with degree 2), Random Forest and Lasso.

The intuition behind selecting Polynomial Regression was to study any existing non-linear relationship between independent (features) and dependent (virality) variables.

Random Forest was selected primarily because of decision trees and it’s proven performance in regression and classification tasks (especially for text and tabular data).

Lasso is generally used for feature selection and drops variables of less significance to make a concise model and hence it was used for the experimentation.

#### Evaluation Metric

The evaluation metrics used in the model analysis was R2 value, Root-Mean Square Error (RMSE) and Mean Absolute Error (MAE). The reason behind using R2 value is its significance as it explains the variability of the dependent variable (virality) by the independent variables collectively.

The RMSE value showcases the error between actual and predicted values and emphasizes large errors (usage of squared values) while the MAE is also an error measure but easy to interpret as it is the mean of absolute difference between actual and predicted values.
The error metrics help to understand the performance of the model as a model with less error is more desirable.




