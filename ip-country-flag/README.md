# IP Country Flag

Every IP range mapped to its country's flag, as an emoji and its Unicode code points.

| Field | Value |
| --- | --- |
| ID | `ip_country_flag_v1` |
| Formats | `csvgz`, `mmdb` |
| Update frequency | Daily |
| Full database | 925,772 entries, 7.40 MB as CSV and 3.98 MB as MMDB, on 2026-11-17 |
| This sample | 100 rows from the 2026-11-17 build |
| License | This sample and the full database: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) |
| Docs | [docs.internetdata.io/database/ip-country-flag](https://docs.internetdata.io/database/ip-country-flag?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-country-flag) |

## Files

- [`ip_country_flag_v1.sample.csv`](ip_country_flag_v1.sample.csv): the rows as plain CSV, which GitHub shows as a table
- [`ip_country_flag_v1.sample.csv.gz`](ip_country_flag_v1.sample.csv.gz): the same rows gzipped, as the full database ships
- [`ip_country_flag_v1.sample.mmdb`](ip_country_flag_v1.sample.mmdb): the same rows as an MMDB, to look up by IP address

## Overview

Every IPv4 and IPv6 range matched to its country, with the flag as both an emoji and its Unicode code points: `flag_emoji` for a system that renders emoji, `flag_unicode` for one that does not. The country is the one [IP Geolocation](https://docs.internetdata.io/database/ip-geolocation?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-country-flag) gives the same range; this file carries no region or city.

Free under [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/), like every Open database: credit InternetData with a link to [internetdata.io](https://internetdata.io/?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-country-flag), and share what you build from it under the same license.

## Fields

### CSV (`csvgz`)

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `start_ip` | `ipaddress` | Start IP of the IP range. | `1.0.0.0` |
| `end_ip` | `ipaddress` | End IP of the IP range. | `1.0.0.255` |
| `country` | `string` | ISO 3166-1 alpha-2 country code. | `AU` |
| `country_name` | `string` | Country name, where known. | `Australia` |
| `flag_emoji` | `string` | Flag emoji of the country, where known. | `🇦🇺` |
| `flag_unicode` | `string` | Unicode code points of the flag emoji. | `U+1F1E6 U+1F1FA` |

### MMDB (`mmdb`)

Each record is looked up by IP address and holds:

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `country` | `string` | ISO 3166-1 alpha-2 country code. | `AU` |
| `country_name` | `string` | Country name, where known. | `Australia` |
| `flag_emoji` | `string` | Flag emoji of the country, where known. | `🇦🇺` |
| `flag_unicode` | `string` | Unicode code points of the flag emoji. | `U+1F1E6 U+1F1FA` |

## The full database

IP Country Flag is an Open database, free under CC BY-SA 4.0 with an InternetData account: [sign up](https://internetdata.io/signup?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-country-flag), then with your API key:

```bash
curl -L -o ip_country_flag_v1.csv.gz 'https://internetdata.io/api/v2/database/download?id=ip_country_flag_v1&format=csvgz&apikey=$APIKEY'
curl -L -o ip_country_flag_v1.mmdb 'https://internetdata.io/api/v2/database/download?id=ip_country_flag_v1&format=mmdb&apikey=$APIKEY'
```

Today's sample is on [its page](https://internetdata.io/databases/ip-country-flag?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-country-flag), cut from the latest build.

Back to [all InternetData sample databases](../).
