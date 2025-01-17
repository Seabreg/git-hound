# Git Hound

A pattern-matching, batch-catching secret snatcher.
**This project is intended to be used for educational purposes.**

![Git Hound](assets/logo.png)

Git Hound makes it easy to find exposed APi keys on GitHub using pattern matching, targetted querying, and a scoring system. This differs from other OSINT GitHub scanners by searching keywords across GitHub rather than targetting specific repositories, exposing a fundamentally different set of results. [GitRob](https://github.com/michenriksen/gitrob) is an excellent tool that specifically targets an organization or user's owned repositories for secrets.

## Usage

`echo "tillsongalloway.com" | python git-hound.py` or `python git-hound.py --subdomain-file subdomains.txt`
We also offer a number of flags to target specific patterns (known service API keys), file names (.htpasswd, .env), and languages (python, javascript).

### Flags

* `--subdomain-file` - The file with the subdomains
* `--output` - The output file (default is stdout)
* `--output-type` - The output type (requires output flag to be set; default is flatfile)
* `--all` - Print all URLs, including ones with no pattern match. Otherwise, the scoring system will do the work.
* `--regex-file` - Supply a custom regex file
* `--api-keys` - Enable generic API key searching. This uses common API key patterns and Shannon entropy to find potential exposed API keys.
* `--language-file` - Supply a custom file with languages to search.
* `--config-file` - Custom config file (default is `config.yml`)
* `--pages` - Max pages to search (default is 100, the page maximum)
* `--silent` - Don't print results to stdout (most reasonably used with --output).
* `--no-antikeywords` - Don't attempt to filter out known mass scans
* `--only-filtered` - Only search filtered queries (languages, file extensions)
* `--debug` - Print debug messages. Helpful for debugging slow expressions.

## Setup

1. Clone this repo
2. Use a Python 3 environment (recommended: virtulenv or [Conda](https://docs.conda.io/en/latest/))
3. `pip install -r requirements.txt` (or `pip3`)
4. Set up a `config.yml` file with GitHub credentials. See [config.example.yml](config.example.yml) for an example. Accounts with 2FA are not currently supported.
5. `echo "tillsongalloway.com" | python git-hound.py`
