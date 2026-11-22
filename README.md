# [<img src="https://s3.internetdata.io/internetdata-public/brand/mark.svg" alt="InternetData" height="28"/>](https://internetdata.io/?utm_source=github&utm_medium=referral&utm_campaign=sample-databases) InternetData Sample Databases

100 real rows of every InternetData database that has a sample, in the formats the full databases ship in, with every field documented. Each sample is cut from that database's own build, so its rows, columns and quoting are the full file's.

## Databases

### Anonymity

| Database | What it holds | Formats | Updated |
| --- | --- | --- | --- |
| [VPN IP](vpn-ip/) | IPs operated as commercial VPN exit infrastructure. | CSV, MMDB | Daily |
| [VPN IP Extended](vpn-ip-extended/) | VPN IP with the evidence behind every range. | CSV, MMDB | Daily |
| [Hosting IP](hosting-ip/) | IPs owned and operated by hosting and cloud providers. | CSV, MMDB | Daily |
| [Tor IP](tor-ip/) (Open) | Currently-active Tor node IPs. | CSV, MMDB | Daily |
| [Relay IP](relay-ip/) (Open) | IPs of privacy relays and enterprise web gateways. | CSV, MMDB | Daily |
| [Datacenter Proxy IP 1d](dcproxy-ip-1d/) | Datacenter-hosted proxy IPs seen in the last 24 hours, with provider attribution. | CSV, MMDB | Daily |
| [Datacenter Proxy IP 7d](dcproxy-ip-7d/) | Datacenter-hosted proxy IPs seen in the last 7 days, with provider attribution. | CSV, MMDB | Daily |
| [Datacenter Proxy IP 14d](dcproxy-ip-14d/) | Datacenter-hosted proxy IPs seen in the last 14 days, with provider attribution. | CSV, MMDB | Daily |
| [Datacenter Proxy IP 30d](dcproxy-ip-30d/) | Datacenter-hosted proxy IPs seen in the last 30 days, with provider attribution. | CSV, MMDB | Daily |
| [Datacenter Proxy IP 60d](dcproxy-ip-60d/) | Datacenter-hosted proxy IPs seen in the last 60 days, with provider attribution. | CSV, MMDB | Daily |
| [Datacenter Proxy IP 90d](dcproxy-ip-90d/) | Datacenter-hosted proxy IPs seen in the last 90 days, with provider attribution. | CSV, MMDB | Daily |
| [Public Proxy IP 1d](pubproxy-ip-1d/) | Addresses where public proxies listened or their traffic exited in the last 24 hours, each flagged entry, exit or both. | CSV, MMDB | Daily |
| [Public Proxy IP 7d](pubproxy-ip-7d/) | Addresses where public proxies listened or their traffic exited in the last 7 days, each flagged entry, exit or both. | CSV, MMDB | Daily |
| [Public Proxy IP 14d](pubproxy-ip-14d/) | Addresses where public proxies listened or their traffic exited in the last 14 days, each flagged entry, exit or both. | CSV, MMDB | Daily |
| [Public Proxy IP 30d](pubproxy-ip-30d/) | Addresses where public proxies listened or their traffic exited in the last 30 days, each flagged entry, exit or both. | CSV, MMDB | Daily |
| [Public Proxy IP 60d](pubproxy-ip-60d/) | Addresses where public proxies listened or their traffic exited in the last 60 days, each flagged entry, exit or both. | CSV, MMDB | Daily |
| [Public Proxy IP 90d](pubproxy-ip-90d/) | Addresses where public proxies listened or their traffic exited in the last 90 days, each flagged entry, exit or both. | CSV, MMDB | Daily |
| [Bot IP](bot-ip/) | IPs bots use, from search and AI crawlers to monitors, scanners and webhook senders, each with its operator, its bots, what they do and whether the operator vouches for the address. | CSV, MMDB | Daily |

### Ownership

