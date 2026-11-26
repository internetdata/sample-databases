# Domain DNS NS

The nameservers each domain is delegated to, one per row.

| Field | Value |
| --- | --- |
| ID | `domain_dns_ns_v1` |
| Formats | `csvgz` |
| Update frequency | Weekly |
| Full database | 875,832,276 entries, 5.29 GB as CSV, on 2026-11-22 |
| This sample | 100 rows from the 2026-11-22 build |
| License | This sample: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). The full database: licensed per database, [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=Domain+DNS+Database+evaluation&products=Domain+DNS+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=domain-dns-ns) |
| Docs | [docs.internetdata.io/database/domain-dns/domain-dns-ns](https://docs.internetdata.io/database/domain-dns/domain-dns-ns?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=domain-dns-ns) |

## Files

- [`domain_dns_ns_v1.sample.csv`](domain_dns_ns_v1.sample.csv): the rows as plain CSV, which GitHub shows as a table
- [`domain_dns_ns_v1.sample.csv.gz`](domain_dns_ns_v1.sample.csv.gz): the same rows gzipped, as the full database ships

## Overview

The nameservers each name is delegated to, one row per name and nameserver. Only a name's own delegation is listed: a name under a CNAME has no rows of its target's.

Names are domains registered under the generic top-level domains and under .ee, .fr, .nu, .se, .sk and a few smaller country-code domains, their `www` names, and widely used names under other country-code domains such as .uk, .de and .cn: lowercase, internationalized ones in punycode (`xn--`).

`last_seen` is the most recent day the delegation was observed.

## Fields

### CSV (`csvgz`)

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `name` | `string` | The domain or host name, lowercase, internationalized names in punycode (xn--). | `0---------------------------------------...` |
| `host` | `string` | A nameserver the name is delegated to. A domain with several has a row for each. | `ns1.domainit.com` |
| `last_seen` | `date` | The most recent day this delegation was observed. | `2026-11-16` |

## The full database

The full database needs a license: [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=Domain+DNS+Database+evaluation&products=Domain+DNS+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=domain-dns-ns) to test the whole file first. With a licensed API key:

```bash
curl -L -o domain_dns_ns_v1.csv.gz "https://internetdata.io/api/v2/database/download?id=domain_dns_ns_v1&format=csvgz&apikey=$APIKEY"
```

Today's sample is on [its page](https://internetdata.io/databases/domain-dns?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=domain-dns-ns#domain-dns-ns), cut from the latest build.

Back to [all InternetData sample databases](../).
