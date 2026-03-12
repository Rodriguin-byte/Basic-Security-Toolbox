SECURITY TOOLS SUITE
Version: 3.0
Python: 3.6+
Author: Rodrigo Gomes

LEGAL DISCLAIMER
THIS TOOL IS FOR EDUCATIONAL PURPOSES AND AUTHORIZED SECURITY TESTING ONLY.

UNAUTHORIZED USE OF THIS TOOL ON SYSTEMS YOU DO NOT OWN OR WITHOUT EXPLICIT PERMISSION IS ILLEGAL AND UNETHICAL. THE USER IS SOLELY RESPONSIBLE FOR ENSURING THEY HAVE PERMISSION TO TEST THEIR TARGETS.

TABLE OF CONTENTS
About

Features

Installation

Quick Start Guide

Detailed Tool Documentation

Configuration

Output & Reports

Dependencies

Limitations

Customization

Contributing

License

Resources

Support

ABOUT
The Security Tools Suite is a comprehensive security testing framework written in Python. It combines multiple common web application auditing and reconnaissance tools into a single, menu-driven interface. This project was created as a learning tool to understand various web vulnerabilities and penetration testing techniques.

FEATURES
The suite includes 11 core tools:

Port Scanner - Multi-threaded TCP port scanning with service detection.

Directory Bruteforcer - Discovers hidden directories and files using a wordlist.

Subdomain Enumerator - Finds subdomains via DNS resolution.

XSS Scanner - Tests for Cross-Site Scripting vulnerabilities in forms and URLs.

SQL Injection Tester - Detects SQL injection flaws using error-based and time-based payloads.

Security Headers Analyzer - Checks for the presence of important HTTP security headers.

WAF Detector - Identifies Web Application Firewalls based on headers and cookies.

SSL/TLS Checker - Examines SSL certificates for validity, issuer, and expiration.

Web Crawler - Discovers and maps internal links of a website.

Full Report - Runs all tools sequentially and generates a consolidated JSON report.

Settings - Configure global target, User-Agent, and session cookies.

INSTALLATION
Prerequisites
Python 3.6 or higher

pip (Python package installer)

Steps
Clone the repository

bash
git clone https://github.com/your-username/security-tools-suite.git
cd security-tools-suite
Install dependencies

bash
pip install requests beautifulsoup4 urllib3
Run the tool

bash
python3 security_suite.py
QUICK START GUIDE
Launch the tool: python3 security_suite.py

Confirm the legal warning by typing 'y' when prompted.

Select a tool from the main menu by entering its corresponding number (0-11).

