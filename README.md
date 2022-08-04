# Correlation-Analysis-in-R-programming
# Correlation Analysis in R programming ###
### Loading the libraries ###
pacman::p_load(pacman, rio, tidyverse)

### loading and preparing the dataset (Google search data)
### Selecting only the quantative variables
data <- import("StateData.xlsx") %>% as_tibble() %>%
  select(instagram:modernDance ) %>% print()
view(data)

## Correlation matrix 
cor(data) # this shows the correlation in a matrix form 

### Rounding the corelation in 2 decimal place 
data %>% cor() %>% round(2)

### Comparing one pair of variables at a time and this will give you
### the r, the hypothesis test and the 95% confidence interval 
cor.test(data$facebook, data$university)

### P value for matrix
### You will have to install Hmisc to obtain the p value for the matrix 
install.packages("Hmisc")
p_load(Hmisc)
 
### We will have to coerce or force the dataframes to get both the correlation matrix
### and the p-values in separate tables 

data %>% as.matrix() %>% rcorr()

