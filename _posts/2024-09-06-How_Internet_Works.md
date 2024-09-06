# how_internet_works

```text
                             Internet Structure
                              ┌───────────────┐
                              │    Internet   │
                              └───────────────┘
                                      │
                ┌─────────────────────┴──────────────────────┐
                │                                            │
        ┌───────────────┐                          ┌─────────────────┐
        │    ISPs       │                          │  Data Centers   │
        │ (Internet     │                          │  (Servers/Cloud)│
        │ Service       │                          │                 │
        │ Providers)    │                          └─────────────────┘
        └───────────────┘                                  │
                │                                          │
                └──────────────────────────────┐           │
                                               │           │
                                    ┌─────────────────┐    │
                                    │ Network Routing │    │
                                    │  (Routers)      │    │
                                    └─────────────────┘    │
                                               │           │
                          ┌────────────────────┴───────────┴────────┐
                          │                                         │
            ┌─────────────────────────┐             ┌──────────────────────┐
            │       DNS Servers       │             │   Web Servers/Apps   │
            │  (Domain Name System)   │             │ (e.g., Websites, API │
            └─────────────────────────┘             │    services, etc.)   │
                          │                         └──────────────────────┘
                          │                                      
                  ┌───────┴────────┐
                  │                │
         ┌───────────────────┐  ┌───────────────────┐
         │   User's Device   │  │ Local Network     │
         │(Phone, Computer,  │  │(Routers, Switches,│
         │     etc.)         │  │  Modem)           │
         └───────────────────┘  └───────────────────┘
                          │
                    ┌─────┴─────┐
                    │           │
            ┌────────────┐   ┌────────────┐
            │  Wireless  │   │   Wired    │
            │ Connections│   │ Connections│
            └────────────┘   └────────────┘

```
Key Elements:

    Internet: The global network of interconnected systems.
    ISPs (Internet Service Providers): Provide internet access to users.
    Data Centers/Cloud: Massive infrastructure housing servers that store websites, apps, data, and services.
    Routers: Direct internet traffic to ensure that data reaches the correct destination.
    DNS Servers: Convert human-friendly domain names (e.g., www.example.com) into IP addresses.
    Web Servers/Apps: Host websites, APIs, or online services.
    User’s Device: Your phone, computer, etc., that connects to the internet.
    Local Network (Routers, Modems): Connect your device to the ISP.
    Wired/Wireless Connections: Physical cables or Wi-Fi connecting your device to the local network.



### Here's a tree structure to show what happens in the background when you search on the internet,



```text
                               ┌─────────────┐
                               │   User      │ 
                               │ (Browser)   │
                               └─────────────┘
                                      │
                                      ▼
                          ┌───────────────────────┐
                          │   DNS Lookup (DNS)    │
                          └───────────────────────┘
                                      │
                                      ▼
                        ┌──────────────────────────┐
                        │   Request to ISP Router  │
                        └──────────────────────────┘
                                      │
                                      ▼
                 ┌────────────────────────────────────────┐
                 │  Data Packets Routed Through Internet  │
                 └────────────────────────────────────────┘
                                      │
                                      ▼
                         ┌──────────────────────────┐
                         │   Target Web Server      │
                         └──────────────────────────┘
                                      │
                                      ▼
                       ┌──────────────────────────────┐
                       │ Web Server Sends Data Back   │
                       └──────────────────────────────┘
                                      │
                                      ▼
                          ┌────────────────────────┐
                          │ Data Returned to User  │
                          └────────────────────────┘

```
Step-by-Step Explanation:

    User (Browser):
        What Happens: When you type a search term or URL (e.g., "www.google.com") and press enter, your browser sends a request to retrieve data from the web.

    DNS Lookup:
        What Happens:
            Your browser first needs to find the IP address of the website you're trying to reach. It uses the Domain Name System (DNS) to convert the human-readable URL (e.g., "www.google.com") into an IP address (e.g., "142.250.72.206").
            If the browser doesn't have the IP cached locally, it will ask a DNS server, usually provided by your ISP or a public DNS (e.g., Google DNS or Cloudflare DNS).

    Request to ISP Router:
        What Happens:
            Once the DNS lookup is complete, your device sends the request (with the IP address) to your ISP’s router. This is the entry point for all your internet traffic.
            The request is broken down into smaller data packets and forwarded to your ISP's network.

    Data Packets Routed Through the Internet:
        What Happens:
            The ISP’s network forwards your data packets to routers across the internet, traveling along a path based on optimal routing.
            These packets move through various servers and routers (owned by different providers) until they reach the server hosting the website you're trying to visit.
            Each router along the way looks at the destination IP and forwards the packet to the next hop in the route.

    Target Web Server:
        What Happens:
            Once the packets reach the web server hosting the website or the service (e.g., Google’s servers), the server processes your request (in the case of a search, it processes your search query).
            The server performs the necessary operations, such as searching its database or loading the requested webpage.

    Web Server Sends Data Back:
        What Happens:
            The server sends a response (usually in the form of HTML, CSS, JavaScript, images, etc.) back to you. This response is also broken down into smaller data packets.
            These packets travel the same way back through the internet routers, eventually reaching your ISP’s router.

    Data Returned to User:
        What Happens:
            Your device collects the incoming data packets and reassembles them. Your browser then interprets the code (HTML, CSS, JavaScript) and displays the requested webpage or search results to you.

Additional Background Processes:

    HTTP/HTTPS Protocols:
        Your browser communicates with the web server via HTTP (or the more secure HTTPS). These protocols define how data is requested and transferred between your browser and the server.

    Caching:
        DNS Caching: Sometimes your browser or system remembers recent DNS lookups, so it doesn't need to ask a DNS server again.
        Content Caching: Browsers may cache (store) parts of websites, like images or scripts, to speed up future requests.

    SSL/TLS Encryption (HTTPS):
        If you're visiting a website over HTTPS, your browser and the server perform a secure handshake, encrypting all communication between you and the server. This ensures that third parties cannot read your data.

This whole process happens in just a few milliseconds to a few seconds, depending on your connection speed and the complexity of the website you're accessing!
