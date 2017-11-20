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

## Step 1: Starting out with our automated résumé reviewer

Here we introduce our machine learning project: an automated resume reviewer to help our
company's HR department filter graduate job applicants. Since competition for talent is fierce,
management wants this rolled out fast. So we grab some historical data and plug it into an
easy-to-use open-source toolkit. Sounds pretty straightforward, right?

Link to notebook: [machine-learning.ipynb](machine-learning.ipynb)

---

## Ideas for classifier design

Represent applicants using these attributes:

* *University*
* *GPA*
* *Race* (use fictional races 'A', 'B', 'C', 'D')
* *Postcode*
* *Income*

Our training/test set will capture these attributes for previously-hired graduates along with
an *Approval* flag indicating whether they were a "good" hire. We'll use this approval flag to
train our model: our goal is to predict whether someone is a good hire and mark their resumes
for further consideration.

## Ideas for stepping through kinds of bias

1. Train a basic model on all features. Point out incorrect predictions for race 'B' and show
   how we *don't have enough data* (e.g. only 3 records with other features inconclusive).
   * **Lession:** We say it's accidental, then this is a cautionary tale about its impact
     if you don't check.
   * **Action:** Add this data in for next step (say we had it all along, we were just holding it
     back to illustrate the "lack of data" bias)
   * **Alternative action:** What if it revealed bias in the recruitment process because there
     were genuinely almost no hires? Should we react
     by excluding people identifying as race 'B' from automated processing and decide manually
     -- with new HR protocols -- since we don't have enough data?
     Or do we add in some data from an industry source, noting it won't have our own company's approval ratings? What are the implications of these?
1. Retrain model with data covering all races. Show that results *discriminate against race 'C'*.
   * **Lesson:** We say it's deliberate and that this strongly suggests a personal bias from
     recruiters in the current manual hiring process.
   * **Action:** We suggest making our model "blind" to race by excluding that attribute from
     training.
1. Retrain model without including the *Race* attribute. Show that it *still discriminates*
   against people from race 'C'!
   * **Lesson:** Illustrate how this happens because *Postcode* and *Income* are enough to
     deduce *Race*.
     There is redundancy in our data set, meaning we don't actually achieve being "blind".
   * **Action:** Exclude both attributes since they are "personal" and not relevant.
     Could current income correlate with someone's ability (better people more highly paid)?
     Does postcode correlate with someone's travel time and could our
     approval rating embed some consideration of punctuality?
1. Retrain the model just on *University* and *GPA*. Show the results.
   * **Lesson:** Does this avoid discrimination? What about correlation of *Race* with
     *University* tuition and socioeconomic factors? How well-represented are some universities
     vs. others in our original dataset? (Maybe we need to rig it so we're not just repeating
     the lack-of-data bias again. Could hinge of *Approval* rating instead?)

After the demo:

1. Maybe show Google Research page with interactive illustrations on [Equality of Opportunity
   ](https://research.googleblog.com/2016/10/equality-of-opportunity-in-machine.html) or
   maybe demographics post from [Moritz Hardt's blog
   ](http://blog.mrtz.org/2016/09/06/approaching-fairness.html) as extension ideas?
