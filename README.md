# Improving search result relevance with emotional modelling and social engagement metrics. CS152 Final Paper  



## Abstract

This paper proposes an improved user experience for web search through the
incorporation of emotional modelling into search result ranking, as a case study for exploring the
role of cognitive modelling to create artificial intelligence algorithms that can have higher utility.
First, the need for current use cases and potential applications of cognitive modelling in artificial
intelligence agents and algorithms is discussed. Then, these arguments are examined in the
specific context of Google’s web search engine. Existing research about cognitive modelling in
AI is discussed, then 2 novel approaches of implementing cognitive modelling are discussed -
the first through examining affinity of emotional and personal entities and category of the result,
and the second through examining the quantity and quality of social engagement. For each of
these approaches, the overview, intuition, high-level system design and limitations are
discussed. The emotional and personal affinity approach is then tested on a limited domain
through, and the responses received through Pagerank and the emotional and personal affinity
approach are tested.

## Background - Artificial Intelligence

Artificial Intelligence is the field of creating algorithms that can model or outperform
human intelligence. Russell & Norvig categorize Artificial Intelligence into 4 quadrants - thinking
rationally, acting rationally, thinking humanly and acting humanly. Generally, thinking rationally
simplifies to following logical syllogisms, acting rationally refers to making the choice that yields
the highest expected value, even in the absence of complete information, acting humanly refers
to passing the Turing test and thinking humanly refers to modelling the human thought process
through cognitive and emotional modelling, and deriving a conclusion based on this model.
Currently, large sections of artificial intelligence is dedicated to logical modelling and
decision making. Examples of this include machine learning, image classification and
recommender systems. These are oriented towards problems with logical outcomes, such as
creating autonomous cars and automating decision-making in various fields. However, even
within these fields, as more progress is made towards an eventual working solution, there are
increasing concerns around ethical concerns. For example, if a self-driving car has to make a
choice between killing it’s passenger or 2 jaywalkers, which would it choose? Many of these
ethical dilemmas are difficult to logically model because human decision-making is highly
emotional but tends to be justified after-the-fact with logical reasoning that does not hold up to
further scrutiny. This phenomenon of how humans think has been described as a “emotional
dog with a logical tail” by scholars. Therefore, research on emotional modelling could prove
highly useful to creating machines that are able to navigate more ambiguous decisions.


While we have discussed the applications of emotional modelling in situations with
logical outcomes, cognitive modelling has significant and immediate implications for several
consumer-facing products and problems where the problems do not have clear logical
outcomes. Current applications of emotional modelling in artificial intelligence are in creating
chatbots and in synthesizing market research. Other situations with ambiguous outcomes where
emotional modelling could improve outcomes are content recommendation, human resource
performance optimization and any sort of integration between artificially intelligent agents and
human agents in natural language environments - ranging from therapy to mentorship to
teaching. Advancements in such integrations would greatly increase the adoption of artificial
intelligence agents in highly personal and personalized environments.

## Background - Search Engine

Currently, Google’s search engine primarily utilizes a pagerank algorithm to determine
the credibility of a website. A web page’s Pagerank can be summarized as a product of the
quantity and quality of incoming links into that website. Pagerank is supplemented by over 200
other factors such as social media engagement and domain diversity. However, according to
Dan Russell, a senior search scientist at Google, Google does not currently conduct any
emotional modelling of either the query or the results. This does not hold any discernible effects
when modelling queries with logical responses. In this case, Pagerank serves as an efficient
dictionary, serving the logical answer to the question. However, it leads to heavy confirmation
bias or just an imperfect search result when applied to queries that are more personal,
emotional or ambiguous where the user may not know exactly what he or she is looking for.
This ineffectiveness is apparent in 2 use cases familiar to the author - queries about health
(mental and physical) and queries about advice.
In health-related queries, Google’s search engine returns results that are tangentially related but
suggest conditions that are often significantly worse than reality. For example, a search on “Why
do I feel tired” returns “​nemia, diabetes, hypothyroidism, hepatitis C, sleep apnea, obstructive
sleep apnea, chronic fatigue syndrome, urinary tract infection, food sensitivities, heart disease,
depression, anxiety disorder, and nasal congestion” ​ as possible reasons. This is a result of the
logic-centered pagerank approach to delivering a result with the highest quantity*quality of
incoming links. Similarly, queries related to advice, such as “Should I go to grad school”, return
highly general results that do not take into consideration the user’s major, country, city or
income level, and thus provide highly unspecific results. The user will need to search several
variations of the search in order to piece together the information that would help him or her.
Cognitive Modelling can be illustrated with both the above examples A cognitive modelling
approach to the “Why do I feel tired” query would establish the user’s state of mind through
triangulating his/her demographic, environment and other data points the user has explicitly
allowed the algorithm to use, and then derive the cognitive process behind the question to
answer it. To provide a concrete example in terms of a single variable, in the case of this query
about being tired, if it were to be asked at 3pm, results related to sleep apnea should have


