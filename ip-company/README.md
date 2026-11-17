# IP Company

The organization that uses each IP range, with its domain and type, and the AS that announces the range.

| Field | Value |
| --- | --- |
| ID | `ip_company_v1` |
| Formats | `csvgz`, `mmdb` |
| Update frequency | Daily |
| Full database | 10,822,637 entries, 160 MB as CSV and 300 MB as MMDB, on 2026-11-17 |
| This sample | 100 rows from the 2026-11-17 build |
| License | This sample: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). The full database: licensed per database, [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=IP+Company+Database+evaluation&products=IP+Company+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-company) |
| Docs | [docs.internetdata.io/database/ip-company](https://docs.internetdata.io/database/ip-company?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-company) |

## Files

- [`ip_company_v1.sample.csv`](ip_company_v1.sample.csv): the rows as plain CSV, which GitHub shows as a table
- [`ip_company_v1.sample.csv.gz`](ip_company_v1.sample.csv.gz): the same rows gzipped, as the full database ships
- [`ip_company_v1.sample.mmdb`](ip_company_v1.sample.mmdb): the same rows as an MMDB, to look up by IP address

## Overview

Every registered or announced IPv4 and IPv6 range with the organization that uses it. Where a network operator has assigned a block to a customer, the row names the customer rather than the operator: a hotel, a bank or a school inside a telecom's space. Where the operator keeps a block for its own subscribers, the row names the operator.

`name` is the organization, `domain` its own registrable domain where one is known, `type` the kind of organization and `country` the country it is registered in. `asn`, `as_name`, `as_domain` and `as_type` are the AS announcing the range, as the [ASN](https://docs.internetdata.io/database/asn/asn?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-company) database publishes them, so a row whose company is not its AS's holder is a customer of that network.

Match `domain` against the accounts you already have to see which customers your traffic comes from, and use `type` to tell an office network from consumer broadband or a hosting provider.

## Fields

### CSV (`csvgz`)

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `start_ip` | `ipaddress` | Start IP of the IP range. | `1.0.0.0` |
| `end_ip` | `ipaddress` | End IP of the IP range. | `1.0.0.255` |
| `name` | `string` | Name of the organization that uses the range. | `APNIC and Cloudflare DNS Resolver projec...` |
| `domain` | `string` | The organization's own registrable domain. | `cloudflare.com` |
| `type` | `string` | Kind of organization that uses the range. Values are listed below. | `hosting` |
| `country` | `string` | ISO 3166 country code the organization is registered in. | `AU` |
| `asn` | `integer` | Autonomous System Number originating the range; empty where no AS announces it. | `13335` |
| `as_name` | `string` | Name of the organization that operates the ASN. | `Cloudflare, Inc.` |
| `as_domain` | `string` | The ASN operator's own registrable domain. | `cloudflare.com` |
| `as_type` | `string` | Kind of network the ASN runs. Values are listed below. | `hosting` |

`type` is one of:

| Value | Description |
| --- | --- |
| `isp` | An Internet service provider: access, mobile or transit networks that connect other people. |
| `hosting` | A hosting, cloud, CDN or content network whose addresses serve machines rather than people. |
| `education` | A university, school or research and education network. |
| `government` | A government body, agency or armed service. |
| `business` | Any other organization running its own network, and the default when no signal says otherwise. |

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
| `name` | `string` | Name of the organization that uses the range. | `APNIC and Cloudflare DNS Resolver projec...` |
| `domain` | `string` | The organization's own registrable domain. | `cloudflare.com` |
| `type` | `string` | Kind of organization that uses the range. Values are listed below. | `hosting` |
| `country` | `string` | ISO 3166 country code the organization is registered in. | `AU` |
| `asn` | `integer` | Autonomous System Number originating the range; empty where no AS announces it. | `13335` |
| `as_name` | `string` | Name of the organization that operates the ASN. | `Cloudflare, Inc.` |
| `as_domain` | `string` | The ASN operator's own registrable domain. | `cloudflare.com` |
| `as_type` | `string` | Kind of network the ASN runs. Values are listed below. | `hosting` |

## The full database

The full database needs a license: [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=IP+Company+Database+evaluation&products=IP+Company+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-company) to test the whole file first. With a licensed API key:

```bash
curl -L -o ip_company_v1.csv.gz 'https://internetdata.io/api/v2/database/download?id=ip_company_v1&format=csvgz&apikey=$APIKEY'
curl -L -o ip_company_v1.mmdb 'https://internetdata.io/api/v2/database/download?id=ip_company_v1&format=mmdb&apikey=$APIKEY'
```

Today's sample is on [its page](https://internetdata.io/databases/ip-company?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ip-company), cut from the latest build.

Back to [all InternetData sample databases](../).
