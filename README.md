# Financial-Report-Text-Mining
About :

A financial reports and statements are formal records of the financial activities and position of a business. Usually it comprises of the balance sheet, a statement of the financial position reports on company assets, liabilities and owners’ equity at a given point of time. 

However, it becomes a tedious task, to determine the gist of the report since, any financial report of a company run for so many pages. Thus, making it hard to take any significant decisions since it involves a lot of labour work and time.


Problem statement:

It’s indeed very difficult to read a and understand the crucks of a lengthy report, especially if it is a financial report. The objective of this project is make the work easier for companies to get a sneak peek about the positive or negative score of a company’s financial report within few seconds, that can help them in taking various decisions like understanding their competitors, or while going for a merger or negotiating during their supply chain management. 
They can also use to understand, the position where their company stands currently and look on to areas where they can improve. Thus this projects aims at extracting some sections from SEC / EDGAR financial reports and perform text analysis to compute variables.

Approach: 

The data of this project is nothing but the financial report of 152 different companies which are present in different links. Thus, I initially use a library called Beautiful soup, which will read the data from these links and also import another library called as requests, which requests to the server for reading the data from these links. I then add these links into the data frame, so that we can have the data from each of the reports going into each row of the column. 

I then import a stop word dictionary containing a list of stop words such as A, about , the etc., in English, which do not add any value to the sentiment analysis of the text. I also import positive dictionary and negative Master dictionary containing a data frame of positive and negative words in English, also giving details about when the particular positive or negative word was added in to the dictionary. 

Thus I create a final list of positive and negative word list by using the index of the word which is added into that respective dictionaries. It is followed by importing a list of uncertainty and constraining words in English. 

Now, that the text from each report is read through the libraries, I create an user defined function for the following:

•	Tokenize:

A function to tokenize the text in to words and replacing every character other than the characters A-Z in upper or lower case with a space. I also convert the entire text to upper case because, some of the lists that we had imported above such as uncertainty words or stop words are all in upper case.
•	Removing stop words:

A function that checks if out text data from teach financial report matches with any of the words in the stop list and if any words match, then it removes those stop words from out financial text. I am removing the stop words because they do not contribute or affect while taking sentiment analysis. 

•	A count function:

It’s a user defined function to count the number of positive and negative words in the text which matches with those in the positive and negative dictionary list created form master dictionary¶

•	Polarity score:

A function that calculates how positive or negative the text form the financial report is by using the formula:

polarity_score = (positive_score - negative_score)/((positive_score + negative_score)+ 0.000001)

•	Sentiment analysis:

A function that evaluates the sentiment score and the text. It suggest that the text from the financial report is Most negative if the polarity score is below -0.5, it gives negative if the value if greater than -0.5 and less than 0, it gives neutral if the sentiment polarity score equals zero. It gives positive if the polarity score is greater than 0 and less than 0.5 and finally it return most positive if the sentiment score is any value greater than 0.5. 

•	Subjectivity: 

A user defined function to calculate whether a sentence is objective or subjective. Subjective sentences includes that contains opinion ,believes etc. It is calculated with the following formula:

(positive_score+negative_score)/(num_words+ 0.000001)

•	Syllable more than two words:

A function that we can use to find how many complex words are there in the financial report. Generally, a word is classified to a complex word, if it has more the two syllables. Thus, I use this function to count the number of words having more than two syllables using the vowels. 

•	Fog index:

It is a feature that does a readability test on the financial report, in order to determine the level of text difficulty or how easy it is to read, by using the following formula:

0.4*(average_sentence_length + percentage_complexwords)

Once, I have created all user defined functions that returns different features that does sentiment analysis on each report, I create new columns in the original data frame that return all the above features for each of the report separately and initialise it with a value of zero. 

Now I have created a loop that iterates throughout all the financial reports in the links. So, while the loop iterates every time, it will read the text from one link, and call all the above user defined functions that is stated above and return with respective values to the column of the original data frame that we had just created. 

I also create columns that returns the value count of the total complex words, uncertain words and constraining words in present in the dataset. 

Finally, I have exported the data frame to a csv file that contains the details about the report and the output giving a clear sentiment analysis with various features after text mining. 












	
