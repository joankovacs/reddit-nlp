
            ______          _           _     _____ 
            | ___ \        (_)         | |   |____ |
            | |_/ / __ ___  _  ___  ___| |_      / /
            |  __/ '__/ _ \| |/ _ \/ __| __|     \ \
            | |  | | | (_) | |  __/ (__| |_  .___/ /
            \_|  |_|  \___/| |\___|\___|\__| \____/ 
                          _/ |                      
                          |_/                       
        
        
TABLE OF CONTENTS:
    [0] PROJECT PARAMETERS & DESCRIPTION
    [1] REVIEW OF SUBMISSION FILES
    [2] PROBLEM STATEMENT
    [3] REVIEW OF PROCESS & METHODOLOGY
    [4] RESULTS AND CONCLUSIONS
    

    **Note of Importance**  To whom it may concern:
This project tackles what I believe to be one of the ethical gray areas at best, black 
area at worst, in data science.  So that this concern does not appear to be buried in 
some subsection of my project, but instead to communicate that this idea has been at the 
forefront of my mind throughout the project, I believe that it is fitting that this note
be added to the beginning of the project description.  For additional information, refer
to Section [2]: Problem Statement.


Without further ado...
==========================================================================================
SECTION [0]:  PROJECT PARAMETERS & DESCRIPTION


The core intent of this project was to create a dataframe of two different subreddits and
build a model that could distinguish between them, then to create a problem statement
postulating a real-world implementation of usefulness and presenting that to the class.

The following steps were undertaken by myself, N.A. Kovacs:  Scraping two subreddits and
creating a dataframe, with all necessary EDA & cleaning;  Testing four different 
gridsearches to find the most efficient model of differentiation;  Making a problem 
statement that uses the model;  Scraping three different subreddits and running the model 
on them to see if the model extrapolates;  Scraping three additional subreddits and 
comparing the Author IDs from one;  dataframe to the next to find author correlations;
Creating a presentation and presenting it to the class.

For additional details & information, refer to section [3].



==========================================================================================
SECTION [1]:  REVIEW OF SUBMISSION FILES


    README.txt -
This file.

    rubric.txt - 
A breakdown of the class-provided rubric, used as a personal checklist.

    project_3_core.ipynb - 
The primary model-building & datascraping notebook that fulfills the core requirements of
the project, complete with annotations & descriptions of each step.  This was the notebook
where the method of scraping, compiling, cleaning, and model construction was established.

    Folder: /data_core - 
Three dataframes were saved as .csv files here so that if a problem occured during the
process, the data would not have to be re-scraped (a time-consuming process):  the Boston
subreddit pulls, the NYC subreddit pulls, and the concatenated dataframe of both of them
together.

    project_3_locations.ipynb - 
Once reliable functions & methodologies for creating a model were established, this
notebook was used for the exploration of the problem statement & the ultimate conclusions
of the project.

    Folder: /data_loc - 
Three dataframes were saved as .csv files here so that if a problem occured during the
process, the data would not have to be re-scraped (a time-consuming process):  the Boston
subreddit pulls, the NYC subreddit pulls, and the Chicago subreddit pulls.

==========================================================================================
SECTION [2]:  PROBLEM STATEMENT


Concept: "Can we use location-specific subreddits to create a model that distinguishes the
location of a user, and then extrapolate that model so that it works on users that do not
participate in location-specific subreddits?"

Purpose: Ostenisbly, as portrayed in my presentation, the purpose of such an activity is
that determining the location of anonymous internet users could have a great deal of
marketable utility.  HOWEVER, MY INTENT WOULD NEVER BE TO MARKET SUCH A SOLUTION BECAUSE I
BELIEVE THERE ARE GRAVE ETHICAL IMPLICATIONS TO THIS SORT OF BEHAVIOR.  
    I have been quite struck by the ethics portions of this class, receiving such examples 
of misbehavior as Cambridge Analytica accumulating personality information based on social
media posts & Target targeting expectant mothers for specific advertising before their
families even knew, based on browsing history.  Furthermore, when exposed, these entities
neither recanted nor reconsidered, instead doubling down - such as Target moving to
"innocuously" mix in pregancy-targeted ads with other ads so as to avoid notice.  What 
struck me the most about these examples was how incredibly accessible this sort of 
analysis seems to be - there's a great deal of NLP & stats modelling open source resources 
everywhere, and it is taking us only three months of intense work to be considered career
ready for these activities.  Thus, it seems that the primary limiting factor of the good
or ill that can come from our actions is NOT limited by our skills, but instead limited by
our VISION.
    We do not have the benefits of centuries or millenia (or even the sort of game-theory
morality that has run in our genes since life began) to develop a sense of morals around
these behaviors that have developed around such ideas as bribery, treason, theft, or 
murder.  
    The purpose of this project was not just to fulfill the class requirements as written,
