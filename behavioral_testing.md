---
layout: default
title: Behavioral Testing
rank: 4
---

This section provides helpful information on conducting Behavioral Experiments as a member of the Predictive Brain Lab. It includes concise summaries of the procedures outlined in the [intranet website](https://intranet.donders.ru.nl/index.php?id=beh-labs), along with helpful tips and tricks, and references to useful resources for behavioral techniques. 


- [Behavioural Labs](#behavioural-labs)
- [Behavioural Testing Software](#behavioural-testing-software)
- [Psychophysics](#psychophysics)
  - [What Do We Use Psychophysics For?](#what-do-we-use-psychophysics-for)
  - [What Are Commonly Used Methods?](#what-are-commonly-used-methods)
  - [Useful Resources](#useful-resources)

  
# Behavioural Labs

The Trigon building of the DCCN has 9 cubicles on the basement (-1) floor that can be employed to conduct behavioral experiments. These cubicles are equipped with:

- A desk with a computer, mouse and keyboard
- Two button boxes
- Audioboxes and a set of headphones

_If you require additional materials, you can check the [intranet page](https://intranet.donders.ru.nl/index.php?id=beh-labs-equipment) to see the different resources the univeristy has to offer_

Additionally, the DCCN has 3 larger behavioral labs that can be employed for your experiments. These have different locations and special lay-outs to match with different experimental paradigms. You can find information for those laboratories [here](https://intranet.donders.ru.nl/index.php?id=beh-labs-layout)

To check for availability of the behavioral lab facilities you can make use of the [Donders Intranet Calendars](https://portal.dccn.nl/calendars/lab) (_Note_ you will need your Donders account to see this). 
There are two different ways to make bookings: 
* Pilots of Floris de Lange - for piloting procedures
* Using your personal number - this is only obtained after the project as been presented in a PPM meeting (see [_Lab Basics_](./lab_basics.md) PPM section)

Remember to always turn on the red light for the behavioral testing rooms. Only in this way, other scientists will know you are currently testing. Likewise, if you see the light on, please be as quiet as possible when walking around the area. 

There is a desk space for the experimenter to wait outside of the cubicle area. It is essential to be nearby in case your participant requires assistance.

For a checklist of a behavioral session, you can use this [template](https://docs.google.com/document/d/1ZSTiefJdUuVGoO00uoj6vZxGBkfi-IeamdLvl56VwdY/edit?usp=sharing) and adapt it according to your personal preferences and needs

# Behavioural Testing Software

There is a variety of software being used to create experiments for neuroscience. Most of the time, you will  likely use the same programs that you were taught during your time as a graduate student of PhD candidate. In the Predictive Brain Lab, we predominantly make use of two programs:

1. [Pyschtoolbox](http://psychtoolbox.org/) - free set of MATLAB functions to create neuroscience experiments. Most members of the lab use this and can provide you with help if needed. 
This [webiste](https://peterscarfe.com/ptbtutorials.html) contains a variety of tutorials to get familiar with coding different types of experimental paradigms. 

2. [PsychoPy](https://www.psychopy.org/) - free set of Pyhton functions to create psychological and neuroscience experiments. A few members of the lab are familiar with this software and can give help if needed. 
The PsychoPy [website](https://psychopy.org/documentation.html) contains tutorials and open source code you can look at to get inspired. 

_**Before starting to code ANY experiment**. Check the compatibility of the software you are planning to use with the Donders Institute computers. The neuroimaging laboratories do not support all software options_

#### Other software options
There are other software options to create your own experiments. These are also popular and you might be familiar with them. Nonetheless, we recommend using one of the two above.
* [Open Sesame](https://osdoc.cogsci.nl/) - A user-friendly interface to create your own psychological experiments
* [Presentation](https://www.neurobs.com/) - A Windows owned program for stimulus delivery and experiment control for neuroscience

# Psychophysics

Psychophysics concerns itself with the relationship between physical properties of stimuli and the sensations and perceptions produced by them. In this section, we provide guidance on how to implement psychophysical procedures that might use in your experiments. We will provide code examples as well as literature for you to consult in case of need. 

## What Do We Use Psychophysics For?
* To estimate thresholds, just-noticeable differences (JND), point of subjective equality (PSE), etc. for every subject.
* To map the shape of psychometric curves for every subject
* To control for task difficulty, so that the task accuracy is comparable across subjects (or conditions)

## What Are Commonly Used Methods?
The two types of staircasing procedures described below have their own pros and cons. To understand them better, we recommend you read the literature associated to each of them. A **key difference** to keep in mind is that _running fit method_ assumes that you know the shape of the underlying psychometric functions. On the other hand, the _up-down method_ works regardless of the shape of the underlying psychometric function. 

### 1. N-Up-M-Down Staircase (_e.g.,_ 2-Up-1 Down)

**How do we decide the N and the M?**
- Check the desired accuracy level you are aiming for, see _Table 2_ of the [Garcia-Perez (1998) paper](https://www.sciencedirect.com/science/article/pii/S0042698997003404?via%3Dihub#SEC2)

  
### 2. Running-Fit Methods

Following every trial, all collected data is used to fit a psychometric function (PF). This fitted PF is then utilized to determine the stimulus intensity for the next trial. 

**bestPEST** ([see here](https://link.springer.com/article/10.3758/BF03204398))

It assumes a specific form of the psychometric function and estimates only the threshold parameter of the psychometric function.

**Quest** ([see here](https://link.springer.com/article/10.3758/BF03202828))

It is essentially the Bayesian alternative to _bestPEST_. Note that when the prior is uniform and we use the mode of the posterior distribution as our estimate of the threshold, Quest is equivalent to the bestPEST.

Also see [here](https://jov.arvojournals.org/article.aspx?articleid=2611972), for a 2017 revised version of QUEST. 

**Practical Tricks**

The following list describes a series of tricks that can help you improve the final outputs of your staircase procedure:

* Provide your subjects with enough time to practice before running your staircase. As a rule of thumb you can provide them with ~50 trials.
* Create plots of every run of your staircase to check for convergence
* Use minimum two runs of staircases, and only read out from the ones that have converged.
* Instead of having very long runs of staircases (_e.g.,_ staircase of 90 trials), split them into short staircases (_e.g.,_~45 trials). This results in better output.

### Useful Resources

To implement any of the aforementioned procedures you are recommended to use [PsychToolbox](http://psychtoolbox.org/) (MATLAB) or [PsychoPy](https://www.psychopy.org/) (Python). _Note_: it is notoriously hard to implement staircases with Presentation. Hence, we recommend using one of the two other software options. 

The following list provides resources to learn more about these procedures:

* [The Palamedes Toolbox](https://www.palamedestoolbox.org/) - MATLAB routines for analyzing psychophysical data
* [Implementing staircase procedures in PsychoPy](https://www.psychopy.org/recipes/interleaveStaircases.html)
* [Forced-choice staircases with fixed step sizes: asymptotic and small-sample properties (Garcia-Perez, 1998)](https://www.sciencedirect.com/science/article/pii/S0042698997003404?via%3Dihub#SEC2) - Essential paper for thresholding
* [Simple adaptive testing with the weighted up-down method (Kaernbach, 1991)](https://psycnet.apa.org/record/1982-02539-001) - More specific resource. Not always applicable (see paper above first for an overview)

