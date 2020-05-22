# System Design Notes

## How to Build [Twitter]

These ideas come from section 30 of The Coding Interview Bootcamp on Udemy. Obviously can be anything, Uber, eBay, etc.

### High Level Notes

- Usually they want you to focus on the data model. For Twitter, how would you store tweets in the database?
- They also want to see what you spend time on in answering the question
- They aren't interested in the technologies (React, redux...etc), but are interested in the requirements and qualities of any framework. Ex: It should be good on mobile
- **Draw stuff out** - Draw out the UI for a site to start then use that to build the data model
- They are looking to see how you can communicate complicated topics. So, they want you to think out loud

### ˝˝

1. Sketch a UI
2. Identify two-core components from the UI (ex: How a tweet is made and then the user feed)
3. Possible implementations then identify and address possible issues (For tweeting: what does a tweet look like in the database, how to make the #topic and @mention systems, and how to implement retweets) (For feeds: how do we identify the most important tweets for a user)
4. Eventually address scaling for big user bases. Don't need concrete solutions, just general strategies. Two common solutions are caching data or deployment options
   1. **Caching** - Store computationally expensive values in a cache. For Twitter: you might cache a feed result for a minute or for five minutes so that you don't have to recalculate that value over and over again
   2. **Load Balancing** - Have a load balancer in between the server. When a request comes in, send the request to a randomly selected server
