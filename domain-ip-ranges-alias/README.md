# Domain IP Ranges Alias

The domains whose home page redirects to an organization's in Domain IP Ranges, each with the domain to look its ranges up by.

| Field | Value |
| --- | --- |
| ID | `domain_ip_ranges_alias_v1` |
| Formats | `csvgz` |
| Update frequency | Daily |
| Full database | 86,813 entries, 697 KB as CSV, on 2026-11-17 |
| This sample | 100 rows from the 2026-11-17 build |
| License | This sample: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). The full database: licensed per database, [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=Domain+IP+Ranges+Database+evaluation&products=Domain+IP+Ranges+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=domain-ip-ranges-alias) |
| Docs | [docs.internetdata.io/database/domain-ip-ranges/domain-ip-ranges-alias](https://docs.internetdata.io/database/domain-ip-ranges/domain-ip-ranges-alias?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=domain-ip-ranges-alias) |

## Files

- [`domain_ip_ranges_alias_v1.sample.csv`](domain_ip_ranges_alias_v1.sample.csv): the rows as plain CSV, which GitHub shows as a table
- [`domain_ip_ranges_alias_v1.sample.csv.gz`](domain_ip_ranges_alias_v1.sample.csv.gz): the same rows gzipped, as the full database ships

## Overview

Domains whose home page redirects to the home page of an organization's own domain in [Domain IP Ranges](https://docs.internetdata.io/database/domain-ip-ranges/domain-ip-ranges?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=domain-ip-ranges-alias), one row per domain: `times.com` to `nytimes.com`, or a product's or an acquired brand's site to its company's. Look a domain up here, then look its `redirects_to` up in Domain IP Ranges for the ranges.

A domain with ranges of its own can be here too, as a brand acquired by another often is.

## Fields

### CSV (`csvgz`)

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `domain` | `string` | A domain whose home page redirects to the home page of an organization's domain in Domain IP Ranges, as one of that organization's own domains. Lowercase, internationalized names in punycode (xn--). | `0-60pc.com` |
| `redirects_to` | `string` | The organization's domain it redirects to: the domain to look up in Domain IP Ranges for its ranges. | `asktheitsource.com` |

## The full database

The full database needs a license: [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=Domain+IP+Ranges+Database+evaluation&products=Domain+IP+Ranges+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=domain-ip-ranges-alias) to test the whole file first. With a licensed API key:

```bash
curl -L -o domain_ip_ranges_alias_v1.csv.gz 'https://internetdata.io/api/v2/database/download?id=domain_ip_ranges_alias_v1&format=csvgz&apikey=$APIKEY'
```

Today's sample is on [its page](https://internetdata.io/databases/domain-ip-ranges?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=domain-ip-ranges-alias#domain-ip-ranges-alias), cut from the latest build.

Back to [all InternetData sample databases](../).
