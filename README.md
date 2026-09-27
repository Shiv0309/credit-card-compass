# The Credit Card Compass 🧭

**Carolina Data Challenge — AI for Social Good**

Just as a compass gives you a clear direction when you're otherwise
lost, this tool gives consumers a clear direction when choosing between
credit card companies, pointing toward the bank most likely to actually
resolve the problems they're worried about.

Choosing a credit card shouldn't come down to guesswork. This tool
helps everyday consumers choose a bank based on how that bank actually
resolves problems, not advertising, not star ratings, and not brand
recognition.

## Why We Built This

Credit cards are nearly universal in American financial life: 82% of
U.S. adults held one in 2025 ([Federal Reserve](https://www.federalreserve.gov/consumerscommunities/shed.htm)).
Yet most people opening their first card have no real way to know how a
bank treats its customers when something goes wrong, a billing dispute,
an unexpected fee, a fraud claim that stalls out. Review platforms are
easy to game, and star ratings capture very little about how a company
actually resolves a problem.

Access to that information isn't evenly distributed, either. The
Federal Reserve found that 97% of households earning $100,000 or more
have a credit card, compared to just 46% of households earning under
$25,000 ([Forbes Advisor, 2025](https://www.forbes.com/advisor/credit-cards/credit-card-statistics/)).
The consumers with the least financial cushion to absorb a bad banking
relationship are often the ones with the least information to avoid
one in the first place.

The CFPB already collects the data needed to answer this: hundreds of
thousands of real complaints against financial companies, and exactly
how each one was resolved. It's public. It's free. It's also a raw,
technical government database that almost no one applying for a credit
card is going to seek out and parse themselves.

This project closes that gap.

## What it Does

1. **A short quiz.** Six plain-language questions, no financial jargon
   required, each tied directly to one consumer concern.
2. **Transparent priority weighting.** Before anything is ranked, the
   tool shows exactly which concerns it inferred matter most based on
   your answers, and why, and lets you adjust any of them yourself.
   Nothing is a black box.
3. **A ranked comparison.** Bank of America, Capital One, Chase, and
   Wells Fargo are ranked by a weighted relief rate, how often each
   company's response to a complaint actually delivered relief, based
   on tens of thousands of real CFPB complaint records.
4. **An interactive visual.** Each bank's score appears as a segmented,
   color-coded bar. Clicking any single concern highlights that
   category's contribution across all four banks at once.

## AI for Social Good

The core idea here is information asymmetry: banks already know
exactly how often they grant relief for each kind of complaint;
consumers don't. Our contribution isn't a flashy predictive model, it's
using a simple, transparent method to translate a large public dataset
into something that gives an ordinary person real leverage before they
commit to a financial product that could affect them for years. That's
the "power to the people" idea behind this project: closing an
information gap that currently favors institutions over the consumers
they serve.

## The Data

CFPB Consumer Complaint Database, filtered to credit card complaints
for four major banks (Bank of America, Capital One, JPMorgan Chase,
Wells Fargo), roughly 86,000 rows. `complaints_86k.zip` contains this
starting dataset; `analysis.ipynb` performs further cleaning, removing
unresolved complaints, filtering out low-volume company/issue pairs,
and grouping specific issue types into six consumer-facing concern
categories, before computing the relief-rate statistics the tool runs on.

Full CFPB database: https://www.consumerfinance.gov/data-research/consumer-complaints/

## Repository Contents

- `index.html`, the interactive tool ([live demo](YOUR_GITHUB_PAGES_LINK_HERE))
- `analysis.ipynb`, data cleaning, aggregation, and the recommendation logic
- `complaints_86k.zip`, the underlying dataset (zipped to fit GitHub's upload limit)

## Limitations

Relief rate measures how a company responded to a complaint, not
whether the consumer was in the right; a company can fairly deny relief
and still close a complaint "with explanation." One bank, Bank of
America, ranks highest across most categories in this dataset. This
may reflect genuinely more generous resolution practices, or
differences in how companies internally classify and report responses,
which the CFPB data alone can't fully disentangle. We treat this as an
open question worth further study rather than a settled conclusion.

## Future Directions

- **More companies.** Expanding beyond four major banks to regional
  banks and credit unions would make this useful to a much wider range
  of consumers, particularly since smaller institutions are
  underrepresented in most existing comparison tools.
- **More priorities.** Additional concern categories, such as foreign
  transaction fees or mobile app reliability, could be added as
  supporting data becomes available.
- **Free-text input.** Allowing users to describe their concern in
  their own words, with a classifier mapping it to the nearest concern
  category, would make the tool more accessible to people whose
  situation doesn't fit neatly into a fixed set of options.
- **An equity lens.** CFPB's existing "Older American" and
  "Servicemember" tags could be used to examine whether certain groups
  experience systematically worse outcomes, extending the tool from a
  decision aid into an accountability resource.
