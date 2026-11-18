# IP RDNS

The reverse DNS name of every IPv4 and IPv6 address that answers a PTR query.

| Field | Value |
| --- | --- |
| ID | `ip_rdns_v1` |
| Formats | `csvgz` |
| Update frequency | Weekly |
| Full database | 1,236,479,428 entries, 9.49 GB as CSV, on 2026-11-14 |
| This sample | 100 rows from the 2026-11-14 build |
| License | This sample: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). The full database: licensed per database, [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=IP+RDNS+Database+evaluation&products=IP+RDNS+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-rdns) |
| Docs | [docs.internetdata.io/database/ip-rdns](https://docs.internetdata.io/database/ip-rdns?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-rdns) |

## Files

- [`ip_rdns_v1.sample.csv`](ip_rdns_v1.sample.csv): the rows as plain CSV, which GitHub shows as a table
- [`ip_rdns_v1.sample.csv.gz`](ip_rdns_v1.sample.csv.gz): the same rows gzipped, as the full database ships

## Overview

One row per address that answers a PTR query, with the host name it returns, from our own scans of the IPv4 address space and of known IPv6 hosts. It is rebuilt weekly.

IPv6 addresses are written in their compressed form, as in every other database here. Rows are in no particular order, so sort on load if you need address order. A name holding a comma, quote, backslash or whitespace, which no valid host name does, is left out.

## Fields

### CSV (`csvgz`)

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `ip` | `ipaddress` | The IP address, IPv4 or IPv6. | `69.36.97.63` |
| `domain` | `string` | The host name its reverse DNS (PTR) record points to. | `69-36-97-63.ip.cal.radiant.net` |
| `forward_confirmed` | `boolean` | Whether the host name's own forward record (A for IPv4, AAAA for IPv6) points back to the address: "true" or "false", or empty when it hasn't been asked yet or every lookup failed. | `true` |

## The full database

The full database needs a license: [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=IP+RDNS+Database+evaluation&products=IP+RDNS+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-rdns) to test the whole file first. With a licensed API key:

```bash
curl -L -o ip_rdns_v1.csv.gz "https://internetdata.io/api/v2/database/download?id=ip_rdns_v1&format=csvgz&apikey=$APIKEY"
```

Today's sample is on [its page](https://internetdata.io/databases/ip-rdns?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-rdns), cut from the latest build.

Back to [all InternetData sample databases](../).
