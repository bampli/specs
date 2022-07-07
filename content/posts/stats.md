---
author: "José Motta Lopes"
date: 2022-07-01
linktitle: Statistical Distributions
menu:
  main:
    parent: tutorials
#next: /posts/github-pages-blog
#prev: /posts/automated-deployments
title: Statistical Distributions
weight: 100
tags: [
    "how-to-change",
]
---
The amount of time each **Stage** requires at run time should be treated as a frequency distribution to be *designed* by the **Process**, ultimately by the **Cyclo**. When implemented by the **Facility**, the [Times of Gain](/docs/cyclo/time) from the running **Cyclo** should be captured and analyzed, in order to check how close they are from the expected timing.

The timing analysis should detect variations due to existing **common** and **special causes** in the **Process**, according to **SPC** (Statistical Process Control) and [**TPM**](/posts/tpm/) (Total Productive Maintenance) directives.

## Summary of a frequency distribution

Inspired on Tukey's idea, referenced in Martin Bland's [*An Introduction to Medical Statistics*](https://www-users.york.ac.uk/~mb55/intro/quantile.htm), a measure based on **Quartiles** & **Box/Whisker Plots** would summarize frequency distributions in a few numbers. The image below shows that median, quartiles, maximum and minimum may be used as a convenient five figure summary of a distribution.

![image](https://user-images.githubusercontent.com/86032/176902527-0039bd50-84bb-4a6a-965f-088f152e970d.png)

The *box* shows the distance between the quartiles, with the median marked as a *line* in between, and the *whiskers* at extremes. Plots are also useful for comparison, the example shows results from patients with AIDS, AIDS Related complex, HIV positive but asymptomatic, and normal.

## Distribution

- **name**: Distribution name.
- **sample**: [data] array
- **size**: Sample size.
- **is_normal**: True if sample fits a normal distribution.
- **is_uniform**: True if sample fits an uniform distribution.
- **summary**: Object with {max, qt3, med, qt1, min}.

TODO: Confidence interval narrows estimated percentiles?
- [95% confidence interval](https://www-users.york.ac.uk/~mb55/intro/cicent.htm)
- [Normal range or reference interval](https://www-users.york.ac.uk/~mb55/intro/refint.htm)

{{< hint info >}}
**Published in [Business Amplifier](https://www.amazon.com/Business-Amplifier-M-Sc-Motta-Lopes/dp/B083XGK14Q), also [e-book](https://www.amazon.com/Business-Amplifier-Jose-Motta-Lopes-ebook-dp-B086L6V6QY/dp/B086L6V6QY/) and [Amplificador de Negócios](https://www.amazon.com/M-Sc-Jose-Motta-Lopes/dp/8592301009).**
{{< /hint >}}
