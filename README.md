# tia-ThreatReportSummarizer
A command-line tool that takes a URL or local path to a text based threat intelligence report and generates a summary highlighting key IOCs, MITRE ATT&CK techniques, and affected systems. The summary includes an extractive summary made of the highest scoring sentences (scored by word frequency), a keyword list from word frequency, and an affected systems field when the report states one. Summarization runs locally; report text is not sent to any other service. The only network call is fetching the report URL the operator supplies, with a 10 second timeout. PDF input is not supported and is rejected with a non-zero exit. If saving the summary fails, the summary is printed to standard output and the run exits non-zero.

## Install
`git clone https://github.com/ShadowGuard-AI/tia-threatreportsummarizer.git`

## Usage
`python3 main.py <source> [--output <path>] [--format text|json]`

IOCs and MITRE ATT&CK techniques are deduplicated in first-mention order, so repeated runs on the same report produce identical output. Technique IDs must appear as whole tokens, and hashes must be hex strings of exactly 32, 40, 64, or 128 characters, in either case.

## Parameters
- `-h`: Show help message and exit
- `source`: URL or local path to the threat intelligence report
- `--output`: Path to save the summary. If not provided, prints to standard output.
- `--format`: Output format: text (default) or json.

## License
MIT License. See LICENSE.
