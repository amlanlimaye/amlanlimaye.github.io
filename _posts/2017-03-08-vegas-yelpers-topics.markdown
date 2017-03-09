---
layout: post
title:  "What are Yelpers talking about in Las Vegas?"
date:   2017-03-08 20:00:00 -0800
categories: LDA
---

Yelp is an American company headquartered in SF. It develops and markets Yelp.com and the Yelp app, which publish crowd-sourced reviews about local businesses, that most of us are familiar with.

A couple of weeks ago, Yelp made their dataset available on the internet and started a new Dataset Challenge. My objective was to use that dataset to unearth the abstract topics being talked about in Yelp Reviews, understand their distribution and just overall develop a solid understanding of Yelp Reviews that would serve as a foundation to tackle more sophisticated questions in the future, such as (show 4 sophisticated questions on slide and explain)

Now, the full dataset contains 4.1 million reviews for businesses in 12 cities from all over the world (show reviews time plot). 
I picked Las Vegas as my city of interest and restricted the year to 2016. The resulting dataset had 400K reviews, 100K tips by 120K users. This is a plot of the number of reviews by date in 2016. You might be wondering what those 2 sharp falls are; they're, as you might expect, Christmas and New Year's!

The next step is to generate topic probabilities for each review

Approach:

I decided to use topic modeling, specifically LDA as my weapon of choice. 

LDA (Latent Dirichlet Allocation) is a type of topic model that posits that each document (or in this case, review) is a mixture of a small number of topics and that each word's creation is attributable to one of the document's topics. 

LDA produces a ranked list of words deemed important for understanding a particular topic. 

The first step is to set the number of topics, K. I experimented with a simple count vectorizer as well as a tfidf vectorizer (tfidf is a measure of how important a word is to a review). I settled on 10 topics using a count vectorizer. 

<script src="http://gist-it.appspot.com/http://github.com/yelp-dataset-challenge/reports/figures/yelp_vegas_reviews_2016_LDA_viz.html"></script>

<div id="ajaxContent"></div>
<script>
var Webflow = Webflow || [];
Webflow.push(function() {
  $.get('https://cdn.https://raw.githubusercontent.com/amlanlimaye/yelp-dataset-challenge/master/reports/figures/yelp_vegas_reviews_2016_LDA_viz.html', function(data) {
    $('#ajaxContent').append(data);
  });
});
</script>

LDAvis tasks:

topic list:

1: "customer_feelings",
   2: "customer_actions",
   3: "restaurant_related",
    4: "compliments",
    5: "las_vegas_related",
    6: "hotel_related",
    7: "location_related",
    8: "chicken_related",
    9: "superlatives",
    10: "ordering_pizza"

- On the right here, the red bars represent the word frequency within a topic and the blue bars represent the overall frequency of each word. I've selected topic 1 and I've listed the top 30 words according to the frequency within this topic. The size of the topic circles is proportional to topic frequency; the topic numbers are sorted by frequency as well; 1 is the most common topic (customer feelings), 2 (customer actions) is the 2nd most and so on.

'like', 'people' appear near the top of the list for multiple topics, which is where our parameter lambda comes in. I can quickly re-rank the words that are more specific to this particular topic and aren't just common words across multiple topics. By reducing lambda, I'm giving more weight to the ratio of the red bar to the blue bar or the ratio of the frequency given this topic to the overall word frequency. This makes it easier to see that this topic is talking mainly about customer feelings. Topic 3 seems to be restaurant related, with words like food, service, eat at the top. Topic 4 contains a lot of compliments near the top; good, nice, pretty, super, fresh.

By hovering over a particular word, I can see it's spread among different topics, which gives me an insight into how that word is used in different contexts.

For example, the word service in topic 5.
these words are mostly describing xyz, this word must be used in the context of ___, the distance between the topics is an approximation of the semantic relationship between these two topics.

Conclusion:

The next step is to generate topic probabilities for each review
