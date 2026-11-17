# Datacenter Proxy IP 90d

Datacenter-hosted proxy IPs seen in the last 90 days, with provider attribution.

| Field | Value |
| --- | --- |
| ID | `dcproxy_ip_90d_v1` |
| Formats | `csvgz`, `mmdb` |
| Update frequency | Daily |
| Full database | 1,380,411 entries, 7.50 MB as CSV and 19.8 MB as MMDB, on 2026-11-17 |
| This sample | 100 rows from the 2026-11-17 build |
| License | This sample: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). The full database: licensed per database, [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=Datacenter+Proxy+IP+Database+evaluation&products=Datacenter+Proxy+IP+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=dcproxy-ip-90d) |
| Docs | [docs.internetdata.io/database/dcproxy-ip/dcproxy-ip-90d](https://docs.internetdata.io/database/dcproxy-ip/dcproxy-ip-90d?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=dcproxy-ip-90d) |

## Files

- [`dcproxy_ip_90d_v1.sample.csv`](dcproxy_ip_90d_v1.sample.csv): the rows as plain CSV, which GitHub shows as a table
- [`dcproxy_ip_90d_v1.sample.csv.gz`](dcproxy_ip_90d_v1.sample.csv.gz): the same rows gzipped, as the full database ships
- [`dcproxy_ip_90d_v1.sample.mmdb`](dcproxy_ip_90d_v1.sample.mmdb): the same rows as an MMDB, to look up by IP address

## Overview

For filtering automation sent through rented datacenter proxies rather than by a real end user.

## Fields

### CSV (`csvgz`)

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `ip` | `ipaddress` | IP address a datacenter proxy service sells or runs on. | `1.0.168.65` |
| `provider` | `string` | Datacenter proxy provider's unique ID. | `floppydata` |
| `first_seen` | `date` | First time within this window this IP was seen as a datacenter proxy address. | `2026-11-13` |
| `last_seen` | `date` | Last time within this window this IP was seen as a datacenter proxy address. | `2026-11-16` |
| `hits` | `integer` | Sightings within this window: one per time it was seen as an exit, or one a day as an address of a proxy server or of a proxy company's own range. | `2` |
| `hits_days_pct` | `float` | Percent of days within this window on which this IP was seen as a datacenter proxy address. | `2` |
| `providers_num` | `integer` | Number of distinct providers attributing this IP within this window. | `1` |

### MMDB (`mmdb`)

Each record is looked up by IP address and holds:

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `provider` | `string` | Datacenter proxy provider's unique ID. | `floppydata` |
| `first_seen` | `date` | First time within this window this IP was seen as a datacenter proxy address. | `2026-11-13` |
| `last_seen` | `date` | Last time within this window this IP was seen as a datacenter proxy address. | `2026-11-16` |
| `hits` | `integer` | Sightings within this window: one per time it was seen as an exit, or one a day as an address of a proxy server or of a proxy company's own range. | `2` |
| `hits_days_pct` | `float` | Percent of days within this window on which this IP was seen as a datacenter proxy address. | `2` |
| `providers_num` | `integer` | Number of distinct providers attributing this IP within this window. | `1` |

## The full database

The full database needs a license: [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=Datacenter+Proxy+IP+Database+evaluation&products=Datacenter+Proxy+IP+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=dcproxy-ip-90d) to test the whole file first. With a licensed API key:

```bash
curl -L -o dcproxy_ip_90d_v1.csv.gz 'https://internetdata.io/api/v2/database/download?id=dcproxy_ip_90d_v1&format=csvgz&apikey=$APIKEY'
curl -L -o dcproxy_ip_90d_v1.mmdb 'https://internetdata.io/api/v2/database/download?id=dcproxy_ip_90d_v1&format=mmdb&apikey=$APIKEY'
```

Today's sample is on [its page](https://internetdata.io/databases/datacenter-proxy-ip?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=dcproxy-ip-90d), cut from the latest build.

Back to [all InternetData sample databases](../).
