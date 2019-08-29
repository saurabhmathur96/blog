---
layout: post
title:  "The perils of Facial Recognition"
date:   2019-08-29
categories: machine-learning
---


On June 28, 2019, the National Crime Records Bureau (NCRB) called for bids for the implementation of a Facial Recognition System
{% sidenote 'ad' 'The RFP is on [the NCRB website](http://web.archive.org/web/20190818023954/http://ncrb.gov.in/TENDERS/AFRS/RFP_NAFRS.pdf)' %}.
 This would allow the police to identify people by clicking a picture or pulling up CCTV footage and automatically matching them against a database of faces. This is a _terrible_ idea and here's why. 


## Bias


Technology has a profound impact on our lives. As John Culkin famously said: 
>"We shape our tools and thereafter our tools shape us." 

Take hip hop for example - a genre invented in house parties in the Bronx has now become a medium for dissent across the world thanks to Spotify and YouTube. The same streaming technology also brought about a trend of shorter tracks as the artists are now paid per stream{% sidenote 'hiphop' '\"Hip Hop and Streaming\", Patriot Act with Hasan Minhaj, Volume 2 Episode 5 ' %}. 

Similarly, when people with conscious and unconscious biases (See racism, sexism, etc.) design Facial Recognition Systems, these biases get transferred to the systems. And when such a system makes mistakes due to these biases, it results in discrimination on a large scale. 

