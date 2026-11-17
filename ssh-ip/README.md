# SSH IP

Every host that completed an SSH handshake on TCP port 22, with its server banner and host-key fingerprint.

| Field | Value |
| --- | --- |
| ID | `ssh_ip_v1` |
| Formats | `csvgz` |
| Update frequency | Weekly |
| Full database | 24,056,065 entries, 934 MB as CSV, on 2026-11-14 |
| This sample | 100 rows from the 2026-11-14 build |
| License | This sample: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). The full database: licensed per database, [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=SSH+IP+Database+evaluation&products=SSH+IP+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ssh-ip) |
| Docs | [docs.internetdata.io/database/ssh-ip](https://docs.internetdata.io/database/ssh-ip?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ssh-ip) |

## Files

- [`ssh_ip_v1.sample.csv`](ssh_ip_v1.sample.csv): the rows as plain CSV, which GitHub shows as a table
- [`ssh_ip_v1.sample.csv.gz`](ssh_ip_v1.sample.csv.gz): the same rows gzipped, as the full database ships

## Overview

Every host that completed an SSH handshake on TCP port 22, with the server banner it announced and its host-key fingerprint. A port that was open but never answered isn't in the file, so `session_ok` is 1 on every row. `first_seen` and `last_seen` are the first and last days in the 90-day window the port was seen open.

## Fields

### CSV (`csvgz`)

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `ip` | `ipaddress` | The IP address, IPv4 or IPv6, that completed an SSH handshake on TCP port 22. | `1.0.16.9` |
| `port` | `integer` | The TCP port scanned (22). | `22` |
| `banner` | `string` | The SSH server identification string the host returned (e.g. SSH-2.0-OpenSSH_9.2p1). | `SSH-1.99-Cisco-1.25` |
| `host_key_fp` | `string` | The SHA256 fingerprint of the host's SSH public key. | `SHA256:734b42a33ad07d6a2f0fc73798d5cd77f...` |
| `session_ok` | `boolean` | Always 1: every row is a host that completed the handshake. A port that was open but silent is not shipped. | `1` |
| `first_seen` | `date` | The first day in the 90-day window the port was observed open. | `2026-08-20` |
| `last_seen` | `date` | The most recent day the port was observed open. | `2026-11-06` |

## The full database

The full database needs a license: [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=SSH+IP+Database+evaluation&products=SSH+IP+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ssh-ip) to test the whole file first. With a licensed API key:

```bash
curl -L -o ssh_ip_v1.csv.gz 'https://internetdata.io/api/v2/database/download?id=ssh_ip_v1&format=csvgz&apikey=$APIKEY'
```

Today's sample is on [its page](https://internetdata.io/databases/ssh-ip?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=ssh-ip), cut from the latest build.

Back to [all InternetData sample databases](../).
