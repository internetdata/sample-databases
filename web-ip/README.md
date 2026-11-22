# Web IP

Every host that answered a TLS handshake or HTTP request on TCP port 443 or 80, with the TLS certificate, JA3S, HTTP Server header, status, redirect, cookie names and page title.

| Field | Value |
| --- | --- |
| ID | `web_ip_v1` |
| Formats | `csvgz` |
| Update frequency | Weekly |
| Full database | 92,297,405 entries, 3.96 GB as CSV, on 2026-11-21 |
| This sample | 100 rows from the 2026-11-21 build |
| License | This sample: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). The full database: licensed per database, [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=Web+IP+Database+evaluation&products=Web+IP+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=web-ip) |
| Docs | [docs.internetdata.io/database/web-ip](https://docs.internetdata.io/database/web-ip?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=web-ip) |

## Files

- [`web_ip_v1.sample.csv`](web_ip_v1.sample.csv): the rows as plain CSV, which GitHub shows as a table
- [`web_ip_v1.sample.csv.gz`](web_ip_v1.sample.csv.gz): the same rows gzipped, as the full database ships

## Overview

Every host that answered a TLS handshake or an HTTP request on TCP port 443 or 80 in the last 30 days, with the TLS certificate (issuer, subject, SAN, validity, SHA256 fingerprint, self-signed and browser-trusted flags), the JA3S of the TLS ServerHello, the negotiated TLS version, cipher and HTTP version, and the HTTP Server header, status, redirect Location, Set-Cookie names and page title. A port that was open but never answered isn't in the file. The TLS columns are empty on port 80, which is plain HTTP, and the HTTP columns are empty for a 443 host that completed TLS but sent no HTTP response.

## Fields

### CSV (`csvgz`)

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| `ip` | `ipaddress` | The IP address, IPv4 or IPv6, that answered on TCP port 443 or 80. | `1.0.0.0` |
| `port` | `integer` | The TCP port captured (443 or 80). | `80` |
| `tls_ok` | `boolean` | 1 if a TLS handshake completed (443); empty on 80, which is plain HTTP. | `1` |
| `session_ok` | `boolean` | 1 if an HTTP response was read; empty for a 443 host that completed TLS but sent no HTTP response. | `1` |
| `status_code` | `integer` | The HTTP status code of the first response (redirects not followed). | `403` |
| `server` | `string` | The HTTP Server response header. | `cloudflare` |
| `location` | `string` | The redirect Location header of the first response, if any. | `http://13.53.89.163/login` |
| `title` | `string` | The HTML <title> of the response body, if any. | `Equity Chain` |
| `set_cookie_names` | `string` | Space-separated names of the cookies the response set (names only, never values). | `XSRF-TOKEN laravel_session` |
| `cert_subject_cn` | `string` | The TLS leaf certificate subject common name. | `*.cctglobal.org` |
| `cert_subject_o` | `string` | The TLS leaf certificate subject organization. | `IBS Software Private Limited` |
| `cert_issuer_dn` | `string` | The TLS leaf certificate issuer distinguished name. | `C=US, O=Amazon, CN=Amazon RSA 2048 M04` |
| `cert_sans` | `string` | Space-separated subject alternative names on the TLS leaf certificate. | `*.cctglobal.org` |
| `cert_not_before` | `date` | The TLS leaf certificate validity start date. | `2026-07-17` |
| `cert_not_after` | `date` | The TLS leaf certificate validity end date. | `2027-01-30` |
| `cert_fp_sha256` | `string` | The SHA256 fingerprint of the TLS leaf certificate. | `98e882867dc1566c6681cdf99afb86ad20327411...` |
| `cert_self_signed` | `boolean` | 1 if the TLS leaf certificate subject equals its issuer (self-signed). | `1` |
| `cert_browser_trusted` | `boolean` | 1 if the TLS certificate chain validates to a browser-trusted root. | `1` |
| `ja3s` | `string` | The JA3S fingerprint of the TLS ServerHello. | `f4febc55ea12b31ae17cfb7e614afda8` |
| `tls_version` | `string` | The negotiated TLS version (e.g. TLSv1.3). | `TLSv1.3` |
| `tls_cipher` | `string` | The negotiated TLS cipher suite (e.g. TLS_AES_128_GCM_SHA256). | `TLS_AES_128_GCM_SHA256` |
| `http_version` | `string` | The negotiated HTTP version (e.g. HTTP/2.0, HTTP/1.1); on 443 this reflects the ALPN outcome. | `HTTP/1.1` |
| `first_seen` | `date` | The first day in the 90-day window the port was observed open. | `2026-08-29` |
| `last_seen` | `date` | The most recent day the port was observed open. | `2026-11-12` |

## The full database

The full database needs a license: [request an evaluation](https://internetdata.io/contact?purpose=evaluation&subject=Web+IP+Database+evaluation&products=Web+IP+Database&utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=web-ip) to test the whole file first. With a licensed API key:

```bash
curl -L -o web_ip_v1.csv.gz "https://internetdata.io/api/v2/database/download?id=web_ip_v1&format=csvgz&apikey=$APIKEY"
```

Today's sample is on [its page](https://internetdata.io/databases/web-ip?utm_source=github&utm_medium=referral&utm_campaign=sample-databases&utm_content=web-ip), cut from the latest build.

Back to [all InternetData sample databases](../).
