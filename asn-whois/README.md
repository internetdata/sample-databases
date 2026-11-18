# ASN Whois

The registry record of every AS number, with its holder and contacts.

| Field | Value |
| --- | --- |
| ID | `asn_whois_v1` |
| Formats | `csvgz` |
| Update frequency | Daily |
| Full database | 118,593 entries, 12.4 MB as CSV, on 2026-11-17 |
| This sample | 100 rows from the 2026-11-17 build |
| License | This sample: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). The full database: licensed per database, [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=ASN+Whois+Database+evaluation&products=ASN+Whois+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=asn-whois) |
| Docs | [docs.internetdata.io/database/asn-whois](https://docs.internetdata.io/database/asn-whois?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=asn-whois) |

## Files

- [`asn_whois_v1.sample.csv`](asn_whois_v1.sample.csv): the rows as plain CSV, which GitHub shows as a table
- [`asn_whois_v1.sample.csv.gz`](asn_whois_v1.sample.csv.gz): the same rows gzipped, as the full database ships

## Overview

One row per AS number, taken from the registry that delegated it. Where another registry keeps a stub that points elsewhere, or a national registry shares the record with APNIC, the delegating registry's record is the one published.

Contacts are resolved to names, emails and phone numbers: admin and technical from the record, else its organization; abuse from the record, else its incident response team, else its organization. Bulk registry data leaves out what privacy rules withhold, most often a personal contact's email, so those fields are empty there.

## Fields

### CSV (`csvgz`)

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `asn` | `integer` | Autonomous System Number. | `0` |
| `handle` | `string` | The AS name the registry holds (as-name), e.g. HETZNER-AS. | `IANA-RSVD-0` |
| `name` | `string` | Name of the holding organization, else the name the ASN dataset gives it. | `Internet Assigned Numbers Authority` |
| `org` | `string` | The registry's handle for the holding organization. | `IANA` |
| `country` | `string` | ISO 3166 country code the registry assigned the ASN to. | `US` |
| `source` | `string` | The registry the record comes from: arin, ripe, apnic, lacnic, afrinic, jpnic, krnic or idnic. | `arin` |
| `status` | `string` | The registry's status for the ASN. | `ASSIGNED` |
| `created` | `date` | When the registry created the record; empty where it predates the registry recording it. | `2002-09-13` |
| `updated` | `date` | When the registry last changed the record. | `2024-05-24` |
| `descr` | `string` | The record's description lines, joined with " / ". | `INSTITUT NATIONAL DE L'INFORMATION GEOGR...` |
| `remarks` | `string` | The record's remarks, joined with " / ", without the notices registries add to every record. | `Reserved - May be used to identify non-r...` |
| `admin` | `string` | Handles of the administrative contacts, pipe-separated. | `KW21-AP` |
| `tech` | `string` | Handles of the technical contacts, pipe-separated. | `LIHD-ARIN` |
| `abuse` | `string` | Handles of the abuse contacts, pipe-separated. | `AT1283-AP` |
| `maintainer` | `string` | Handles of the maintainers allowed to change the record, pipe-separated. | `RIPE-NCC-END-MNT\|FR-NIC-MNT` |
| `maintainer_email` | `string` | Emails of the record's maintainers, pipe-separated, where the registry publishes them (APNIC, IDNIC). | `helpdesk@apnic.net` |
| `abuse_email` | `string` | Email of the ASN's abuse contact. | `abuse@iana.org` |
| `abuse_name` | `string` | Name of the ASN's abuse contact. | `ICANN` |
| `abuse_phone` | `string` | Phone number of the ASN's abuse contact. | `+1-310-301-5820` |
| `abuse_kind` | `string` | What the abuse contact is: person, role (a role account) or irt (an incident response team). | `role` |
| `abuse_country` | `string` | ISO 3166 country code of the abuse contact, where the registry states one (ARIN, APNIC, IDNIC). | `US` |
| `abuse_city` | `string` | City of the abuse contact, where the registry states one (ARIN). | `Los Angeles` |
| `admin_name` | `string` | Name of the administrative contact. | `Internet Corporation for Assigned Names ...` |
| `admin_email` | `string` | Email of the administrative contact. | `res-ip@iana.org` |
| `admin_phone` | `string` | Phone number of the administrative contact. | `+1-310-823-9358` |
| `admin_kind` | `string` | What the administrative contact is: person or role (a role account). | `role` |
| `admin_country` | `string` | ISO 3166 country code of the administrative contact, where the registry states one (ARIN, APNIC, IDNIC). | `US` |
| `admin_city` | `string` | City of the administrative contact, where the registry states one (ARIN). | `Los Angeles` |
| `tech_name` | `string` | Name of the technical contact. | `ICANN` |
| `tech_email` | `string` | Email of the technical contact. | `abuse@iana.org` |
| `tech_phone` | `string` | Phone number of the technical contact. | `+1-310-301-5820` |
| `tech_kind` | `string` | What the technical contact is: person or role (a role account). | `role` |
| `tech_country` | `string` | ISO 3166 country code of the technical contact, where the registry states one (ARIN, APNIC, IDNIC). | `US` |
| `tech_city` | `string` | City of the technical contact, where the registry states one (ARIN). | `Los Angeles` |
| `org_name` | `string` | Name of the holding organization. | `Internet Assigned Numbers Authority` |
| `org_address` | `string` | Postal address of the holding organization. | `12025 Waterfront Drive, Suite 300, Los A...` |
| `org_country` | `string` | ISO 3166 country code of the holding organization. | `US` |
| `org_city` | `string` | City of the holding organization, where the registry states one (ARIN). | `Los Angeles` |
| `abuse_validated` | `boolean` | 1 when ARIN reports that the abuse contact answered its yearly validation, else empty. The other registries publish no such state. | `1` |
| `abuse_unvalidated_since` | `date` | The date since which the abuse contact has not answered ARIN's yearly validation; empty when it has, or where the registry does not say. | `2024-01-05` |

## The full database

The full database needs a license: [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=ASN+Whois+Database+evaluation&products=ASN+Whois+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=asn-whois) to test the whole file first. With a licensed API key:

```bash
curl -L -o asn_whois_v1.csv.gz "https://internetdata.io/api/v2/database/download?id=asn_whois_v1&format=csvgz&apikey=$APIKEY"
```

Today's sample is on [its page](https://internetdata.io/databases/asn-whois?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=asn-whois), cut from the latest build.

Back to [all InternetData sample databases](../).
