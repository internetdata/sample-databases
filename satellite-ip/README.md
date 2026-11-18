# Satellite IP

Satellite internet address space, with the operator, its orbit and market, the subscribers' country and a confidence.

| Field | Value |
| --- | --- |
| ID | `satellite_ip_v1` |
| Formats | `csvgz`, `mmdb` |
| Update frequency | Daily |
| Full database | 4,334 entries, 39.5 KB as CSV and 93.7 KB as MMDB, on 2026-11-16 |
| This sample | 100 rows from the 2026-11-16 build |
| License | This sample: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). The full database: licensed per database, [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=Satellite+IP+Database+evaluation&products=Satellite+IP+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=satellite-ip) |
| Docs | [docs.internetdata.io/database/satellite-ip/satellite-ip](https://docs.internetdata.io/database/satellite-ip/satellite-ip?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=satellite-ip) |

## Files

- [`satellite_ip_v1.sample.csv`](satellite_ip_v1.sample.csv): the rows as plain CSV, which GitHub shows as a table
- [`satellite_ip_v1.sample.csv.gz`](satellite_ip_v1.sample.csv.gz): the same rows gzipped, as the full database ships
- [`satellite_ip_v1.sample.mmdb`](satellite_ip_v1.sample.mmdb): the same rows as an MMDB, to look up by IP address

## Overview

Ranges satellite internet operators assign to their subscribers, each with the operator, the orbit its satellites fly in, the market it sells the range to, the subscribers' country and how sure we are. Low Earth orbit networks such as Starlink and Amazon Leo and geostationary ones such as Viasat and Hughes are in one file, IPv4 and IPv6 together.

`provider` is the operator's ID, which [Satellite IP Provider](https://docs.internetdata.io/database/satellite-ip/satellite-ip-provider?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=satellite-ip) resolves to its name and homepage, and `asn` the AS announcing the range. `orbit` is `leo`, `meo` or `geo`, which sets how slow the link is: tens of milliseconds for a low Earth orbit network, 600 or more for a geostationary one. `segment` says who the operator sells the range to, homes, businesses and governments, ships or aircraft, and `mixed` where it sells several from the same addresses. `country` is where the range's subscribers are.

A satellite subscriber's traffic reaches the internet where the operator's network does, often a country or more from the dish, and an operator may put many subscribers behind one address. Don't read a location mismatch on one as fraud, and rate limit or ban one with care. Filter on `confidence` `high` where a false positive costs you more than a miss.

## Fields

### CSV (`csvgz`)

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `start_ip` | `ipaddress` | Start IP of the IP range. | `5.8.184.0` |
| `end_ip` | `ipaddress` | End IP of the IP range. | `5.8.187.255` |
| `provider` | `string` | Unique ID of the satellite internet operator whose subscribers use the range, which satellite_ip_provider_v1 names. | `viasat` |
| `asn` | `integer` | Autonomous System Number originating the range. | `7155` |
| `orbit` | `string` | Orbit of the satellites the range's traffic goes through. Values are listed below. | `geo` |
| `segment` | `string` | Market the operator sells the range to. Values are listed below. | `mixed` |
| `country` | `string` | ISO 3166 country code of the range's subscribers. | `ES` |
| `confidence` | `string` | How sure we are that the range carries the operator's subscribers. Values are listed below. | `high` |

`orbit` is one of:

| Value | Description |
| --- | --- |
| `leo` | Low Earth orbit: a constellation a few hundred to about 1,200 km up, such as Starlink's. Round trips are tens of milliseconds. |
| `meo` | Medium Earth orbit, about 8,000 km up, such as SES's O3b. Round trips are about 120 to 150 ms. |
| `geo` | Geostationary orbit, about 35,786 km up over the equator. Round trips are about 600 ms or more. |

`segment` is one of:

| Value | Description |
| --- | --- |
| `consumer` | Residential satellite broadband sold to homes and small offices. |
| `enterprise` | Satellite links sold to businesses, governments and aid agencies: VSAT networks, branch and remote sites. |
| `maritime` | Connectivity on ships, yachts, cruise liners and offshore platforms. |
| `aviation` | In-flight connectivity on aircraft. |
| `mixed` | The operator serves several of these markets from the same addresses. |

`confidence` is one of:

| Value | Description |
| --- | --- |
| `high` | We are sure the range carries the satellite operator's subscribers. |
| `medium` | The range belongs to the satellite operator, and is less certain to carry subscribers than a high range. |

### MMDB (`mmdb`)

Each record is looked up by IP address and holds:

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `provider` | `string` | Unique ID of the satellite internet operator whose subscribers use the range, which satellite_ip_provider_v1 names. | `viasat` |
| `asn` | `integer` | Autonomous System Number originating the range. | `7155` |
| `orbit` | `string` | Orbit of the satellites the range's traffic goes through. Values are listed below. | `geo` |
| `segment` | `string` | Market the operator sells the range to. Values are listed below. | `mixed` |
| `country` | `string` | ISO 3166 country code of the range's subscribers. | `ES` |
| `confidence` | `string` | How sure we are that the range carries the operator's subscribers. Values are listed below. | `high` |

## The full database

The full database needs a license: [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=Satellite+IP+Database+evaluation&products=Satellite+IP+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=satellite-ip) to test the whole file first. With a licensed API key:

```bash
curl -L -o satellite_ip_v1.csv.gz "https://internetdata.io/api/v2/database/download?id=satellite_ip_v1&format=csvgz&apikey=$APIKEY"
curl -L -o satellite_ip_v1.mmdb "https://internetdata.io/api/v2/database/download?id=satellite_ip_v1&format=mmdb&apikey=$APIKEY"
```

Today's sample is on [its page](https://internetdata.io/databases/satellite-ip?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=satellite-ip), cut from the latest build.

Back to [all InternetData sample databases](../).
