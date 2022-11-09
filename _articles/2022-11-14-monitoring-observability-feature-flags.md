---
layout: article
title: Monitoring, Observability, and Feature Flags
author: Michael
draft: true
---

Monitoring & observability forms the pillar of knowing the state of your application and product. It lets you know how features are performing or if the application is working at all. Feature Flags allow you to leverage the monitoring an observability to safely roll out features or run experiments.

<!--more-->

## Monitoring & Observability

“Is my application working?” That is the very basis for monitoring and observability. “Working” in this case means many things. In a mature product, teams will have numerous dashboards to monitor uptime, performance, experimentation results, and many other key metrics. But at the early MVP or post-MVP stages, none or almost none of these exist.

#### Visibility into your systems

When trying to find product-market fit, fast iteration is key. But contrary to the early Silicon Valley mantra, you want to move fast but NOT break things. With early-stage rapid iteration, only two questions really need to be answered: “is my application broken?” and “did my change make a measurable impact?” To be confident in deploying changes frequently, you need an autonomous process to quickly let you know if anything is broken. And to know if your changes even mattered in your quest for product-market fit, you need to know if and how your changes made an impact on your users’ behavior.

There are two basic metrics to look at when starting to monitor if your changes broke anything: uptime and error rate. In a mature application, these would not be nearly enough. They will tell you that something is broken, but they won’t necessarily tell you what or why or the severity. However, uptime and error rate are Good Enough™ to start with.

#### Are things broken

Once you’re monitoring these basic metrics, you can then use them to trigger alerts. It’s better to have computers tell you things are broken rather than your users. These alerts would be triggered if an API endpoint or a website goes down or when a spike in the rate of errors occurs. Bonus points if the API endpoint for uptime can also verify the health of underlying systems like your database, caching server, etc. For further reading on how to do proper alerting as your application matures and becomes more complex, I recommend [My Philosophy on Alerting](https://docs.google.com/document/d/199PqyG3UsyXlwieHaqbGiWVa8eMWi8zzAn0YfcApr8Q) and [Chapter 6 - Monitoring Distributed Systems](https://sre.google/sre-book/monitoring-distributed-systems/) from Site Reliability Engineering written by Rob Ewaschuk, a Site Reliability Engineer at Google.

#### Did users respond to my change

The other important question: “did my change make a measurable impact?” is a bit harder to give specific guidance on. It really depends on what the change is and in which part of the stack it was made, but one way to get started with this might be to ask yourself “how do I know people are using the feature?” and “what needle was I trying to move?”. These are the basis for identifying users that are entering your funnel and converting thus determining if your feature had a positive or negative impact.

For example, you’re working on an e-commerce website and want to implement a feature to reduce cart abandonment. You’ve decided to set up an automatic email reminder to users who added items to their cart but didn’t checkout. A rough way of determining if that made a difference is to compare the rate of completed purchases both before and after the feature. You could also test sending the reminder either 24 hours or 48 hours after cart abandonment, and look at the number of users who opened the email, the number that clicked the recovered cart link, and how many completed a purchase. You could use logs, database records, web analytics platforms, etc. to measure these checkpoints. It all depends on what makes the most sense for your application and knowing which metric matters.

#### Test without deploying changes

Again this is a rough way of verifying changes made an impact since you can’t guarantee that your control group (the users pre-deploy) would behave the same as the treatment group (the users post-deploy). The next section discusses feature flags to solve that particular problem, but setting up this observability now is the basis for running experiments.

## Feature Flags

Feature flags are one of the most important tools for rapidly and iteratively deploying changes as you try and find product-market fit with your application. They are the basis for deploying chunks of a feature before it’s ready, responding to system outages, and experimenting. A feature flag is nothing more than a branch in code that can be configured to be “off”, “on”, or any other value via configuration without needing to release code.

#### Deploy smaller releases

When you’re in the MVP phase, you’ve probably been pushing complete features in one massive deployment – because how else would you do it? But as the team grows and there are more developers in the mix, this becomes a major pain point. I’ll discuss the value of Small Releases in a future article, but they’re only possible because of feature toggles. Using feature toggles, you can merge and deploy chunks of code without users ever touching them! You no longer need to wait until an entire feature is completed before merging and deploying your code and testing it in production. In non-product environments, you can even start manually testing and using the bits of the new feature while working on it.

#### Disable broken features instantly

Why is this important? Well, when pushing out new features or developing with dependencies on external resources, things will inevitably go wrong. You don’t always need to push code to fix a problem. Feature flags let you immediately (even automatically) disable a feature that isn’t working or a potential third-party resource that isn’t available without having it go through an entire deployment process. The page you just launched is crashing unexpectedly? Disable the feature flag that shows the button to users! The migration from “legacy step in your checkout process” to your “refactored and totally 100% works for me” step not actually working for users? Disable the feature flag and have users continue with the legacy step! Feature flags let you respond to production issues much faster than with code changes. I’d argue that every new substantial feature or migration should be deployed behind at least a short-lived feature toggle.

#### Feature toggles systems

The engineering teams at larger companies like [Shopify](https://shopify.engineering/using-betas-to-deploy-new-features-safel) and [Yelp](https://venturebeat.com/business/yelp-bunsen-lets-us-test-products-at-scale) have built bespoke feature flag tooling into their CI/CD pipelines, but there are ready-made solutions for the rest of us. While not an endorsement, we’ve had good experiences with [LaunchDarkly](https://launchdarkly.com), a reasonably priced, fully featured platform for getting started with feature flags.

Monitoring and observability allows you to know if a feature had an impact on your users’ behavior. With feature toggles, you can run A/B tests to measure the impact of your changes and experiment with doing phased rollouts. Roll out your feature to X% of your users, see how it performs, roll it out to another X% of users, check again, and proceed from there. For a more technical deep dive into feature flags, how they work, and implementation strategies, I recommend Pete Hodgson’s [Feature Toggles (aka Feature Flags)](https://martinfowler.com/articles/feature-toggles.html) article on Martin Fowler’s blog.
