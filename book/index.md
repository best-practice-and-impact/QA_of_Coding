
# Introduction

## Quality Assurance of Code for Analysis and Research

This is an early draft of Government Statistical Service (GSS) and Analysis Function guidance, produced by the Best Practice and Impact division of the Office for National Statistics.

This guidance has been written to support analysts in government who use coding in their work.
This includes those who produce statistics, carry out modelling or apply data science.

## About us

You can find us on:
- Our websites: [Government Statistical Service](https://gss.civilservice.gov.uk/) and [Government Analytical Function](https://www.gov.uk/government/organisations/government-analysis-function)
- Email: [gsshelp@statistics.gov.uk](mailto:gsshelp@statistics.gov.uk) and [analysis.function@ons.gov.uk](mailto:analysis.function@ons.gov.uk)
- Slack: [GSS](https://gov-stats-service.slack.com) and [Gov Data Science](https://govdatascience.slack.com)
- Twitter: [GSS Good Practice Team](https://twitter.com/gssgoodpractice) and [UK GSS](https://twitter.com/ukgss)

```{figure} ./_static/GSS_logo.jpg
---
width: 60%
name: GSS_logo
alt: The Governments Statistical Service logo
---
```


## Structure of the book

The content of the book is ordered roughly in increasing depth. 
Each chapter is also broken down into sections that gradually increase in difficulty. 
We have noted a rough guide to difficulty for each section using a ★★★★★ rating system.


## How to get the most out of the book

This guidance is tailored to government analysts who would like to quality assure their code and increase the reproducibility of their analyses.
We have tried to interpret the requirements of pieces of guidance (the [principles](/principles.md)) into actions and deliverables for analytical programming.

However, the practices outlined in the book are general to many applications of programming, so may also be insightful for those outside of government.

This book might be most useful for you if you are:
- writing code to automate part of your work and would like to assure that it is working as expected
- developing a statistical production pipeline and would like to assure that it is long term sustainable and reproducible
- developing models and would like to assure that they are transparent and reproducible
- developing data science techniques and would like your code to be useful to others
- looking for a high level introduction to software engineering practices in the context of analysis and research

This book can be used to guide your learning and as a reference.
The start of each chapter describes the risks which the described practices may help to address.
Therefore, you should strive to apply the most appropriate practices given the risks associated with your work.

The principles in this book are language agnostic.  
It does not form a comprehensive learning resource and you may often need to study further resources to implement these practices.
That said, examples and useful references are provided for **Python** and **R**, as open source languages that are commonly applied across government.

Many of the learning references in this book point to the UK Statistics Authority Learning Hub, which are labelled GSS only.
All government analysts can request an account for the Hub via [gss.capability@ons.gov.uk](mailto:gss.capability@ons.gov.uk).


## Accessibility statement

This accessibility statement applies to the Quality Assurance of Code for Analysis and Research.
Please not that this does not include third-party content that is referenced from this guidance.

The website is managed by the Best Practice and Impact division of the Office for National Statistics.
We would like this guidance to be accessible for as many people as possible.
This means that you should be able to:
* change colours, contrast levels and fonts
* zoom in up to 300% without the text spilling off the screen
* navigate most of the website using just a keyboard
* navigate most of the website using speech recognition software
* listen to most of the website using a screen reader (including the most recent versions of JAWS, NVDA and VoiceOver)

For keyboard navigation, up and down arrow keys can be used to scroll up and down on the current page.
Left and right arrow keys can be used to move forwards and backwards thought the pages of the book.
Tabbed content (including code example) can be focused using the tab key.
Arrow keys are then used to focus the required tab option, where Enter can be used to select that option and display the associated content.

Parts of this guidance which are not accessible include:
* Our star rating for sections, which are not screen-reader friendly.


### Feedback and reporting accessibility problems

We’re always looking to improve the accessibility of our guidance.
If you find any problems not listed on this page or think that we’re not meeting accessibility requirements, please contact us by email at [gsshelp@statistics.gov.uk](mailto:gsshelp@statistics.gov.uk).
Please also get in touch if you are unable to access any part of this guidance, or require the content in a different format.

We will consider your request and aim to get back to you within 5 working days.


### Enforcement procedure

The Equality and Human Rights Commission (EHRC) is responsible for enforcing the [Public Sector Bodies (Websites and Mobile Applications) (No. 2) Accessibility Regulations 2018 (the ‘accessibility regulations’)](https://www.legislation.gov.uk/uksi/2018/952/made). 
If you’re not happy with how we respond to your complaint, you should [contact the Equality Advisory and Support Service (EASS)](https://www.equalityadvisoryservice.com/).