Enter your target (e.g., example.com or http://example.com). The tool will add http:// if no protocol is specified.

Configure any tool-specific options (like port ranges or thread counts) when asked.

Review the results displayed in the terminal. A JSON report will also be saved automatically.

DETAILED TOOL DOCUMENTATION
1. Port Scanner
Description: Scans a range of TCP ports on a target IP or domain to find open ports and identify running services.

Configuration: Port range (start-end), number of threads, connection timeout.

Output: List of open ports with their guessed service names. Saves a report with target IP and scan duration.

2. Directory Bruteforcer
Description: Attempts to discover hidden web directories and files by requesting common paths from a built-in wordlist. It also tests for files with various extensions.

Configuration: Number of threads, file extensions to test (e.g., php, asp, txt).

Output: List of discovered URLs with their HTTP status codes and any redirect locations.

3. Subdomain Enumerator
Description: Tries to find subdomains for a given domain by prepending common words (e.g., 'www', 'mail', 'admin') and checking if they resolve via DNS. It also attempts a basic HTTP connection to see if the subdomain is live.

Configuration: Number of threads.

Output: List of found subdomains and their resolved IP addresses.

4. XSS Vulnerability Scanner
Description: Injects common XSS payloads into forms and URL parameters of the target page. It then checks if the payload is reflected in the server's response.

Requirement: BeautifulSoup4 must be installed.

Output: List of potential XSS vulnerabilities, including the vulnerable URL, parameter/form, and the payload used.

5. SQL Injection Tester
Description: Tests URL parameters for SQL injection vulnerabilities. It uses error-based payloads to look for database error messages in the response and time-based payloads to detect potential blind SQLi by measuring response delays.

Output: List of potentially vulnerable parameters, including the type of vulnerability (error-based, time-based) and the evidence found.

6. Security Headers Analyzer
Description: Analyzes the HTTP response headers of the target and checks for the presence of important security headers like Strict-Transport-Security, Content-Security-Policy, X-Frame-Options, and others.

Output: A table showing which security headers are present and their values, and which are missing. Provides a simple security score.

7. WAF Detector
Description: Attempts to identify if a Web Application Firewall is protecting the target. It analyzes response headers and cookies for known WAF signatures. It also sends a malicious payload to see if the request is blocked.

Output: Name of the detected WAF (e.g., Cloudflare, AWS WAF) or a message indicating no WAF was clearly identified.

8. SSL/TLS Checker
Description: Connects to the target over HTTPS, retrieves the SSL certificate, and displays detailed information. This includes the issuer, subject, validity period, days until expiration, Subject Alternative Names (SANs), TLS version, and the cipher suite in use.

Output: A detailed breakdown of the SSL/TLS configuration.

9. Web Crawler
Description: Recursively visits pages on the target website, starting from the given URL. It extracts links from each page and continues crawling until a set page limit is reached.

Requirement: BeautifulSoup4 must be installed.

Configuration: Maximum number of pages to crawl.

Output: A list of all visited pages, along with their page titles, HTTP status, and content size.

10. Full Report
Description: Executes a subset of the tools (Security Headers, Port Scan on common ports, WAF Detection, and SSL Checker) automatically and compiles the results into a single, comprehensive JSON report.

Output: A single JSON file containing the results from all the executed tools, providing a quick overview of the target's security posture.

11. Settings
Description: Allows you to configure global settings for the current session.

Options:

Set or change the global target.

Change the User-Agent string used in HTTP requests.

Add a session cookie (e.g., PHPSESSID=value).

Check which Python dependencies are installed.

CONFIGURATION
The suite can be configured in two ways:

Per-Tool Prompts: Most tools will ask you for specific parameters (e.g., port range, thread count) when you run them.

Global Settings (Option 11): You can set a persistent target, User-Agent, or session cookie that will be used across all tools for the duration of the session.

OUTPUT & REPORTS
All scan results are saved automatically in the current working directory.

Format: JSON

Naming Convention: {tool_name}_{YYYYMMDD_HHMMSS}.json

Example: port_scan_20231027_143022.json

The JSON report contains metadata about the scan (tool, target, timestamp) and the specific results from the tool.

DEPENDENCIES
Library	Required For	Installation Command
requests	All HTTP-based tools (2-7, 9, 10)	pip install requests
beautifulsoup4	XSS Scanner, Web Crawler (optional tools)	pip install beautifulsoup4
urllib3	Used by requests for HTTP/SSL handling	(Installed with requests)
LIMITATIONS
Speed: The multi-threading is basic and may not be as fast as professional tools like Nmap or ffuf.

Wordlists: The built-in wordlists for directories and subdomains are relatively small and intended for educational use.

False Positives: The XSS and SQLi scanners may produce false positives. Manual verification is always required.

Rate Limiting: The tool does not implement rate limiting, which could trigger WAF blocks or DoS protections on the target site.

CUSTOMIZATION
Adding Your Own Wordlists
You can easily replace the built-in wordlists in the code:

For Directory Bruteforcer: Modify the wordlist list inside the directory_bruteforcer function.

For Subdomain Enumerator: Modify the subdomains list inside the subdomain_enumerator function.

Modifying Payloads
XSS Payloads: Edit the payloads list in the xss_scanner function.

SQLi Payloads: Edit the payloads list in the sql_tester function.

Changing HTTP Headers
Use the Settings menu (option 11) to change the User-Agent or add cookies for authenticated scanning.

CONTRIBUTING
Contributions are welcome. Areas for improvement include:

Adding more comprehensive and varied payloads for XSS and SQLi.

Expanding the built-in wordlists.

Improving the accuracy of vulnerability detection.

Adding new tools (e.g., CORS checker, open redirect tester).

Bug fixes and code optimization.

Enhancing documentation.

To contribute, please fork the repository, make your changes, and submit a pull request.

LICENSE
This project is licensed under the MIT License. See the LICENSE file for more details.

RESOURCES
To learn more about web security:

OWASP Top 10

PortSwigger Web Security Academy

Hack The Box

TryHackMe

SUPPORT
For questions, suggestions, or to report bugs:

Open an issue on the GitHub repository.

Submit a pull request with your proposed changes.

REMEMBER: This tool is a powerful educational resource. Use it responsibly, ethically, and only on systems you are authorized to test.

