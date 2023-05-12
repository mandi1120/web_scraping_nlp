# Web Scraping & Natural Language Processing   
- Description: Scraping text from websites for Natural Language Processing
- Created: 5/10/23  

## Overview:
- This code scrapes text from two websites and performs natural language processing (NLP) tasks for sentiment analysis and summarization   
- Web scraping is accomplished using <a href="https://beautiful-soup-4.readthedocs.io/en/latest/" target="_blank">Beautiful Soup</a>, a Python library for pulling data out of HTML and XML files
- NLP tasks are done with <a href="https://spacy.io/" target="_blank">SpaCy</a>, an open-sourced Python library of NLP tools 

## Files & Links:
- Jupyter Notebook: [web_scraping_nlp.ipynb](web_scraping_nlp.ipynb)
- Scraped Websites:  
    - <a href="https://www.mckinsey.com/industries/healthcare/our-insights/driving-growth-through-consumer-centricity-in-healthcare" target="_blank"/>
    - <a href="https://www.mckinsey.com/industries/healthcare/our-insights/women-in-healthcare-and-life-sciences-the-ongoing-stress-of-covid-19" target="_blank"/>
- Scraped Text:  
    - [scraped-consumer-centricity-in-healthcare.html](scraped-consumer-centricity-in-healthcare.html) 
    - [scraped-women-in-healthcare.html](scraped-women-in-healthcare.html) 
- Summarized Text:   
    - [summary-consumer-centricity-in-healthcare.txt](summary-consumer-centricity-in-healthcare.txt)
    - [summary-women-in-healthcare.txt](summary-women-in-healthcare.txt) 

## Setup  
Required Libraries:  
- request, beautifulsoup, spacy, spacytextblob, collections, matplotlib, wordcloud, re, numpy

Documentation:  
- SpaCy: https://spacy.io/  
- Beautiful Soup: https://beautiful-soup-4.readthedocs.io/en/latest/  

## Process:  
1. Scrape Text Content
    1. Create variables to store the website url and an article label
    2. Scrape the html from the website
    3. Extract text from the html file
    4. Specify html or css tags or elements that contain the desired text, and tags or elements that should be excluded from the text
    5. Clean the text by removing newline characters and special characters
    6. Write the scraped text to a file
    7. Repeat for additional websites
    8. Create a list of article content and article label for all sraped pages
2. Create Sentiment Analysis Function
    1. Load the text to the model
    2. Calculate a polarity score and give it a label of positive, negative, or neutral
    3. Print the score and label to the screen
3. Create Summarization Functions
Summarization breaks longer text down into key sentences and information. Through lemmatization, words are grouped into their lemma or dictionary form, which are then tallied. Each sentence is scored based on presence of the most frequent lemmas or key concepts.
    1. we_care_about(token): remove whitepace, stopwords, and punctuation 
    2. plot_histogram(scores, label): plot a histogram of sentence score frequency 
    3. create_wordcloud(content, label): create a word cloud 
    4. summarize_text(content, label): summarize a given set of text 
        1. Load the text to the model
        2. Remove whitespace, stopwords, and punctuation & make text lowercase
        3. Remove special characters
        4. Count lemma frequency and find the five most common lemmas
        5. Count number of sentences
        6. Count words in each sentence and generate an importance score for the sentence based on presence of important lemmas
        7. Create a summary by adding sentences to a list if their score is in the top 10%
        8. Print the most common lemmas and summary to the screen 
        9. Plot a histogram and save it to a file
        10. Create a word cloud and save it to a file
        11. Write the text summary to a file
4. Run the Program


## NLP Results  

