# DNS Resolver IP

Every host answering DNS on UDP port 53, flagged for recursion and whether it is a working open resolver.

| Field | Value |
| --- | --- |
| ID | `dns_resolver_ip_v1` |
| Formats | `csvgz` |
| Update frequency | Weekly |
| Full database | 6,706,146 entries, 35.4 MB as CSV, on 2026-11-14 |
| This sample | 100 rows from the 2026-11-14 build |
| License | This sample: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). The full database: licensed per database, [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=DNS+Resolver+IP+Database+evaluation&products=DNS+Resolver+IP+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=dns-resolver-ip) |
| Docs | [docs.internetdata.io/database/dns-resolver-ip](https://docs.internetdata.io/database/dns-resolver-ip?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=dns-resolver-ip) |

## Files

- [`dns_resolver_ip_v1.sample.csv`](dns_resolver_ip_v1.sample.csv): the rows as plain CSV, which GitHub shows as a table
- [`dns_resolver_ip_v1.sample.csv.gz`](dns_resolver_ip_v1.sample.csv.gz): the same rows gzipped, as the full database ships

## Overview

`recursion_available` is the RA bit the server sets, and `rcode` its response code, which separates a resolver that answers anyone from one that advertises recursion but refuses outside queries. `answer_correct` is 1 only where a query for our own hostname came back with our address: a working open resolver that doesn't tamper with answers.

## Fields

### CSV (`csvgz`)

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `ip` | `ipaddress` | The IP address, IPv4 or IPv6, that returned a valid DNS reply on UDP port 53. | `1.0.0.1` |
| `port` | `integer` | The UDP port scanned (53). | `53` |
| `recursion_available` | `boolean` | The RA bit in the reply: 1 when the server advertises recursion, empty when it does not. | `1` |
| `rcode` | `integer` | The DNS response code (0 = NOERROR, 5 = REFUSED, ...), which separates a true open resolver from one that advertises recursion but refuses off-net queries. | `0` |
| `answer_correct` | `boolean` | 1 if a recursive query for our own hostname returned our address, the scanner's current one or an earlier one a cache kept past the record's 5-minute TTL: a working open recursive resolver with no DNS manipulation. Empty otherwise. | `1` |
| `first_seen` | `date` | The first day in the 90-day window the host replied. | `2026-08-18` |
| `last_seen` | `date` | The most recent day the host replied. | `2026-11-14` |

## The full database

The full database needs a license: [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=DNS+Resolver+IP+Database+evaluation&products=DNS+Resolver+IP+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=dns-resolver-ip) to test the whole file first. With a licensed API key:

```bash
curl -L -o dns_resolver_ip_v1.csv.gz 'https://internetdata.io/api/v2/database/download?id=dns_resolver_ip_v1&format=csvgz&apikey=$APIKEY'
```

Today's sample is on [its page](https://internetdata.io/databases/dns-resolver-ip?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=dns-resolver-ip), cut from the latest build.

Back to [all InternetData sample databases](../).
