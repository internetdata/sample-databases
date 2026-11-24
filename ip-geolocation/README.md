# IP Geolocation

Every IP range mapped to continent, country, region and city, with the city's coordinates, timezone, postal code and GeoNames ID, an accuracy radius, the date the location last changed, and a US range's DMA code.

| Field | Value |
| --- | --- |
| ID | `ip_geolocation_v1` |
| Formats | `csvgz`, `mmdb` |
| Update frequency | Daily |
| Full database | 13,136,611 entries, 156 MB as CSV and 91.0 MB as MMDB, on 2026-11-24 |
| This sample | 100 rows from the 2026-11-24 build |
| License | This sample: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). The full database: licensed per database, [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=IP+Geolocation+Database+evaluation&products=IP+Geolocation+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-geolocation) |
| Docs | [docs.internetdata.io/database/ip-geolocation](https://docs.internetdata.io/database/ip-geolocation?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-geolocation) |

## Files

- [`ip_geolocation_v1.sample.csv`](ip_geolocation_v1.sample.csv): the rows as plain CSV, which GitHub shows as a table
- [`ip_geolocation_v1.sample.csv.gz`](ip_geolocation_v1.sample.csv.gz): the same rows gzipped, as the full database ships
- [`ip_geolocation_v1.sample.mmdb`](ip_geolocation_v1.sample.mmdb): the same rows as an MMDB, to look up by IP address

## Overview

Every IPv4 and IPv6 range mapped to a continent, a country, a region and a city, with the latitude and longitude of the city, its IANA timezone and a postal code: the range's own where it's known, else the city's main one. Every range carries a country, and all but a handful a city: a range placed only to its region or country names that area's most likely city. The few without one are in Bouvet Island (BV) and Heard Island (HM).

Each row also carries:

- `geoname_id`: the city's ID in the [GeoNames](https://www.geonames.org/) gazetteer.
- `accuracy_radius`: the radius in kilometers around the latitude and longitude that holds the true location with 67% confidence. An anycast range, which answers from many places, has 20000.
- `last_changed`: the date the range's location (its country, region, city or coordinates) last changed. The earliest date in the file means on or before that day.
- `dma_code`: a US city's TV market (DMA, designated market area) as its 3-digit code: 501 is New York, 803 Los Angeles. Empty outside the US.

The continent, the country, the timezone, the currency and the flag of every range, and nothing finer, are free in [IP Country](https://docs.internetdata.io/database/ip-country?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-geolocation).

## Fields

### CSV (`csvgz`)

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `start_ip` | `ipaddress` | Start IP of the IP range. | `1.0.0.0` |
| `end_ip` | `ipaddress` | End IP of the IP range. | `1.0.0.255` |
| `continent` | `string` | Continent of the IP range. | `OC` |
| `country` | `string` | ISO 3166-1 alpha-2 country code. | `AU` |
| `country_name` | `string` | Country name of the IP range. | `Australia` |
| `region_code` | `string` | ISO 3166-2 region code, where it has one. | `AU-QLD` |
| `region` | `string` | Region (state/province) name, if any. | `Queensland` |
| `city` | `string` | City name, on every row but the few in BV and HM, which have no city: a range placed only to its region or country names that area's most likely city. | `Brisbane` |
| `latitude` | `float` | Latitude of the city. | `-27.46794` |
| `longitude` | `float` | Longitude of the city. | `153.02809` |
| `timezone` | `string` | IANA timezone of the IP range. | `Australia/Brisbane` |
| `postal_code` | `string` | The range's own postal code where known, else its city's main postal code. Empty where the country has no postal codes, or none are known for it. | `4000` |
| `geoname_id` | `string` | GeoNames ID of the city. | `2174003` |
| `accuracy_radius` | `integer` | Radius in km around the latitude and longitude that holds the true location with 67% confidence; 20000 for an anycast range, which answers from many places. | `20000` |
| `last_changed` | `date` | Date the range's location (country, region, city or coordinates) last changed. The earliest date in the file means on or before that day. | `2026-10-13` |
| `dma_code` | `string` | The city's US TV market (DMA, designated market area) as its 3-digit code: 501 is New York, 803 Los Angeles. Empty outside the US. | `602` |

### MMDB (`mmdb`)

Each record is looked up by IP address and holds:

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `continent` | `string` | Continent of the IP range. | `OC` |
| `country` | `string` | ISO 3166-1 alpha-2 country code. | `AU` |
| `country_name` | `string` | Country name of the IP range. | `Australia` |
| `region_code` | `string` | ISO 3166-2 region code, where it has one. | `AU-QLD` |
| `region` | `string` | Region (state/province) name, if any. | `Queensland` |
| `city` | `string` | City name, on every row but the few in BV and HM, which have no city: a range placed only to its region or country names that area's most likely city. | `Brisbane` |
| `latitude` | `float` | Latitude of the city. | `-27.46794` |
| `longitude` | `float` | Longitude of the city. | `153.02809` |
| `timezone` | `string` | IANA timezone of the IP range. | `Australia/Brisbane` |
| `postal_code` | `string` | The range's own postal code where known, else its city's main postal code. Empty where the country has no postal codes, or none are known for it. | `4000` |
| `geoname_id` | `string` | GeoNames ID of the city. | `2174003` |
| `accuracy_radius` | `integer` | Radius in km around the latitude and longitude that holds the true location with 67% confidence; 20000 for an anycast range, which answers from many places. | `20000` |
| `last_changed` | `date` | Date the range's location (country, region, city or coordinates) last changed. The earliest date in the file means on or before that day. | `2026-10-13` |
| `dma_code` | `string` | The city's US TV market (DMA, designated market area) as its 3-digit code: 501 is New York, 803 Los Angeles. Empty outside the US. | `602` |

## The full database

The full database needs a license: [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=IP+Geolocation+Database+evaluation&products=IP+Geolocation+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-geolocation) to test the whole file first. With a licensed API key:

```bash
curl -L -o ip_geolocation_v1.csv.gz "https://internetdata.io/api/v2/database/download?id=ip_geolocation_v1&format=csvgz&apikey=$APIKEY"
curl -L -o ip_geolocation_v1.mmdb "https://internetdata.io/api/v2/database/download?id=ip_geolocation_v1&format=mmdb&apikey=$APIKEY"
```

Today's sample is on [its page](https://internetdata.io/databases/ip-geolocation?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-geolocation), cut from the latest build.

Back to [all InternetData sample databases](../).
