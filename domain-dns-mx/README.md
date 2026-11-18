# Domain DNS MX

Each domain's mail exchangers from its MX records, with their priorities, one record per row.

| Field | Value |
| --- | --- |
| ID | `domain_dns_mx_v1` |
| Formats | `csvgz` |
| Update frequency | Weekly |
| Full database | 316,374,066 entries, 2.22 GB as CSV, on 2026-11-15 |
| This sample | 100 rows from the 2026-11-15 build |
| License | This sample: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). The full database: licensed per database, [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=Domain+DNS+Database+evaluation&products=Domain+DNS+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=domain-dns-mx) |
| Docs | [docs.internetdata.io/database/domain-dns/domain-dns-mx](https://docs.internetdata.io/database/domain-dns/domain-dns-mx?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=domain-dns-mx) |

## Files

- [`domain_dns_mx_v1.sample.csv`](domain_dns_mx_v1.sample.csv): the rows as plain CSV, which GitHub shows as a table
- [`domain_dns_mx_v1.sample.csv.gz`](domain_dns_mx_v1.sample.csv.gz): the same rows gzipped, as the full database ships

## Overview

Each domain's MX records, one row per record: `host` is a mail exchanger and `priority` its preference, lowest tried first. A name under a CNAME lists the MX records of the name its chain ends at, as a sender would.

A `host` of `.` is a null MX (RFC 7505): the domain publishes that it accepts no mail. Names are domains registered under the generic top-level domains and under .ee, .nu, .se, .sk and a few smaller country-code domains, their `www` names, and widely used names under other country-code domains such as .uk, .de and .fr: lowercase, internationalized ones in punycode (`xn--`).

`last_seen` is the most recent day the record was observed. A name with no MX record has no rows.

## Fields

### CSV (`csvgz`)

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `name` | `string` | The domain or host name, lowercase, internationalized names in punycode (xn--). | `0---------------------------------------...` |
| `priority` | `integer` | The MX preference: mail goes to the lowest first. | `10` |
| `host` | `string` | The mail exchanger's host name, following any CNAME on the name. A single . is a null MX: the domain accepts no mail. | `mail.domainit.com` |
| `last_seen` | `date` | The most recent day this record was observed. | `2026-10-29` |

## The full database

The full database needs a license: [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=Domain+DNS+Database+evaluation&products=Domain+DNS+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=domain-dns-mx) to test the whole file first. With a licensed API key:

```bash
curl -L -o domain_dns_mx_v1.csv.gz "https://internetdata.io/api/v2/database/download?id=domain_dns_mx_v1&format=csvgz&apikey=$APIKEY"
```

Today's sample is on [its page](https://internetdata.io/databases/domain-dns?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=domain-dns-mx#domain-dns-mx), cut from the latest build.

Back to [all InternetData sample databases](../).