but to test the limits of my (and my classmates') own capabilities in a safe environment.
Just we should know the ins and outs of gun safety - up to and including firing the gun -
in order to safely own such a weapon, as data scientists we should practice such exercises
and be aware of the implications.  Just because I missed the target the first time I chose
to fire does not mean this weapon is any less powerful.



==========================================================================================
SECTION [3]:  REVIEW OF PROCESS & METHODOLOGY


The exact process & methodology of this experiment was as follows:

[a-0] Create functions for efficiently scraping subreddits and test them;
[a-1] Scrape two subreddits and explore & clean the data;
        **Note: for the initial model, both submissions & comments were used.
[a-2] Compile the two subreddits into a dataframe of FEATURES:
        ["body"]:  The body of text in the submission or comment,
        ["subreddit"]:  The subreddit from which the body came from;
[a-3] Explore some of the most common words from each subreddit;
        **Note: I perceived the common words as largely "generic" and didn't derive a lot 
            of use from this exercise.
[a-4] Run some initial models to test their efficacy prior to time-consuming GridSearch
        **Note: Throughout all testing, models suffered from a high degree of overfitting
            regardless of what combination of hyperparameters given.
        MULTINOMIAL NB - The default parameters of which yielded the highest accuracy.
        KNN - Terribly ineffective, which was largely expected.
[a-5] Run several gridsearches to find high performing models:
        MULTI NB - Unsurprisingly continued to be the most effective.  A great deal of
            successive hyperparameters searching was conducted to find the most effective 
            construction, but none of these performed substantially better than defaults.
        KNN - Gridsearching improved the scores noticeably but it was still the worst.
        EXTRA TREES - Used instead of Random Forest because the gridsearches were taking
            a very long time and Extra Trees runs quicker, albeit less accurately.  How-
            ever the results were not within such a range that I thought switching to 
            Random Forest might beat Naive Bayes' score.  This model probably could have
            benefitted the most from increased time & attention in hyperparameter search
            from me.
        SVM - Given that this was supposed to be the gold standard of data science until
            neural nets, I was excited to try this out for the first time on some real
            world data.  It performed second only to Naive Bayes, which was pretty cool to
            see.  Spent some time engaged in intensive hyperparameter searching but was
            unable to break the ~64% accuracy in testing data barrier.  It would be
            very interesting to see how this model would perform on other types of data
            we've worked with, such as linear and log regressions.

We have now established that one can determine whether an author is posting on r/boston or
r/nyc based on the word content of their posts.  This brings us to the second phase of the 
project: extrapolation.
            
[b-0] Create a second Jupyter notebook in order to keep the data more accessible;
[b-1] Use slightly modified functions to scrape r/boston, r/nyc, and r/chicago;
        **Note: for this iteration, only comments were used.
[b-2] Create a database from the three pulls with FEATURES:
        ["author"]: the Reddit username of post author,
        ["body"]:  The body of text in the submission or comment,
        ["subreddit"]:  The subreddit from which the body came from;
[b-3] Use Naive Bayes to test three-category predictions (still perform ~17% above base);
[b-4] Pull comments & authors from three different popular non-locational subreddits;
[b-5] Create a database from the three pulls with FEATURES:
        ["author"]: the Reddit username of post author,
        ["body"]:  The body of text in the submission or comment;
[b-6] Create a set{} of all users from the first and second databases;
[b-7] Get the intersection of the set such that we have a corpus of posts & users that we
        know the "location" (which city subreddit they post on) of these users;
[b-8] Run the model on this intersection to see if the model can predict the "location" of
        posts from the SECOND dataframe based on the content of the posts themselves.



==========================================================================================
SECTION [4]:  RESULTS AND CONCLUSIONS

Ultimately, in step [b-8] of the process, the model did not extrapolate to the intersect-
ion of users.  It was unable to accurately predict the location of known users.  However
there are several noticeable gaps in the thoroughness of the project as defined below:
    [a] Lemmatization & stemming: The words were not lemmatized because I wanted to keep
            the word choices of the users "authentic" - users from different locations may
            use differences in word forms.  This nuance may have been lost in the process
            of lemmatization.  By the time it was determined that the model didn't work
            anyways, there wasn't enough time to work in effective lemmatization to the
            pipeline.
    [b] Poor city choice: Chicago, Boston, and New York City are all northeastern or middle
            northern regions, and they are all cities.  Perhaps if more disparate cities
            (West vs East, or North vs South) were chosen, the model would have been able
            to differentiate better.  In addition, it may have been better to chose states
            as subreddits rather than cities, to avoid some of the commonalities of major
            cities that may lead to commonalities of communication.
    [c] One cultural source:  All data fed to the model was drawn from one website: Reddit.
            Despite the vastness of Reddit, there may be some commonalities of culture
            between all users of a given website that make it harder to distinguish region-
            al differences.
    [d] Small intersections:  Despite having a set{} of many thousands of users, there
            weren't very many overlapping users between the city reddit users and the most
            popular subreddits on Reddit.  Perhaps the data I was working with for the
            intersection wasn't particularly good.
    
As a result, I am not convinced that my methods can't be used to determine certain traits
about a user, even if those traits aren't necessarily location.  Location may not have a
huge impact on word choice, but traits such as sex, ethnicity, or age groups might be
derived from certain word choices - with similar or even more severe concerns about the
ethical implications.  

















