# Using-Autoencoder-For-Dimensionality-Reduction-to-Obtain-Higher-Accuracy-in-Pytorch
Project for Intro to Deep Learning @ IU. Task was to combine two machine learning methods. I combined and autoencoder with a basic feed-forward neural network. Autoencoder was used to reduce dimensions of data, and the ANN was used to make predictions about the data. The use of the Autoencoder led to about a 10% increase in test accuracy.

# Data

The data was obtained from the UCI Machine Learning Repository (https://archive.ics.uci.edu/ml/datasets/bank+marketing). The data was gathered from a Portuguese banking institution marketing campaign, regarding whether or not individuals subscribed a term deposit. The dataset has sixteen different features: age (age), job (job), marital status (marital), education (education), whether the individual has credit in default (default), balance (balance), a housing loan (housing), or a personal loan (loan), their contact communication type (contact), the month (month), day (day), the duration of the last contact (duration), number of contacts performed during the campaign (campaign), the number of days since the individual was contacted by a previous campaign (pdays), the number of contacts performed before this campaign (previous), and the outcome of the previous campaign (poutcome). The target value (y) is a binary value, denoting whether or not the client has subscribed to a term deposit. 

# Data Preprocessing

Thankfully, there were no missing values in the dataset, thus imputation was not required. The first step of data preprocessing, then, was to normalize the continuous features (age, balance, duration, campaign, and previous) so that they lie between 0 and 1. Once this was done, one-hot encoding of the categorical features (job, marital, education, contact, month, and poutcome) was also required. Finally, the binary features (default, housing, loan, and the target) required discretization. The day feature was deleted, which described the day of the month, because it seemed unimportant. 

# Model Building & Fine-Tuning (Autoencoder & ANN)

First, the Autoencoder was built, to reduce the dimensions of the training set. The Autoencoder had eight layers with sizes 32, 16, 8, 2, 8, 16, 32, and 46, respectively. Thus, the aim was to reduce the data to just 2 dimensions. I used the Tanh activation function instead of ReLU, because when I used ReLU, a large portion of the reduced data consisted of zeros (because ReLU sets and number >= 0 to 0). I used the mean squared error loss function, with a learning rate of 1e-6 and a weight decay of 0.5. I trained the autoencoder for 15 epochs and got a loss of 0.39. The dimension reduced data is visualized below
