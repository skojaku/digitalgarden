---
{"dg-publish":true,"permalink":"/literature-notes/research-note/name-disambiguation/author-name-disambiguation/","dgHomeLink":true,"dgPassFrontmatter":false}
---


# Author name disambiguation
updated: 2022-09-21
#science-of-science/name-disambiguation 

Despite the importance of credit allocations, it is surprisingly difficult to answer *who wrote which paper.* We know the name of authors. But an author can have multiple names, and different persons can have the same name. Names are not sufficient to locate the authors. There are efforts to create digital author IDs such as ORCHID. Google Scholar automatically associates papers with authors, and everyone edits own publication list. ArXiv recently lets authors to claim authorships. Yet, these author IDs are far from a universal adoption because the author IDs are limited to the users of a paricular system, and they cannot handle old papers. We still lack a universal system that can link papers and authors across fields and time. 

# Trait types 
One can guess who an author is based on names and other information provided in papers. I call these information possibly pertained to author identity as *author trait*. Author traits include but not limited to names, coauthor names, affiliations, publication venues, paper title, publication year, and citations. 

### Names 
Although names are not a perfect indicator, it is still a useful trait, especially when we focus on a very specific field. Names work especially well for rare names. For instance, my name is pretty rare (there are only about 50 households on the planet who have my family name) so that I can be easily identified just by names. 

#### First initial method and all initial method:
The first initial method is probably the most simplest approach. For instance, "John Smith" is transfomed into "J. Smith" and we consider every "J. Smith" as the same person. The first name is shortened to deal with abbreviation. The all initial method also takes the middle initial into account. For instance "JM Smith". 
	
- [The structure of scientific collaboration networks | PNAS](https://www.pnas.org/doi/10.1073/pnas.98.2.404)

#### Hybrid approach: 
The first initial method tends to overmerge and the all initial method tends to oversplit. The accuracy of the two methods depends on the commonality of last names. For instance, the first initial method works if middle names are not indicative of author identity. This is the case for rare last names. On the other hand, the all initial methods are better for common names as the last name is not sufficient to pinpoint the author. The hybrid approach is to decide which method to use based on the variations in the middle name. 

- [Accuracy of simple, initials-based methods for author name disambiguation - ScienceDirect](https://www.sciencedirect.com/science/article/abs/pii/S1751157713000539?via%3Dihub)
### Citations 
Citations reflect topics and author identity. By topics, a paper cites another paper because the citing paper gounds itself on the cited paper. If two papers cite the same papers, these citing papers are likely to be related in topics. 

By author identity, I mean by two sense. First, an author tends to cite own papers. So if one paper cites another paper, and the author of the two papers have the same name, the authors are likely to be the same person. Second, authors are on average conservative and rarely change subjects. Two authors are likely to be the same person if they wrote papers on the same subject. 

- [Exploiting citation networks for large-scale author name disambiguation | EPJ Data Science | Full Text](https://epjdatascience.springeropen.com/articles/10.1140/epjds/s13688-014-0011-3)

### Coauthorships
Coauthorships are strong indicator of authorship. Scientists are embedded in social networks. In most sciences, scientists tend to work on a small number of other scientists, forming a small team. It is rare that two scientists with the same name happen to be in the same team. 

- [On Graph-Based Name Disambiguation | Journal of Data and Information Quality](https://dl.acm.org/doi/10.1145/1891879.1891883)

#### Based on other featuers
Affiliations, publication venues, and paper titles can be a strong indicator of author identity, although surprisingly few algorithms take these traits into account, possibly because it requires *disambiguation of traits*. For instance, [there are so many universities with similar names](https://www.collegeconfidential.com/articles/help-many-u-s-college-names-sound-alike/), which are hard to distinguished without external knowledge. 

# Trait weigting 
No single trait is sufficient to identify author identities. Still, we can create a strong predictor of author identities by combine multiple traits. Not all traits are equally powerful. Can we find strong traits? How should we weight them and aggregate them into a single prediction score?

## Rule based 
Rule-based approach determines a weight of a trait based on a set of predefined rules. Each rule consists of a condition and a score. For each pair of papers, one examine whether the two papers meet the condition (e.g., number of coauthors is greater than two), and if it does, adds up the score. The sum of the scores is the final prediction score, with a higher value indicating a higher likelihood that two papers are written by the same author. 

A virtue of the rule-based approach is its explainability, interpretability, and transparency. An issue is that making a good set of rules hinges on tacit knowledge about data domains. It is not clear why one rules has a higher score than the other, and often these rules are compiled based on intutitions and iterative experiments.  

## Machine Learning & Statistical mdoels

## Rule-based vs Machine learning 

# Benchmark and Dataset 
[S2Dataset](@subramanianS2ANDBenchmarkEvaluation2022.md)

# Code repository 


# References
- [Publishing: Credit where credit is due | Nature](https://www.nature.com/articles/508312a)
- [Accuracy of simple, initials-based methods for author name disambiguation - ScienceDirect](https://www.sciencedirect.com/science/article/abs/pii/S1751157713000539?via%3Dihub)