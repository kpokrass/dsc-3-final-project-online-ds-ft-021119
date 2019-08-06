
# World Happiness Index

## Happiness Feedback Loop
Since the publication of the Wealth of Nations by Adam Smith in the 1700’s, it has been thought that a nation’s wealth is directly proportional to its citizen's happiness. And for the most part, that is true as 15 of the top 25 happiest countries in 2019 are also in the top 25 countries with the highest GDP. Thus, most current governmental policies are focused on increasing GDP as the main strategy for promoting the happiness of its citizens. However, the [World Happiness Report](https://worldhappiness.report/), an annual publication from the United Nation’s Sustainable Development Solutions Network summarizing global happiness measures, has found that while the world is becoming richer as a whole there is still considerable unhappiness and that many of the most affluent nations are actually declining in happiness. In a sense, we now have data to prove the old saying that money can’t buy happiness.

To combat the socioeconomic burden of declining mental health, the Global Council for Happiness and Well-Being analyzes the findings and data from these reports with the aim of creating a framework for government policy makers to follow that will promote happiness in accordance with 17 sustainable development goals. These goals outline a holistic approach to the development of happiness by focusing on fostering equitable and inclusive economies, quality education, accessible healthcare, social protection, and the preservation of the natural environment. The council has found that not only do the policies of the happiest countries align with a majority of the sustainable development goals, but that the citizens of the happiest countries are also more prosocial, engaged in government, and productive. Essentially, happiness breeds more happiness. Because the Global Happiness Report’s initial publication was in 2012, the long-term effects of adhering to the sustainable development goals is unknown. But, being able to model happiness scores for a  nation will better inform that nation’s policy makers on developing a stable and productive environment for its citizens.


_It is heard time and time again that money can’t buy happiness. However, the main strategy for many countries to promote happiness is to increase its GDP. While these two statements seem contradictory, that line of thinking holds some truth as the happiest countries also have the highest GDP. But, this is not the whole story as the UN’s Global Happiness Report has found that many of the most affluent nations are actually declining in happiness. These reports indicate that the relationship between GDP and happiness is actually reversed due to the fact that happier people are more engaged and productive and that this increased productivity is what actually drives GDP growth._

<p align="center">
<img src="happy_feedback_loop.png" width="450" height="350">
</p>

This happiness feedback loop can be illustrated using Venezuela as a specific example to evaluate how happiness scores change in response to public policy as it has seen some dramatic changes in the past 10 years. In the 2015 Global Happiness Report, Venezuela was ranked 22nd with a happiness score of 6.8 (out of 10). Since then it has fallen 85 spots to 107th in the 2019 report and dropped its happiness score by 2.1 points. The dramatic decline of the happiness of this nation’s citizens is a direct result of it current socioeconomic crisis. Venezuela is currently experiencing shortages of basic goods, increased child mortality and disease, rapidly rising unemployment rates, and unprecedented hyperinflation. Understandably, Venezuelans are unhappy, which has led the the mass emigration of 3 million people to the surrounding countries.

_In 2014, it was ranked the 22nd happiest country in the world. Since then, it has fallen 85 spots to 107th and made international headlines with growing concerns over its current socioeconomic crisis._

<p align="center">
<img src="venezuela_loop1.png" width="750" height="450">
</p>

These three graphs represent the three points on the happiness feedback loop. The graph at the top of the screen displays the change in Venezuela’s socioeconomic equality from 2006 to 2018. The graph in the bottom right of the screen displays its happiness scores over that same time period and the graph in the bottom left displays its GDP. Beginning with GDP, we can see a sharp increase between 2006-2008. As Venezuela is one of the world’s leading oil exporters, this is most likely in response to the rebound of oil prices in the early 2000’s. This increase in revenue then funded numerous populist social policies that dramatically decreased wealth inequality, as shown by the steep drop in the yellow line in the top graph. This decrease in inequality corresponds with an increase in national happiness as displayed in the bottom right graph. 

<p align="center">
<img src="venezuela_loop2.png" width="750" height="450">
</p>

Happiness scores remained high until 2013, when a contested election following the death of Hugo Chavez and widespread corruption sent the country on its current downward spiral.  The sharp increase seen in the inequality measure aligns with the drastic decrease in both the nation’s happiness scores and GDP. To frame this in the context of the happiness feedback loop. Rising levels of inequality have lead to an unhappy and unproductive economy, which has in turn resulted in a decrease in GDP and thus fewer available funds to invest in prosocial public policies and projects.

