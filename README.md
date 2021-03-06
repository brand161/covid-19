# Covid-19 (probably) isn't as bad as you think it is: A critical analysis of case fatality rate and basic reproduction rate
 
## Background
 
Over the past couple weeks I've become increasingly frustrated and disappointed with the misrepresentation and short sighted reporting around the severity of the Covid-19 outbreak from government agencies, "expert" sources, and the various media outlets.
 
As a software engineer that works in the machine learning space, I'm frequently involved with the analysis of data and understanding what the outcomes of a given data set mean.
 
An important thing that I've learned over time, is that the most essential requirement for any machine learning endeavor is a high quality data set. If there are any biases present in the data, they will be reflected in the outcomes generated by the machine learning model. ~Note to add examples~
 
Now, I'm no epidemiologist, but fundamentally, the analysis of a viral outbreak, such as Covid-19, also relies on having a data set that is free from bias. The same is true for any mathematical analysis of data; machine learning, disease modeling, etc. 
 
What prompted me to write this are the associated outcomes that misunderstanding and misrepresentation of various data cause in the context of public health and policy decisions for Covid-19, in addition to undue panic and fear circulating in communities. 
 
Specifically, the primary dimensions of Covid-19 that I see being misrepresented in news reports, tweets, etc are the Case Fatality Rate (CFR) and Basic Reproduction Rate (R0).
 
While these two data points are valuable decision making tools for qualified professionals, they're easily misunderstood by the general public and act as fuel for panic if not properly explained.
 
## R0 and CFR Explained
 
Before we dive into the nuances of the two data points, let's take a look at their simple definitions and touch on the history of them. 
 
The Basic Reproduction Rate is simply a measure of the contagiousness or transmissibility of infectious and parasitic agents. It is commonly "reported as a single numeric value or low–high range, and the interpretation is typically presented as straightforward; an outbreak is expected to continue if R0 has a value >1 and to end if R0 is <1". In simpler terms, it allows epidemiologists to determine "the number of secondary cases one case would produce in a completely susceptible population”.
 
The Case Fatality rate is an even simpler data point. It simply produces a ratio from dividing the number of deaths from a given disease by the total number of infected individuals. This gives an idea as to the lethality of the disease.
 
## Introduction to sampling bias
 
At a high level, sampling bias can be described as a bias in which samples for a dataset are collected or determined in such a way that some members of the intended population have a lower chance of being sampled than others. A very simple example for this would be trying to answer the question: "What percentage of people would eat candy for breakfast?", but only involving 4th grade children in the study. The likely outcome here would be an inflated percentage because we didn't include (or have access to) a well represented population in the study.
 
## The problems with R0 and CFR
 
With the concept of sampling bias in mind, let's take a closer look at the specific calculations. Since CFR is simpler, we'll start there.
 
### CFR
 
As mentioned earlier, the calculation for this is deaths / cases. Or in other words, the numerator of the fraction is deaths and the denominator is cases. As with any fraction, if you adjust either of these factors, the ratio it produces changes. 
 
In the case of CFR, this is especially important, because the accuracy of the ratio produced can be considerably skewed by underreporting of cases via sampling bias or inability to derive associated deaths from the disease. 
 
Put frankly though, it's a lot harder to miss dead bodies than it is to underreport the total number of cases. This is why during the beginning of an outbreak, the CFR tends to skew significantly higher, due to sampling bias discussed above. More specifically, in the case of sampling bias for CFR, asymptomatic / mild / moderate cases are much less likely to be accounted for in official numbers.
 
This happens for a myriad of reasons, but the obvious reason is this: People who aren't that sick likely won't seek treatment.
 
Therefore the only people being included in the population for determining CFR, are those who were sick enough to seek medical care.
 
You should see the clear error in this thinking; similar to our school children example, we've inflated the CFR by only deriving deaths from people who were severely / critically ill, or those who went out of their way to get tested. If we were able to include all cases (asymptomatic / mild / moderation), the CFR would be substantially lower. 
 
