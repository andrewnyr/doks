---
title: Frequently Asked Questions
description: Some of the commonly asked questions about Statusflare!
lead: ''
date: 2021-04-22T04:00:00.000+00:00
lastmod: 2021-04-22T04:00:00.000+00:00
images: []
menu:
  docs:
    parent: "Docs"
weight: "130"
toc: true

---
## Where do I sign up?

Welcome, you can sign up [here](https://dash.statusflare.com)!

## How do I add a custom domain?

Custom domains add a level of personalization with a few different ways to add them, you can start [here](https://docs.statusflare.com/custom-domains)!

## What type of checks are offered?

You are limited to HTTP(s) on the free plan, while all paid plans also include TCP and ICMP (ping) checks.

## Do you have a free plan?

Yes, we do! Our free plan is perfect to check our service out and to run checks on smaller websites.

## Why is my status page showing no state?

Status pages will show no state if the status page is very new or no monitors have been assigned to the status page yet.

## Can I select the location the check is performed from?

Yes, you can! On the monitors page in the dash you will see a dropdown box titled "Worker." In the dropdown you can select where you want your checks performed from.

## How often are the checks executed?

Checks are executed every 5 minutes on free plans and every minute for all paid plans.

## What are the IP addresses that the monitors will be checked from?

None of the IPs are static as of now and will likely to be rotated several times during the beta, so if you need IP whitelisting, please reach out to us.

## Are redirects followed?

Yes. Redirects are followed as the default option for now but will be part of the settings in the future.

## Can I specify HTTP headers?

As of right now, no. The feature is definitely coming to Statusflare soon.

## What is the timeout, can I change it?

Right now the entire platform has a timeout of 20 seconds, in the future you will be able to set a lower limit.

## What is the beta plan?

The beta plan is the custom plan created for new users to try out our product while we are in beta. Currently, the beta plan allows for five monitors, one integration, one status page, and five minute checks.

## After beta, will my account be removed?

When beta is over, current beta accounts will be turned into free plan accounts, if over the free limit, you won't be able to create more monitors, but already existing monitors will still be checked.

## What are monitor retries?

A monitor might be checked multiple times to confirm outage before notifying you. These retries will happen within the minute.

## Why is status page still active if I just deleted it?

Sometimes status pages are still shown because they are cached at the edge. If the page still shows up after a few minutes you can [contact us](/support).

## What locations are in the random regions?

Random regions usually rotate between Eastern North America, Eastern/Western Europe, Asia, and Oceania.

## Can I manage my account via an API? Where do I find the API documentation?

Statusflare is built _for_ developers and we do have an API. Stay tuned, the documentation for the API is being created right now.