## Model Stacking

<img src="stacked_schema.png">

The technique of stacked generalization, informally known as model stacking, was first proposed by by David H. Wolpert in 1992. Its basic schema can be thought of as multiple levels of generalizers, models that each have been trained to describe the characteristics of a population. Essentially, the data (a learning set of dimension (j,k)) is fed to n number of first-level generalizers. These first-level generalizers each make a prediction on the data to produce second-level data of dimension (j,n). This second-level data is then presented to the second-level generalizer, which produces the final predictions for the dataset. Of course, this schema could also be extended to more than two levels of generalizers if required by the particular problem being solved.

There are two main reasons why stacked generalization improves upon the performance of a single generalizer. First, the composition of the first-level generalizers allows for greater coverage/description of the total population. For example, let’s say our first-level has three generalizers, A, B, and C. Generalizer A describes 70% of the total population, whereas generalizers B and C describe 10% and 5%, respectively, of the total population. Because generalizer A does a good job of describing the population, generalizers B and C would be useless, or at best redundant, unless they described a portion of the population that was not covered well by generalizer A. By including generalizers B and C roughly 85% of the total population is described. Thus, combining the three first-level generalizers allows for a better generalization of the total population over any single generalizer alone.

Second, utilizing a second-level generalizer allows for a more sophisticated combination of the outputs from the first-level generalizers. Two common, unsophisticated methods for combining the outputs of the first-level generalizers are “winner-takes-all” and a simple average. The “winner-takes-all” approach would just base the final output on the first-level generalizer output that has the highest correlation with the correct value. In our example, this would be no different than simply using the output from generalizer A as the final output. The simple average method is just as it sounds in that the outputs of the three first-level generalizers are averaged together to produce the final output. Both of these methods fail to take into account the strengths and weaknesses of each first-level generalizer. By using a more sophisticated combination method (i.e. a second-level generalizer), the fringe cases covered by generalizers B and C can be combined with the majority of the population covered by generalizer A in a way that increases overall performance.


## Semi-Supervised Learning

<img src="semi-supervised.png">

Machine learning algorithms fall under two categories based on how they “learn” the data they are given; they are either supervised or unsupervised. In both supervised an unsupervised learning, the algorithm infers a function to describe the data it has been given. The main difference between the two learning styles is that the data used to train the supervised learning algorithm has an output value (also known as a supervisory signal or ground-truth label) in which the inferred function is trying to reproduce, whereas the data used to train the unsupervised learning algorithm does not have an accompanying output value. Thus, the unsupervised learning algorithms are using the training data to find similarities in the overall data structure and responds to the presence/absence of these similarities when presented with new data.

Labeled data, data that has an accompanying output value, is not always readily available in the real world. If the data exists without the label, people can be paid to undertake the painstaking, time-consuming, and expensive task of analyzing each observation and declaring the appropriate label. However, this option is becoming less realistic as the collection and demand for data reaches ever-increasing levels. For this reason, companies such as Google, Microsoft, and Facebook are turning to an approach called semi-supervised learning.

Semi-supervised learning utilizes a supervised learning algorithm trained on ground-truth labeled data to predict the output values of the unlabeled data. These predicted output values are called pseudo-labels for the unlabeled data and can be considered as accurate as the model that was used to predict them. For example, if the model used has 85% accuracy when predicting the output value of the ground-truth labeled data, it can be assumed that 85% of the generated pseudo-labels are correct for the unlabeled data. 

The theory behind using semi-supervised learning is that it allows access to a greater amount of data to use while training a model. The more training data a model has access to equates to better model performance because the underlying algorithm has access to more information about the inherent structure and trends present in the data. Thus, the algorithm will be better able to infer a function to describe the data.

## Model Structure and Performance

<img src="stacked_model.png">

The data used for this project was a collection of survey responses to the Gallop World Poll from the citizens of different nations from 2005 to 2018 covering topics such as life expectancy, perceptions of corruption, freedom of choice, and accessibility to social support. The model created to predict the global happiness scores from this data employed a stacking strategy where a collection of base-level classifying models make happiness score predictions, which are then presented along with the original data to a second-level classifying model to make the final happiness prediction. While the survey responses from the Gallop World Poll were accessible back to 2005 for most countries, only the most recent 5 years of happiness scores were available. Thus, this project utilized semi-supervised learning to generate pseudo-labels for the data collected prior to 2014. This decision was made with the aim of increasing model performance by increasing the amount of available training data.


## Conclusion

