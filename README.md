# Neural_Network_Charity_Analysis

## Overview

The purpose of this project was to examine a CSV of over 34,000 businesses containing a number of descriptive features including funding amounts and whether or not those businesses ultimately succeeded, and to use neural networking in order to try and predict the likelihood of new businesses failing, in a bid to try and prevent lost investments.

## Analysis

### Data Preprocessing

- The target variables for this model is the "IS_SUCCESSFUL" column in the "charity_data.csv" file. Because it is binary, with a 0 meaning no success and a 1 meaning success, it's simple to try and predict.
- The feature variables for this model are the "APPLICATION_TYPE" and "AFFILIATION" columns. They were the only two variables that, when removed, led to a decrease in accuracy of any kind.
- The erroneous variables that served no purpose were the "EIN", "NAME", "ASK_AMT", "ORGANIZATION", "USE_CASE", "INCOME_AMT", "CLASSIFICATION", "STATUS", and "SPECIAL_CONSIDERATIONS" columns. When removed, they either had a near-zero effect on the accuracy of the neural network, or gave a significant boost to accuracy.

### Compiling, Training, and Evaluating the Model

- For this project, we used three hidden layers aside from the output layer. The first used 100 neurons activated by a tanh function; the second used 20 neurons, also activated by a tanh function; the third used 35 neurons and was activated via a softplus function; and the output layer used a single neuron activated by a sigmoid function. We found that, when put together, the two layers that activated via tanh function greatly increased the accuracy of the model and prevented significant loss in the process, and that the softplus function on the third hidden layer provided better results than a relu function. Neurons for each layer were chosen at levels where adding more neurons wouldn't provide any additional bonus or risk oversampling. Although the code doesn't show it, different neuron levels were attempted over 100 times, and the one we settled with was the best we could muster.
- Unfortunately, we could not get the accuracy past 72%. We tried numerous options, from messing with neuron levels and activation functions to adding and removing further columns from the neural network, but at the end of the day, a consistent 72% is much better than a random accuracy between 30% and 65%.
- In order to try and maximize accuracy, we attempted removing single columns at a time and running the neural network to see how well or how poorly the accuracy would turn up. When different runs of the neural network with the same parameters started giving significantly different values (i.e. 0.40 and 0.65), we knew we had to find what was causing so much noise. As it turns out, the main driving factor was the "ASK_AMT" column, whose values were wildly throwing off the neural network's results. After that was solved, it came time to test the hidden layers to try and get the activation functions just right and tweak the numbers of neurons for each layer in order to try and maximize the accuracy of the neural network. We eventually couldn't optimize that any further. From there, it was a matter of weeding out columns that consistently reduced the accuracy of the neural network. This, as previously stated, only mustered up about 72% accuracy at most.

### Summary

All in all, the deep learning model was inconsistent. It needs significantly more training than any other machine learning model, and has a frequent habit of oversampling even when trained otherwise. This much could be seen while working with the code: There would be times where we would run the same neural network three times and get wildly different results, and times where we couldn't reasonably decide if an action was beneficial for maximizing accuracy or not, on account of the range that the results would fall into depending on the time of day. In truth, a logistic regression model would work better, preferably done with an ensemble system in place, as most of the problems with the deep learning model stemmed from every last bit of trial and error being something that could have been dealt with better through an ensemble system.
