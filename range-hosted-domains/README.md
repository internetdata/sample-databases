# Range Hosted Domains

Every announced IP range registered domains resolve to, with its AS, how many domains there are and up to 1,000 of them, the most popular first, one range per row.

| Field | Value |
| --- | --- |
| ID | `range_hosted_domains_v1` |
| Formats | `csvgz` |
| Update frequency | Weekly |
| Full database | 393,179 entries, 196 MB as CSV, on 2026-11-22 |
| This sample | 100 rows from the 2026-11-22 build |
| License | This sample: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). The full database: licensed per database, [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=Range+Hosted+Domains+Database+evaluation&products=Range+Hosted+Domains+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=range-hosted-domains) |
| Docs | [docs.internetdata.io/database/range-hosted-domains](https://docs.internetdata.io/database/range-hosted-domains?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=range-hosted-domains) |

## Files

- [`range_hosted_domains_v1.sample.csv`](range_hosted_domains_v1.sample.csv): the rows as plain CSV, which GitHub shows as a table
- [`range_hosted_domains_v1.sample.csv.gz`](range_hosted_domains_v1.sample.csv.gz): the same rows gzipped, as the full database ships

## Overview

Every announced IPv4 and IPv6 range that registered domains resolve to, one row per range, with the AS that announces it. `total` counts the domains on the range's addresses, each once however many of its addresses it is on: every registered domain whose own A or AAAA record, or its `www` host's, points into the range, following any CNAME. `domains` lists them in one comma-separated field, the most popular first: all of them where there are 1,000 or fewer, and the 1,000 most popular where there are more.

A range is the one [IP ASN](https://docs.internetdata.io/database/ip-asn?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=range-hosted-domains) gives an address: the most specific prefix announcing it, with its origin AS. A range holds none of the addresses of a more specific prefix inside it, which is a row of its own. Addresses in no announced range are left out.

The domains and their order are [IP Hosted Domains](https://docs.internetdata.io/database/ip-hosted-domains?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=range-hosted-domains)' own, grouped by range: a range carrying thousands is usually a hosting platform, a CDN or a parking service, where unrelated sites sit side by side. [ASN Hosted Domains](https://docs.internetdata.io/database/asn-hosted-domains?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=range-hosted-domains) groups the same domains by AS.

Teams read it to judge a range before they block, allow or report it, and filter on `asn` to rank the ranges a host or a cloud announces by the sites on them.

## Fields

### CSV (`csvgz`)

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `prefix` | `string` | An announced IPv4 or IPv6 prefix, as a CIDR. | `1.0.0.0/24` |
| `asn` | `integer` | The Autonomous System Number announcing the prefix. | `13335` |
| `total` | `integer` | How many registered domains resolve to an address in the prefix, through their own A or AAAA record or their www host's, each counted once. | `163` |
| `domains` | `string` | Those domains, comma-separated, the most popular first: all of them, or the 1,000 most popular where there are more. Lowercase, internationalized names in punycode (xn--). | `fizzylizzybath.com,municipio.gob.pa,meal...` |

## The full database

The full database needs a license: [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=Range+Hosted+Domains+Database+evaluation&products=Range+Hosted+Domains+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=range-hosted-domains) to test the whole file first. With a licensed API key:

```bash
curl -L -o range_hosted_domains_v1.csv.gz "https://internetdata.io/api/v2/database/download?id=range_hosted_domains_v1&format=csvgz&apikey=$APIKEY"
```

Today's sample is on [its page](https://internetdata.io/databases/range-hosted-domains?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=range-hosted-domains), cut from the latest build.

Back to [all InternetData sample databases](../).
