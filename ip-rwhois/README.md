# IP RWHOIS

Reassignments published on network operators' RWHOIS servers, with their holders and contacts.

| Field | Value |
| --- | --- |
| ID | `ip_rwhois_v1` |
| Formats | `csvgz`, `mmdb` |
| Update frequency | Weekly |
| Full database | 191,600 entries, 5.78 MB as CSV and 10.2 MB as MMDB, on 2026-11-17 |
| This sample | 100 rows from the 2026-11-17 build |
| License | This sample: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). The full database: licensed per database, [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=IP+RWHOIS+Database+evaluation&products=IP+RWHOIS+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-rwhois) |
| Docs | [docs.internetdata.io/database/ip-rwhois](https://docs.internetdata.io/database/ip-rwhois?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-rwhois) |

## Files

- [`ip_rwhois_v1.sample.csv`](ip_rwhois_v1.sample.csv): the rows as plain CSV, which GitHub shows as a table
- [`ip_rwhois_v1.sample.csv.gz`](ip_rwhois_v1.sample.csv.gz): the same rows gzipped, as the full database ships
- [`ip_rwhois_v1.sample.mmdb`](ip_rwhois_v1.sample.mmdb): the same rows as an MMDB, to look up by IP address

## Overview

Operators publish the blocks they reassign to their own customers on RWHOIS servers, below what the registries record. This database is every network those servers return, collected weekly from the servers the registries refer to. `host` is the server that answered, `source` the operator, and `parent` the enclosing network the server names. RWHOIS servers publish IPv4 networks alone.

## Fields

### CSV (`csvgz`)

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `start_ip` | `ipaddress` | Start IP of the network. | `23.28.0.0` |
| `end_ip` | `ipaddress` | End IP of the network. | `23.28.63.255` |
| `id` | `string` | The network's identifier on the operator's RWHOIS server. | `ASTOUND-003` |
| `name` | `string` | Name of the organization the network is assigned to. | `Private Customer` |
| `descr` | `string` | The network's name on the RWHOIS server. | `ASTOUND-003` |
| `host` | `string` | The RWHOIS server that published the network. | `rwhois.rcn.net` |
| `email` | `string` | Email of the network's point of contact. | `ipAdmin@hivelocity.net` |
| `abuse` | `string` | Email of the network's abuse contact. | `abuse@hivelocity.net` |
| `domain` | `string` | The registrable domain of the contact emails. | `hivelocity.net` |
| `country` | `string` | ISO 3166 country code the record states. | `US` |
| `city` | `string` | City of the assignee. | `Princeton` |
| `street` | `string` | Street address of the assignee. | `650 College Road suite 3100` |
| `postal` | `string` | Postal code of the assignee. | `20170` |
| `updated` | `date` | When the operator last changed the record. | `2026-10-16` |
| `imported` | `date` | When our scan collected the record. | `2026-11-12` |
| `parent` | `string` | The enclosing network the RWHOIS server names, if any. |  |
| `source` | `string` | The operator whose RWHOIS server published the network. | `rcn_net` |
| `created` | `date` | When the operator created the record. | `2025-07-22` |
| `admin_name` | `string` | Name of the network's point of contact. | `Network Administrator` |
| `admin_phone` | `string` | Phone number of the network's point of contact. | `888-869-4678` |
| `admin_country` | `string` | ISO 3166 country code of the network's point of contact, where the server publishes contact objects. |  |
| `admin_city` | `string` | City of the network's point of contact, where the server publishes contact objects. |  |
| `tech_name` | `string` | Name of the technical contact. | `Network Administrator` |
| `tech_email` | `string` | Email of the technical contact. | `ipAdmin@hivelocity.net` |
| `tech_phone` | `string` | Phone number of the technical contact. | `888-869-4678` |
| `tech_country` | `string` | ISO 3166 country code of the technical contact, where the server publishes contact objects. |  |
| `tech_city` | `string` | City of the technical contact, where the server publishes contact objects. |  |
| `abuse_name` | `string` | Name of the abuse contact. | `Hivelocity Abuse Department` |
| `abuse_phone` | `string` | Phone number of the abuse contact. | `888-869-4678` |
| `abuse_country` | `string` | ISO 3166 country code of the abuse contact, where the server publishes contact objects. |  |
| `abuse_city` | `string` | City of the abuse contact, where the server publishes contact objects. |  |

### MMDB (`mmdb`)

Each record is looked up by IP address and holds:

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `id` | `string` | Identifier of the most specific network covering the address. | `ASTOUND-003` |
| `name` | `string` | Name of the organization that network is assigned to. | `Private Customer` |
| `country` | `string` | ISO 3166 country code the record states. | `US` |
| `source` | `string` | The operator whose RWHOIS server published it. | `rcn_net` |
| `abuse` | `string` | Email of the network's abuse contact. | `abuse@hivelocity.net` |
| `domain` | `string` | The registrable domain of the contact emails. | `hivelocity.net` |

## The full database

The full database needs a license: [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=IP+RWHOIS+Database+evaluation&products=IP+RWHOIS+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-rwhois) to test the whole file first. With a licensed API key:

```bash
curl -L -o ip_rwhois_v1.csv.gz "https://internetdata.io/api/v2/database/download?id=ip_rwhois_v1&format=csvgz&apikey=$APIKEY"
curl -L -o ip_rwhois_v1.mmdb "https://internetdata.io/api/v2/database/download?id=ip_rwhois_v1&format=mmdb&apikey=$APIKEY"
```

Today's sample is on [its page](https://internetdata.io/databases/ip-rwhois?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-rwhois), cut from the latest build.

Back to [all InternetData sample databases](../).
