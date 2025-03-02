---
title: "Assignment 1 - Analyzing ROR Corpus with Voyant and R"
categories:
  - Assignments
  - Blog
tags:
  - Assignments
  - Voyant
---

**Thesis**  
This assignment attempts to analyze how three distinct NYUAD Facebook groups—ROR (open to all students), Male ROR, and Female ROR—use language when discussing campus life, with a focus on posts containing the word “everyone.” Motivated by the need to see patterns not easily captured in a manual reading, the analysis employs computational methods in R to tokenize text, remove stopwords, and compare word frequencies across the three corpora, making it possible to quickly spot trends that would be difficult to notice through a purely linear reading. The results reveal that each group exhibits unique linguistic characteristics: the Female ROR group appears to use more emotionally charged words, while the Male ROR group includes more institution-oriented vocabulary, while the general ROR group contains a blend of both. These findings highlight not only surprising differences (such as the prevalence of certain personal or organizational terms in specific groups) but also the value of digital tools in displaying such distinctions.

**Introduction**  
In this assignment, we analyzed three separate collections of text drawn from NYUAD Facebook groups: the main “ROR” group (open to all students), “Male ROR” (restricted to male identifying students), and “Female ROR” (restricted to female identifying students). Each corpus consisted of 20 random posts containing the word “everyone,” yielding a total of 60 posts across the three groups. After preparing these texts in .txt files, we ran them through a notebook in R (Posit Cloud) that used functions from the tidyverse to tokenize the texts, remove stopwords, and compare word frequencies across the three corpora. This computer-assisted approach enabled us to discover patterns in usage that would be more difficult to spot in a purely linear reading.

**Importance of the corpus**

**Victor**  
What I noticed from the male ROR group is that the average post length is very short, not to mention that the group does not see a lot of participation since most posts are from months/years ago, as well as a lot of the more recent ones coming from anonymous members (for reference, the option of posting anonymously on Facebook was introduced in April 2022). This makes sense because a significant amount of posts have topics that could be seen as “taboo” by some people, such as questions related to sex and mental health, and romantic relationships. Still, a lot of the posts seem to be related to academic and institutional matters, such as advice on which classes to choose or requests to change rooms with others. Nonetheless, most of the posts tend to be short and straightforward, albeit much more intimate than ROR.

**Methodology**  
The decision of using R and tools like Voyant or the tidyverse came from the ability to quickly identify trends in word usage and frequency. With a linear reading of 60 separate posts (and thousands of words), it would be challenging to systematically notice which words appear uniquely or more frequently in one group versus another. In contrast, the R code provided in the Posit Cloud allowed us to:

1. Tokenize each text (split it into individual words).  
2. Remove common stopwords (e.g., “the,” “of,” “and,” etc.).  
3. Count the frequency of each remaining word in each corpus.  
4. Calculate proportions (i.e., how often a word appears relative to the total number of words in that corpus).  
5. Visualize differences using a scatterplot that compares the ROR corpus (on the y-axis) to each of the other two corpora (on the x-axis).

A purely manual or linear approach would be time-consuming and prone to human error. In the time allotted, it would have been much more difficult to read and reliably tally every single occurrence of each word. By leveraging the mentioned computational tools, we could spot outliers, subtle differences, and shared linguistic habits among the three groups with much greater speed and accuracy.

**Voyant Tools observations**

**R observations**  
By utilizing the “MostDistinctiveWords” R code provided by the Professor, we were able to upload the three collections of text (ROR, Male ROR, and Female ROR), clean and tokenize their contents, and then compare word frequencies across the corpora. This is achieved by importing each text as a single string, breaking it into sentences, and then further splitting those sentences into individual words using the tidytext function `unnest_tokens()`. Next, it removes common stopwords (e.g., “the,” “of,” “and”) to focus on the most meaningful terms. By binding the three datasets together and labeling each one (“ROR,” “Male_ROR,” “Female_ROR”), the code can then compute the relative frequency (proportion) of each word in each corpus. Finally, the script uses **ggplot2** to create a scatterplot that highlights the differences in word usage between ROR and the other two groups, making it easy to spot which words appear disproportionately in one corpus versus the others.

![Plot made with R - Large version](./assets/images/plot.png)
![Plot made with R - Small version](./assets/images/plot2.png)

Looking at the plot comparing word frequencies, we can notice several patterns in the corpus:

- **Words Appearing More Frequently in Female ROR**: Certain terms related to personal experiences, feelings, or interpersonal dynamics (for instance, “feel,” “experience,” “appreciated”) appear more often in the Female ROR group than in the main ROR corpus. This might suggest that discussions in the Female ROR group have a more emotional tone and more intimate support.  
- **Words Appearing More Frequently in Male ROR**: By contrast, words such as “campus,” “students,” “voice,” or “uncomfortable” appeared more often in the Male ROR group. This suggests that users in the Male ROR group might share more concerns on personal issues or questions based on institutional issues (e.g., campus policies).  
- **Shared Vocabulary**: Many words in each corpus lie near the diagonal in the scatterplots, indicating that some topics (such as references to “everyone,” “people,” or “students”) are common across all three groups. This makes sense, as these groups are all part of the broader NYUAD student community.

By looking at the text this way, we learn that even though all three groups revolve around student life, there are distinct linguistic nuances. It highlights how group identity or membership (male-only vs. female-only vs. general) can subtly shape the topics and tone of online participation on Facebook.

**Conclusion**

**Work breakdown**  
In the first meeting, we both worked together to brainstorm the initial idea, which was suggested by Insiya. In the second meeting, we brainstormed the methodology of selecting the posts and collected all of them equally, making sure to replace any duplicated posts that we collected from ROR. In the third and final meeting, we divided each other’s roles and began the process of using the tools and writing the analysis, which resulted in the following breakdown:

**Insiya**  
- Came up with the initial idea during the brainstorming  
- Used Voyant to analyze the corpus  
- Wrote the following sections:  
  - Importance of the corpus
  - Voyant Tools observations  
  - Conclusion  
  - References  

**Victor**  
- Separated the corpus into three different text files  
- Used the R code in the Posit Cloud to analyze the corpus  
- Formatted the Markdown code  
- Wrote the following sections:  
  - Thesis  
  - Introduction  
  - Importance of the corpus
  - Methodology  
  - R observations  
  - Work breakdown  

**Bibliography**

<!-- This assignment is ready to be graded. -->