higher value, but if it were to be asked at 7am, results related to sleep quality should be
prioritized.
A cognitive modelling to the “Should I go to grad school” query would similarly establish the
user’s mind space - what is his or her major, income and geographic area - and come up with an answer for ​ why ​ the user is asking that query - for example which academic area is it in, is it
based on professional interest or academic interest? This would then allow results that address
the thoughts that led to the query - for example a possible result that could be returned in this
model would be about an alternative to grad school. Therefore, emotional modelling in this
instance provides the user much more valuable set of information rather than a general set of
results that directly addresses the question.

## Cognitive Modelling

There are several frameworks for Cognitive modelling. The “OCC” Model is a model developed
by Ortony, Clore and Collins models emotions and established itself as the standard model for
emotion synthesis. It specifies 22 emotion categories based on reactions to situations that are
either goal relevant events, acts of an accountable agent or as attractive or unattractive objects.
However, this model lacks the specificity to incorporate the multiple nuanced emotions
individuals may feel. For example, there are only 3 categories to classify emotions towards
objects, and this greatly generalizes the wide spectrum of emotions humans have towards
objects. Moreover, this framework merely maps emotions but fails to deconstruct or attempt to
model environment that led to that emotion, which is important to effective cognitive modelling.


There are other popular forms of cognitive modelling, such as utilizing neural networks, that
form a bottom-up approach by modelling individual neurons. However, these models have not
been trained by centuries of evolution or the human lived experience and hence do not display
the same complex intuition or emotional responses.
This paper suggests 2 new models of modelling emotional affinity and engagement. First, a
measure of categorization and entity recognition is used to provide results that are similarly
categorized and contain similar entities. Second, a measure of social emotional engagement is
proposed.
The overall model will first qualify the query with background information that will be gleaned
from the user’s profile. Results will be similarly categorized. Within each category, emotional
entities will be recognized and ranked. Results will be returned based on these emotional
entities through a search mechanism. The content of the page itself is examined for these
entities. Then, an extension of this algorithm that analyzes social emotional engagement is also
put forward and analyzed.

## Examining affinity of emotional and personal entities

The first step is qualification of the search query. The algorithm only caters to queries that
require emotional modelling, as queries that have clear logical answers are presently served
well by the existing pagerank algorithm.
However, current research is highly concentrated on categorizing text as either positive or
negative, but does not break this down into more refined emotional states. Even this analysis
has been limited to cases such as one-line headlines or other datasets of small size and limited
scope (Gaint, Syal & Padgalwar). There is no dataset of emotion words that are labelled
according to emotion categories. Gaind, Syal & Padgalwar algorithmically created a dataset of
words in 6 emotional categories - Happiness, Sadness, Anger, Surprise, Fear and Disgust, and
trained an algorithm that can detect these entities. This is only a small subset of human
emotion, however, and therefore more research needs to be done to achieve an algorithm that
can recognize emotional entities in text. Another step is to quantify personal entities in the
search queries. A simple way this can be done is to identify words that are related to the sense
of self, such as “I”, “my”, “me”. The quantity of personal entities as well as the distance between
the query and result emotional categories in an emotional category tree will be factors that can
supplement Google pagerank.
Then, the results will be put through a similar algorithm to identify affinity of emotional and
personal entities. Affinity of emotional entities can be recognized through a similar process of
training a classifier that can identify words or phrases that represent emotion-based entities.
Quantifying personal entities is slightly more comprehensive as terms that are related to not
only the sense of self but also to persons in general could be deduced to have content that is
personal. For example, a career advice blog or a story about a person struggling with a career


change both are stories that are relevant as they both contain personal entities.
Concretely, the overall system design is as follows.

## Social Engagement

Another key difference between logical and emotional content is the differing effects of having
content that effectively addresses the intended purpose of the website visitor. Pagerank works
well for Logical content because writing effective content creates credibility and increases the
number of incoming links. However, this may not hold for emotional content because the
sharing and expression of emotional content tends to take place in private social networks that
are not indexable by the web.
Therefore, audience engagement in the form of quantity of sharing on social media as well as
the quantity and quality of audience interaction, in the form of comments. It is assumed that a
post that effectively engages audience on an emotional level will solicit comments, and
therefore the quantity of comments will be taken as a factor. Moreover, beyond quantity, the


quality of the response in terms of length, popularity and affinity of emotional entities to the main
post can also be examined, in order to quantify the emotional engagement of commenters. The
design and implementation of this mechanism is outside the scope of this paper.

## Constraints

