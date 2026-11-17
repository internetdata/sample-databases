# IP Timezone

Every IP range mapped to an IANA timezone, with its country.

| Field | Value |
| --- | --- |
| ID | `ip_timezone_v1` |
| Formats | `csvgz`, `mmdb` |
| Update frequency | Daily |
| Full database | 2,541,753 entries, 17.4 MB as CSV and 8.33 MB as MMDB, on 2026-11-17 |
| This sample | 100 rows from the 2026-11-17 build |
| License | This sample and the full database: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) |
| Docs | [docs.internetdata.io/database/ip-timezone](https://docs.internetdata.io/database/ip-timezone?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-timezone) |

## Files

- [`ip_timezone_v1.sample.csv`](ip_timezone_v1.sample.csv): the rows as plain CSV, which GitHub shows as a table
- [`ip_timezone_v1.sample.csv.gz`](ip_timezone_v1.sample.csv.gz): the same rows gzipped, as the full database ships
- [`ip_timezone_v1.sample.mmdb`](ip_timezone_v1.sample.mmdb): the same rows as an MMDB, to look up by IP address

## Overview

Every IPv4 and IPv6 range mapped to an IANA timezone, with the country alongside it. A range's zone is the one [IP Geolocation](https://docs.internetdata.io/database/ip-geolocation?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-timezone) gives it, the zone of its city, and neighboring ranges in the same zone are merged into one row, so this file holds fewer rows than IP Geolocation. The few ranges with no city, in Bouvet Island (BV) and Heard Island (HM), have no zone and are left out.

Free under [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/), like every Open database: credit InternetData with a link to [internetdata.io](https://internetdata.io/?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-timezone), and share what you build from it under the same license.

## Fields

### CSV (`csvgz`)

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `start_ip` | `ipaddress` | Start IP of the IP range. | `1.0.0.0` |
| `end_ip` | `ipaddress` | End IP of the IP range. | `1.0.0.255` |
| `timezone` | `string` | IANA timezone of the IP range. | `Australia/Brisbane` |
| `country` | `string` | ISO 3166-1 alpha-2 country code. | `AU` |

### MMDB (`mmdb`)

Each record is looked up by IP address and holds:

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `timezone` | `string` | IANA timezone of the IP range. | `Australia/Brisbane` |
| `country` | `string` | ISO 3166-1 alpha-2 country code. | `AU` |

## The full database

IP Timezone is an Open database, free under CC BY-SA 4.0 with an InternetData account: [sign up](https://internetdata.io/signup?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-timezone), then with your API key:

```bash
curl -L -o ip_timezone_v1.csv.gz 'https://internetdata.io/api/v2/database/download?id=ip_timezone_v1&format=csvgz&apikey=$APIKEY'
curl -L -o ip_timezone_v1.mmdb 'https://internetdata.io/api/v2/database/download?id=ip_timezone_v1&format=mmdb&apikey=$APIKEY'
```

Today's sample is on [its page](https://internetdata.io/databases/ip-timezone?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-timezone), cut from the latest build.

Back to [all InternetData sample databases](../).
