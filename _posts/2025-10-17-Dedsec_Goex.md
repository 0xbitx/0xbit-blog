
<p align="center">
<img src="https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExMTU5MXQ1Y25sYjV0Mnp2b3BuMm5jZ3dmN29oeWRwNDk5azFrY3o5dCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/5NPhdqmyRxn8I/giphy.gif", width="300", height="300">
</p>

<h1 align="center">GOEX</h1>
<h4 align="center"> GOEX - A linux-based tool to extract metadata from Google Drive links.</h4>

### DESCRIPTION
GOEX is a linux-based tool designed to extract and display information from Google Drive documents, such as files, folders, spreadsheets, and other Google Workspace items. It parses a Google Drive URL or ID, fetches metadata using the Google Drive API, and presents details like the owner, permissions, creation date, and last modified date.

This tool is intended for educational and personal use only. It requires the document to be publicly accessible; otherwise, it will handle errors gracefully.


### Features:
  * URL/ID Parsing: Automatically extracts the Google Drive document ID from various URL formats (e.g., files, folders, documents, spreadsheets, etc.).
      Metadata Extraction: Retrieves and displays key information, including:
          Owner's name and email.
          File permissions (e.g., reader, writer).
          Creation and last modified dates.
          User-specific permissions.
  * Error Handling: Checks for non-public links, rate limits, and invalid inputs.
  * User-Friendly Interface: Displays results in a formatted table using color-coded output for better readability.
  * Recursive Prompt: Allows users to enter multiple links without restarting the script.
  * Example Links: Provides sample URLs for quick testing.

### INSTALLATION
    git clone https://github.com/0xbitx/DEDSEC_GOEX.git
    cd DEDSEC_GOEX
    pip3 install httpx tabulate
    chmod +x dedsec-goex
    ./dedsec-goex
    
### TESTED ON FOLLOWING
* Kali Linux 
* Parrot OS 
  
## Legal Disclaimer

This tool is intended for educational and security research purposes only. Unauthorized usage may be illegal in your jurisdiction. The author is not responsible for any misuse of this tool.
