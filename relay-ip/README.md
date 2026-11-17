# Relay IP

IPs of privacy relays and enterprise web gateways.

| Field | Value |
| --- | --- |
| ID | `relay_ip_v1` |
| Formats | `csvgz`, `mmdb` |
| Update frequency | Daily |
| Full database | 176,223 entries, 1.13 MB as CSV and 1.06 MB as MMDB, on 2026-11-17 |
| This sample | 100 rows from the 2026-11-17 build |
| License | This sample and the full database: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) |
| Docs | [docs.internetdata.io/database/relay-ip/relay-ip](https://docs.internetdata.io/database/relay-ip/relay-ip?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=relay-ip) |

## Files

- [`relay_ip_v1.sample.csv`](relay_ip_v1.sample.csv): the rows as plain CSV, which GitHub shows as a table
- [`relay_ip_v1.sample.csv.gz`](relay_ip_v1.sample.csv.gz): the same rows gzipped, as the full database ships
- [`relay_ip_v1.sample.mmdb`](relay_ip_v1.sample.mmdb): the same rows as an MMDB, to look up by IP address

## Overview

IPs of privacy relays, such as iCloud Private Relay, and of enterprise web gateways, such as Zscaler. Use it to tell relayed traffic from direct traffic without blocking it outright: relay users are typically real people with a privacy setting on, and a gateway carries a company's staff at work.

Free under [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/), like every Open database: credit InternetData with a link to [internetdata.io](https://internetdata.io/?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=relay-ip), and share what you build from it under the same license.

## Fields

### CSV (`csvgz`)

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `start_ip` | `ipaddress` | Start IP of the IP range. | `3.0.6.66` |
| `end_ip` | `ipaddress` | End IP of the IP range. | `3.0.6.66` |
| `provider` | `string` | Relay/proxy provider's unique ID. | `cisco_secure_access` |
| `confidence` | `string` | Confidence of the correctness of this observation. | `medium` |
| `last_seen` | `date` | Last time this observation was made. | `2026-11-06` |

### MMDB (`mmdb`)

Each record is looked up by IP address and holds:

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `provider` | `string` | Relay/proxy provider's unique ID. | `cisco_secure_access` |
| `confidence` | `string` | Confidence of the correctness of this observation. | `medium` |
| `last_seen` | `date` | Last time this observation was made. | `2026-11-06` |

## The full database

Relay IP is an Open database, free under CC BY-SA 4.0 with an InternetData account: [sign up](https://internetdata.io/signup?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=relay-ip), then with your API key:

```bash
curl -L -o relay_ip_v1.csv.gz 'https://internetdata.io/api/v2/database/download?id=relay_ip_v1&format=csvgz&apikey=$APIKEY'
curl -L -o relay_ip_v1.mmdb 'https://internetdata.io/api/v2/database/download?id=relay_ip_v1&format=mmdb&apikey=$APIKEY'
```

Today's sample is on [its page](https://internetdata.io/databases/relay-ip?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=relay-ip), cut from the latest build.

Back to [all InternetData sample databases](../).
