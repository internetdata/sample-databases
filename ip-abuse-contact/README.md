# IP Abuse Contact

Who takes abuse reports for every address range, with the email, phone and address.

| Field | Value |
| --- | --- |
| ID | `ip_abuse_contact_v1` |
| Formats | `csvgz`, `mmdb` |
| Update frequency | Daily |
| Full database | 4,226,374 entries, 68.9 MB as CSV and 238 MB as MMDB, on 2026-11-24 |
| This sample | 100 rows from the 2026-11-24 build |
| License | This sample: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). The full database: licensed per database, [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=IP+Abuse+Contact+Database+evaluation&products=IP+Abuse+Contact+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-abuse-contact) |
| Docs | [docs.internetdata.io/database/ip-abuse-contact](https://docs.internetdata.io/database/ip-abuse-contact?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-abuse-contact) |

## Files

- [`ip_abuse_contact_v1.sample.csv`](ip_abuse_contact_v1.sample.csv): the rows as plain CSV, which GitHub shows as a table
- [`ip_abuse_contact_v1.sample.csv.gz`](ip_abuse_contact_v1.sample.csv.gz): the same rows gzipped, as the full database ships
- [`ip_abuse_contact_v1.sample.mmdb`](ip_abuse_contact_v1.sample.mmdb): the same rows as an MMDB, to look up by IP address

## Overview

For each address range, the contact that takes its abuse reports: from the most specific registry record or RWHOIS network that names one. `network` is the block whose record named it, which can be larger than the range when the range inherits a parent's contact.

Registry placeholders, the masked or dummy emails, phone numbers and addresses some registries publish in their bulk data, are removed rather than passed on.

## Fields

### CSV (`csvgz`)

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `start_ip` | `ipaddress` | Start IP of the IP range. | `1.0.0.0` |
| `end_ip` | `ipaddress` | End IP of the IP range. | `1.0.0.255` |
| `network` | `string` | The original registry network block the contact was derived from. | `1.0.0.0-1.0.0.255` |
| `name` | `string` | Abuse contact name (falls back to the holder organization name). | `Abuse` |
| `email` | `string` | Abuse contact email address. | `abuse@cloudflare.com` |
| `phone` | `string` | Abuse contact phone number, when published. | `+1-650-319-8930` |
| `country` | `string` | ISO country code of the network. | `AU` |
| `address` | `string` | Abuse contact postal address, when published. | `101 Townsend Street, San Francisco, CA, ...` |
| `validated` | `boolean` | 1 when ARIN reports that the contact answered its yearly validation, else empty. The other registries publish no such state. | `1` |
| `unvalidated_since` | `date` | The date since which the contact has not answered ARIN's yearly validation; empty when it has, or where the registry does not say. | `2025-09-04` |

### MMDB (`mmdb`)

Each record is looked up by IP address and holds:

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `network` | `string` | The original registry network block the contact was derived from. | `1.0.0.0-1.0.0.255` |
| `name` | `string` | Abuse contact name (falls back to the holder organization name). | `Abuse` |
| `email` | `string` | Abuse contact email address. | `abuse@cloudflare.com` |
| `phone` | `string` | Abuse contact phone number, when published. | `+1-650-319-8930` |
| `country` | `string` | ISO country code of the network. | `AU` |
| `address` | `string` | Abuse contact postal address, when published. | `101 Townsend Street, San Francisco, CA, ...` |
| `validated` | `boolean` | 1 when ARIN reports that the contact answered its yearly validation, else empty. The other registries publish no such state. | `1` |
| `unvalidated_since` | `date` | The date since which the contact has not answered ARIN's yearly validation; empty when it has, or where the registry does not say. | `2025-09-04` |

## The full database

The full database needs a license: [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=IP+Abuse+Contact+Database+evaluation&products=IP+Abuse+Contact+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-abuse-contact) to test the whole file first. With a licensed API key:

```bash
curl -L -o ip_abuse_contact_v1.csv.gz "https://internetdata.io/api/v2/database/download?id=ip_abuse_contact_v1&format=csvgz&apikey=$APIKEY"
curl -L -o ip_abuse_contact_v1.mmdb "https://internetdata.io/api/v2/database/download?id=ip_abuse_contact_v1&format=mmdb&apikey=$APIKEY"
```

Today's sample is on [its page](https://internetdata.io/databases/ip-abuse-contact?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-abuse-contact), cut from the latest build.

Back to [all InternetData sample databases](../).
