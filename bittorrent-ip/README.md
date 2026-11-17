# BitTorrent IP

Every address where a BitTorrent client was seen in the last 90 days, flagged verified or not, with how many clients shared it at once and the codes they identify themselves by.

| Field | Value |
| --- | --- |
| ID | `bittorrent_ip_v1` |
| Formats | `csvgz` |
| Update frequency | Daily |
| Full database | 62,964,046 entries, 786 MB as CSV, on 2026-11-16 |
| This sample | 100 rows from the 2026-11-16 build |
| License | This sample: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). The full database: licensed per database, [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=BitTorrent+IP+Database+evaluation&products=BitTorrent+IP+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=bittorrent-ip) |
| Docs | [docs.internetdata.io/database/bittorrent-ip](https://docs.internetdata.io/database/bittorrent-ip?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=bittorrent-ip) |

## Files

- [`bittorrent_ip_v1.sample.csv`](bittorrent_ip_v1.sample.csv): the rows as plain CSV, which GitHub shows as a table
- [`bittorrent_ip_v1.sample.csv.gz`](bittorrent_ip_v1.sample.csv.gz): the same rows gzipped, as the full database ships

## Overview

Every IPv4 and IPv6 address where a BitTorrent client was seen in the last 90 days, one row per address. `verified` is true where a client at the address answered directly, or two or more other clients reported it at the same time. An address only one client reported stays in the file with `verified` false: most are clients behind NAT, which can't be reached from outside. `id_matches_ip` is true where a client at the address derived its identity on the network from the address itself, as clients that implement BEP 42 do, so a client ran there even where `verified` is false.

`peak_num_ports` is the most ports seen at the address on one day, about how many clients shared it at once: many on a VPN exit, a proxy or a carrier's NAT, and 1 on a single machine. `indexer` marks an address that indexes the BitTorrent network rather than downloading from it. `clients` holds the two-letter codes the clients identify themselves by, such as `LT` (libtorrent), `UT` (µTorrent) and `lt` (rTorrent).

`first_seen` and `last_seen` are the first and last days in the window a client was seen at the address, and `last_reachable` the last day one answered directly. A row never says what an address shared or downloaded.

## Fields

### CSV (`csvgz`)

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `ip` | `ipaddress` | The IP address, IPv4 or IPv6, where a BitTorrent client was seen in the last 90 days. | `1.0.64.239` |
| `verified` | `boolean` | Whether the address is confirmed: a client there answered directly, or two or more other clients reported it at the same time. An unconfirmed address was reported by one client only, most often one behind NAT that cannot be reached from outside it. | `true` |
| `id_matches_ip` | `boolean` | Whether a client at the address derived its identity on the network from the address itself, as clients that implement BEP 42 do (libtorrent, µTorrent and others): evidence a real client was there, confirmed or not. False where none did, often a client that does not implement BEP 42. | `true` |
| `first_seen` | `date` | The first day in the 90-day window a BitTorrent client was seen at the address. | `2026-10-20` |
| `last_seen` | `date` | The most recent day a BitTorrent client was seen at the address. | `2026-11-14` |
| `last_reachable` | `date` | The most recent day a client at the address answered directly; empty when none did, as for a client behind NAT. | `2026-11-14` |
| `days_seen` | `integer` | The number of days in the window a client was seen at the address. | `16` |
| `num_ports` | `integer` | The number of distinct ports BitTorrent clients used at the address in the window. | `1` |
| `peak_num_ports` | `integer` | The most distinct ports seen at the address on one day: about how many clients shared it at once, high on a VPN exit or a carrier's NAT. | `1` |
| `indexer` | `boolean` | Whether the address runs an indexer or crawler of the BitTorrent network rather than ordinary clients: far more client identities than ports. | `false` |
| `clients` | `string` | Comma-joined two-letter codes the clients at the address identify themselves by, such as LT (libtorrent: qBittorrent, Deluge and others), UT (µTorrent) and lt (rTorrent); empty when none did. | `LT` |

## The full database

The full database needs a license: [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=BitTorrent+IP+Database+evaluation&products=BitTorrent+IP+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=bittorrent-ip) to test the whole file first. With a licensed API key:

```bash
curl -L -o bittorrent_ip_v1.csv.gz 'https://internetdata.io/api/v2/database/download?id=bittorrent_ip_v1&format=csvgz&apikey=$APIKEY'
```

Today's sample is on [its page](https://internetdata.io/databases/bittorrent-ip?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=bittorrent-ip), cut from the latest build.

Back to [all InternetData sample databases](../).
