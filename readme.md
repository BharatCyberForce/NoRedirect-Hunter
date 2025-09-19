# No Redirect Hunter

> Massive level No redirect bug hunt

## Features

* Multi-threaded scanning of list of common admin/management paths.
* Detects status codes (200, 3xx, 4xx).
* Save host+path entries in text file.
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

## Usage

```
usage: no-red.py [-h] (-u URL | -f FILE) [--follow-redirects]
                           [-o OUTPUT] [--timeout TIMEOUT] [-t THREADS]

|No Redirect Hunter|

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
python no-red.py -u https://target.pk
```

Scan a list of targets from `targets.txt`:

```bash
python no-red.py -f targets.txt -t 20 --timeout 8 -o found_paths.txt
```

Scan and follow redirects:

```bash
python no-red.py -u target.pk --follow-redirects -o saved.txt
```

### output

```
http://target.pk/admin/dashboard.php (200) · keyword matched:dashboard
http://target.pk/admin/index.php (404)
http://target.pk/wp-admin/ (301)
saved: saved.txt (2)
```
## Ethical & legal notice

This tool actively probes web servers. Only run scans against systems that you own or have explicit permission to test. Unauthorized scanning can be considered intrusive and may be illegal. Use responsibly.
