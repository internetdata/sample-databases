# Disposable Domain

Every domain whose email addresses are disposable, rated high, medium or low, with the first and last day we saw it in use and the providers behind it, one domain per row.

| Field | Value |
| --- | --- |
| ID | `disposable_domain_v1` |
| Formats | `csvgz` |
| Update frequency | Daily |
| Full database | 33,423 entries, 390 KB as CSV, on 2026-11-24 |
| This sample | 100 rows from the 2026-11-24 build |
| License | This sample: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). The full database: licensed per database, [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=Disposable+Domain+Database+evaluation&products=Disposable+Domain+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=disposable-domain) |
| Docs | [docs.internetdata.io/database/disposable-domain/disposable-domain](https://docs.internetdata.io/database/disposable-domain/disposable-domain?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=disposable-domain) |

## Files

- [`disposable_domain_v1.sample.csv`](disposable_domain_v1.sample.csv): the rows as plain CSV, which GitHub shows as a table
- [`disposable_domain_v1.sample.csv.gz`](disposable_domain_v1.sample.csv.gz): the same rows gzipped, as the full database ships

## Overview

Every domain whose email addresses are disposable, because a disposable email provider gives them out or takes the mail sent there: the temporary inboxes people use once, to get past a signup without their own address. One row per domain, lowercase, internationalized names in punycode (`xn--`).

`confidence` is how sure we are. `high` is a domain we're certain of, the one to block an address on; `medium` is very likely, on indirect evidence; `low` is weak evidence, not enough to block on alone.

`first_seen` and `last_seen` are the first and most recent days we saw a disposable email provider use the domain, not when it was registered. A domain last seen long ago may have gone out of use.

`providers` lists the providers behind the domain, pipe-joined, since providers share domains. Each is an `id` in [Disposable Domain Provider](https://docs.internetdata.io/database/disposable-domain/disposable-domain-provider?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=disposable-domain), which gives the provider's name and website.

Some providers give each inbox a random subdomain of a domain they control, and each of those is its own row.

## Fields

### CSV (`csvgz`)

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `domain` | `string` | A domain whose email addresses are disposable: a disposable email provider gives them out or receives their mail. Lowercase, internationalized names in punycode (xn--). | `0-mail.com` |
| `first_seen` | `date` | The first day we saw this domain in use by a disposable email provider. | `2024-03-11` |
| `last_seen` | `date` | The most recent day we saw this domain in use by a disposable email provider. | `2026-11-24` |
| `providers` | `string` | Pipe-joined IDs of the providers behind it (e.g. "mail_tm\|temp_mail_org"), each an ID in the disposable_domain_provider_v1 dataset. | `rotvpn_com\|torvpn_com` |
| `confidence` | `string` | How sure we are that addresses at this domain are disposable: high (certain), medium (very likely, on indirect evidence) or low (weak evidence, not enough to block an address on alone). | `low` |

## The full database

The full database needs a license: [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=Disposable+Domain+Database+evaluation&products=Disposable+Domain+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=disposable-domain) to test the whole file first. With a licensed API key:

```bash
curl -L -o disposable_domain_v1.csv.gz "https://internetdata.io/api/v2/database/download?id=disposable_domain_v1&format=csvgz&apikey=$APIKEY"
```

Today's sample is on [its page](https://internetdata.io/databases/disposable-domain?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=disposable-domain), cut from the latest build.

Back to [all InternetData sample databases](../).
