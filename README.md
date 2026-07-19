# Building a Secure Test Environment: Virtual Machine & VPN Implementation

This project demonstrates the deployment of an isolated Virtual Machine (VM) and the configuration of a secure Virtual Private Network (VPN) connection. Through this project, I established a secure sandbox environment designed for testing applications, analyzing network traffic, and simulating remote work scenarios without exposing the host machine to potential security risks.

## Environments and Technologies Used
* **Hypervisor:** Oracle VirtualBox Manager
* **Operating System Used:** Windows 11 Pro N (x64)
* **VPN Client:** Proton VPN (Free Plan)
* **Network Protocol Focus:** Virtual Private Networks (VPN), Split Tunneling, Cryptographic Handshakes, Geolocation Verification, DNS/IP Routing

## Project Objectives
1. **Host-Isolation:** Install and configure a fully functional guest operating system inside a virtualized sandbox.
2. **Traffic Encryption:** Secure all data entering and leaving the virtual environment by routing it through an encrypted VPN tunnel.
3. **Network Verification:** Confirm routing changes and verify successful encryption and anonymity by auditing external geolocation tags.

---

## Part 1: Virtual Machine Installation

*[...The steps from the previous write-up would go here...]*

---

## Part 2: VPN Installation and Traffic Security

### Step 7: Proton VPN Account Registration and Authentication
I initiated the secure tunnel implementation by setting up the necessary service account within the guest OS. Using the standard browser, I navigated to the Proton VPN portal to register a new user under the Free plan.

![Proton VPN Account Setup](YOUR_IMAGE_LINK_HERE)
*Ref 7: Registering and authenticating a new user account on the Proton VPN portal (Screenshot_20260716_163448.jpg).*

### Step 8: VPN Client Provisioning and Installation
Once authenticated, I navigated to the official download section to obtain the legitimate VPN client software optimized for the Windows platform. I downloaded and executed the setup file inside the virtual machine.

![Downloading the VPN Client](YOUR_IMAGE_LINK_HERE)
*Ref 8: Acquiring the Windows-specific Proton VPN application (Screenshot_20260716_163712.jpg).*

### Step 9: Launching and Initializing the Client
Following a successful installation, the Proton VPN client daemon was launched. The interface initialized, presenting the security dashboard that confirms that all local traffic remains unsecured prior to establishing the cryptographic tunnel.

![Initializing the VPN Client](YOUR_IMAGE_LINK_HERE)
*Ref 9: First launch of the VPN client dashboard, indicating an unsecured connection status (Screenshot_20260716_164334.jpg).*

### Step 10: Establishing Baseline Geolocation (The "Control" Test)
To verify that the secure tunnel works as intended, I needed a control baseline. I launched YouTube to check its automatic regional localization. YouTube correctly identified my connection origin, displaying the localized logo.

![Baseline Geolocation Check](YOUR_IMAGE_LINK_HERE)
*Ref 10: Establishing a network baseline. YouTube geolocates the browser to the native origin (Screenshot_20260716_164742.png).*

### Step 11: Active Tunnel Negotiation
I returned to the Proton VPN client and clicked "Quick Connect." The software automated the cryptographic handshake, establishing a secure, encrypted tunnel to the optimal free endpoint, which in this case was a high-load server based in Singapore. The client confirmed a successful connection and assigned a new external IP address (`103.216.221.108`).

![Active Tunnel Negotiation](YOUR_IMAGE_LINK_HERE)
*Ref 11: Establishing an active VPN tunnel to a Singapore-based secure endpoint (Screenshot_20260716_164849.jpg).*

### Step 12: Verifying Traffic Obscuration and Successful Geolocation Shift
To conclude the implementation audit, I returned to the browser (Ref 10) and refreshed the YouTube homepage. The verification test was successful: YouTube no longer saw my native origin and now localized my browser based on the VPN's egress point. This shift confirms that all traffic from the virtual machine is successfully encapsulated, encrypted, and correctly routed through the obscure network endpoint.

![VPN Security Verification](YOUR_IMAGE_LINK_HERE)
*Ref 12: Successful implementation audit. YouTube now localizes the browser based on the secure VPN endpoint, proving successful traffic obscuration (Screenshot_20260716_164911.png).*