Further, the biases get reinforced by [Automation bias](https://en.wikipedia.org/wiki/Automation_bias){% sidenote 'automation' 'People trust machine-made decisions more than they should.' %} and [Confirmation bias](https://en.wikipedia.org/wiki/Confirmation_bias){% sidenote 'automation' 'The machine is correct if it agrees with me.' %} . So, even if the AI doesn't make the final decision, the judgment of human-experts does get colored by it. To make problems worse, even the testing datasets are biased. In all the hype around AI, we _kind of forgot_ to check if our standard testing datasets represented the real world. So, the cycle continued silently. Until recently that is. 


In 2018, [Joy Buolamwini and Timnit Gebru](http://proceedings.mlr.press/v81/buolamwini18a.html) found that state-of-the-art Facial Recognition engines from giants like Amazon were biased. {% marginfigure '1' 'static/images/gender-shades.png' 'From the [Gender Shades project](http://gendershades.org/overview.html)' %} These off-the-shelf engines were 30 times more likely to misidentify dark-skinned women as compared to light-skinned men.


In a test last year, Amazon's _Rekognition_ service [falsely identified 28 US congresspeople as criminals](https://www.theguardian.com/technology/2018/jul/26/amazon-facial-rekognition-congress-mugshots-aclu).
78 concerned scientists wrote [this open letter](https://medium.com/@bu64dcjrytwitb8/on-recent-research-auditing-commercial-facial-analysis-technology-19148bda1832) to Amazon about the dangers of selling this technology to law enforcement.




## Transparency


Not only is facial recognition biased, but it is hard to fix. A lot of the recent progress in AI has been due to deep learning. With deep learning, the AI agent learns patterns directly from large amounts of data. In the case of facial recognition, for example, it would consider things like facial hair and texture of the skin. While this reduces the need for human-experts, it makes interpretability{% sidenote 'interpret' 'Why did the agent make a particular decision?' %} and feedback{% sidenote 'feedback' 'Correcting wrong decisions' %} hard. 

Ali Rahimi, [in his talk at NIPS 2017](http://www.argmin.net/2017/12/05/kitchen-sinks/), said:
>  We say things like "machine learning is the new electricity". I’d like to offer an alternative metaphor: machine learning has become alchemy.


And then there are adversarial attacks. Facial Recognition Systems, just like any other piece of software, can be attacked. Except, in the case of facial recognition, [the attack can be worn](https://dl.acm.org/citation.cfm?id=2978392). Not only can you evade detection but you can also impersonate someone just by wearing a pair of glasses with a specific pattern.

[equalAIs](https://equalais.media.mit.edu/) is a project by the MIT Media lab demonstrates the fragility of state-of-the-art Facial Recognition Systems. It makes a very small change to a picture such that the facial recognition system fails.




## Privacy

On 23rd August 2017, the Supreme Court of India unanimously recognized privacy as a fundamental right guaranteed by the Constitution after Justice K S Puttaswamy, a retired judge of the High Court, filed a writ petition in the Supreme Court. Mass surveillance using facial recognition infringes this Right to Privacy. 

Power corrupts and absolute power corrupts absolutely. In the modern context, information provides the corrupting absolute power. We've seen this happen throughout history whether it was [the IBM powered German census](https://www.jewishvirtuallibrary.org/ibm-and-quot-death-s-calculator-quot-2) or [the South African Book of Life](https://wiser.wits.ac.za/content/book-life-south-african-population-register-and-invention-racial-descent-1950%e2%80%931980-11640). The Chinese government has large-scale mass surveillance across the country. There have been reports about these surveillance systems being used to [track-down minorities and crush dissent](https://www.nytimes.com/2019/04/14/technology/china-surveillance-artificial-intelligence-racial-profiling.html). 

Governments across the world have justified this invasion of privacy and weaponization of data with broad terms like greater good and public interest.  In the Economic Survey of India 2018-19, the Ministry of Finance said that the elite's preference of privacy should not be imposed on the poor, who care for a better quality of living the most - which is _literally_ the opposite of what the supreme court ruled in the Right to Privacy case! As Puttaswamy puts it:
> "The refrain that the poor need no civil and political rights and are concerned only with economic well being has been utilised through history to wreak the most egregious violations of human rights." 





## The Indian Government


Surely if data can be weaponized like this, there would be laws regulating its usage. But there are none. In fact, the data protection bill which was drafted on the Supreme Court's directions last year has still not been passed{% sidenote 'privacy' 'The was part of the Right to Privacy case. This is the same case in which the government unsuccessfully argued that the people of India do not have a right to their own body. '%}.


Further, the Minister for IT, R S Prasad refused to release the _public_ consultations held in the drafting of the personal data protection bill{% sidenote 'meity' 'Response to Unstarred Question #3685 on 25th July in the Rajya Sabha.' %}. In contrast, the US House of Representatives invited experts to testify in Congress for over three hours and live-streamed it on YouTube.  The full video of the live-stream from 22nd May 2019 is available [here](https://www.youtube.com/watch?v=jLmzEFkbNsg) and the specific questions by Congresswoman Alexandria Ocasio-Cortez are available [here](https://www.youtube.com/watch?v=pxZk6IQxaLY).


The Indian Government's disregard for personal privacy and misuse of data is not just an abstract concept - it is already happening. The Minister of Road Transport and Highways, Nitin Gadkari said that ministry has been selling vehicle registration and driving license data of Indian citizens without consent. {% sidenote 'mrth' 'Response to Unstarred Question #1698 on 8th July in the Rajya Sabha. The government has provided access to 87 private and 32 government entities, earning Rs. 65 crore.' %} 


The general lack of government accountability only makes it worse. The state of accountability is so bad that NCRB, the government agency that is having a Facial Recognition System built, [has not published its annual report after 2016](https://www.thehindu.com/news/national/ncrb-report-centre-blames-bengal-bihar/article28128233.ece). 


## The Solution

In their 172 page RFC, the NCRB failed to address even a single one of these issues, and therein lies the problem. Had there been public consultations, experts would have pointed out these flaws. Given the fast rate of technological progress, public consultations are vital to ensure that the people's interests are represented. 

As far as Facial Recognition is concerned, the technology is far from perfect and its use by law enforcement has been banned in many places around the world. If a similar ban is not enacted in India, there should at least be laws defining precisely when and how the technology will be used.
