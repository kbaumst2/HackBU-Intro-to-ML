# HackBU-Intro-to-ML

## Getting Started
Welcome to HackBU's Introduction to Machine Learning workshop! Today, we'll be covering some commonly used machine learning algorithms. To get started, make sure you have Python 3 (and optionally Git) installed. If you need help at any point, please ask one of the organizers for help!

## Part 1: Machine Learning with scikit-learn
### Part 1a: Finding and Exploring a Dataset
The first step to developing a good machine learning algorithm is using a good dataset. Many of the most accurate machine learning algorithms have millions if not billions of entries in their training data sets. Fortuntately for us, there are many robust datasets we can use to build our ML algorithms. 

The scikit-learn library comes with some good starting datasets. For today's activity, we'll be using the digits dataset, which contains images of handwritten numerical digits. To use this dataset, we'll import the load_digits function from sklearn.datasets and store it in a variable called digits.

```
from sklearn.datasets import load_digits
digits = load_digits()
```

To get a better sense of what we're working with, let's take a look at the attributes of `digits`. If we add the following line to our code:
```
print(dir(digits))
```
we can see that the digits dataset has 5 attributes - DESCR, data, images, target, and target_names. If we want to know even more about the dataset, we can add
```
print(digits.DESCR)
```
which prints out the description of the dataset.

For thoroughness, we can print the shape of the dataset with
```
print(digits.data.shape)
```
which shows that the dataset has 1797 rows and 64 columns.

We can also use the Python library matplotlib to display the images in this dataset. Add the following code:
```
import matplotlib.pyplot as plt 
plt.gray() 
plt.matshow(digits.images[0]) 
plt.show() 
```

to your script and run it. You'll see an image like

## TODO: Add image

You can find other useful datasets in the [official scikit-learn documentation](https://scikit-learn.org/stable/datasets/index.html).

### Part 1b: Implementing a Machine Learning Algorithm
For now, we'll start off with two regression-based algorithms for supervised learning - Linear Regression and Logistic Regression.


We'll start by importing both algorithms from scikit-learn.
```
from sklearn.linear_model import LinearRegression, LogisticRegression
```

Now, we're going to split the data into two sets - a training set and a testing set. The training set will be used to train the machine learning algorithms, whereas the testing set will be used to verify the accuracy of the machine learning algorithms. 


To better visualize this relationship, think of a time where you studied for a math exam by completing practice problems. Then, you tested your knowledge by completing the exam. The practice problems you completed were your training set, and the real exam was the testing set. **It is imperative that you keep your training and testing sets separate during the training process** - if your machine learning algorithm is tested with a data point it's already seen before, it may report a testing accuracy that is higher than it actually is.


Thankfully, scikit-learn gives us a method for automatically splitting up our full dataset into smaller training and testing sets.

```
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(digits.data, digits.target, test_size=0.50, random_state=42)
```

In the above example, we import the `train_test_split` method from scikit-learn's `model_selection` sublibrary and use it to generate four smaller arrays:
`X_train`, a two-dimensional array containing a certain amount of entries from the main dataset. Does not include the expected outcome of each data entry.
`Y_train`, a one-dimensional array containing the expected outcome of each data entry in `X_train`.

`X_test`, a two-dimensional array containing a certain amount of entries from the main dataset. Does not include the expected outcome of each data entry.
`Y_test`, a one-dimensional array containing the expected outcome of each data entry in `X_test`.


🤔 **Food for Thought:** It can be tough to find a good ratio between the training and testing set size. In this case, we split it evenly (`test_size=0.5`), but many algorithms use much smaller testing set sizes (closer to 0.2). Although it may be tempting to improve your algorithm's accuracy by increasing the size of the training set, also consider that this will increase the margin of error of your testing accuracy.


Let's 