| Database | What it holds | Formats | Updated |
| --- | --- | --- | --- |
| [IP Company](ip-company/) | The organization that uses each IP range, with its domain and type, and the AS that announces the range. | CSV, MMDB | Daily |
| [Domain IP Ranges](domain-ip-ranges/) | Every IP range an organization owns or uses, keyed by its domain, with the name and country registered for each range, one CIDR per row. | CSV | Daily |
| [Domain IP Ranges Alias](domain-ip-ranges-alias/) | The domains whose home page redirects to an organization's in Domain IP Ranges, each with the domain to look its ranges up by. | CSV | Daily |
| [IP ASN](ip-asn/) (Open) | Announced IPv4 and IPv6 space mapped to its origin AS, with the holder and RPKI status. | CSV, MMDB | Daily |
| [IP Whois](ip-whois/) | Every network record the registries publish, with its holder, status, contacts and parent network. | CSV, MMDB | Daily |
| [IP RWHOIS](ip-rwhois/) | Reassignments published on network operators' RWHOIS servers, with their holders and contacts. | CSV, MMDB | Weekly |
| [ASN](asn/) (Open) | Every allocated or announced AS number with its holder, domain, network type, announced space and RPKI standing. | CSV | Daily |
| [ASN Extended](asn-extended/) | ASN with each AS number's upstreams, peers and downstreams, its customer cone, its rank and whether it is Tier 1. | CSV | Daily |
| [ASN Whois](asn-whois/) | The registry record of every AS number, with its holder and contacts. | CSV | Daily |
| [IP Abuse Contact](ip-abuse-contact/) | Who takes abuse reports for every address range, with the email, phone and address. | CSV, MMDB | Daily |
| [IP RDNS](ip-rdns/) | The reverse DNS name of every IPv4 and IPv6 address that answers a PTR query. | CSV | Weekly |

### Geolocation

| Database | What it holds | Formats | Updated |
| --- | --- | --- | --- |
| [IP Geolocation](ip-geolocation/) | Every IP range mapped to continent, country, region and city, with the city's coordinates, timezone, postal code and GeoNames ID, an accuracy radius, the date the location last changed, and a US range's DMA code. | CSV, MMDB | Daily |
| [IP Country](ip-country/) (Open) | Every IP range mapped to its continent and country, each as a code and a name, with its timezone and the country's currency and flag. | CSV, MMDB | Daily |
| [IP Timezone](ip-timezone/) (Open) | Every IP range mapped to an IANA timezone, with its country. | CSV, MMDB | Daily |
| [IP Country Flag](ip-country-flag/) (Open) | Every IP range mapped to its country's flag, as an emoji and its Unicode code points. | CSV, MMDB | Daily |
| [IP Country Currency](ip-country-currency/) (Open) | Every IP range mapped to its country's currency: the code, the name and the symbol. | CSV, MMDB | Daily |

### Network

| Database | What it holds | Formats | Updated |
| --- | --- | --- | --- |
| [Carrier IP](carrier-ip/) | Mobile carrier address space, with the operator, its MCC and MNC, and the country. | CSV, MMDB | Daily |
| [Satellite IP](satellite-ip/) | Satellite internet address space, with the operator, its orbit and market, the subscribers' country and a confidence. | CSV, MMDB | Daily |
| [CDN IP](cdn-ip/) | IPs operated by content delivery networks. | CSV, MMDB | Daily |
| [BGP Route](bgp-route/) | Every announced BGP prefix with its origin AS, collector visibility and RPKI status; multi-origin (MOAS) prefixes kept, one row per origin. | CSV | Daily |

### Services

| Database | What it holds | Formats | Updated |
| --- | --- | --- | --- |
| [SSH IP](ssh-ip/) | Every host that completed an SSH handshake on TCP port 22, with its server banner and host-key fingerprint. | CSV | Weekly |
| [SMTP IP](smtp-ip/) | Every host that returned an SMTP greeting on TCP port 587, with the greeting banner. | CSV | Weekly |
| [DNS Resolver IP](dns-resolver-ip/) | Every host answering DNS on UDP port 53, flagged for recursion and whether it is a working open resolver. | CSV | Weekly |
| [Web IP](web-ip/) | Every host that answered a TLS handshake or HTTP request on TCP port 443 or 80, with the TLS certificate, JA3S, HTTP Server header, status, redirect, cookie names and page title. | CSV | Weekly |
| [BitTorrent IP](bittorrent-ip/) | Every address where a BitTorrent client was seen in the last 90 days, flagged verified or not, with how many clients shared it at once and the codes they identify themselves by. | CSV | Daily |

