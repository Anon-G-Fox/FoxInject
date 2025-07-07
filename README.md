FoxInject
FoxInject is a security testing tool designed to identify web vulnerabilities such as SQL Injection, Cross-Site Scripting (XSS), Local/Remote File Inclusion (LFI/RFI), and Command Injection. It supports Linux systems (32-bit and 64-bit) and provides both command-line and (optional) API-based operation.
⚠️ Legal Disclaimer: This tool is intended for educational purposes and authorized security testing only. Unauthorized use against systems without explicit permission is illegal and prohibited. The developers are not responsible for any misuse or damage caused by this tool.
Features

Test for multiple web vulnerabilities: SQL Injection, XSS, LFI/RFI, and Command Injection.
Search for potentially vulnerable websites in the co.il domain (requires Google API keys).
Supports anonymous scanning via Tor.
Optional nmap integration for port and service scanning.
Generate reports in JSON or HTML formats.
Pre-built binaries for Linux (32-bit and 64-bit).

Download
Pre-built binaries are available for Linux:

64-bit Linux: FoxInject_amd64
32-bit Linux: FoxInject_386

Note: Replace <your-username> and <your-repo> with your GitHub username and repository name after creating the release.
Installation

Download the Binary:
For 64-bit Linux:wget https://github.com/<your-username>/<your-repo>/releases/download/v1.0.0/FoxInject_amd64 -O FoxInject


For 32-bit Linux:wget https://github.com/<your-username>/<your-repo>/releases/download/v1.0.0/FoxInject_386 -O FoxInject




Make the Binary Executable:chmod +x FoxInject


Install Dependencies (if using specific features):
sqlmap (required for --sql-mode sqlmap or --sql-mode both):sudo apt-get install sqlmap

Or clone from: https://github.com/sqlmapproject/sqlmap.git
Tor (required for --tor):sudo apt-get install tor
service tor start


nmap (required for --nmap):sudo apt-get install nmap




Configure Google API (required for --search):
Create a config.yaml file in the same directory as the binary:google_api_key: "YOUR_GOOGLE_API_KEY"
google_cse_id: "YOUR_GOOGLE_CSE_ID"


Obtain keys from Google Cloud Console and set up a Custom Search Engine.



Usage
Run the tool with the following command:
./FoxInject [options]

Options



Option
Description



--target <url>
Target URL to scan (e.g., https://example.com/page.php?id=1). Required unless --search is used.


--scan <type>
Scan type: sql, xss, lfi, cmd, or full. Default: sql.


--search <domain>
Search for vulnerable sites in the co.il domain only. Cannot be used with --target.


--search-keyword <keyword>
Refine search with a keyword (e.g., login, admin). Default: none.


--search-max <number>
Maximum number of search results to scan. Default: 10.


--report <format>
Report format: json or html. Default: json.


--tor
Enable Tor for anonymous scanning (requires Tor service).


--tor-bridge <bridge>
Custom Tor bridge address (e.g., 127.0.0.1:9051). Default: none.


--nmap
Run nmap scan before attacking. Output included in the report.


--sql-mode <mode>
SQL Injection mode: internal, sqlmap, or both. Default: internal.


--help
Display the help message and exit.


Examples
# Test a target for SQL Injection with both sqlmap and internal engine using Tor
./FoxInject --target https://example.com/page.php?id=1 --scan sql --sql-mode both --tor

# Search for vulnerable co.il sites with keyword "login" and generate an HTML report
./FoxInject --search co.il --search-keyword login --search-max 20 --report html

# Perform a full scan with nmap
./FoxInject --target https://example.com --scan full --nmap

# Use a custom Tor bridge
./FoxInject --target https://example.com --scan sql --tor --tor-bridge 127.0.0.1:9051

# Search co.il sites with nmap and JSON report
./FoxInject --search co.il --search-keyword admin --search-max 10 --nmap --report json

Troubleshooting

sqlmap errors: Run sqlmap --version to verify installation. Install via sudo apt-get install sqlmap.
Tor connection issues: Check Tor status with service tor status. Ensure the bridge address is correct.
Database errors: Verify that attack_history.db is writable and not corrupted.
Google API errors: Ensure config.yaml contains valid google_api_key and google_cse_id.
Timeout issues: Check network stability or adjust HTTP client timeout in the tool's configuration.

Notes

The --search option is currently limited to co.il domains.
Logs are saved to attack_log_<timestamp>.txt, and results are stored in attack_history.db.
Use this tool responsibly and only with explicit permission from the target owner.
For API usage (if enabled), the server runs on localhost:9932. Test with:curl -X POST http://localhost:9932/hack -H "Content-Type: application/json" -d '{"target":"https://example.com","scanType":"sql","sqlMode":"internal","useNmap":false,"injectionType":""}'



License
This project is licensed under the MIT License. See the LICENSE file for details.
Contact
For inquiries, contact Anonymous-Islamic.
