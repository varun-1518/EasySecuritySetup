
# EasySecuritySetup
---

## Cybersecurity Tool Setup Script

This repository contains a Python script for automating the setup of various cybersecurity tools and configurations on a Linux server. The tools include Intrusion Detection Systems (IDS), firewall configuration, VPN setup, proxy configuration, and more.

## Features
- **Installs and Configures Tools**: The script installs and configures multiple cybersecurity tools, including Snort (IDS), Suricata (IDS/IPS), Zeek (Network Analysis), OpenVPN (VPN), Squid (Proxy), and more.
- **Firewall Configuration**: Configures `iptables` to allow secure communication and restrict unauthorized access.
- **Logging Setup**: Configures logging for better visibility into the server's activities.
- **Security Enhancements**: Adds additional security features like disabling root login via SSH, blocking remote desktop apps, and setting up secure VPN and proxy configurations.

## Tools and Services Configured
- **Snort** - Intrusion Detection System (IDS)
- **Suricata** - IDS/IPS
- **Zeek (formerly Bro)** - Network Analysis Framework
- **iptables** - Firewall configuration
- **OpenVPN** - Virtual Private Network (VPN) setup
- **Squid** - Proxy server setup
- **SSH** - Secure login configuration
- **rsyslog** - Log management for monitoring system activity

## Requirements
Before running the script, ensure that you have the following prerequisites installed:
- **Python 3**: Required to run the setup script.
- **sudo privileges**: The script requires administrative permissions to install and configure tools.
- **Linux-based OS**: The script is designed to work on Debian-based systems (Ubuntu, etc.).
- **Internet Access**: The script will need access to external repositories to install tools via `apt-get`.

## Installation

1. **Clone the repository**:

```bash
git clone https://github.com/varun-1518/EasySecuritySetup.git
cd EasySecuritySetup
```

2. **Install dependencies**:

Make sure your system has `apt-get` and other required tools. You can install the necessary packages by running:

```bash
sudo apt-get update
sudo apt-get install -y python3 python3-pip sudo
```

3. **Run the setup script**:

Make sure the script has executable permissions and run it:

```bash
chmod +x setup.py
sudo python3 setup.py
```

This will install and configure all the necessary tools and services on your server.

## How It Works

The script works in the following steps:

1. **Install Tools**: It first installs the required cybersecurity tools such as Snort, Suricata, Zeek, OpenVPN, Squid, and others using `apt-get`.
   
2. **Configure Tools**: Each tool is configured with default settings. This includes:
   - **IDS/IPS Configuration**: Snort, Suricata, and Zeek are configured to monitor the system for potential threats.
   - **VPN Setup**: OpenVPN is configured for secure communication.
   - **Proxy Configuration**: Squid is set up to act as a proxy server for better internet privacy.
   - **Firewall Configuration**: The script configures `iptables` to allow only necessary traffic and block unwanted access.
   - **SSH Configuration**: SSH is configured for secure login (root login is disabled).
   
3. **Log Management**: Configures `rsyslog` to handle logs from various services (IDS, firewall, VPN, etc.).

4. **Security Enhancements**: Additional security features are configured, including blocking remote desktop applications and applying security policies to the VPN.

## Post-Installation Checks

After running the script, you should:
- Verify that the services (OpenVPN, Squid, Snort, etc.) are running:

```bash
sudo systemctl status openvpn
sudo systemctl status squid
sudo systemctl status snort
```

- Check the status of your firewall rules:

```bash
sudo iptables -L
```

- Verify that logging is working correctly:

```bash
tail -f /var/log/snort/alert
tail -f /var/log/syslog
```

## Customization

- **Configuration Files**: You can customize the configuration files for each tool (e.g., `/etc/openvpn/server.conf`, `/etc/squid/squid.conf`, `/etc/snort/snort.conf`) based on your specific environment.
- **Network Interfaces**: Ensure that the network interfaces (`eth0` in the script) match your system's configuration.
- **Firewall Rules**: Modify the `iptables` rules according to your specific network and security requirements.

## Security Best Practices
- **Regular Updates**: Ensure that the system and installed tools are regularly updated to maintain security.
- **Review Logs**: Set up additional monitoring or integrate with SIEM tools for better log management.
- **MFA for VPN**: For more secure VPN authentication, consider integrating Multi-Factor Authentication (MFA) solutions.

## Troubleshooting

- **Permission Issues**: Ensure that the user running the script has `sudo` privileges.
- **Installation Errors**: If you encounter issues with package installation, make sure your package repository is up-to-date or manually install missing dependencies.
- **Service Not Starting**: If a service fails to start, check its configuration file for errors and consult the respective tool's logs for more details.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

This README file should guide users through the steps required to set up and customize the cybersecurity tool configuration script for their needs.
