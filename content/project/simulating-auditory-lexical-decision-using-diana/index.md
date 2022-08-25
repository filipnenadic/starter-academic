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
external_link:
image:
  filename: featured.jpg
  focal_point: Smart
  preview_only: false
---
This project is done in collaboration with [Benjamin V. Tucker](https://sites.ualberta.ca/~bvtucker/index.html) and [Louis ten Bosch](https://scholar.google.com/citations?user=BtRalMYAAAAJ&hl=sr&oi=ao).

Computational models of spoken word recognition attempt to both describe and simulate the process of spoken word recognition. Usually, the performance of these models is compared against the performance of human listeners in behavioral tasks. We used an end-to-end model of spoken word recognition called [DIANA](https://www.internationalphoneticassociation.org/icphs-proceedings/ICPhS2015/Papers/ICPHS0480.pdf) to simulate participant behavior in an auditory lexical decision task and test whether DIANA's performance matches human performance.

As can be seen in the figure above, DIANA takes actual sound as input. It calculates the activation of different candidates (for example, words) based on the input signal and depending on its acoustic models, what exists in its "mental" lexicon, and some preconceptions about what is expected to be heared (for example, higher frequency words are given higher activation; this is controlled by the gamma parameter you see in the image). As it calculates activation, DIANA also makes decisions. One such decision is which word is presented in the input signal. The decision is governed through a series of weights and thresholds that I won't describe in detail here, but one of the more important thresholds states what the difference in activation between the leading candidate and the runner-up should be for the model to finally settle and say "without doubt" that the leading candidate is indeed the winner. Finally, when a decision was reached, DIANA executes this decision in a simulation of a button press.

This architecture enables us to see what the model thought was presented and how much time it took it to make the decision and compare that to decisions that human listeners make and the time it takes them to make it. We tested exactly that by comparing DIANA estimates to human data from the [Massive Auditory Lexical Decision](http://aphl.artsrn.ualberta.ca/?page_id=827) project, while presenting DIANA with the same word recordings that the human subjects heard.

We simulated the lexical decision process by...

We also simulated the response latency estimates by...

Our results can inform further development of DIANA, also discussed in this [publication](https://www.mdpi.com/2076-3425/12/5/681).

Our work is presented in more detail in a [freely available paper](https://doi.org/10.1177/00238309221111752), with the [supplementary material available online](https://doi.org/10.7939/r3-jdpa-dn72).
