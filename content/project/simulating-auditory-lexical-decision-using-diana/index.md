---
title: Simulating auditory lexical decision using DIANA
date: 2022-08-25T12:05:52.170Z
summary: DIANA uses actual sound input and provides RT estimates, but the
  current way of calculating added time to decide between word candidates does
  not match behavioral data
draft: false
featured: false
tags:
  - SWR
external_link: asd
image:
  filename: featured.jpg
  focal_point: Smart
  preview_only: false
---
This project is done in collaboration with [Benjamin V. Tucker](https://sites.ualberta.ca/~bvtucker/index.html) and [Louis ten Bosch](https://scholar.google.com/citations?user=BtRalMYAAAAJ&hl=sr&oi=ao).

Computational models of spoken word recognition attempt to both describe and simulate the process of spoken word recognition. Usually, the performance of these models is compared against the performance of human listeners in behavioral tasks. We used an end-to-end model of spoken word recognition called [DIANA](https://www.internationalphoneticassociation.org/icphs-proceedings/ICPhS2015/Papers/ICPHS0480.pdf) to simulate participant behavior in an auditory lexical decision task and test whether DIANA's performance matches human performance.

As can be seen in the figure above, DIANA takes actual sound as input. It calculates the activation of different candidates (for example, words) depending on its acoustic models, what exists in its "mental" lexicon, and some preconceptions about what is expected to be heared (for example, higher frequency words are given higher activation; this is controlled by the gamma parameter you see in the image). As it calculates activation, DIANA also makes decisions, and this process is governed through a few weights and thresholds applied to the activation values. Finally, when a decision is reached, DIANA executes this decision in a simulation of a button press.

This architecture enables us to generate model estimates of response latency and accuracy and compare them to decisions that human listeners make. We tested exactly that by comparing DIANA estimates to human data from the [Massive Auditory Lexical Decision](http://aphl.artsrn.ualberta.ca/?page_id=827) project, while presenting DIANA with the same word recordings that the human subjects heard.

DIANA decides whether the input signal is a word or not by comparing activation levels in under two conditions. First, DIANA calculates the best possible activation obtained when the input signal is forced to activate one of the words in its lexicon (word activation). Second, DIANA calculates the best possible activation obtained when the input signal is not forced to align to any existing string of speech sounds (phone activation). If the input signal 

DIANA estimates when a decision is made by 

 that I won't describe in detail here., but one of the more important thresholds states what the difference in activation between the leading candidate and the runner-up should be for the model to finally settle and say "without doubt" that the leading candidate is indeed the winner. 

To summarize, DIANA can take actual acoustic signal as input and provide explicit estimates of response accuracy and latency, allowing comparability to behavioral data. It also features an interesting mechanism for deciding whether the signal is a word or not that performs fairly well. However, the current implementation of the decision time past word offset does not align with behavioral data, so some adjustments may be needed in the future. A lot more detail is presented in a [freely available paper](https://doi.org/10.1177/00238309221111752) we published, with the [supplementary material available online](https://doi.org/10.7939/r3-jdpa-dn72). If you're interested, you should also look at this [publication](https://www.mdpi.com/2076-3425/12/5/681) about DIANA by Louis ten Bosch, [Lou Boves](https://www.researchgate.net/profile/Lou-Boves-2), and [Mirjam Ernestus](https://mirjamernestus.nl/Ernestus/Home.php).