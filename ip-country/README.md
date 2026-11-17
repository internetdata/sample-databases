# IP Country

Every IP range mapped to its continent and country, each as a code and a name, with its timezone and the country's currency and flag.

| Field | Value |
| --- | --- |
| ID | `ip_country_v1` |
| Formats | `csvgz`, `mmdb` |
| Update frequency | Daily |
| Full database | 2,541,921 entries, 21.2 MB as CSV and 8.36 MB as MMDB, on 2026-11-17 |
| This sample | 100 rows from the 2026-11-17 build |
| License | This sample and the full database: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) |
| Docs | [docs.internetdata.io/database/ip-country](https://docs.internetdata.io/database/ip-country?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-country) |

## Files

- [`ip_country_v1.sample.csv`](ip_country_v1.sample.csv): the rows as plain CSV, which GitHub shows as a table
- [`ip_country_v1.sample.csv.gz`](ip_country_v1.sample.csv.gz): the same rows gzipped, as the full database ships
- [`ip_country_v1.sample.mmdb`](ip_country_v1.sample.mmdb): the same rows as an MMDB, to look up by IP address

## Overview

Every IPv4 and IPv6 range matched to its continent and country, each by code and name, with the range's IANA timezone and the country's currency and flag. The country and the zone are the ones [IP Geolocation](https://docs.internetdata.io/database/ip-geolocation?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-country) gives the same range, and neighboring ranges of the same country and zone are merged into one row; this file carries no region or city.

- `continent`: the continent code, `AF`, `AN` (Antarctica), `AS`, `EU`, `NA`, `OC` or `SA`, and `continent_name` its name.
- `country`: the ISO 3166-1 alpha-2 code, and `country_name` its name.
- `timezone`: the range's IANA timezone. Empty in the few ranges in Bouvet Island (BV) and Heard Island (HM), which have none.
- `currency_code`, `currency_name` and `currency_symbol`: the country's currency, by its ISO 4217 code.
- `flag_emoji` and `flag_unicode`: the country's flag as an emoji and as its two Unicode code points.

Free under [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/), like every Open database: credit InternetData with a link to [internetdata.io](https://internetdata.io/?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-country), and share what you build from it under the same license.

## Fields

### CSV (`csvgz`)

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `start_ip` | `ipaddress` | Start IP of the IP range. | `1.0.0.0` |
| `end_ip` | `ipaddress` | End IP of the IP range. | `1.0.0.255` |
| `continent` | `string` | Continent code: AF, AN (Antarctica), AS, EU, NA, OC or SA. | `OC` |
| `continent_name` | `string` | Continent name. | `Oceania` |
| `country` | `string` | ISO 3166-1 alpha-2 country code. | `AU` |
| `country_name` | `string` | Country name. | `Australia` |
| `timezone` | `string` | IANA timezone of the IP range. Empty in the few ranges in BV and HM, which have none. | `Australia/Brisbane` |
| `currency_code` | `string` | ISO 4217 code, where there is one. | `AUD` |
| `currency_name` | `string` | Currency name, where there is one. | `Dollar` |
| `currency_symbol` | `string` | Currency symbol, where known. | `A$` |
| `flag_emoji` | `string` | Flag emoji of the country. | `🇦🇺` |
| `flag_unicode` | `string` | Unicode code points of the flag emoji. | `U+1F1E6 U+1F1FA` |

### MMDB (`mmdb`)

Each record is looked up by IP address and holds:

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `continent` | `string` | Continent code: AF, AN (Antarctica), AS, EU, NA, OC or SA. | `OC` |
| `continent_name` | `string` | Continent name. | `Oceania` |
| `country` | `string` | ISO 3166-1 alpha-2 country code. | `AU` |
| `country_name` | `string` | Country name. | `Australia` |
| `timezone` | `string` | IANA timezone of the IP range. Empty in the few ranges in BV and HM, which have none. | `Australia/Brisbane` |
| `currency_code` | `string` | ISO 4217 code, where there is one. | `AUD` |
| `currency_name` | `string` | Currency name, where there is one. | `Dollar` |
| `currency_symbol` | `string` | Currency symbol, where known. | `A$` |
| `flag_emoji` | `string` | Flag emoji of the country. | `🇦🇺` |
| `flag_unicode` | `string` | Unicode code points of the flag emoji. | `U+1F1E6 U+1F1FA` |

## The full database

IP Country is an Open database, free under CC BY-SA 4.0 with an InternetData account: [sign up](https://internetdata.io/signup?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-country), then with your API key:

```bash
curl -L -o ip_country_v1.csv.gz 'https://internetdata.io/api/v2/database/download?id=ip_country_v1&format=csvgz&apikey=$APIKEY'
curl -L -o ip_country_v1.mmdb 'https://internetdata.io/api/v2/database/download?id=ip_country_v1&format=mmdb&apikey=$APIKEY'
```

Today's sample is on [its page](https://internetdata.io/databases/ip-country?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-country), cut from the latest build.

Back to [all InternetData sample databases](../).
