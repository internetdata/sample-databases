# Domain List

Every registered domain in the generic top-level domains, .com, .net and .org among them, and in .fr, .se, .sk and a few other country codes, with the domains in use under the rest, .de and .uk among them, one name per row.

| Field | Value |
| --- | --- |
| ID | `domain_list_v1` |
| Formats | `csvgz` |
| Update frequency | Weekly |
| Full database | 347,648,195 entries, 1.33 GB as CSV, on 2026-11-13 |
| This sample | 100 rows from the 2026-11-13 build |
| License | This sample: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). The full database: licensed per database, [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=Domain+List+Database+evaluation&products=Domain+List+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=domain-list) |
| Docs | [docs.internetdata.io/database/domain-list](https://docs.internetdata.io/database/domain-list?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=domain-list) |

## Files

- [`domain_list_v1.sample.csv`](domain_list_v1.sample.csv): the rows as plain CSV, which GitHub shows as a table
- [`domain_list_v1.sample.csv.gz`](domain_list_v1.sample.csv.gz): the same rows gzipped, as the full database ships

## Overview

Every domain registered under the generic top-level domains: .com, .net and .org, and over a thousand newer ones such as .top, .xyz and .info. It also holds every domain registered under five country-code domains, .ee, .fr, .nu, .se and .sk, and under a few smaller ones. Under the other country codes, .de, .uk, .cn and .br the largest, it holds the registered domains seen in use in the last 90 days, so a domain registered there that nobody uses can be missing. One name per row, lowercase, as registered: one label under its TLD, two under .name, which registers `first.last.name`, or one under a country-code second level such as `co.uk` or `pp.se`. Internationalized names are in their ASCII (punycode) form, `xn--` followed by the encoding.

A row is never a subdomain, a nameserver host such as `ns1.example.com`, or a TLD or a registry's second level, such as `com.fj`, on its own.

## Fields

### CSV (`csvgz`)

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `domain` | `string` | Fully-qualified domain name. | `0---------------------------------------...` |

## The full database

The full database needs a license: [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=Domain+List+Database+evaluation&products=Domain+List+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=domain-list) to test the whole file first. With a licensed API key:

```bash
curl -L -o domain_list_v1.csv.gz 'https://internetdata.io/api/v2/database/download?id=domain_list_v1&format=csvgz&apikey=$APIKEY'
```

Today's sample is on [its page](https://internetdata.io/databases/domain-list?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=domain-list), cut from the latest build.

Back to [all InternetData sample databases](../).
