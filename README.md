# Taiwan Blocked Domains

A list of scam and fraudulent website domains reported to **TWNIC** (Taiwan Network Information Center), for which DNS resolution was subsequently stopped. The data is intended for use in blocklists such as DNS filters, ad blockers, firewalls, and browser extensions.

- **Records:** 1,734 domains
- **Reports received:** 2023-06-29 to 2026-10-08
- **Source:** TWNIC scam URL report summary (通報TWNIC詐騙網址彙整表), dated 2026-10-08

## Files

| File | Description |
|---|---|
| `blocked_domains.txt` | Plain-text domain list, one domain per line, sorted alphabetically |
| `taiwan_blocked_domains.json` | Full records with details, translated into English |

## Usage

### Plain-text list

`blocked_domains.txt` contains one domain per line with no comments or extra formatting, so it can be imported into most tools directly.

```
01.wen.ooguy.com
0zkoahs.shop
101shop.tw
...
```

Example: convert to a hosts file format (`0.0.0.0 domain`):

```bash
sed 's/^/0.0.0.0 /' blocked_domains.txt > hosts.txt
```

Example: check a domain against the list:

```bash
grep -Fxq "example.com" blocked_domains.txt && echo "blocked"
```

### JSON data

Each record in the JSON file looks like this:

```json
{
  "id": "1",
  "one_page_digital_economy_scam_site": "Links to PChome 24H shopping website homepage",
  "fake_url": "https://tobuyersepc24.com/57vgaqk#/login",
  "domain_name": "tobuyersepc24.com",
  "scam_site_creation_date": "2023-06-28T11:07:03",
  "report_received_date": "20230629",
  "dns_resolution_stopped_date": "20230629"
}
```

| Field | Description |
|---|---|
| `id` | Record number in the original report |
| `one_page_digital_economy_scam_site` | Description of the scam (what it impersonates or how it works) |
| `fake_url` | The reported fraudulent URL |
| `domain_name` | The domain name of the fraudulent site |
| `scam_site_creation_date` | When the scam site was created (ISO 8601) |
| `report_received_date` | Date the report was received (`YYYYMMDD`) |
| `dns_resolution_stopped_date` | Date DNS resolution was stopped (`YYYYMMDD`) |

## Notes

- Descriptions were translated from Traditional Chinese. Where no official English name was available for a company, a transliteration is given with the original Chinese name in parentheses. Items marked `[sic]` reflect typos in the original report.
- Some creation dates in the source data may be inaccurate (for example, domains that were later re-registered), so treat them as informational only.
- Some entries are subdomains (for example `01.wen.ooguy.com`). Check how your tool handles subdomain matching before importing.
- Domains may be re-registered or reused by new owners after being taken down. Review the list periodically and remove entries that are no longer relevant.

## Disclaimer

This project is not affiliated with or endorsed by TWNIC. The data is provided as-is, without warranty. If you believe a domain was listed in error, please open an issue.