### Consumer Centricity in Healthcare
- Full article: <a href="https://www.mckinsey.com/industries/healthcare/our-insights/driving-growth-through-consumer-centricity-in-healthcare" target="_blank"/>
- Scraped text: [scraped-consumer-centricity-in-healthcare.html](https://raw.githubusercontent.com/mandi1120/web_scraping_nlp/main/scraped-consumer-centricity-in-healthcare.html)
- Summarized text: [summary-consumer-centricity-in-healthcare.txt](https://raw.githubusercontent.com/mandi1120/web_scraping_nlp/main/summary-consumer-centricity-in-healthcare.txt)

#### Polarity:  
- This article's sentiment was slightly positive with a score of 0.15

#### Most Frequent Lemmas:
1. Consumer: appeared 95 times
2. Care: appeared 81 times
3. Healthcare: appeared 62 times
4. Experience: appeared 23 times
5. Report: appeared 21 times
  
![wordcloud](images/wordcloud-consumer-centricity-in-healthcare.png)

#### Summary:
- This article was summarized into 10 sentences containing key concepts.
- The histogram below displays the frequency of sentences that were identified to contain key information and received higher scores, and less important sentences with lower scores.
- Sentences that scored in the top 10% for importance make up the following summary:  
    - This article discusses the steps along the healthcare journey and the adverse consequences that result when consumers defer care because of poor healthcare experiences. Care deferral has serious consequences for consumers and health systems Given the challenges of navigating todays healthcare journeys, it is no wonder that nearly a quarter of US consumers have reported deferring healthcare. Negative experiences simply reinforce the cycle of care deferral. Bolstering consumer trust in the healthcare system could encourage more consumers to seek needed care. Likewise, bolstering consumer trust in the healthcare system could encourage more consumers to seek needed care. Addressing consumer pain points can unlock better outcomes satisfied consumers report deferring care ten percentage points less, getting routine care 14 percentage points more, and using inpatient care 13 percentage points less than unsatisfied consumers. Ultimately, consumer health improves. Understand consumers. Second, consumers want meaningful, trust-based relationships with their care teams. Six times more consumers with longitudinal-care-team relationships and care continuity report engaging with their primary care physician for future health needs.

![histogram](images/scores-consumer-centricity-in-healthcare.png)


### Women in Healthcare
- Full article: <a href="https://www.mckinsey.com/industries/healthcare/our-insights/women-in-healthcare-and-life-sciences-the-ongoing-stress-of-covid-19" target="_blank"/>
- Scraped text: [scraped-women-in-healthcare.html](https://raw.githubusercontent.com/mandi1120/web_scraping_nlp/main/scraped-women-in-healthcare.html) 
- Summarized text: [summary-women-in-healthcare.txt](https://raw.githubusercontent.com/mandi1120/web_scraping_nlp/main/summary-women-in-healthcare.txt) 

#### Polarity:  
- This article's sentiment was slightly positive with a score of 0.10

#### Most Frequent Lemmas:
1. Woman: appeared 118 times
2. Healthcare: appeared 74 times
3. Level: appeared 62 times
4. Representation: appeared 46 times
5. Rate: appeared 26 times

![wordcloud](images/wordcloud-women-in-healthcare.png)

#### Summary:
- This article was summarized into 17 sentences containing key concepts. 
- The histogram below displays the frequency of sentences that were identified to contain key information and received higher scores, and less important sentences with lower scores. 
- Sentences that scored in the top 10% for importance make up the following summary:  
    - Representation Healthcare continues to outpace other industries in the representation of women however, women especially women of color remain underrepresented at senior levels in healthcare organizations Exhibit 1. Increased representation. At all levels, womens representation in healthcare remains higher than in corporate America overall. Lack of representation in senior levels. But the representation of women drops in each successive career level to a low of 32 percent at the C-suite level. Women in senior-level roles in healthcare are predominantly White. Attrition Higher rates of attrition. Promotions Lower promotion rates. Internal promotion rates for women in healthcare are lower than the average for women in all industries at every level. Healthcare companies can keep a critical eye on the ratio of womens representation at a given level and the share of women hired into that level. Women continue to have higher levels of representation, hiring, and advancement in healthcare than in corporate America overall. The healthcare sector is examining how to better hire and promote women to the highest levels. We identified three important shifts in 2021 increased representation of women at specific managerial levels, lower rates of attrition among women in healthcare than in other sectors, and increased external hiring of women at specific levels of the pipeline.   Increased representation In healthcare, the representation of women at the senior-manager or director level improved by four percentage points on average, to 53 percent, in 2021. Lower rates of attrition On average, in 2021 women left jobs in healthcare at lower rates than women in other sectors, men in healthcare, and women in healthcare in previous years. This effect can compound over time, resulting in lower representation for women at the highest levels. Gender parity and proportionate representation of women of color in healthcare at the top levels remains aspirational.

![histogram](images/scores-women-in-healthcare.png)





<br/>  
<br/>  
<br/>  
<br/>  
<br/>  
<br/>     

