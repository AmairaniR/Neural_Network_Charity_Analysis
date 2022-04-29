# Neural_Network_Charity_Analysis

## Overview 

This repo implements a deep learning neural network binary classifier using tensorflow capable of predicting whether applicants will be successful if funded by the non-profit organization AlphabetSoup. Different optimization techniques are then applied to the initial model to attempt to reach a target predictive accuracy higher then 75%.

## Results 

-Data Preprocessing 

    -Target variables for model: 'IS_SUCCESSFUL'

    -Feature variables for model: 'APPLICATION_TYPE', 'AFFILIATION', 'CLASSIFICATION', 'USE_CASE', 'ORGANIZATION', 'STATUS', 'INCOME_AMT', 'SPECIAL_CONSIDERATIONS', 'ASK_AMT'

    -Non feature/target variables removed from input data: 'EIN', 'NAME'

-Compiling, Training, and Evaluating Model

    -For the intial model I selected 2 hidden layers with 80 and 30 neurons respectively, activated with the relu activation funciton. I selected 80 neurons for the first layer since it was about double the number of input features. I selected the relu function since it is the most common. For the output layer I selected one neuron and the sigmoid activation function since the target is a binary classifier. ![nn_summary](https://github.com/AmairaniR/Neural_Network_Charity_Analysis/blob/main/images/nn_summary.png)

    -The initial model was unable to achieve the target model performance of 75%. The inital model's performance was 0.73609. ![nn_accuracy](https://github.com/AmairaniR/Neural_Network_Charity_Analysis/blob/main/images/nn_accuracy.png)

    -To increase model performance I dropped the 'SPECIAL_CONSIDERATIONS' feature and I bucketed the 'ASK_AMT' feature to only two values. Then I created a function to use with the kerastuner library to run through several hyperparameters for the new optimized model. Kerastuner ran through models with the activation functions relu, tanh, and sigmoid. The hyperparameter for the neurons for the first layer ran between 80 and 120 neurons in steps of 10. The hyperparatmeter for the hidden layers went all the way up to six layers with neurons between 10 and 60 in steps of 10. The best hyperparameter returned by kerastuner was a model with the relu activation function, seven hidden layers, 110 neurons, in the first layer, and 20, 10, 10, 20, 40, and 10 for the respective remaining layers. ![nn_model_function](https://github.com/AmairaniR/Neural_Network_Charity_Analysis/blob/main/images/nn_model_function.png) ![nn_model_kerastuner](https://github.com/AmairaniR/Neural_Network_Charity_Analysis/blob/main/images/nn_kereastuner.png)  

## Summary 

Overall, the deep learning neural network model, even when optimized, was unable to reach target performance accuracy. However, not all optimization techniques were exhausted, it is possible to rerun the model with a higher number of epochs, additional hidden layers, and the binning can be changed to reduce the number of features. The splitting of the data can also be changed so more of the data is included in the training set. Ideally, more data points would also make for a better model. 