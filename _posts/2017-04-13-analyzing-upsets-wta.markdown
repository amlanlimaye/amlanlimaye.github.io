---
layout: default
title:  "Examining Favorites and Underdogs on the WTA Tour"
date:   2017-04-13 12:20:00 -0800
categories: Tennis
---

ADD MORE CONCLUSIONS!!!

<h2>Examining Favorites and Underdogs on the WTA Tour</h2>

<img src="http://i.imgur.com/LLuuYjK.jpg">

Off late, Women's Tennis has received a lot of flak for being "inconsistent"; a notion bolstered by what's happened in the last month or so. Russia's Elena Vesnina, who was 125/1 to win at Indian Wells (a Premier Mandatory event that's perhaps regarded as the biggest event outside of the 4 Grand Slams) before the tournament began, took home the trophy by beating compatriot Svetlana Kuznetsova 6-7, 7-5, 6-4. Vesnina is 0-2 since Indian Wells, having lost to Wildcard and World No. 594, Ajla Tomljanovic at Miami, as well as Qualifier and World No. 282, the delightfully named, Fanny Stollar. World No.1 Angelique Kerber's recent struggles haven't helped either; Kerber is 1-8 vs top 35 opponents this year, with her lone win coming against World No. 25, Carla Suarez Navarro.

Although it may not appear so, "consistency" in Women's Tennis isn't too different from that in the Men's game as <a href="https://www.sciencedaily.com/releases/2015/08/150809170256.htm">Stephanie Kovalchik explains</a>; evidence of inconsistency in women's play is likely attributable to match format (e.g., best of three or five sets), not gender.

Upsets excite me; I enjoy rooting for (under)dogs in pretty much any domain and tennis is no different. There's nothing like watching an unheralded outsider take down a top seed and there's plenty of incentives to analyze and predict upsets, monetary and fun-related. I took a look at WTA matches from Jan 2014 - Mar 2017 using a <a href="https://github.com/skoval/deuce/blob/master/data/wta_odds.RData">dataset containing betting odds</a> from Bet365, Centrebet, Expekt, Pinnacles, Unibet and Ladbrokes to see if I could find something interesting about favorites and dogs.

I figured betting odds or wisdom of the (betting) crowd would be a reasonable way of quantifying which player is "expected to win" in any matchup. All 5 bookmakers (as well as the average of their odds) correctly predicted the result of a match ~70% of the time (compared to 64% correct predictions using WTA Rankings), which leads us to our first "insight": ~30% of all WTA matches are upsets (where an upset is defined as a match won by the player with the longer odds). Turns out, <a href="http://www.tennisabstract.com/blog/2017/01/15/measuring-the-performance-of-tennis-prediction-models/">70% isn't great</a>, but I guess it's a decent starting point.

Of course, with betting data, this is more like "Examining which players are overrated and which players are underrated by the bookies and the betting crowd" than "Analyzing Favorites and Underdogs", which is equally, if not more interesting.

These are the top 10 "upsetters" in the last 3 years:

<img src="http://i.imgur.com/0hVrfI5.png">

Kiki Mladenovic and Karolina Pliskova have caused the most upsets in the last 3 years; expected since they've steadily risen through the ranks in that time. Not all upsets are the same though; there's a pretty big difference between an upset that has an implied probability of 10% (from betting odds) and an upset that has an implied probability of 49%. 

I thought I'd capture this by squaring the difference in win probabilities between players playing a match (so that larger upsets are exaggerated; I think it's desirable to exaggerate an upset with win probability 5% compared to one with 45%), adding all the upset squares for a player and dividing by the number of matches in which that player was an underdog (which gives you a measure of how "upsetting" that player is; don't worry, we'll give it a less upsetting name - "upset score").

Let's check out what matches "upset score" considers to be the biggest upsets:

<img src="http://i.imgur.com/aadTc4j.png">

Top "upsetters" by "upset score" (min 20 matches played as underdog):

<img src="http://i.imgur.com/wqSUsrz.png">

Kucova seems to be getting underestimated by the public pretty often; she's won 46% of games as an underdog and has the highest "upset score" in the dataset! Also interesting to see Lucic-Baroni, who can smoke anyone off the court on her day, Pennetta, who's probably on this list on the back of an upset US Open win in 2015 and up-and-comer Naomi Osaka, who's doing a pretty good job of thwarting bookies' and bettors' expectations off late.

And by "percentage of underdog matches won" (min 20 matches played as underdog):

