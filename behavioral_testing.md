---
layout: default
title: Behavioral Testing
rank: 4
---

This section provides helpful information on conducting Behavioral Experiments as a member of the Predictive Brain Lab. It includes concise summaries of the procedures outlined in the [intranet website](https://intranet.donders.ru.nl/index.php?id=beh-labs), along with helpful tips and tricks, and references to useful resources for behavioral techniques. 


- [Behavioural Labs](#behavioural-labs)
- [Psychophysics](#psychophysics)
  - [What Do We Use Psychophysics For?](#what-do-we-use-psychophysics-for)
  - [What Are Commonly Used Methods?](#what-are-commonly-used-methods)

  
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

**Practical Tricks**
The following list describes a series of tricks that can help you improve the final outputs of your staircase procedure:

* Provide your subjects with enough time to practice before running your staircase. As a rule of thumb you can provide them with ~50 trials.
* Create plots of every run of your staircase to check for convergence
* Use minimum two runs of staircases, and only read out from the ones that have converged.
* Instead of having very long runs of staircases (_e.g.,_ staircase of 90 trials), split them into short staircases (_e.g.,_~45 trials). This results in better output.
* 


Before explaining how to do psychophysics, it is important to note that it is notoriously hard to implement staircases with Presentation (sorry, Presentation users). To do psychophysics, you’re recommended to use PsychToolbox or PsychoPy. The following description is based on PsychToolbox, as it has the most users in our lab.




1. N-Up-M-down staircase (e.g., 2-Up-1-Down)

1.1. How do we decide the N and the M?
- Check what accuracy level you’re targeting, see Table 2 of the Garcıa-Pérez (1998) paper.

1.2. Practical tricks?
- Besides coding up your Up-Down staircases correctly, there are several tricks that would improve the final outputs of the staircase procedure.

Give your subjects enough practice before running your staircases. Fifty trials or more practice trials would be a good start.
Plot every run of your staircase to check convergence.
Use at least two runs of staircases, and only read out from the ones that have converged.
Instead of having long runs of staircases (e.g., staircase of 90 trials), splitting it into short staircases (e.g., staircases of 45 trials) would give you better output.
2. Running-fit methods: after every trial a psychometric function (PF) is fit to all the data collected so far, the fitted PF then serves to select a stimulus intensity for the upcoming trial.

2.1. bestPEST assumes a specific form of the psychometric function and estimates only the threshold parameter of the psychometric function.

2.2. Quest is essentially a Bayesian version of the bestPEST, note when the prior is uniform and we use the mode of the posterior distribution as our estimate of the threshold, Quest is equivalent to the bestPEST.
Practical tricks? - The same tricks mentioned above apply here as well.

Useful resources
The Palamedes toolbox
Implementing staircase procedures in PsychoPy
