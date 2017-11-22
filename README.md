# Discrimination in Machine Learning

A hands-on demonstration of how applying machine learning can lead to discrimination.
Without being cautious in selecting data and applying learning algorithms, resulting models can
make decisions that are either hostile to certain groups of people or ignore their needs.

The demo features example datasets and a guided path through running "real" machine learning code
using [Python](https://www.python.org/) and [scikit-learn](http://scikit-learn.org/) through
visual and interactive [Jupyter notebooks](http://jupyter.org/).

The datasets and code here are only "real" in sense that they're working software, illustrating
issues in machine learning using technologies that are now part of the mainstream IT industry.
However, they are intentionally trivial examples for demonstration purposes and don't reflect
industry-standard techniques or the more subtle issues that arise in actual projects.

## Our project: an automated job applicant reviewer

We're implementing an automated resume reviewer to help our
company's HR department filter graduate job applicants. Since competition for talent is fierce,
management wants this rolled out fast. So we grab some historical data and plug it into an
easy-to-use open-source toolkit. Sounds pretty straightforward, right?

We represent applicants using these attributes:

* *University*
* *GPA*
* *Tribe* (use fictional tribes 'A', 'B', 'C', 'D')
* *Postcode*
* *Income*

Our training/test set will capture these attributes for previously-hired graduates along with
an *Approval* flag indicating whether they were a "good" hire. We'll use this approval flag to
train our model: our goal is to predict whether someone is a good hire and mark their resumes
for further consideration.

Click here to open the notebook: [notebook.ipynb](notebook.ipynb)

As you step through it, you'll see how a machine learning model is trained and tested using the
historical recruitment data - and the kinds of discrimination we encounter as we try variations
of the model.

## Stepping through kinds of bias

1. Train a basic model on all features. Point out incorrect predictions for tribe 'B' and show
   how we don't have enough data (e.g. only 1 record in the training set).
1. Retrain model with data covering all tribes. Show that results discriminate against tribe 'C'.
   This strongly suggests a personal bias from recruiters in the current manual hiring process.
1. Retrain model without including the *Tribe* attribute. Show that it still discriminates
   against people from tribe 'C'! How does *Postcode* correlate with *Tribe*?
1. Retrain the model just on *University* and *GPA*. Show the results.
   Does this avoid discrimination? What about correlation of *Tribe* with
   *University* and socioeconomic factors?
