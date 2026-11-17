# Carrier IP

Mobile carrier address space, with the operator, its MCC and MNC, and the country.

| Field | Value |
| --- | --- |
| ID | `carrier_ip_v1` |
| Formats | `csvgz`, `mmdb` |
| Update frequency | Daily |
| Full database | 209,230 entries, 1.46 MB as CSV and 3.75 MB as MMDB, on 2026-11-17 |
| This sample | 100 rows from the 2026-11-17 build |
| License | This sample: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). The full database: licensed per database, [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=Carrier+IP+Database+evaluation&products=Carrier+IP+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=carrier-ip) |
| Docs | [docs.internetdata.io/database/carrier-ip](https://docs.internetdata.io/database/carrier-ip?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=carrier-ip) |

## Files

- [`carrier_ip_v1.sample.csv`](carrier_ip_v1.sample.csv): the rows as plain CSV, which GitHub shows as a table
- [`carrier_ip_v1.sample.csv.gz`](carrier_ip_v1.sample.csv.gz): the same rows gzipped, as the full database ships
- [`carrier_ip_v1.sample.mmdb`](carrier_ip_v1.sample.mmdb): the same rows as an MMDB, to look up by IP address

## Overview

Ranges mobile network operators assign to subscribers on cellular data, each with the operator, its Mobile Country Code and Mobile Network Code, and the country. Many subscribers share one carrier address, so a phone on cellular data can look like a proxy; this file tells the two apart.

## Fields

### CSV (`csvgz`)

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `start_ip` | `ipaddress` | Start IP of the IP range. | `1.5.0.0` |
| `end_ip` | `ipaddress` | End IP of the IP range. | `1.5.255.255` |
| `name` | `string` | Mobile carrier brand name. | `SoftBank` |
| `mcc` | `string` | Mobile Country Code of the carrier. | `440` |
| `mnc` | `string` | Mobile Network Code of the carrier. | `20` |
| `country` | `string` | ISO 3166 country code of the carrier. | `JP` |
| `confidence` | `string` | Confidence of the correctness of this observation. | `high` |

### MMDB (`mmdb`)

Each record is looked up by IP address and holds:

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `name` | `string` | Mobile carrier brand name. | `SoftBank` |
| `mcc` | `string` | Mobile Country Code of the carrier. | `440` |
| `mnc` | `string` | Mobile Network Code of the carrier. | `20` |
| `country` | `string` | ISO 3166 country code of the carrier. | `JP` |
| `confidence` | `string` | Confidence of the correctness of this observation. | `high` |

## The full database

The full database needs a license: [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=Carrier+IP+Database+evaluation&products=Carrier+IP+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=carrier-ip) to test the whole file first. With a licensed API key:

```bash
curl -L -o carrier_ip_v1.csv.gz 'https://internetdata.io/api/v2/database/download?id=carrier_ip_v1&format=csvgz&apikey=$APIKEY'
curl -L -o carrier_ip_v1.mmdb 'https://internetdata.io/api/v2/database/download?id=carrier_ip_v1&format=mmdb&apikey=$APIKEY'
```

Today's sample is on [its page](https://internetdata.io/databases/carrier-ip?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=carrier-ip), cut from the latest build.

Back to [all InternetData sample databases](../).
