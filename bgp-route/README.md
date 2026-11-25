# BGP Route

Every announced BGP prefix with its origin AS, collector visibility and RPKI status; multi-origin (MOAS) prefixes kept, one row per origin.

| Field | Value |
| --- | --- |
| ID | `bgp_route_v1` |
| Formats | `csvgz` |
| Update frequency | Daily |
| Full database | 1,452,931 entries, 5.97 MB as CSV, on 2026-11-24 |
| This sample | 100 rows from the 2026-11-24 build |
| License | This sample: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). The full database: licensed per database, [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=BGP+Route+Database+evaluation&products=BGP+Route+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=bgp-route) |
| Docs | [docs.internetdata.io/database/bgp-route](https://docs.internetdata.io/database/bgp-route?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=bgp-route) |

## Files

- [`bgp_route_v1.sample.csv`](bgp_route_v1.sample.csv): the rows as plain CSV, which GitHub shows as a table
- [`bgp_route_v1.sample.csv.gz`](bgp_route_v1.sample.csv.gz): the same rows gzipped, as the full database ships

## Overview

A prefix that more than one AS originates (MOAS) has a row per origin. `peer_count` counts the collector peers that saw the route, a measure of how widely it's visible, and `first_seen` is the first day it appeared in our routing history.

## Fields

### CSV (`csvgz`)

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `prefix` | `string` | The announced CIDR prefix, IPv4 or IPv6. | `1.0.0.0/24` |
| `family` | `integer` | IP family: 4 or 6. | `4` |
| `origin_asn` | `integer` | The origin AS announcing this prefix. A prefix with several origins (MOAS) appears once per origin. | `13335` |
| `peer_count` | `integer` | How many route collector peers saw this (prefix, origin): a measure of how widely it's visible. | `17` |
| `rpki_status` | `string` | RFC 6811 route origin validation: valid, invalid:origin, invalid:length, or not_found. | `valid` |
| `first_seen` | `date` | The first day this (prefix, origin) was observed in our BGP history. | `2026-10-02` |

## The full database

The full database needs a license: [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=BGP+Route+Database+evaluation&products=BGP+Route+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=bgp-route) to test the whole file first. With a licensed API key:

```bash
curl -L -o bgp_route_v1.csv.gz "https://internetdata.io/api/v2/database/download?id=bgp_route_v1&format=csvgz&apikey=$APIKEY"
```

Today's sample is on [its page](https://internetdata.io/databases/bgp-route?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=bgp-route), cut from the latest build.

Back to [all InternetData sample databases](../).
