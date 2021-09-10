---
layout: single
title: Chapter 2

mathjax: true
author_profile: false

categories:
   - Machine Learning
   - ISLR
---
{% include toc title="Contents" %}

# Case Study

## Description and Goal

We are investigating the association between advertising and sales of a particular product. We will use the **Advertising** data set. This data set consists of **sales** in 200 different markets along with advertising budgets for the product in each of those markets for 3 different media: **TV**, **radio** and **newspaper**. 

It is not possible for our client to directly increase sales, rather we can help them by analysing if there is an association between sales and advertising methods and if such an association exists, how to adjust advertising budgets, thereby indirectly increasing sales. In other words our goal is to develop an accurate model that can be used to predict sales on the basis of the 3 media budgets.

## Setting
The advertising budgets are *input variables* while sales is an *output variable*.  The input variables are typically denoted using the symbol $X$, with a subscript to distinguish them. So $X_1$might be the TV budget, $X_2$ the radio budget, and $X_3$ the newspaper budget. The inputs can go by different names, such as *predictors*, *independent variables*, *features*, or sometimes just *variables*. The output variable is often called the *response* or *dependent variable* and is typically denoted using the symbol $Y$.

<figure>
  <img src="/assets/images/posts/2021-09-08-islr-chapter2/salesVsAdvertising.png" alt="" style="width:100%">
  <figcaption>Figure 1: This plot displays <b>sales</b>, in thousands of units, as a function of <b>TV</b>, <b>radio</b> and <b>newspaper</b> budgets, in thousands of dollars, for 200 different markets.</figcaption>
</figure>

In general, suppose that we observe a quantitative response $Y$ and $p$ different predictors, $X_1,\dots,X_p$. We assume that there is some relationship between $Y$ and $X = (X_1,\dots,X_p)$, which can be written in the very general form

$$\begin{equation}
Y = f(X) + \epsilon
\end{equation}$$

Here $f$ is some fixed but unknown function of $X_1,\dots,X_p$, and $\epsilon$ is a random error term independent of $X$ and has mean zero. $f$ represents the *systematic* information that $X$ provides about $Y$.

# Why estimate $f$?

2 main reasons to estimate $f$: ***Prediction*** and ***Inference***.

## Prediction

In many situations, a set of inputs $X$ are readily available, but the output $Y$ cannot be easily obtained. We can predict $Y$ using: 

$$\begin{equation}
\hat Y = \hat f(X)
\end{equation}$$

where, $\hat f$ represents our estimate of $f$, and $\hat Y$ represents the resulting prediction for $Y$ and is often treated as a *black box*.

**Example**

Suppose $X_1,\dots,X_p$ are characteristics of a patient's blood sample that can be easily measured in a lab, and $Y$ is a variable encoding the patient's risk for a severe adverse reaction to a drug. In this case it is natural to seek to predict $Y$ using $X$, since then we can avoid giving the drug in question to patients who are at high risk of an adverse reaction - that is, patients for whom the estimate of $Y$ is high.

The accuracy of $\hat Y$ depends on 2 quantities - Reducible and Irreducible Error

**Reducible Error**

In general $\hat f$ will not be a perfect estimate. However, we can get the best estimate by using a variety of statistical techniques to minimise the error and get $\hat f \approx f$. However it is not possible to form a perfect estimate as there will always be some error in the function due to the nature of $f$ where $f$ depends on $\epsilon \neq 0$ as well.

**Irreducible Error**

The $\epsilon$ is the irreducible error and arises due to data. One more thing to notice is that this quantity cannot be determined with $X$. Therefore variance of $\epsilon$  also affects the accuracy of $\hat f$. No matter how accurately we estimate $f$, we cannot reduce this error. This error can arise due to non measurable variance or missing data.

Let us now consider the expectation of error given a $\hat f$ and $f$

$$\begin{equation}
\begin{aligned}
E\left[Y - \hat Y\right]^2 &= E\left[f(X) + \epsilon - \hat f(X)\right]^2 \\
&= \left[f(X) - \hat f(X)\right]^2 + \text{Var}(\epsilon)
\end{aligned}
\end{equation}$$

Here $\left[f(X) - \hat f(X)\right]^2$ is the reducible error and $\text{Var}(\epsilon)$ is irreducible error or the variance associated with the error term.

## Inference

We use this when we want to understand the association between $X$ and $Y$. In this situation we cannot keep $\hat f$ as a black box, as we will need to know it's exact form. In this setting, we might be interested to answer the following questions:

1. Which predictors are associated with response? ⇒ Most important features that are associated with $Y$?
2. What is the relationship between the response and each predictor? ⇒ Correlation of predictors and output?
3. Can the relationship between $Y$ and each predictor be adequately summarised using a linear equation or is the relationship more complicated?

In a real world setting, generally we tend to model for both prediction and inference. 

**Example**

Inference ⇒ How much extra will a house be worth if it has a view of a river?

Prediction ⇒ Is the house over-valued or under-valued?

# How to estimate $f$?

Many linear and non-linear methods share certain characteristics. The set of observations that we use to train our model is known as the **training data**. 
Let $x_{ij}$ represent the value of the $j^{th}$ predictor, for observation $i$, where $i\in[1,n],\ j\in[1,p]$. Correspondingly we will have a $y_i$ represent the response variable of the $i^{th}$  observation. Then our training data consists of $$\left\{(x_1,y_1),\dots,(x_n,y_n)\right\}$$ where $$x_i = \left(x_{i1},\dots,x_{ip}\right)$$

