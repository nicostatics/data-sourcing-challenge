# Module 6 Challenge

## Overview
The purpose of this challenge was to get us to be familiar with the process of requesting data from APIs - using API keys, throttling requests, and making sure that we get clean data.

## Code Details
The repository includes:  
1. The Jupyter Notebook where the majority of the work is done - `retrieve_movie_data.ipynb`
2. The output CSV that is the end result from the code in the Jupyter Notebook/

## Nico note
Whilst this challenge was a great exercise, there are differences between what was shown in the Jupyter Notebook as the expected result and what ended up coming out.  Some are detailed below:  
1. Because we are including 'snippet' as part of the request from the NYT API, there are multiple reviews for the same movie from two different people which have two snippets.  This causes two separate rows for the same film in the resulting df/csv.  The example output only had one row for films to which this idiosyncrasy applies. 
2. The lambda function used to extract the film title from the headline column did not account for all variations of headlines (it's difficult to do so when dealing with strings, understandable).  However, the fact that it was explicitly looking for an end quotiation followed by the word "Review" at the end of the substring query resulted in a lot of film titles not being properly extracted.  I realized this was the case because for *those* films the word "Review" was at the beginning of the headline, not after the end of the title.  Example: `Review: 'Movie Title', witty headline` vs `'Movie Title' Review: witty headline`.  Because of that, I ammended the lambda function to capture more correct film titles.
