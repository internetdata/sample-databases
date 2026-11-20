# IP Hosted Domains

Every IP address registered domains resolve to, with how many there are and up to 1,000 of them, the most popular first, one address per row.

| Field | Value |
| --- | --- |
| ID | `ip_hosted_domains_v1` |
| Formats | `csvgz` |
| Update frequency | Weekly |
| Full database | 39,012,516 entries, 1.75 GB as CSV, on 2026-11-15 |
| This sample | 100 rows from the 2026-11-15 build |
| License | This sample: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). The full database: licensed per database, [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=IP+Hosted+Domains+Database+evaluation&products=IP+Hosted+Domains+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-hosted-domains) |
| Docs | [docs.internetdata.io/database/ip-hosted-domains](https://docs.internetdata.io/database/ip-hosted-domains?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-hosted-domains) |

## Files

- [`ip_hosted_domains_v1.sample.csv`](ip_hosted_domains_v1.sample.csv): the rows as plain CSV, which GitHub shows as a table
- [`ip_hosted_domains_v1.sample.csv.gz`](ip_hosted_domains_v1.sample.csv.gz): the same rows gzipped, as the full database ships

## Overview

Every IPv4 and IPv6 address that registered domains resolve to, one row per address. `total` counts the domains on the address: each registered domain whose own A or AAAA record, or its `www` host's, points there, following any CNAME. `domains` lists them in one comma-separated field, the most popular first: all of them where there are 1,000 or fewer, and the 1,000 most popular where there are more.

The domains are those in Domain List: every one registered under the generic top-level domains and under .ee, .fr, .nu, .se and .sk, and those in use under the other country codes. Subdomains other than `www` don't count, and an address that never appears on the public internet, such as 127.0.0.1, is left out.

A few domains on one address are usually one owner's server. An address with thousands is a hosting platform, a CDN edge or a parking service, where unrelated sites sit side by side, so read `total` before you treat the domains on an address as related. Most addresses hold a single domain.

For a whole network, [Range Hosted Domains](https://docs.internetdata.io/database/range-hosted-domains?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-hosted-domains) counts the domains on each announced range and [ASN Hosted Domains](https://docs.internetdata.io/database/asn-hosted-domains?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-hosted-domains) on each AS, each domain once. Adding up this file's rows can't give those counts: a domain on several of a network's addresses would count once for each, and an address lists 1,000 domains at most.

## Fields

### CSV (`csvgz`)

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `ip` | `ipaddress` | The IP address, IPv4 or IPv6, that the domains resolve to. | `1.0.0.0` |
| `total` | `integer` | How many registered domains resolve to the address, through their own A or AAAA record or their www host's, following any CNAME. | `38` |
| `domains` | `string` | Those domains, comma-separated, the most popular first: all of them, or the 1,000 most popular where there are more. Lowercase, internationalized names in punycode (xn--). | `municipio.gob.pa,mealeysfurniture.com,aa...` |

## The full database

The full database needs a license: [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=IP+Hosted+Domains+Database+evaluation&products=IP+Hosted+Domains+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-hosted-domains) to test the whole file first. With a licensed API key:

```bash
curl -L -o ip_hosted_domains_v1.csv.gz "https://internetdata.io/api/v2/database/download?id=ip_hosted_domains_v1&format=csvgz&apikey=$APIKEY"
```

Today's sample is on [its page](https://internetdata.io/databases/ip-hosted-domains?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-hosted-domains), cut from the latest build.

Back to [all InternetData sample databases](../).
