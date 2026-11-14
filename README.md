# Blocklists

A collection of plain-text network blocklists for use in firewall rules, DNS
sinkholes, and traffic-filtering policies. Each file holds one type of indicator
(IP address or domain name), one per line, intended to be pulled directly into
security tooling.

## Format

- One indicator per line: an IPv4 address or a fully-qualified domain name.
- Blank lines and lines beginning with `#` are comments and should be ignored by
  consumers.
- Lists are refreshed on a regular automated schedule. Pull the raw URLs to stay
  current rather than copying the contents.

## Lists

| File | Type | Description |
|------|------|-------------|
| `CISA-IP.txt`     | IP     | Malicious IP addresses referenced in public cybersecurity advisories and threat bulletins. |
| `CISA-FQDN.txt`   | Domain | Malicious or suspicious domains referenced in public cybersecurity advisories and threat bulletins. |
| `OSINT-IP.txt`    | IP     | Suspicious and malicious IP addresses aggregated from open-source threat-intelligence feeds. |
| `TOR-IP.txt`      | IP     | Tor network relay and exit-node addresses, for environments that restrict anonymized traffic. |
| `VPN-IP.txt`      | IP     | IP addresses observed making unauthorized or suspicious VPN and remote-access login attempts. |
| `AI-FQDN.txt`     | Domain | Domains for public generative-AI and large-language-model services, for environments that restrict their use. |
| `Urgent-IP.txt`   | IP     | Rapid-response, temporary indicators tied to active or emerging threats. Short-lived; reviewed and pruned regularly. |
| `Urgent-FQDN.txt` | Domain | Rapid-response, temporary domain indicators tied to active or emerging threats. Short-lived; reviewed and pruned regularly. |

## Usage

Point a firewall, DNS filter, or threat-feed importer at the raw file URL, for example:

```
https://raw.githubusercontent.com/TuckerNET/BLOCKLISTS/main/CISA-IP.txt
```

Most consumers (pi-hole, pfSense / OPNsense, and common feed importers) strip
`#` comment lines automatically.

## Notes

- Provided as-is, with no warranty of accuracy or completeness.
- Aggregated and automated feeds can contain false positives. Validate indicators
  against your own environment before enforcing a block, especially for the VPN,
  Tor, and AI lists, which describe categories of traffic rather than confirmed
  malicious activity.
- Collection sources and methods are intentionally left unspecified.
- Use at your own risk.
