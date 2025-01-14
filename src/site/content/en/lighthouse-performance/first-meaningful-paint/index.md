---
layout: post
title: First Meaningful Paint
description: |
  Learn about Lighthouse's First Meaningful Paint metric and
  how to measure and optimize it.
date: 2019-05-02
updated: 2019-10-04
web_lighthouse:
  - first-meaningful-paint
---

First Meaningful Paint (FMP) is one of six metrics
tracked in the **Performance** section of the Lighthouse report.
Each metric captures some aspect of page load speed.

Lighthouse displays displays FMP in seconds:

<figure class="w-figure">
  <img class="w-screenshot" src="first-meaningful-paint.png" alt="A screenshot of the Lighthouse First Meaningful Paint audit">
</figure>

## What FMP measures

FMP measures when the primary content of a page is visible to the user.
The raw score for FMP is the time in seconds between the user initiating the page load
and the page rendering the primary above-the-fold content.
FMP essentially shows the timing of the paint
after which the biggest above-the-fold layout change happens.
Learn more about the technical details of FMP in Google's
[Time to First Meaningful Paint: a layout-based approach](https://docs.google.com/document/d/1BR94tJdZLsin5poeet0XoTW60M0SjvOJQttKT-JK8HI/view).

[First Contentful Paint (FCP)](/first-contentful-paint)
and FMP are often the same
when the first bit of content rendered on the page includes the content above the fold.
However, these metrics can differ when, for example,
there's content above the fold within an iframe.
FMP registers when the content within the iframe is visible to the user,
while FCP _doesn't_ include iframe content.

## How Lighthouse determines your FMP score

Just like FCP, FMP is based on
[real website performance data from the HTTP Archive](https://httparchive.org/reports/loading-speed#fcp).

When FMP and FCP are the same,
their scores are identical.
If FMP occurs after FCP—for example, when a page contains iframe content—the
FMP score will be lower than the FCP score.

For example, let's say your FCP is 1.5&nbsp;seconds,
and your FMP is 3&nbsp;seconds.
The FCP score would be 99, but the FMP score would be 75.

This table shows how to interpret your FMP score:

<div class="w-table-wrapper">
  <table>
    <thead>
      <tr>
        <th>FMP metric<br>(in seconds)</th>
        <th>Color-coding</th>
        <th>FMP score<br>(FCP HTTP Archive percentile)</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>0–2</td>
        <td>Green (fast)</td>
        <td>75–100</td>
      </tr>
      <tr>
        <td>2–4</td>
        <td>Orange (average)</td>
        <td>50–74</td>
      </tr>
      <tr>
        <td>Over 4</td>
        <td>Red (slow)</td>
        <td>0–49</td>
      </tr>
    </tbody>
  </table>
</div>

{% include 'content/lighthouse-performance/scoring.njk' %}

## How to improve your FMP score

{% include 'content/lighthouse-performance/improve.njk' %}

## Tracking FMP on real users' devices

To learn how to measure when FMP actually occurs on your users' devices,
see Google's [User-centric Performance Metrics][metrics] page.
The [Tracking FMP using hero elements][tracking] section describes
how to programmatically access FCP data and submit it to Google Analytics.

See Google's [Assessing Loading Performance in Real Life with Navigation and Resource Timing](https://developers.google.com/web/fundamentals/performance/navigation-and-resource-timing/)
for more on collecting real-user metrics.
The [User Timing Marks and Measures Lighthouse audit](/user-timings)
enables you to see User Timing data in your report.

## Resources

- [Source code for **First Meaningful Paint** audit](https://github.com/GoogleChrome/lighthouse/blob/master/lighthouse-core/audits/metrics/first-meaningful-paint.js)
- [Lighthouse v3 Scoring Guide](https://developers.google.com/web/tools/lighthouse/v3/scoring)
- [Time to First Meaningful Paint: a layout-based approach](https://docs.google.com/document/d/1BR94tJdZLsin5poeet0XoTW60M0SjvOJQttKT-JK8HI/view)

[metrics]: https://developers.google.com/web/fundamentals/performance/user-centric-performance-metrics
[tracking]: https://developers.google.com/web/fundamentals/performance/user-centric-performance-metrics#tracking_fmp_using_hero_elements
