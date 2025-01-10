---
title: "Bayesian Optimization in Biotech"
date: 2025-01-09T15:01:00
draft: false
author: "Divya Ramamoorthy"
tags:
 - Bayesian
 - Bayesian optimization
 - Iterative design
#image: /images/profile_picture.jpg
description: "Bayesian optimization in biotechnology"
toc:
---
##
<p align="center">
  <img src=/images/010925_bayes_opt_header.png />
</p>

**Biology is ripe for machine learning, but there remains one central limitation: biological data is often expensive to generate and time-consuming to collect.** This means that most companies trying to leverage machine learning are working with small datasets.

One of the most powerful paradigms in this small-dataset domain is **Bayesian Optimization.** This article breaks down what Bayesian Optimization is and explains how it can be applied to design experiments.

# Uncertainty in Machine Learning

Bayesian models are different than traditional models in that they explicitly represent uncertainty - when the model is less clear about it's predictions. For example, if you are using AI for self-driving cars or medical diagnoses, you want the model to signal when it’s unsure of its predictions so that a human can step in to double-check.

Uncertainty in machine learning typically arises from two sources:

1. **Aleatoric uncertainty**: Caused by inherent noise in the data. This could be due to experimental error, mislabeled samples, or natural variation.
2. **Epistemic uncertainty**: Arises when the model is asked to make a prediction on a case  with little data to base the prediction on.

Bayesian models account for both types of uncertainty, adjusting their confidence at each prediction point based on the quality and amount of available data.

## What is Bayesian Optimization?

Many machine learning models are designed for large datasets, but in biology, we often need models tailored for small datasets. **Bayesian Optimization** is a sequential design strategy that works by iteratively running small experiments. This approach aligns well with how scientists naturally run experiments: screening a small number of molecules, analyzing patterns and designing the next set of molecules, and running the next experiment, until they reach their goal.

Let’s illustrate Bayesian Optimization with a real-world biology example. Imagine we’re a biotech company trying to identify the most potent antibiotic from millions of candidates. Screening all of them is infeasible, so we’re limited to testing 50 samples at a time. Here’s how Bayesian Optimization helps:

1. **Select an initial dataset**: Start by choosing 50 molecules from the library. If we don’t know which properties impact potency, we can select them randomly. Alternatively, we can ensure diversity by picking molecules with different properties.

2. **Build a surrogate model**: Using the initial dataset, build a Bayesian model (also called a surrogate model) to correlate the properties of the antibiotics with their potency. This model highlights areas where predictions are less confident.

3. **Calculate an acquisition function**: The acquisition function balances two objectives:

    - **Exploration**: Since we’ve only sampled a small part of the design space, we want to test other molecules in our library where the model is less confident.
    - **Exploitation**: We also want to prioritize molecules that the model predicts will be highly potent.

    Common acquisition functions include the **Upper Confidence Bound** (a weighted sum of exploitation and exploration) and **Expected Improvement** (the likelihood that a sample will outperform the current best).

    In our antibiotic example, this function provides a mathematical basis for selecting molecules that are likely to improve both the model’s understanding and potency predictions.

4. **Iterate**: Use the acquisition function to select the next set of 50 molecules, test them, and refine the model. Repeat until you achieve the desired results or the model suggests that further improvement is unlikely.

## Limitations of Bayesian Optimization

One significant limitation of Bayesian Optimization is the trade-off between cost and time. The approach requires multiple iterative steps, which can extend timelines. If the design-build-test cycle is lengthy, the time cost may outweigh the financial savings. Factors to consider include the duration of each experimental round, the cost per sample, the size of the design space, and the distance from the target.

## Conclusion

Bayesian Optimization is a powerful tool for experimental design, particularly in biology. With small, noisy datasets and expensive experiments, this method enables thoughtful, resource-efficient screening. Moreover, because it aligns naturally with how scientists run wet-lab experiments, it’s often easier for organizations to adopt. Companies can avoid the significant risk of sinking resources into large datasets, quickly gauging whether the model is providing meaningful improvements without wasting resources. Ultimately, Bayesian Optimization not only accelerates discovery but also empowers researchers to make smarter, data-driven decisions in the face of uncertainty.
