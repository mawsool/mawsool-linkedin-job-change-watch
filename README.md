# LinkedIn Job Change Detector & Alerts

**Schedule a LinkedIn URL list and receive a `needsUpdate` verdict when a company or headline changes.**

**Mawsool LinkedIn data suite:** use **Current Company Checker** for one-time CRM audits, **Profile Details from URL** to enrich changed records, and **Mass LinkedIn Profile Scraper** for large backfills.

## How does scheduled job-change monitoring work?

1. Save an Actor task containing your LinkedIn URLs.
2. Add an Apify Schedule: daily, weekly, or monthly.
3. The first run stores the baseline.
4. Later runs compare the current company and headline with the previous snapshot.
5. Changed rows appear in the dataset and can be POSTed to your HTTPS webhook.

State is kept in a named key-value store in your Apify account. Your CRM database and custom attributes do not leave your account; only submitted LinkedIn URLs are checked.

## What do I pay if I check weekly?

Every scheduled run checks every URL once. Every URL checked is billed, whether changed or unchanged.

`monthly cost ≈ URLs × plan price per URL × runs per month`

At the FREE tier ($0.60 / 1,000 checks):

- 1,000 weekly URLs: $0.60/week.
- 1,000 daily URLs: about $18 in a 30-day month.
- 10,000 monthly URLs: $6/month.

## Output

The baseline run writes baseline rows. Later runs write changed rows only: previous/current company, previous/current headline, `needsUpdate`, and `changeType`.

## Alerts

Set `webhookUrl` to receive changed rows. You can also connect the scheduled task to Apify email, Slack, Make, or Zapier integrations.

## FAQ

### How does a job-change watch work?

Each scheduled run checks the company and headline. The first run is the baseline. Later runs report company and headline changes. From $0.60 per 1,000 profile URLs per run.

### Does a stopped run start over at the first URL?

No. The next run continues the URLs that were not checked, then starts a fresh cycle after the full list is done.

## Where to run it

Run the published Actor on Apify, or start from [mawsool.tech](https://mawsool.tech). This repository does not include the lookup address.
