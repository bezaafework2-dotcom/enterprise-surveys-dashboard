# Enterprise Surveys country dashboard

An interactive dashboard of the World Bank Enterprise Surveys indicators, built from the public World Bank Data360 API.

**Open the dashboard:** https://bezaafework2-dotcom.github.io/enterprise-surveys-dashboard/

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/bezaafework2-dotcom/enterprise-surveys-dashboard/blob/main/dashboard.ipynb)

## What it does

Pick a country, a topic and what to compare with. The charts, the table and the CSV download change with your choices.

- **Country and topic.** About 200 indicators, grouped by topic (Finance, Gender, Corruption, Trade and others). The default view, "What stands out", shows the indicators where the country sits furthest from the rest of its region or changed most since its previous survey.
- **Comparators.** Up to three other countries, plus the region, the income group and all countries, as averages or medians.
- **Each panel** shows the country's latest survey, its previous survey, the comparators, and the country's rank in its region.
- **Checks.** Large changes between two surveys are flagged, so the reader knows to look at the survey before using the number.
- **Table and CSV.** Any view can be shown as a table or downloaded.

## How it is built

`dashboard.ipynb` is a Python notebook that:

1. Finds every national Enterprise Surveys indicator in the Data360 API.
2. Collects each indicator for all countries and keeps the latest and the previous survey.
3. Runs rule-based checks on the data (duplicates, missing values, survey years, shares between 0 and 100) and stops if one fails.
4. Writes everything into one file, `index.html`.

The page needs no server and no API key, because the data sits inside the file. GitHub Pages serves it.

| File | What it is |
|---|---|
| `dashboard.ipynb` | The notebook that collects the data and writes the page |
| `index.html` | The dashboard, as written by the notebook |

## Update the data

1. Open `dashboard.ipynb` in Colab with the badge at the top of this page.
2. Click **Runtime > Run all**. It takes about a minute, and `index.html` downloads.
3. Replace `index.html` in this repository with the new file.

The date the data was retrieved is shown at the bottom of the dashboard.

## Notes on the data

- Source: [World Bank Enterprise Surveys](https://www.enterprisesurveys.org), through the [World Bank Data360 API](https://data360.worldbank.org). Only public data is used.
- Group figures are simple averages or medians of each country's most recent survey. They are calculated on the page and are not official World Bank aggregates.
- Countries are surveyed in different years, so comparisons mix survey years. Surveys before 2010 are left out.
- The API has no topic field. Topics are assigned from the indicator code, following the Enterprise Surveys Indicator Descriptions document.

## Related

[enterprise-surveys-country-briefs](https://github.com/bezaafework2-dotcom/enterprise-surveys-country-briefs): a notebook that writes a one-page country brief from the same indicators, with an AI step whose numbers are checked against the data.

## About

A personal project by Beza Afework, built with the help of an AI coding assistant. It is not an official World Bank product.
