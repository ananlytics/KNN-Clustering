# KNN-Clustering Using R-Programming
## Clustering Data to apply KNN-Classification on Iris Dataset.


```ruby
# Installation of Packages (directly load them if already installed)
install.packages("e1071")
install.packages("caTools")
install.packages("class")
install.packages("ggplot2")
```
## We will use four libraries for this projects.

```ruby  
# Loading above installed packages 
library(e1071)
library(caTools)
library(class)
library(ggplot2)
```
## We are using iris dataset(available on R).

```ruby  
# Viewing first few rows of the data
data(iris)
head(iris)
```
```ruby  
# Splitting data into training and testing data sets

split <- sample.split(iris, SplitRatio = 0.8)
train_cl <- subset(iris, split == "TRUE")
test_cl <- subset(iris, split == "FALSE")
```
```ruby  
# Feature Scaling
train_scale <- scale(train_cl[, 1:4])
test_scale <- scale(test_cl[, 1:4])
```
```ruby  
# Devising Model Fitness using Training Data set (80% if available data)
classifier_knn <- knn(train = train_scale,
                      test = test_scale,
                      cl = train_cl$Species,
                      k = 1)
``` 

## We can use different K-Values and check accuracy. Generally best accuracy is near Knee point.

```ruby                      
classifier_knn
  
# Confusion Matrix
cm <- table(test_cl$Species, classifier_knn)
cm
  
# Model Evaluation - Choosing K
# Calculate out of Sample error
misClassError <- mean(classifier_knn != test_cl$Species)
print(paste('Accuracy =', 1-misClassError))
  
# K = 3
classifier_knn <- knn(train = train_scale,
                      test = test_scale,
                      cl = train_cl$Species,
                      k = 3)
misClassError <- mean(classifier_knn != test_cl$Species)
print(paste('Accuracy =', 1-misClassError))
  
# K = 5
classifier_knn <- knn(train = train_scale,
                      test = test_scale,
                      cl = train_cl$Species,
                      k = 5)
misClassError <- mean(classifier_knn != test_cl$Species)
print(paste('Accuracy =', 1-misClassError))
  
# K = 7
classifier_knn <- knn(train = train_scale,
                      test = test_scale,
                      cl = train_cl$Species,
                      k = 7)
misClassError <- mean(classifier_knn != test_cl$Species)
print(paste('Accuracy =', 1-misClassError))
  
# K = 15
classifier_knn <- knn(train = train_scale,
                      test = test_scale,
                      cl = train_cl$Species,
                      k = 15)
misClassError <- mean(classifier_knn != test_cl$Species)
print(paste('Accuracy =', 1-misClassError))
  
# K = 19
classifier_knn <- knn(train = train_scale,
                      test = test_scale,
                      cl = train_cl$Species,
                      k = 19)
misClassError <- mean(classifier_knn != test_cl$Species)
print(paste('Accuracy =', 1-misClassError))

```
### Plotting model to visualize:Once we have identified best K-value, we can plot model to generate insights.

![1](https://user-images.githubusercontent.com/104814594/170922428-97f0479e-ecc6-4a24-8bda-31a04713cf4e.JPG)
