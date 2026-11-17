# IP Whois

Every network record the registries publish, with its holder, status, contacts and parent network.

| Field | Value |
| --- | --- |
| ID | `ip_whois_v1` |
| Formats | `csvgz`, `mmdb` |
| Update frequency | Daily |
| Full database | 12,321,316 entries, 481 MB as CSV and 717 MB as MMDB, on 2026-11-17 |
| This sample | 100 rows from the 2026-11-17 build |
| License | This sample: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). The full database: licensed per database, [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=IP+Whois+Database+evaluation&products=IP+Whois+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-whois) |
| Docs | [docs.internetdata.io/database/ip-whois](https://docs.internetdata.io/database/ip-whois?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-whois) |

## Files

- [`ip_whois_v1.sample.csv`](ip_whois_v1.sample.csv): the rows as plain CSV, which GitHub shows as a table
- [`ip_whois_v1.sample.csv.gz`](ip_whois_v1.sample.csv.gz): the same rows gzipped, as the full database ships
- [`ip_whois_v1.sample.mmdb`](ip_whois_v1.sample.mmdb): the same rows as an MMDB, to look up by IP address

## Overview

One row per network record in the public data of AFRINIC, APNIC, ARIN, LACNIC and the RIPE NCC, the national registries under APNIC, and operators' RWHOIS servers, at every level of nesting, IPv4 and IPv6. `source` says where a record comes from, and `parent` names the smallest other record that contains it.

Admin and technical contacts are the record's own, else its organization's. The abuse contact is the record's own, else its incident response team's, else its organization's. Bulk registry data leaves out what privacy rules withhold, most often a personal contact's email, so those fields are empty there.

`asn` is the AS announcing the record's first address, with its name, domain and type from the [ASN](https://docs.internetdata.io/database/asn/asn?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-whois) database. `rdns_domain` is the domain most reverse DNS names inside the record share, for records of up to 64 /24s.

The MMDB answers each address with the most specific record holding it, in fewer columns.

## Fields

### CSV (`csvgz`)

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `start_ip` | `ipaddress` | Start IP of the registered range. | `0.0.0.0` |
| `end_ip` | `ipaddress` | End IP of the registered range. | `1.178.111.255` |
| `id` | `string` | The record's network name (netname) in the registry. | `NON-RIPE-NCC-MANAGED-ADDRESS-BLOCK` |
| `name` | `string` | Name of the organization holding the range, else its description. | `IPv4 address block not managed by the RI...` |
| `country` | `string` | ISO 3166 country code the record states. | `EU` |
| `status` | `string` | The registry's assignment status, e.g. ALLOCATED PA, ASSIGNED PA, reassignment. | `ALLOCATED UNSPECIFIED` |
| `tech` | `string` | Handles of the technical contacts, pipe-separated. | `ZC108-ARIN` |
| `maintainer` | `string` | Handles of the maintainers allowed to change the record, pipe-separated. | `RIPE-NCC-HM-MNT` |
| `admin` | `string` | Handles of the administrative contacts, pipe-separated. | `FM6-AFRINIC` |
| `source` | `string` | Where the record comes from: the registry (arin, ripe, apnic, lacnic, afrinic, jpnic, krnic, twnic, idnic) or rwhois. | `ripe` |
| `whois_domain` | `string` | The registrable domain of the record's contact emails. | `mindray.com` |
| `updated` | `date` | When the registry last changed the record. | `2021-12-06` |
| `org` | `string` | The registry's handle for the holding organization. | `MN-233` |
| `rdns_domain` | `string` | The registrable domain most reverse-DNS names inside the range belong to. | `mtel.gr` |
| `domain` | `string` | The holder's domain: whois_domain, else rdns_domain. | `mindray.com` |
| `geoloc` | `string` | Latitude and longitude the record states. | `40.523586351723324 22.203712463378906` |
| `org_address` | `string` | Postal address of the holding organization. | `2100 GOLD NONE, SJ, CA, 95002` |
| `asn` | `integer` | The ASN announcing the start of the range in global BGP. | `7018` |
| `as_name` | `string` | Name of that ASN's operator. | `AT&T Enterprises, LLC` |
| `as_domain` | `string` | Domain of that ASN's operator. | `att.com` |
| `as_type` | `string` | Kind of network that ASN runs. Values are listed below. | `isp` |
| `created` | `date` | When the registry created the record; empty where it predates the registry recording it. | `2021-12-06` |
| `descr` | `string` | The record's description lines, joined with " / ". | `IPv4 address block not managed by the RI...` |
| `parent` | `string` | The smallest other record whose range encloses this one, as start-end. | `12.0.0.0-12.255.255.255` |
| `handle` | `string` | The registry's own handle for the record: ARIN's NetHandle, LACNIC's handle, an RWHOIS network's ID. Empty for RIPE, APNIC, AFRINIC and the national registries, which key a record by its range. | `NET-12-1-72-104-1` |
| `as_route` | `string` | The prefix announced in global BGP that holds the range's start address. | `12.0.0.0/9` |
| `remarks` | `string` | The record's remarks, joined with " / ", without the notices registries add to every record. | `For registration information, / you can ...` |
| `abuse_email` | `string` | Email of the record's abuse contact. | `d.bayani@mindray.com` |
| `abuse_name` | `string` | Name of the record's abuse contact. | `Danny Bayani` |
| `abuse_phone` | `string` | Phone number of the record's abuse contact. | `+1-201-825-8115` |
| `abuse_kind` | `string` | What the abuse contact is: person, role (a role account) or irt (an incident response team). | `person` |
| `abuse_country` | `string` | ISO 3166 country code of the abuse contact, where the registry states one (ARIN, APNIC, IDNIC). | `US` |
| `abuse_city` | `string` | City of the abuse contact, where the registry states one (ARIN). | `IRVING` |
| `admin_name` | `string` | Name of the administrative contact. | `Danny Bayani` |
| `admin_email` | `string` | Email of the administrative contact. | `d.bayani@mindray.com` |
| `admin_phone` | `string` | Phone number of the administrative contact. | `+1-201-825-8115` |
| `admin_kind` | `string` | What the administrative contact is: person or role (a role account). | `person` |
| `admin_country` | `string` | ISO 3166 country code of the administrative contact, where the registry states one (ARIN, APNIC, IDNIC). | `US` |
| `admin_city` | `string` | City of the administrative contact, where the registry states one (ARIN). | `IRVING` |
| `tech_name` | `string` | Name of the technical contact. | `Danny Bayani` |
| `tech_email` | `string` | Email of the technical contact. | `d.bayani@mindray.com` |
| `tech_phone` | `string` | Phone number of the technical contact. | `+1-201-825-8115` |
| `tech_kind` | `string` | What the technical contact is: person or role (a role account). | `person` |
| `tech_country` | `string` | ISO 3166 country code of the technical contact, where the registry states one (ARIN, APNIC, IDNIC). | `US` |
| `tech_city` | `string` | City of the technical contact, where the registry states one (ARIN). | `IRVING` |
| `org_name` | `string` | Name of the holding organization. | `MINDRAY NA` |
| `org_country` | `string` | ISO 3166 country code of the holding organization. | `US` |
| `org_city` | `string` | City of the holding organization, where the registry states one (ARIN). | `SJ` |
| `maintainer_email` | `string` | Emails of the record's maintainers, pipe-separated, where the registry publishes them (APNIC, IDNIC). | `Noc_pldt@pldt.com.ph` |
| `domain_maintainer` | `string` | Handles of the maintainers of the range's reverse DNS delegations (mnt-domains), pipe-separated. |  |
| `abuse_validated` | `boolean` | 1 when ARIN reports that the abuse contact answered its yearly validation, else empty. The other registries publish no such state. |  |
| `abuse_unvalidated_since` | `date` | The date since which the abuse contact has not answered ARIN's yearly validation; empty when it has, or where the registry does not say. | `2018-04-21` |

`as_type` is one of:

| Value | Description |
| --- | --- |
| `isp` | An Internet service provider: access, mobile or transit networks that connect other people. |
| `hosting` | A hosting, cloud, CDN or content network whose addresses serve machines rather than people. |
| `education` | A university, school or research and education network. |
| `government` | A government body, agency or armed service. |
| `business` | Any other organization running its own network, and the default when no signal says otherwise. |

### MMDB (`mmdb`)

Each record is looked up by IP address and holds:

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `id` | `string` | Network name of the most specific record covering the address. | `NON-RIPE-NCC-MANAGED-ADDRESS-BLOCK` |
| `name` | `string` | Name of the organization holding that record's range. | `IPv4 address block not managed by the RI...` |
| `country` | `string` | ISO 3166 country code the record states. | `EU` |
| `status` | `string` | The registry's assignment status. | `ALLOCATED UNSPECIFIED` |
| `org` | `string` | The registry's handle for the holding organization. | `MN-233` |
| `source` | `string` | The registry the record comes from, or rwhois. | `ripe` |
| `abuse_email` | `string` | Email of the record's abuse contact. | `d.bayani@mindray.com` |
| `domain` | `string` | The holder's domain. | `mindray.com` |
| `asn` | `integer` | The ASN announcing the record's start address. | `7018` |

## The full database

The full database needs a license: [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=IP+Whois+Database+evaluation&products=IP+Whois+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-whois) to test the whole file first. With a licensed API key:

```bash
curl -L -o ip_whois_v1.csv.gz 'https://internetdata.io/api/v2/database/download?id=ip_whois_v1&format=csvgz&apikey=$APIKEY'
curl -L -o ip_whois_v1.mmdb 'https://internetdata.io/api/v2/database/download?id=ip_whois_v1&format=mmdb&apikey=$APIKEY'
```

Today's sample is on [its page](https://internetdata.io/databases/ip-whois?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-whois), cut from the latest build.

Back to [all InternetData sample databases](../).