<img src="http://i.imgur.com/aDscAbl.png">

Strycova is winning an absolutely ridiculous 51% of her matches as an underdog. Lots of big names as well; Kvitova, Muguruza, Cibulkova and Pliskova all seem to react pretty strongly when given "underdog" status.

Those 4 probably aren't underdogs too often though; they've been in and around the top 10 for a while. They're probably very slight underdogs (when they are underdogs), which is another interesting situation; that of "tight games". Again, not easy to define a "tight game" or an "expected tight game" but I think a game in which the difference in implied win probabilities between the players is less than 10% is a reasonable definition for a "tight game" (win probabilities higher than 45% and lesser than 55%).

<img src="http://i.imgur.com/LMYO1M5.png">

Dellacqua keeps coming back from injury and won 90% of tight games in the last 3 years; likely a result of being heavily "faded" by betting markets. Muguruza is making a (great) habit of winning tight games; much harder the closer you get to the top and Dasha Gavrilova seems to be killing it in tight games as well.

<img src="http://i.imgur.com/6qKs4vx.png">

Some pretty damning numbers for Stosur, Wozniacki and Radwanska, 3 wannabe top players who have all won less than 1/3rd of games they were expected to be competitive in. Vekic, who was rising up the ranks pretty quickly a couple of years ago, seems to have hit a wall off late and is also winning less than 1/3rd of her tight games.

What about on the other side of the spectrum: games featuring a big favorite? I'm considering all games with an implied win probability difference of 50% or more to be in this category. Let's have a look at which players performed the best when big favorites:

<img src="http://i.imgur.com/9TvKhzo.png">

A bit of redemption for Wozniacki as she heads this list, winning over 90% of games in which she's considered a big favorite. Other former World No.1's, often labelled "consistent" by commentators and journalists, Kerber, Venus, Azarenka, Ivanovic and current No.1, Serena, also feature. But what do they really mean when they say "consistent"? Most of the time they're referring to the players being consistently good; producing solid results over a long period of time. I'm interested in a more textbook definition. A truly consistent player would be one who wins all the matches they're expected to win and loses the ones they're expected to lose; kills it when they're a big favorite and folds like a cheap suit when they're a big dog. 

<b><h3>Consistency</h3></b>

I've defined "consistency score" as the sum of matches won as favorite and matches lost as underdog divided by the total number of matches played. The most consistent player on tour (min 20 matches played) is... Romania's ANA BOGDAN!!! Bogdan won 5/5 of her matches as favorite and lost 15/17 matches as underdog to edge ahead of Serena (144/160 matches won as favorite, 0 matches played as underdog).

<img src="http://i.imgur.com/lX9Z8BY.png">

Li Na, Sharapova and Azarenka are all incredibly consistent (elo, which is widely regarded as the best rankings system for individual sports, puts Serena, Sharapova and Azarenka as <a href="http://tennisabstract.com/reports/wta_elo_ratings.html">miles better than everyone else</a> on tour as well as classifying Konta and Pliskova as the "best of the rest" (as of 4/14/2017).

<img src="http://i.imgur.com/9zyO8tq.png">

Speaking of Pliskova (Karolina), her development into a solid servebot++ type player might be causing bettors to overestimate her twin sister, Kristyna, who somehow lost 70% of her matches as favorite (or they're just straight up confusing Kristyna with her sister). Cirstea, Watson, Bertens, Ostapenko all seem to be pretty coin-flippy.

While "consistency" measures how close a player's win-loss record is to what's expected, "volatility" is a slightly different concept, it has more to do with upset size. On their day, volatile players take down the biggest of favorites but they're also prone to losses against players who are not expected to threaten them at all. A couple of names should've popped into your head after reading that description; let's see if they've made it to the "most volatile" list.

<img src="http://i.imgur.com/8AGuF3Q.png">

I'm talking, of course, about the frankly ridiculous, Mirjana Lucic-Baroni, who lost 11/15 matches as favorite with a volatility score second only to perennially-involved-in-a-comeback Petra Cetkovska. Kvitova's got a bit of a hit or miss game as well; no surprise to see her on the list but Radwanska and Halep can't be happy about being on there. One might have expected to see those two among the least volatile but they really seem to be struggling with the power-based game that's dominating women's tennis off late.

<img src="http://i.imgur.com/0eCn0G7.png">

No one comes close to Paula Ormachea in this regard. Paula lost 3/12 matches as favorite and folded like a cheap suit when given underdog status, winning only 1/18 games.