Constraints of the first method - examining affinity of emotional and personal entities - are that
there does not exist an existing database or classification algorithm that can comprehensively
identify and categorize emotion-based entities or person-based entities. There are some
frameworks that can be used, but these frameworks are heavily limited as they only allow
gauging individual words for emotions, not entire texts. General sentiment analysis algorithms
provide an overall positive or negative sentiment without isolating specific words that convey
emotion, which can be used as entities. This implementation therefore utilizes Google’s Natural
Language Processing API to get the entities present. Google’s NLP API returns broad
categories but allows the training of a custom model that better fits our intended outcome, but
that is outside the scope of this course. Another constraint introduced by the lack of available
data on emotional modelling is that a central premise of the overall system design - content
recommendation based on distance from the general emotional category of the query from the
general emotional category of the result. This implementation utilizes Google’s Content
Classification algorithm to get a general category of content, and the search results implement
the metrics outlined in this paper. Although outside the scope of this course, a future paper for a
machine learning course would implement trained models with learning and test data for both of
these problems, in order to create a more specific implementation.

## Analysis of results

Given the constraints outlined above, a limited search algorithm was implemented. The sample
query was ‘Why do I feel tired all the time’. Google’s search was limited to the Humans of New
York website from the past year. This was done by inserting the query parameter
site:humansofnewyork.com and limiting the time range.

The author attempted to replicate the pagerank algorithm but unfortunately was not able to do
so. However, each of the functions proposed was implemented and tested as shown in the
accompanying python notebook. It is not possible to implement these functions without access
to a search algorithm, which is difficult to create from scratch, but the independent tests do
show that each individual function works, and therefore the overall system design proposed can
be implemented and tested with more work in machine learning and access to an open source
search engine. The author attempted to limit his sample but this led to large tradeoffs in terms of
quality of results returned.

## Conclusion
Artificial intelligence has so far been dominated by modelling logic. This paper takes a deep dive
into an unexplored area of Artificial Intelligence - emotional modelling - and examines the
background, use cases and potential in the future. A case study in web search was explored,
with several new mechanisms suggested for qualifying search queries as emotional or logical,
quantifying search results by social emotional engagement and presence of personal and
emotional entities. These mechanisms were designed implemented with the exception of the
metric for social emotional engagement. Current search was explored and analyzed and the
constraints for integrating a solution were discovered in terms of a lack of emotion classification
frameworks and lack of open source search frameworks that allowed limiting search queries.
Further research could expand on the ideas explored towards the concrete goal of creating
better search and eventually more emotionally intelligent artificial intelligence.


**LOs and HCs**
#aiconcepts - A novel approach was taken to examining emotional modelling in Artificial
Intelligence. Concepts from AI, Psychology and ethics are integrated to present a persuasive
argument for further research on creating AI algorithms that think humanly, as described by
Russell & Norvig. Prior research was examined, the implications for the current and future state
of AI were discussed and a new model for incorporating emotional modelling in search engines
was proposed and then implemented in a limited manner within the constraints of lack of data,
prior research and flexible open source web search frameworks.
#search - The limitations of the existing graph search algorithm utilized by Google, Pagerank,
were examined and several new functions were proposed and created in order to optimize for
emotional intelligence. How these algorithms fit into the current informed search algorithm used
by Google by adding a dimensionality of personal and emotional entity recognition and
modelling is also discussed.
#thesis - A well structured thesis was written with a clear problems statement that is addressed
and referred back to throughout the paper.
#emergentproperties - A nuanced discussion of the implications of Artificial Intelligence with and
without Emotional Intelligence is undertaken and used to justify further research into creating
emotional models.
## **References**

Contents of Volume 21. (2004). ​ Artificial Intelligence Review ​, ​ 21 ​(3/4), 401–402. doi:10.1023/b:aire.0000036301.92865.

Dean, B. (2018, December 28). Google's 200 Ranking Factors: The Complete List (2019).
Retrieved from https://backlinko.com/google-ranking-factors.

Emotion Modelling. (2016, May 17). Retrieved fromhttps://www.uu.nl/en/research/artificial-intelligence/intelligent-systems/research-themes/emotion-modelling.

How Does Google Rank Websites? (2019, October 17). Retrieved from https://www.seomark.co.uk/how-does-google-rank-websites/.

Implementing web search. (n.d.). ​ Making Search Work ​, 95–104. doi:10.29085/9781856048736.

Pfeifer, R. (1988). Artificial Intelligence Models of Emotion. ​ Cognitive Perspectives on

Emotion and Motivation ​, 287–320. doi: 10.1007/978-94-009-2792-6_

Russell, S. J., & Norvig, P. (2021). ​ Artificial intelligence: a modern approach ​. Hoboken:Pearson.

Wiltz, C. (2019, September 10). What's the State of Emotional AI? Retrieved from https://www.designnews.com/electronics-test/whats-state-emotional-ai/203153414061482.


