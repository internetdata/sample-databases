# Domain IP Ranges

Every IP range an organization owns or uses, keyed by its domain, with the name and country registered for each range, one CIDR per row.

| Field | Value |
| --- | --- |
| ID | `domain_ip_ranges_v1` |
| Formats | `csvgz` |
| Update frequency | Daily |
| Full database | 8,275,394 entries, 49.0 MB as CSV, on 2026-11-17 |
| This sample | 100 rows from the 2026-11-17 build |
| License | This sample: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). The full database: licensed per database, [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=Domain+IP+Ranges+Database+evaluation&products=Domain+IP+Ranges+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=domain-ip-ranges) |
| Docs | [docs.internetdata.io/database/domain-ip-ranges/domain-ip-ranges](https://docs.internetdata.io/database/domain-ip-ranges/domain-ip-ranges?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=domain-ip-ranges) |

## Files

- [`domain_ip_ranges_v1.sample.csv`](domain_ip_ranges_v1.sample.csv): the rows as plain CSV, which GitHub shows as a table
- [`domain_ip_ranges_v1.sample.csv.gz`](domain_ip_ranges_v1.sample.csv.gz): the same rows gzipped, as the full database ships

## Overview

Every IPv4 and IPv6 range an organization owns or uses, one row per CIDR, keyed by the organization's own domain. `name` and `country` are what's registered for the range: the company itself, or one of its subsidiaries or offices under its own name. So `nytimes.com` lists The New York Times Company's own allocation beside the small blocks its ISPs assigned to it.

Each range belongs to one company, and no address is in two rows. A large ISP's own space comes in thousands of pieces, because every block it assigned to a customer is that customer's row, not the ISP's.

Adjacent ranges of one company merge where the name and country match, and a range whose ends don't fall on one prefix boundary is split into the fewest CIDRs that cover it exactly.

To look a company up by another of its domains, read [Domain IP Ranges Alias](https://docs.internetdata.io/database/domain-ip-ranges/domain-ip-ranges-alias?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=domain-ip-ranges) first. It maps a domain whose home page redirects to a company's own, such as `times.com`, to the domain this file is keyed by.

## Fields

### CSV (`csvgz`)

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `range` | `string` | An IPv4 or IPv6 range the organization behind the domain owns or uses, as a CIDR. | `199.242.132.0/24` |
| `domain` | `string` | The organization's own registrable domain, lowercase, shared by every row of its ranges. Internationalized names in punycode (xn--). | `0-1.com` |
| `name` | `string` | Name of the organization registered as using the range: the company itself, or one of its subsidiaries or offices. | `Zero & One Engineering, Inc.` |
| `country` | `string` | ISO 3166 country code the organization using the range is registered in; empty where none is known. | `US` |

## The full database

The full database needs a license: [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=Domain+IP+Ranges+Database+evaluation&products=Domain+IP+Ranges+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=domain-ip-ranges) to test the whole file first. With a licensed API key:

```bash
curl -L -o domain_ip_ranges_v1.csv.gz 'https://internetdata.io/api/v2/database/download?id=domain_ip_ranges_v1&format=csvgz&apikey=$APIKEY'
```

Today's sample is on [its page](https://internetdata.io/databases/domain-ip-ranges?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=domain-ip-ranges), cut from the latest build.

Back to [all InternetData sample databases](../).
