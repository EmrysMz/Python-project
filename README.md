# Python-project : Online News Popularity

This project is part of the assessment for the "Python for Data Analysis" module in the first semester of the Master 1 "Data & Artificial Intelligence" at ESILV, 2023-2024.
Working in a group of two students, here Emrys MEZIANI and Sébastien MOINE from DIA5, we are required to apply what we have learned during lecture
and tutorial sessions, and more.
Two datasets were proposed to us, and we ultimately chose the one focusing on the popularity of online articles, "Online News Popularity".

The project involves analyzing the dataset, processing the data (data pre-processing),
visualizing the data to demonstrate the connection between the variables and the "target", which is the variable we wish to explain and predict.
The final aspect is the modeling of predictive models using the scikit-learn library, modifying and optimizing the hyperparameters, and comparing the results.
Additionally, we are asked to transform the predictive model of our choice into an API.
Finally, the team will have to present their topic to their tutorial professor during a reserved slot,with a PowerPoint
explaining the "ins" and "outs" of the problem, the thought process, the different variables, how the project aligns with the module, the results obtained, etc.

In short, the overall objective of the project is to provide a complete solution for analyzing data, developing an accurate predictive model,
and making it accessible via an API. This will allow us to solve the problem and obtain usable results.

Dataset : "Online News Popularity"

Citation :     K. Fernandes, P. Vinagre and P. Cortez. A Proactive Intelligent Decision
    Support System for Predicting the Popularity of Online News. Proceedings
    of the 17th EPIA 2015 - Portuguese Conference on Artificial Intelligence,
    September, Coimbra, Portugal.





## ********** Our results **********

	- 2 methods of cleaning the dataset : capped and deleted outliers (from 61 to 25 columns)

	- Treating the outliers, the correlated columns and merging columns if necessary to only keep the essential and most relevant

	- Regression : 5 models (LinearRegression, LassoRegressor, DecisionTreeRegressor, RandomForestRegressor, SupportMachineRegressor) applied on 1 dataframe
		- Best model : RandomForestRegressor has reached R² : 0.10 on the test set

	- Classification : 
		- Machine Learning : 4 models (DecisionTreeClassifier, KNNClassifier, GaussianNB (Naive Bayes), RandomForestClassifier) applied on 1 dataframe

			- Binary Classification : 'shares' divided in 2 parts at its mean value (about 1540 for the same dataframe)
				- Best model : RandomForestClassifier has reached 0.709 of accuracy on the test set (w/ GridSearch), and 0.72 of AUC (w/ GridSearch).

			- Multi-labels Classification : 'shares' divided in 5 parts using the quantiles (pd.qcut, on the same dataframe)
				- Best model : RandomForestClassifier has reached 0.33 of accuracy

		- Deep Learning : two ANN using Keras/TensorFlow for both classification methods (regression is not made for our data)
				- Binary ANN : 
						Binary Crossentropy Train : 0.561 || Accuracy Train : 0.712
						Binary Crossentropy Test  : 0.598 || Accuracy Test : 0.684
				- Multi-labels ANN : 
						Categorical Crossentropy Train : 1.468 || Accuracy Train : 0.355
						Categorical Crossentropy Test  : 1.533 || Accuracy Test : 0.313

	- Feature importance and the impact of the most importance features, on the model regarding their values.

	- Data visualisations to concoct the best recipe for a popular article.

	- Flask API linked to our RandomForestClassifier model (binary classification) : fill a form and get the prediciton on the popularity.



## ********** The recipe for a successful article **********

	- Title Length: Aim for a concise title with precisely 4 words.

	- Content Length: Ensure the article falls within the range of 1200 to 1400 words.

	- Word Metrics: 
		- Maintain a unique words ratio between 30% to 40%.
		- Try to keep in mind, when writing your article, to make the effort to write words of 4 to 5 letters.

	- Word Sentiment:
		- Strive for a higher global rate of positive words compared to negative words.
		- Positive words polarity should range from 20% to 60%.
		- Negative words polarity should range from -10% to -60%.
		- Aim for an overall global sentiment polarity of 0% to 33% positive.

	- Content Subjectivity: Keep the content subjectivity within the range of 30% to 60%.

	- Publication Timing: Optimal publishing day is Saturday.

	- Theme: Tailor the article content to revolve around social media (Socmed).

	- Multimedia Elements:
		- Include 6 images to enhance visual appeal.
		- Embed 2 videos for a dynamic and engaging experience.

	- SEO and Links:
		- Utilize 7 carefully chosen keywords to enhance search engine visibility.
		- Include 23 hyperlinks to relevant sources.
		- Ensure 7 self-referential hyperlinks within the article.
		- Aim for an average of 3000 to 3200 shares for articles linked within the content.
		  Overall, the more the articles you reference are popular and therefore widely shared,
		  the more your article will take on this same popular trend.


## ********** Conclusion **********
We tried our best to make the good decisions regarding the dataset. We passed a lot of time cleaning it, thinking about how to treat outliers etc...
but also on which visualitions are relevant for our goal : predictive models, relevant features and what make a good article.

We could have tried different ways of treating the outliers, but we have already seen that between capped outliers, and lines including outliers, deleted,
in the end the distributions were quite close (see boxplots).

We applied web scrapping as seen in class. We think that there must have been other resources that could have been relevant to scrape because we were lucky
to have all the URLs of each article, but even scraping the images and videos on 1000 instances would give us took time in terms of machine research,
and we hadn't taken the time to deepen our scrapping skills any further. But possibly a study on authors who have to come back often, with their jobs could have been useful.

Despite all our efforts, we are quite disappointed that we were unable to achieve much better results than those who published the dataset.
We had hoped to surpass the symbolic threshold of 75% accuracy in binary classification.
With a more in-depth study, stricter data cleaning, and perhaps a GradientBoostingClassifier, or XGBoost, or another models, this goal should be possible to achieve.

We believe that the quality of the dataset plays a significant role, and that certain columns
derived from NLP scores or unknown keywords with values that sometimes make no sense have affected the performance.

Similarly, we made it a point to sort the columns because we knew that regression is sensitive to multicollinearity.
Despite removing many columns that were not necessarily useful compared to their highly correlated counterparts,
the regression presented a very disappointing R² of only 10.0% on the test set.

Ultimately, this project has allowed us to gain better proficiency in Python, especially with Pandas, Matplotlib, Seaborn, and sklearn.
We had a lot of fun creating and comparing models, as well as implementing neural networks (ANN).
This project has strengthened our passion for programming, especially in the field of Data Science.
We sincerely believe that it is projects like these that not only enhance our skills but also confirm our interests and aspirations.

In conclusion, we would like to express our gratitude to Mr. SABRY Abdellah, our teaching assistant, for his dedication, availability, and good advice.
