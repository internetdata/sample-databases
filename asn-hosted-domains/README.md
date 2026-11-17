# ASN Hosted Domains

Every AS whose addresses registered domains resolve to, with how many domains there are and up to 1,000 of them, the most popular first, one AS per row.

| Field | Value |
| --- | --- |
| ID | `asn_hosted_domains_v1` |
| Formats | `csvgz` |
| Update frequency | Weekly |
| Full database | 52,321 entries, 35.4 MB as CSV, on 2026-11-15 |
| This sample | 100 rows from the 2026-11-15 build |
| License | This sample: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). The full database: licensed per database, [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=IP+Hosted+Domains+Database+evaluation&products=IP+Hosted+Domains+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=asn-hosted-domains) |
| Docs | [docs.internetdata.io/database/ip-hosted-domains/asn-hosted-domains](https://docs.internetdata.io/database/ip-hosted-domains/asn-hosted-domains?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=asn-hosted-domains) |

## Files

- [`asn_hosted_domains_v1.sample.csv`](asn_hosted_domains_v1.sample.csv): the rows as plain CSV, which GitHub shows as a table
- [`asn_hosted_domains_v1.sample.csv.gz`](asn_hosted_domains_v1.sample.csv.gz): the same rows gzipped, as the full database ships

## Overview

Every AS whose addresses registered domains resolve to, one row per AS. `total` counts the domains on the addresses the AS announces, each once however many of its addresses it is on: every registered domain whose own A or AAAA record, or its `www` host's, points into the AS's space, following any CNAME. `domains` lists them in one comma-separated field, the most popular first: all of them where there are 1,000 or fewer, and the 1,000 most popular where there are more.

An address counts for the AS [IP ASN](https://docs.internetdata.io/database/ip-asn?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=asn-hosted-domains) gives it, the origin of the most specific prefix announcing it. Addresses in no announced range are left out.

The domains and their order are [IP Hosted Domains](https://docs.internetdata.io/database/ip-hosted-domains/ip-hosted-domains?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=asn-hosted-domains)' own, grouped by AS. For a host, a CDN or a cloud, its domains are its customers' sites; for an enterprise network, they are usually the company's own.

## Fields

### CSV (`csvgz`)

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `asn` | `integer` | The Autonomous System Number. | `2` |
| `total` | `integer` | How many registered domains resolve to an address the AS announces, through their own A or AAAA record or their www host's, each counted once. | `9` |
| `domains` | `string` | Those domains, comma-separated, the most popular first: all of them, or the 1,000 most popular where there are more. Lowercase, internationalized names in punycode (xn--). | `gals-telecom.ru,skagp.ru,infranet.ru,skk...` |

## The full database

The full database needs a license: [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=IP+Hosted+Domains+Database+evaluation&products=IP+Hosted+Domains+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=asn-hosted-domains) to test the whole file first. With a licensed API key:

```bash
curl -L -o asn_hosted_domains_v1.csv.gz 'https://internetdata.io/api/v2/database/download?id=asn_hosted_domains_v1&format=csvgz&apikey=$APIKEY'
```

Today's sample is on [its page](https://internetdata.io/databases/ip-hosted-domains?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=asn-hosted-domains#asn-hosted-domains), cut from the latest build.

Back to [all InternetData sample databases](../).
