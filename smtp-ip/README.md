# SMTP IP

Every host that returned an SMTP greeting on TCP port 587, with the greeting banner.

| Field | Value |
| --- | --- |
| ID | `smtp_ip_v1` |
| Formats | `csvgz` |
| Update frequency | Weekly |
| Full database | 3,265,950 entries, 50.7 MB as CSV, on 2026-11-14 |
| This sample | 100 rows from the 2026-11-14 build |
| License | This sample: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). The full database: licensed per database, [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=SMTP+IP+Database+evaluation&products=SMTP+IP+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=smtp-ip) |
| Docs | [docs.internetdata.io/database/smtp-ip](https://docs.internetdata.io/database/smtp-ip?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=smtp-ip) |

## Files

- [`smtp_ip_v1.sample.csv`](smtp_ip_v1.sample.csv): the rows as plain CSV, which GitHub shows as a table
- [`smtp_ip_v1.sample.csv.gz`](smtp_ip_v1.sample.csv.gz): the same rows gzipped, as the full database ships

## Overview

Every host that returned an SMTP greeting on TCP port 587, with the greeting it sent, line breaks collapsed to spaces. A port that was open but never greeted isn't in the file, so `session_ok` is 1 on every row. `first_seen` and `last_seen` are the first and last days in the 90-day window the port was seen open.

## Fields

### CSV (`csvgz`)

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `ip` | `ipaddress` | The IP address, IPv4 or IPv6, that returned an SMTP greeting on TCP port 587. | `1.0.72.22` |
| `port` | `integer` | The TCP port scanned (587, SMTP submission). | `587` |
| `banner` | `string` | The SMTP greeting (220 line) the host returned, with any line breaks collapsed to spaces. | `220 zakix.com ESMTP` |
| `session_ok` | `boolean` | Always 1: every row is a host that returned a greeting. A port that was open but silent is not shipped. | `1` |
| `first_seen` | `date` | The first day in the 90-day window the port was observed open. | `2026-09-01` |
| `last_seen` | `date` | The most recent day the port was observed open. | `2026-09-08` |

## The full database

The full database needs a license: [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=SMTP+IP+Database+evaluation&products=SMTP+IP+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=smtp-ip) to test the whole file first. With a licensed API key:

```bash
curl -L -o smtp_ip_v1.csv.gz 'https://internetdata.io/api/v2/database/download?id=smtp_ip_v1&format=csvgz&apikey=$APIKEY'
```

Today's sample is on [its page](https://internetdata.io/databases/smtp-ip?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=smtp-ip), cut from the latest build.

Back to [all InternetData sample databases](../).