### Domain

| Database | What it holds | Formats | Updated |
| --- | --- | --- | --- |
| [Domain List](domain-list/) | Every registered domain in the generic top-level domains, .com, .net and .org among them, and in .fr, .se, .sk and a few other country codes, with the domains in use under the rest, .de and .uk among them, one name per row. | CSV | Weekly |
| [Domain DNS A](domain-dns-a/) | Each domain's IPv4 addresses from its A records, with CNAMEs followed, one address per row. | CSV | Weekly |
| [Domain DNS AAAA](domain-dns-aaaa/) | Each domain's IPv6 addresses from its AAAA records, with CNAMEs followed, one address per row. | CSV | Weekly |
| [Domain DNS MX](domain-dns-mx/) | Each domain's mail exchangers from its MX records, with their priorities, one record per row. | CSV | Weekly |
| [Domain DNS NS](domain-dns-ns/) | The nameservers each domain is delegated to, one per row. | CSV | Weekly |
| [Domain DNS CNAME](domain-dns-cname/) | Every CNAME record seen on a domain or host name, with the name it points to, one per row. | CSV | Weekly |
| [IP Hosted Domains](ip-hosted-domains/) | Every IP address registered domains resolve to, with how many there are and up to 1,000 of them, the most popular first, one address per row. | CSV | Weekly |
| [Range Hosted Domains](range-hosted-domains/) | Every announced IP range registered domains resolve to, with its AS, how many domains there are and up to 1,000 of them, the most popular first, one range per row. | CSV | Weekly |
| [ASN Hosted Domains](asn-hosted-domains/) | Every AS whose addresses registered domains resolve to, with how many domains there are and up to 1,000 of them, the most popular first, one AS per row. | CSV | Weekly |
| [Disposable Domain](disposable-domain/) | Every domain whose email addresses are disposable, rated high, medium or low, with the first and last day we saw it in use and the providers behind it, one domain per row. | CSV | Daily |

## Reading a sample

The CSV is gzipped, with a header row:

```bash
gunzip -c vpn-ip/vpn_ip_v1.sample.csv.gz | head -3
```

The MMDB opens in any MaxMind DB reader through its generic lookup: a GeoIP2 reader's `city()` or `country()` expects MaxMind's own field layout, which ours doesn't follow. In Python, after `pip install maxminddb`:

```python
import maxminddb

with maxminddb.open_database("vpn-ip/vpn_ip_v1.sample.mmdb") as db:
    print(db.get("1.0.7.231"))
```

Or with our free [`mmdb`](https://github.com/internetdata/mmdb) CLI: `mmdb read 1.0.7.231 vpn-ip/vpn_ip_v1.sample.mmdb`.

Both formats hold every value as text: a number or a date is a string, and an empty field is an empty string. The plain `.csv` beside each sample is the same rows ungzipped, which GitHub shows as a table. `datasets.json` lists every sample with its columns and files, for tooling.

## The full databases

Each folder's README has its database's download command. The Open databases are free under CC BY-SA 4.0 with an InternetData account; the rest are licensed per database, and an [evaluation](https://internetdata.io/contact?purpose=evaluation&subject=Evaluation+license&utm_source=github&utm_medium=referral&utm_campaign=sample-databases) puts a whole one in your hands to test first.

The samples here are refreshed weekly, and at once when a database's columns change. The database pages at [internetdata.io/databases](https://internetdata.io/databases?utm_source=github&utm_medium=referral&utm_campaign=sample-databases) have today's.

## License

The samples are licensed under [CC BY-SA 4.0](LICENSE): credit InternetData with a link to [internetdata.io](https://internetdata.io/?utm_source=github&utm_medium=referral&utm_campaign=sample-databases), and share what you build from them under the same license.

## About InternetData

[<img src="https://s3.internetdata.io/internetdata-public/brand/mark.svg" alt="InternetData" height="64"/>](https://internetdata.io/?utm_source=github&utm_medium=referral&utm_campaign=sample-databases)

Geolocation, anonymity, ownership, network, service and domain data for any IP address, AS or domain, by API or as databases you download.
