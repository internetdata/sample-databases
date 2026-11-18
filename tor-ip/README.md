# Tor IP

Currently-active Tor node IPs.

| Field | Value |
| --- | --- |
| ID | `tor_ip_v1` |
| Formats | `csvgz`, `mmdb` |
| Update frequency | Daily |
| Full database | 13,825 entries, 113 KB as CSV and 936 KB as MMDB, on 2026-11-17 |
| This sample | 100 rows from the 2026-11-17 build |
| License | This sample and the full database: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) |
| Docs | [docs.internetdata.io/database/tor-ip](https://docs.internetdata.io/database/tor-ip?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=tor-ip) |

## Files

- [`tor_ip_v1.sample.csv`](tor_ip_v1.sample.csv): the rows as plain CSV, which GitHub shows as a table
- [`tor_ip_v1.sample.csv.gz`](tor_ip_v1.sample.csv.gz): the same rows gzipped, as the full database ships
- [`tor_ip_v1.sample.mmdb`](tor_ip_v1.sample.mmdb): the same rows as an MMDB, to look up by IP address

## Overview

Traffic from a Tor node is most often sent to extra fraud or abuse review.

Free under [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/), like every Open database: credit InternetData with a link to [internetdata.io](https://internetdata.io/?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=tor-ip), and share what you build from it under the same license.

## Fields

### CSV (`csvgz`)

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `start_ip` | `ipaddress` | Start IP of the Tor node IP range. | `1.34.44.234` |
| `end_ip` | `ipaddress` | End IP of the Tor node IP range. | `1.34.44.234` |
| `confidence` | `string` | Confidence of the correctness of this observation. | `high` |
| `last_seen` | `date` | Last time this observation was made. | `2026-11-17` |

### MMDB (`mmdb`)

Each record is looked up by IP address and holds:

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `confidence` | `string` | Confidence of the correctness of this observation. | `high` |
| `last_seen` | `date` | Last time this observation was made. | `2026-11-17` |

## The full database

Tor IP is an Open database, free under CC BY-SA 4.0 with an InternetData account: [sign up](https://internetdata.io/signup?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=tor-ip), then with your API key:

```bash
curl -L -o tor_ip_v1.csv.gz "https://internetdata.io/api/v2/database/download?id=tor_ip_v1&format=csvgz&apikey=$APIKEY"
curl -L -o tor_ip_v1.mmdb "https://internetdata.io/api/v2/database/download?id=tor_ip_v1&format=mmdb&apikey=$APIKEY"
```

Today's sample is on [its page](https://internetdata.io/databases/tor-ip?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=tor-ip), cut from the latest build.

Back to [all InternetData sample databases](../).
