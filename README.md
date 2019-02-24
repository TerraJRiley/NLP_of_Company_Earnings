# Performing NLP on Transcripts of Multiple Companie's Earnings Calls
Seeking Alpha is a website that provides information on the stock market.  One of the stockmarket related services that they provide are transcripts of Earnings Calls made with a variety of companies.  These earnings calls are updates on how the company has done in it's earnings during a period of time, usually in the form of yearly quarters.

## Problem Statement
The client wanted to have the Earning Call Transcripts scraped from Finding Alpha and have them analyzed for sentiment and complexity.

## Data Collection

I gathered the data by using Selenium.  I started by collecting the urls of all transcripts that I wanted to collect.  I then went to each transcript page individually and scraped them one at a time.

In order to avoid having the website question my code's humanity I started by changing the user agent name.  When having just one user name stopped working I had the browser close and then reopen with a new user name for every pull.  Eventually I had to add in a sleep timer of 20 seconds, but the full scrape of a single url took almost a full minute.  This meant that collecting the number of transcripts I wanted took a few days to collect.

## Data Analysis
This project gave me the opportunity to learn about the Gunning Fog formula for complexity.
The full formula is as follows: 
![](https://wikimedia.org/api/rest_v1/media/math/render/svg/84cd504cf61d43230ef59fbd0ecf201796e5e577)

The idea is that the result is supposed to represent the number of years one would have to spend in a school to easily understand the piece of text.  Thus, a score of 12 would suggest an equivalent of a high school senior.  Unfortunately this doesn’t show in practice as many results can end up in the highs of 24 or more.  Thus this score should best be taken as a measurement without the comparison to years in school.

## Results
I was able to provide the information requested and created a column for the Complexity and Sentiment scores for both the speech and Q-and-A portions of the transcripts.
Is there more info to elaborate on the results? It seems brief compared to the other sections.

## Future Steps
 - Setting up an AWS instance for running the code in the cloud so the work will not require a computer on hand.  Slowly scraping the remainder of the transcripts with the cloud instance.  The original scraping was done via my own personal computer and with 1 transcript being scraped per second it would be best to automate this on somebody else’s machine.
 - Storing the data scraped in an SQL server.  The data I scraped for 6,000 transcripts was over the 100MB limit for Github in a few of it’s different forms.  Thus over 100,000 would again be best suited for somebody else’s machine.  Like Amazon’s machine(s) or another cloud service.
