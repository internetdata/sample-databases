# Domain DNS A

Each domain's IPv4 addresses from its A records, with CNAMEs followed, one address per row.

| Field | Value |
| --- | --- |
| ID | `domain_dns_a_v1` |
| Formats | `csvgz` |
| Update frequency | Weekly |
| Full database | 616,716,442 entries, 4.50 GB as CSV, on 2026-11-22 |
| This sample | 100 rows from the 2026-11-22 build |
| License | This sample: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). The full database: licensed per database, [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=Domain+DNS+Database+evaluation&products=Domain+DNS+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=domain-dns-a) |
| Docs | [docs.internetdata.io/database/domain-dns/domain-dns-a](https://docs.internetdata.io/database/domain-dns/domain-dns-a?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=domain-dns-a) |

## Files

- [`domain_dns_a_v1.sample.csv`](domain_dns_a_v1.sample.csv): the rows as plain CSV, which GitHub shows as a table
- [`domain_dns_a_v1.sample.csv.gz`](domain_dns_a_v1.sample.csv.gz): the same rows gzipped, as the full database ships

## Overview

The IPv4 addresses each name resolves to, one row per name and address. A name under a CNAME lists the addresses its chain ends at, so `ip` is always an address, never an alias; the chain itself is in [Domain DNS CNAME](https://docs.internetdata.io/database/domain-dns/domain-dns-cname?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=domain-dns-a).

Names are domains registered under the generic top-level domains and under .ee, .nu, .se, .sk and a few smaller country-code domains, their `www` names, and widely used names under other country-code domains such as .uk, .de and .fr: lowercase, internationalized ones in punycode (`xn--`). A `www` name has rows only where its addresses differ from its domain's: when `www.example.com` resolves to exactly the addresses `example.com` does, only `example.com` has rows.

`last_seen` is the most recent day the name resolved to the address. A name with no A record has no rows. IPv6 addresses are in [Domain DNS AAAA](https://docs.internetdata.io/database/domain-dns/domain-dns-aaaa?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=domain-dns-a), in the same shape.

## Fields

### CSV (`csvgz`)

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `name` | `string` | The domain or host name, lowercase, internationalized names in punycode (xn--). A www. name is listed only where its addresses differ from its domain's. | `-----kmew8x55zm.330141.com` |
| `ip` | `ipaddress` | An IPv4 address the name resolves to, following any CNAME. A name with several addresses has a row for each. | `103.85.22.25` |
| `last_seen` | `date` | The most recent day the name was resolved to this address. | `2026-11-21` |

## The full database

The full database needs a license: [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=Domain+DNS+Database+evaluation&products=Domain+DNS+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=domain-dns-a) to test the whole file first. With a licensed API key:

```bash
curl -L -o domain_dns_a_v1.csv.gz "https://internetdata.io/api/v2/database/download?id=domain_dns_a_v1&format=csvgz&apikey=$APIKEY"
```

Today's sample is on [its page](https://internetdata.io/databases/domain-dns?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=domain-dns-a), cut from the latest build.

Back to [all InternetData sample databases](../).
