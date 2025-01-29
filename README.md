# PhantomHop
PhantomHop is a Python-based Tor IP rotation tool designed to enhance anonymity by periodically changing your public IP address using the Tor network. It ensures seamless proxy configuration and automates the process of requesting new Tor circuits.

# Tor-Based IP Spoofing Tool for Anonymity

## Abstract

This Python-based tool leverages the Tor network to dynamically rotate  IP addresses, providing anonymity during online activities. Designed for tasks such as reconnaissance or secure browsing, it routes traffic through Tor's SOCKS5 proxy and rotates IP addresses periodically to minimize traceability. The tool focuses on session-specific proxying, ensuring that all requests made within the same terminal session are anonymized while keeping the rest of the system unaffected. This approach balances automation and privacy, offering users control over their network anonymity. It works on both windows and linux

## How It Works

### 1. Proxy Configuration

The tool configures environment variables `http_proxy` and `https_proxy` to route HTTP and HTTPS traffic through the Tor network (`socks5h://127.0.0.1:9050`). These settings ensure that any tool or request in the current terminal session uses the Tor proxy for internet communication.

### 2. IP Rotation via Tor

To prevent prolonged use of the same IP address, the tool interacts with Tor's ControlPort (`9051`) to signal a circuit renewal using the `NEWNYM` signal. This command instructs Tor to rotate its IP address, ensuring a new exit node is used for subsequent requests.

### 3. Session-Specific Operation

Instead of altering global system proxy settings, the tool applies changes to the current terminal session. This session-specific proxying isolates the tool's effects, preventing disruptions to other applications or system-wide settings.

### 4. Real-Time IP Monitoring

The tool queries public IP-checking services like `api.ipify.org` to display the current Tor exit node's IP address. This feedback loop helps users verify that their requests are anonymized and track IP changes in real-time.

## Key Features

- **Dynamic IP Spoofing:** Periodically rotates the IP address via Tor to enhance anonymity.
- **Session-Specific Proxying:** Affects only the current terminal session, leaving global system settings untouched.
- **Lightweight and Automated:** Automates Tor proxy setup, IP rotation, and monitoring without requiring extensive configuration.
- **Real-Time Feedback:** Displays the current spoofed IP address, aiding transparency and debugging.

## Benefits

- **Privacy:** Shields the user's real IP from being exposed to external servers.
- **Anonymity:** Regular IP rotation makes it difficult to track or profile the user's online activity.
- **Modularity:** Can be integrated into larger workflows or tools requiring anonymized network traffic.

## Limitations

1. **Session-Specific Scope:** The tool only anonymizes traffic in the terminal session it is running in. Opening a new terminal requires reapplying the proxy settings.
2. **Dependency on Tor:** Requires Tor to be installed and properly configured on the system.
3. **Latency:** Using the Tor network can introduce delays due to its routing architecture.

## Usage Scenarios

- **Reconnaissance:** Anonymous data collection during penetration testing.
- **Secure Browsing:** Shielding browsing activities from being linked to a real IP.
- **Testing Environments:** Verifying the behavior of tools or services under anonymized conditions.