## Parametric Models

Parametric models involve a 2-step model based approach - 

1. First, we make a assumption about the functional form, or shape of $f$.  For example one very simple assumption is that $f$ is linear in $X$:

    $$\begin{equation}
    f(X) = \beta_0 + \beta_1X_1 + \dots + \beta_pX_p
    \end{equation}$$

    This is a linear model. Once we have assumed that $f$ is linear, it becomes easier to estimate as we only need to estimate $(p+1)$ coefficients $$\left\{\beta_i: i \in \left[0,p\right]\right\}$$

2. After a model has been selected, we need to determine a procedure that uses the training data to **fit or train** the model. In case of linear models, the most common approach is to use the **least squares method**.

Referred to as parametric as it reduces the estimation problem to just estimating a set of parameters which is generally much easier to do. One of the disadvantages of such models is that if the assumption of the shape of the model is wrong, the estimation of the model will be poor and the data will be **underfit**. We can try to address this problem by using flexible models which can fit many different functional forms, but the issue with this is that this can lead to **overfitting**  the model, which essentially means they follow the errors, or **noise**, too closely.

## Non-Parametric Models

Non-parametric methods do not make explicit assumptions about the function form of $f$, instead we seek an estimate of $f$ that gets close the data points without being too rough or wiggly. Any parametric model brings with it the possibility of the $1^{st}$ assumption being wrong which will result in a bad fit. But since we do not estimate only a small set of parameters, a large number of observations is required.

# Measuring Quality of Fit

We need a measure to quantify the fit of the model or in other words, the extent to which the predicted response value for a given observation is close to the true response value for that observation. One of the most common measure used is called the Mean Square Error (MSE) - 

$$\begin{equation}MSE = \frac 1 n \sum_{i=1}^n\left(y_i - \hat f(x_i)\right)^2
\end{equation}$$

MSE will be small if predicted response are very close to the true responses. 

The MSE in $(1)$ is called the training MSE as it was calculated using training data. However, **we are more interested in the accuracy of the predictions that we obtain when we apply our method to previously unseen test data**. 

**Example** - When we develop a model to predict stock prices, we do not care about predictions about previous week's stock prices, but rather the price of a stock tomorrow or next month

> More formally, we want to develop a model $\hat f$ such that $\hat f(x_0)$ is approximately equal to $y_0$ where $(x_0,y_0)$ is a previously unseen test observation not used to train the model. We want to choose a model with lowest test MSE as compared to lowest training MSE.

# Bias-Variance Trade-Off

The expected test MSE for a given value $x_0$ can always be decomposed into the sum of 3 fundamental quantities 

$$\begin{equation}
E\left(y_0 - \hat f(x_0)\right)^2 = \text{Var}\left(\hat f(x_0)\right) + \left[\text{Bias}\left(\hat f(x_0)\right)\right]^2 + \text{Var}(\epsilon)
\end{equation}$$

1. The variance of $\hat f(x_0)$
2. The squared bias of $\hat f(x_0)$
3. Variance of error $\epsilon$

> This equation tells us that in order to minimise the test error, we need to have a model that can have both low bias and low variance at the same time.

## Variance

Variance is the amount by which $\hat f$ would change if we estimated it using a different training data set. Since the training data used to fit the model are different, we would get $\hat f$ for each training set. Ideally, $f$ should not vary too much between these training sets. 
High variance generally leads to overfitting of the data, meaning the if the data changes, the model function will also change significantly. 

## Bias

Bias refers to the error that is introduced by approximating a complex problem using a simple model. For example - Linear Regression almost always has high bias, as we rarely see linear relationships in data. Ideally we would always want a more flexible method to reduce bias.
High bias leads to underfitting the data.

## General Rule

As a general rule, more flexible methods, variance increases and bias decreases. The relative rate of change of these 2 quantities determines whether the test MSE increases or decreases.
As we increase the flexibility of a class of methods, the initially bias tends to decrease faster than the variance increases. Consequently the test MSE decreases.

# Error Rate

$$\begin{equation}\frac 1 n \sum_{i=1}^nI(y_i \neq \hat y_i)\end{equation}$$

Here $\hat y_i$ is the predicted class label for the $i^{th}$ observation using $\hat f$.  $I(y_i \neq \hat y_i)$ is the indicator variable that equal $1 \iff y_i \neq \hat y_i$ and $0 \iff y_i = \hat y_i$. Therefore this equation computes the fraction of incorrect classifications. 

# Bayes Classifier

We assign each observation to the most likely class, given its predictor values. In other words, we should simply assign a test observation with predictor vector $x_0$ to the class $j$ for which the conditional probability $\text{Pr}(Y=j \mid X=x_0)$ is largest. This is known as the **Bayes Classifier**. We get a **Bayes Decision Boundary** in the case of binary classification that separates the 2 classes. The overall Bayes error rate is given by: 

$$\begin{equation}1 - E\left(\max_j\text{Pr}(Y=j\mid X)\right)
\end{equation}$$

where the expectation averages the probability over all possible values of $X$. This Bayes error rate is analogous to the irreducible error.

Bayes classifier is not always possible as we almost never know the distribution of $\text{Pr}(X\mid Y=j)$ which is necessary to calculate this. Therefore the Bayesian Classifier is a golden standard for classification.