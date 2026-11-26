# Domain DNS CNAME

Every CNAME record seen on a domain or host name, with the name it points to, one per row.

| Field | Value |
| --- | --- |
| ID | `domain_dns_cname_v1` |
| Formats | `csvgz` |
| Update frequency | Weekly |
| Full database | 155,262,722 entries, 1.45 GB as CSV, on 2026-11-22 |
| This sample | 100 rows from the 2026-11-22 build |
| License | This sample: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). The full database: licensed per database, [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=Domain+DNS+Database+evaluation&products=Domain+DNS+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=domain-dns-cname) |
| Docs | [docs.internetdata.io/database/domain-dns/domain-dns-cname](https://docs.internetdata.io/database/domain-dns/domain-dns-cname?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=domain-dns-cname) |

## Files

- [`domain_dns_cname_v1.sample.csv`](domain_dns_cname_v1.sample.csv): the rows as plain CSV, which GitHub shows as a table
- [`domain_dns_cname_v1.sample.csv.gz`](domain_dns_cname_v1.sample.csv.gz): the same rows gzipped, as the full database ships

## Overview

Every CNAME record, one row per alias and target. Each hop of a chain is its own row, its alias as `name`, so a chain can be followed from name to name to the one that holds addresses: `www.example.com` to `example.cdn.example.net` to `edge.cdn.example.net`.

Every `www` CNAME is here, including a `www` name pointing back at its own domain. An alias seen pointing at two names over time has a row for each, and `last_seen` says which was seen most recently. Names are domains registered under the generic top-level domains and under .ee, .fr, .nu, .se, .sk and a few smaller country-code domains, their `www` names, and widely used names under other country-code domains such as .uk, .de and .cn: lowercase, internationalized ones in punycode (`xn--`).

The addresses a chain ends at are in [Domain DNS A](https://docs.internetdata.io/database/domain-dns/domain-dns-a?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=domain-dns-cname) and [Domain DNS AAAA](https://docs.internetdata.io/database/domain-dns/domain-dns-aaaa?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=domain-dns-cname), under the alias's own name, or under its domain's for a `www` name with the same addresses.

## Fields

### CSV (`csvgz`)

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `name` | `string` | The alias: a domain or host name with a CNAME record, lowercase, internationalized names in punycode (xn--). | `-cdn-talkdesk.s3.amazonaws.com` |
| `target` | `string` | The name the alias points to. A target can be an alias itself, with a row of its own in this file. | `s3-1-w.amazonaws.com` |
| `last_seen` | `date` | The most recent day this record was observed. | `2026-11-18` |

## The full database

The full database needs a license: [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=Domain+DNS+Database+evaluation&products=Domain+DNS+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=domain-dns-cname) to test the whole file first. With a licensed API key:

```bash
curl -L -o domain_dns_cname_v1.csv.gz "https://internetdata.io/api/v2/database/download?id=domain_dns_cname_v1&format=csvgz&apikey=$APIKEY"
```

Today's sample is on [its page](https://internetdata.io/databases/domain-dns?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=domain-dns-cname#domain-dns-cname), cut from the latest build.

Back to [all InternetData sample databases](../).
