# ASN Extended

ASN with each AS number's upstreams, peers and downstreams, its customer cone, its rank and whether it is Tier 1.

| Field | Value |
| --- | --- |
| ID | `asn_extended_v1` |
| Formats | `csvgz` |
| Update frequency | Daily |
| Full database | 123,821 entries, 7.26 MB as CSV, on 2026-11-24 |
| This sample | 100 rows from the 2026-11-24 build |
| License | This sample: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). The full database: licensed per database, [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=ASN+Extended+Database+evaluation&products=ASN+Extended+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=asn-extended) |
| Docs | [docs.internetdata.io/database/asn/asn-extended](https://docs.internetdata.io/database/asn/asn-extended?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=asn-extended) |

## Files

- [`asn_extended_v1.sample.csv`](asn_extended_v1.sample.csv): the rows as plain CSV, which GitHub shows as a table
- [`asn_extended_v1.sample.csv.gz`](asn_extended_v1.sample.csv.gz): the same rows gzipped, as the full database ships

## Overview

Every row and column of [ASN](https://docs.internetdata.io/database/asn/asn?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=asn-extended), and fifteen more:

- `upstreams`, `peers` and `downstreams`: the AS numbers it gets transit from, exchanges its own and its customers' routes with, and provides transit to, pipe-separated in ascending order. `num_upstreams`, `num_peers` and `num_downstreams` count them. A relationship is how two networks route each other's traffic, which is not always what either one pays the other.
- `customer_cone_asns`: its customer cone, itself, its customers, their customers and so on down. `customer_cone_ips`, `customer_cone_prefixes4` and `customer_cone_prefixes6` count the IPv4 addresses those networks originate and the prefixes they announce.
- `rank`: its place among all AS numbers in global routing by the size of its customer cone, 1 the largest.
- `transit_degree`: how many distinct networks it is seen carrying routes between.
- `tier1`: 1 for the transit-free networks at the top of the hierarchy, which get transit from no one and peer with each other.
- `siblings`: the other AS numbers registered to the same organization, routed or not, and `num_siblings` counts them. They're left out of `upstreams`, `peers` and `downstreams`.

An AS number seen in no AS path keeps its row, with no rank and zeros elsewhere.

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
| `rank` | `integer` | The ASN's place among all ASNs in global routing by the size of its customer cone, 1 the largest. Empty for an ASN seen in no AS path. | `6923` |
| `tier1` | `boolean` | 1 when the ASN is one of the transit-free networks at the top of the routing hierarchy, which get transit from no one and peer with each other (Tier 1), else empty. |  |
| `transit_degree` | `integer` | Distinct neighbors the ASN carries routes between: ASNs seen on either side of it in an AS path. 0 for a network that carries no one's routes. | `4` |
| `customer_cone_asns` | `integer` | ASNs in the ASN's customer cone: itself, its customers, their customers and so on down. 0 for an ASN seen in no AS path. | `3` |
| `customer_cone_ips` | `integer` | IPv4 addresses the ASNs of its customer cone originate. | `8448` |
| `customer_cone_prefixes4` | `integer` | IPv4 prefixes the ASNs of its customer cone announce. | `138` |
| `customer_cone_prefixes6` | `integer` | IPv6 prefixes the ASNs of its customer cone announce. | `7` |
| `num_upstreams` | `integer` | Upstream providers: the networks the ASN gets transit from, which carry its routes to the rest of the internet. | `6` |
| `num_peers` | `integer` | Peers: the networks the ASN exchanges its own and its customers' routes with. | `2` |
| `num_downstreams` | `integer` | Downstream customers: the networks the ASN provides transit to. | `2` |
| `upstreams` | `string` | ASNs of its upstream providers, pipe-separated in ascending order (e.g. "174\|3356"). Empty when it has none. | `7046\|29132\|262544\|263309\|264773\|396455` |
| `peers` | `string` | ASNs of its peers, pipe-separated in ascending order. Empty when it has none. | `11537\|58689` |
| `downstreams` | `string` | ASNs of its downstream customers, pipe-separated in ascending order. Empty when it has none. | `54043\|154799` |
| `num_siblings` | `integer` | Other ASNs the same organization holds, as its registry's records name it. | `39` |
| `siblings` | `string` | Those ASNs, pipe-separated in ascending order. Empty when it has none. A sibling is in none of upstreams, peers and downstreams. | `189\|199\|200\|201\|202\|203\|279\|281\|560\|594\|...` |

`type` is one of:

| Value | Description |
| --- | --- |
| `isp` | An Internet service provider: access, mobile or transit networks that connect other people. |
| `hosting` | A hosting, cloud, CDN or content network whose addresses serve machines rather than people. |
| `education` | A university, school or research and education network. |
| `government` | A government body, agency or armed service. |
| `business` | Any other organization running its own network, and the default when no signal says otherwise. |

## The full database

The full database needs a license: [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=ASN+Extended+Database+evaluation&products=ASN+Extended+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=asn-extended) to test the whole file first. With a licensed API key:

```bash
curl -L -o asn_extended_v1.csv.gz "https://internetdata.io/api/v2/database/download?id=asn_extended_v1&format=csvgz&apikey=$APIKEY"
```

Today's sample is on [its page](https://internetdata.io/databases/asn-extended?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=asn-extended), cut from the latest build.

Back to [all InternetData sample databases](../).