For these reasons (most) experts add a caveat to any CFR number they publish, something along the lines of "crude estimation" or "estimated CFR". Also for these reasons, many agencies simply do not report the CFR during the beginning of an outbreak, because technically speaking, it is impossible to calculate during an ongoing spread of disease (e.g. we don't have the required variables).
 
### R0
 
Basic reproduction rate is a trickier data point to describe, due to the complex mathematics involved, which is exactly why it's often misunderstood and used erroneously.  
 
In as simple of a way I can describe it, it is a ratio produced by solving a system of ordinary differential equations for a combination of components described by a given epidemiological model. These models usually include 3 primary parameters - the duration of contagiousness after a person becomes infected, the likelihood of infection per contact between a susceptible person and an infectious person or vector, and the contact rate, but more complex models include many more parameters.
 
In that lies the problem with using R0 for a measurement of a disease's severity or contagiousness. R0 values are estimated from mathematical models, and the estimated values are dependent on the decisions made in the modeling process. 
 
The selection of those values are based on specific populations and assumptions on demographics of a given outbreak - Any factor having the potential to influence the contact rate, including population density (e.g., rural vs. urban), social organization (e.g., integrated vs. segregated), and seasonality (e.g., wet vs. rainy season for vector borne infections), will ultimately affect R0. There is extremely limited evidence that the R0 of a given disease is even applicable outside the region where it was initially calculated. 
 
Furthermore, many of the parameters included in the models used to estimate R0 are merely educated guesses; the true values are often unknown or difficult or impossible to measure directly.
 
Succinctly put: "R0 is an estimate of contagiousness that is a function of human behavior and biological characteristics of pathogens. R0 is not a measure of the severity of an infectious disease or the rapidity of a pathogen’s spread through a population."
 
## Putting this all together 
 
So we've covered the issues inherent with CFR and R0, what does this all mean for Covid-19? 
 
It's probably not as bad as it seems. 
 
The data sets available have shown that roughly 30-80% of cases are asymptomatic to moderate, e.g. medical care not required. That means potentially up to 80% of cases are being unreported - which seems to fit the narrative that the virus has spread much more than thought. 
 
If we do some napkin math and extrapolate on that (and take a middle ground of 50%, we can estimate a global case count closer to 190,000. Performing our CFR calculation with that number produces a CFR of ~1.6% (~3.4% CFR not performing extrapolation). 
 
Still, 1.6% is fairly high. That being said, even adjusted for total case count, we have to remember that the majority of data has come out of Wuhan, and if we remember earlier, the R0 cannot be relied upon as an indicator for how the virus will spread elsewhere. Not only that, but Wuhan also was the start of the outbreak, which leads to incurring a higher than normal fatality rate. This is especially noted in the final report of the WHO-China joint mission, which pointed out a CFR of 5.8% for Wuhan and 0.7 in other areas of China.
 
A better estimate for our CFR would be building a composite dataset based on a more well balanced population, that is representative of the United States (Sorry, this is focused on the USA since I live here). 
 
For this composite, we'll take the numbers from Japan (inc. Diamond Princess), South Korea, and China (excluding Wuhan cases). This gives us 19,265 total cases and 372 deaths. We can then extrapolate our cases using the same percentage as before (e.g. assuming we're missing 50% of asymptomatic / mild or moderate case) and this results in 38,530 cases with a CFR of .96%, or roughly 1%. 
 
It doesn't end here though - 1% is about ~72% less than the current reported CFR of 3.6% and given that the distribution of severity is tightly correlated to age group, we should adjust the values by that factor per age group as well:
 
80+ years old
14.8% -> 4%
 
70-79 years old
8.0% -> 2.4%
 
60-69 years old
3.6% -> 1%
 
50-59 years old
1.3% -> .3%
 
40-49 years old
0.4% -> .1%
 
30-39 years old
0.2% -> .05%
 
20-29 years old
0.2% -> .05%
 
10-19 years old
0.2% -> .05%
 
Average = ~1%
 
We can can further simplify as follows: < 60 CFR = ~.11% and > 60 = 2.4% CFR
 
In other words, for persons under the age of 60 in the United States, your risk of death from Covid-19, is .1% - this is not cause for alarm or panic. 
 
 
## Conclusions
 
I hope I've been able to shed some light on the different values being used to describe the severity and contagiousness on Covid-19.
 
Any data referencing R0 or CFR as a measurement of severity or contagiousness should be taken with a huge grain of salt.
 
Already there's been drastic revisions downard for both values since the beginning of the outbreak.
 
To reiterate, R0 is easily subject to misrepresentation, misinterpretation, and misapplication. R0 values reported in scientific literature are often obsolete and values reported in the media fail to include the necessary context for understanding the true meaning behind the value. R0 must be estimated, applied, and reported with great caution. 
 
CFR is also easily subject to those same issues, namely due to lack of cases being added into the dataset - by virtue of minor cases being missed entirely, ever changing diagnosis criteria, and lack of testing ability. It should be used carefully and not without a proper disclaimer that it is purely an estimate, nothing more. 
 
Adjusting these values in light of the aforementioned issues results in a significantly more positive outlook for the USA outbreak of Covid-19. 
 
The vast majority of folks will be completely unaffected.
 
That being said, this is still a virus capable of killing - especially those in at risk groups. Extra caution should be taken with those groups. This can be accomplished by doing what you should be doing anyways: Wash your hands. Do it often. Cover your cough. Disinfect high use areas.
 
I'm not going to try and estimate an R0 for the USA, since it's far too variable to generate any meaningful value yet. For all we know, the virus could be a dud here entirely since we haven't seen how it spreads in less dense areas with different hygiene / social practices.
 
The estimates I've seen from experts (Marc Lipsitch) point to an R0 that indicates that 20-60% of a population will become infected (which has been revised down several times, which I believe will continue). In the USA, the number of deaths could range from 654,000 -> 1,962,000 based on that speculation. 
 
So again, this virus will absolutely kill, but it's not as bad as it's being made out to be. 
 
Practice your regular flu prevention processes and you'll probably be fine.
 
## Disclaimer
 
I'm not an expert. This is my interpretation of the data set currently available. I'm still subject to the same issues I discussed and if the data set drastically changes any certain way, I'll need to update this. Any figure I derived is an estimate and subject to change based on new / adjusted data. 
 
## Sources
 
* https://wwwnc.cdc.gov/eid/article/25/1/17-1901_article
* https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3935673/#fd1
* https://www.worldometers.info/
* https://www.who.int/docs/default-source/coronaviruse/who-china-joint-mission-on-covid-19-final-report.pdf
* https://journals.plos.org/plosntds/article?id=10.1371/journal.pntd.0003846
* https://gisanddata.maps.arcgis.com/apps/opsdashboard/index.html#/bda7594740fd40299423467b48e9ecf6
* https://www.nejm.org/doi/full/10.1056/NEJMe2002387?query=RP

## TODO

* Add citations
* Add examples for first paragraph
