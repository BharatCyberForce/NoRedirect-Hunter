# No Redirect Hunter

> Massive level No redirect bug hunt

## Features

* Multi-threaded scanning of a fixed list of common admin/management paths.
* Detects status codes (200, 3xx, 4xx, 5xx) and highlights responses containing configured keywords (`dashboard`, `logout`).
* Save discovered host+path entries to a text file.
* Simple CLI with options for threads, timeout, and following redirects.

## Requirements

* Python 3.8+
* The script depends on:

  * `requests`
  * `colorama`

Install dependencies with pip:

```bash
pip install requests colorama
```

## Files

* `noredirecthunter.py` — main script (the code you provided).
* `README.md` — this file.

(Replace `no-red.py` with the actual filename you use.)

## Usage

```
usage: no-red.py [-h] (-u URL | -f FILE) [--follow-redirects]
                           [-o OUTPUT] [--timeout TIMEOUT] [-t THREADS]

No Redirect Hunter

optional arguments:
  -h, --help            show this help message and exit
  -u, --url URL         single target URL (http://target.pk)
  -f, --file FILE       file with one target URL per line
  --follow-redirects    allow following redirects
  -o, --output OUTPUT   write discovered host+path entries to a text file
  --timeout TIMEOUT     request timeout in seconds (default: 6)
  -t, --threads THREADS number of concurrent worker threads (default: 12)
```

### Examples

Scan a single URL:

```bash
python noredirecthunter.py -u https://example.com
```

Scan a list of targets from `targets.txt`:

```bash
python noredirecthunter.py -f targets.txt -t 20 --timeout 8 -o found_paths.txt
```

Scan and follow redirects:

```bash
python noredirecthunter.py -u target.pk --follow-redirects -o saved.txt
```

### output

```
http://example.com/admin/dashboard.php (200) · keyword matched:dashboard
http://example.com/admin/index.php (404)
http://example.com/wp-admin/ (301)
saved: found_paths.txt (2)
```

Saved output format (`found_paths.txt`) — each discovered entry is saved as:

```
example.com/admin/dashboard.php
another.example.com/wp-admin
```
## Ethical & legal notice

This tool actively probes web servers. Only run scans against systems that you own or have explicit permission to test. Unauthorized scanning can be considered intrusive and may be illegal in many jurisdictions. Use responsibly.
