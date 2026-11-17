# Domain DNS AAAA

Each domain's IPv6 addresses from its AAAA records, with CNAMEs followed, one address per row.

| Field | Value |
| --- | --- |
| ID | `domain_dns_aaaa_v1` |
| Formats | `csvgz` |
| Update frequency | Weekly |
| Full database | 161,491,248 entries, 1.53 GB as CSV, on 2026-11-15 |
| This sample | 100 rows from the 2026-11-15 build |
| License | This sample: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). The full database: licensed per database, [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=Domain+DNS+Database+evaluation&products=Domain+DNS+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=domain-dns-aaaa) |
| Docs | [docs.internetdata.io/database/domain-dns/domain-dns-aaaa](https://docs.internetdata.io/database/domain-dns/domain-dns-aaaa?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=domain-dns-aaaa) |

## Files

- [`domain_dns_aaaa_v1.sample.csv`](domain_dns_aaaa_v1.sample.csv): the rows as plain CSV, which GitHub shows as a table
- [`domain_dns_aaaa_v1.sample.csv.gz`](domain_dns_aaaa_v1.sample.csv.gz): the same rows gzipped, as the full database ships

## Overview

The IPv6 addresses each name resolves to, one row per name and address. A name under a CNAME lists the addresses its chain ends at, so `ip` is always an address, never an alias; the chain itself is in [Domain DNS CNAME](https://docs.internetdata.io/database/domain-dns/domain-dns-cname?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=domain-dns-aaaa).

Names are domains registered under the generic top-level domains and under .ee, .nu, .se, .sk and a few smaller country-code domains, their `www` names, and widely used names under other country-code domains such as .uk, .de and .fr: lowercase, internationalized ones in punycode (`xn--`). A `www` name has rows only where its addresses differ from its domain's.

`last_seen` is the most recent day the name resolved to the address. A name with no AAAA record has no rows. IPv4 addresses are in [Domain DNS A](https://docs.internetdata.io/database/domain-dns/domain-dns-a?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=domain-dns-aaaa), in the same shape.

## Fields

### CSV (`csvgz`)

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `name` | `string` | The domain or host name, lowercase, internationalized names in punycode (xn--). A www. name is listed only where its addresses differ from its domain's. | `-103wire.canva-apps.cn` |
| `ip` | `ipaddress` | An IPv6 address the name resolves to, following any CNAME. A name with several addresses has a row for each. | `2409:8c44:1b00:d06:3c72:3a9b:96e1:fffe` |
| `last_seen` | `date` | The most recent day the name was resolved to this address. | `2026-11-09` |

## The full database

The full database needs a license: [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=Domain+DNS+Database+evaluation&products=Domain+DNS+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=domain-dns-aaaa) to test the whole file first. With a licensed API key:

```bash
curl -L -o domain_dns_aaaa_v1.csv.gz 'https://internetdata.io/api/v2/database/download?id=domain_dns_aaaa_v1&format=csvgz&apikey=$APIKEY'
```

Today's sample is on [its page](https://internetdata.io/databases/domain-dns?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=domain-dns-aaaa#domain-dns-aaaa), cut from the latest build.

Back to [all InternetData sample databases](../).
