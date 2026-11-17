# ASN

Every allocated or announced AS number with its holder, domain, network type, announced space and RPKI standing.

| Field | Value |
| --- | --- |
| ID | `asn_v1` |
| Formats | `csvgz` |
| Update frequency | Daily |
| Full database | 123,708 entries, 2.92 MB as CSV, on 2026-11-17 |
| This sample | 100 rows from the 2026-11-17 build |
| License | This sample and the full database: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) |
| Docs | [docs.internetdata.io/database/asn/asn](https://docs.internetdata.io/database/asn/asn?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=asn) |

## Files

- [`asn_v1.sample.csv`](asn_v1.sample.csv): the rows as plain CSV, which GitHub shows as a table
- [`asn_v1.sample.csv.gz`](asn_v1.sample.csv.gz): the same rows gzipped, as the full database ships

## Overview

One row per AS number the regional registries have allocated, and one per other AS number seen originating a route in global BGP, whose `registry` is empty. The holder's name, country, registry and allocation date come from the registries' own records. `domain` is the holder's own domain where one can be established, and `type` is our classification of the network the AS runs.

The announcement columns count what the AS originates in the global routing table: `num_ips` its IPv4 addresses, `num_prefixes4` and `num_prefixes6` its prefixes, and `rpki_valid`, `rpki_invalid` and `rpki_not_found` its routes by RPKI validation state. An AS that announces nothing has zeros there.

[IP ASN](https://docs.internetdata.io/database/ip-asn?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=asn) maps every announced range to its origin AS, and [ASN Whois](https://docs.internetdata.io/database/asn-whois?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=asn) carries each AS number's registry record and contacts. [ASN Extended](https://docs.internetdata.io/database/asn/asn-extended?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=asn) adds each AS number's upstreams, peers and downstreams, its customer cone, its rank, whether it is Tier 1 and the other AS numbers its organization holds.

Free under [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/), like every Open database: credit InternetData with a link to [internetdata.io](https://internetdata.io/?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=asn), and share what you build from it under the same license.

## Fields

### CSV (`csvgz`)

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `asn` | `integer` | Autonomous System Number. | `1` |
| `name` | `string` | Name of the organization that operates the ASN. | `Level 3 Parent, LLC` |
| `country` | `string` | ISO 3166 country code the registry assigned the ASN to. | `US` |
| `registry` | `string` | The regional internet registry that allocated the ASN: afrinic, apnic, arin, lacnic or ripe. | `arin` |
| `allocated` | `date` | Date the registry allocated the ASN. | `2001-09-20` |
| `domain` | `string` | The operator's own registrable domain. | `level3.com` |
| `type` | `string` | Kind of network the ASN runs. Values are listed below. | `isp` |
| `num_ips` | `integer` | IPv4 addresses the ASN originates in global BGP. | `6912` |
| `num_prefixes4` | `integer` | IPv4 prefixes the ASN announces. | `129` |
| `num_prefixes6` | `integer` | IPv6 prefixes the ASN announces. | `0` |
| `rpki_valid` | `integer` | Announcements an RPKI ROA authorizes. | `0` |
| `rpki_invalid` | `integer` | Announcements RPKI ROAs contradict: a wrong origin, or more specific than allowed. | `0` |
| `rpki_not_found` | `integer` | Announcements no RPKI ROA covers. | `129` |

`type` is one of:

| Value | Description |
| --- | --- |
| `isp` | An Internet service provider: access, mobile or transit networks that connect other people. |
| `hosting` | A hosting, cloud, CDN or content network whose addresses serve machines rather than people. |
| `education` | A university, school or research and education network. |
| `government` | A government body, agency or armed service. |
| `business` | Any other organization running its own network, and the default when no signal says otherwise. |

## The full database

ASN is an Open database, free under CC BY-SA 4.0 with an InternetData account: [sign up](https://internetdata.io/signup?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=asn), then with your API key:

```bash
curl -L -o asn_v1.csv.gz 'https://internetdata.io/api/v2/database/download?id=asn_v1&format=csvgz&apikey=$APIKEY'
```

Today's sample is on [its page](https://internetdata.io/databases/asn?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=asn), cut from the latest build.

Back to [all InternetData sample databases](../).
