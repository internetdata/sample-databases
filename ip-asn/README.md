# IP ASN

Announced IPv4 and IPv6 space mapped to its origin AS, with the holder and RPKI status.

| Field | Value |
| --- | --- |
| ID | `ip_asn_v1` |
| Formats | `csvgz`, `mmdb` |
| Update frequency | Daily |
| Full database | 1,506,563 entries, 20.5 MB as CSV and 78.5 MB as MMDB, on 2026-11-24 |
| This sample | 100 rows from the 2026-11-24 build |
| License | This sample and the full database: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) |
| Docs | [docs.internetdata.io/database/ip-asn](https://docs.internetdata.io/database/ip-asn?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-asn) |

## Files

- [`ip_asn_v1.sample.csv`](ip_asn_v1.sample.csv): the rows as plain CSV, which GitHub shows as a table
- [`ip_asn_v1.sample.csv.gz`](ip_asn_v1.sample.csv.gz): the same rows gzipped, as the full database ships
- [`ip_asn_v1.sample.mmdb`](ip_asn_v1.sample.mmdb): the same rows as an MMDB, to look up by IP address

## Overview

Every range in the global routing table, split so that each address belongs to the most specific prefix announcing it. `prefix` is that announcement and `asn` its origin; where more than one AS originates a prefix, the one most of the routing table sees is kept. `name`, `domain`, `type` and `country` are the origin AS's, as the [ASN](https://docs.internetdata.io/database/asn/asn?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-asn) database publishes them.

`rpki_status` is the route's validation against the published RPKI data (RFC 6811). Bogon space and reserved AS numbers are left out.

Free under [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/), like every Open database: credit InternetData with a link to [internetdata.io](https://internetdata.io/?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-asn), and share what you build from it under the same license.

## Fields

### CSV (`csvgz`)

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `start_ip` | `ipaddress` | Start IP of the IP range. | `1.0.0.0` |
| `end_ip` | `ipaddress` | End IP of the IP range. | `1.0.0.255` |
| `prefix` | `string` | The announced BGP prefix that covers the range; the most specific when several do. | `1.0.0.0/24` |
| `asn` | `integer` | Autonomous System Number originating the prefix. | `13335` |
| `name` | `string` | Name of the organization that operates the ASN. | `Cloudflare, Inc.` |
| `domain` | `string` | The ASN operator's own registrable domain. | `cloudflare.com` |
| `type` | `string` | Kind of network the ASN runs. Values are listed below. | `hosting` |
| `country` | `string` | ISO 3166 country code the registry assigned the ASN to. | `US` |
| `rpki_status` | `string` | RPKI route origin validation (RFC 6811) of the covering announcement. Values are listed below. | `valid` |

`type` is one of:

| Value | Description |
| --- | --- |
| `isp` | An Internet service provider: access, mobile or transit networks that connect other people. |
| `hosting` | A hosting, cloud, CDN or content network whose addresses serve machines rather than people. |
| `education` | A university, school or research and education network. |
| `government` | A government body, agency or armed service. |
| `business` | Any other organization running its own network, and the default when no signal says otherwise. |

`rpki_status` is one of:

| Value | Description |
| --- | --- |
| `valid` | A published ROA authorizes this origin AS to announce this prefix at this length. |
| `invalid:origin` | ROAs cover this prefix, but none authorizes the AS originating it. |
| `invalid:length` | A ROA authorizes the origin AS for a shorter prefix only; this announcement is more specific than it allows. |
| `not_found` | No ROA covers this prefix, so RPKI says nothing about who may announce it. |

### MMDB (`mmdb`)

Each record is looked up by IP address and holds:

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `prefix` | `string` | The announced BGP prefix that covers the range; the most specific when several do. | `1.0.0.0/24` |
| `asn` | `integer` | Autonomous System Number originating the prefix. | `13335` |
| `name` | `string` | Name of the organization that operates the ASN. | `Cloudflare, Inc.` |
| `domain` | `string` | The ASN operator's own registrable domain. | `cloudflare.com` |
| `type` | `string` | Kind of network the ASN runs. Values are listed below. | `hosting` |
| `country` | `string` | ISO 3166 country code the registry assigned the ASN to. | `US` |
| `rpki_status` | `string` | RPKI route origin validation (RFC 6811) of the covering announcement. Values are listed below. | `valid` |

## The full database

IP ASN is an Open database, free under CC BY-SA 4.0 with an InternetData account: [sign up](https://internetdata.io/signup?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-asn), then with your API key:

```bash
curl -L -o ip_asn_v1.csv.gz "https://internetdata.io/api/v2/database/download?id=ip_asn_v1&format=csvgz&apikey=$APIKEY"
curl -L -o ip_asn_v1.mmdb "https://internetdata.io/api/v2/database/download?id=ip_asn_v1&format=mmdb&apikey=$APIKEY"
```

Today's sample is on [its page](https://internetdata.io/databases/ip-asn?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-asn), cut from the latest build.

Back to [all InternetData sample databases](../).
