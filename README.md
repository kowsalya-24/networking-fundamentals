# 📡 IP Addresses and Subnets

An **IP address** is a unique numerical label assigned to every device on a computer network that uses the Internet Protocol for communication.  
Think of it as a **street address** for your computer.

---

## 🌐 IPv4
An **IPv4 address** is represented by four numbers, each ranging from `0` to `255`, separated by dots:

`192.168.1.1`

- Each number is called an **octet**.
- Each octet = **8-bit binary number** → Range: 0–255 (`2^8 = 256` possible values).
- Full IPv4 address length: **32 bits** (4 × 8 bits).

---

## 🏢 Subnets (Subnetworks)
A **subnet** is a logical subdivision of an IP network, used for:
- Improving **security**.
- Managing **traffic**.
- Isolating **network segments**.

💡 **Example Analogy**:  
A large office building (your network) has one main street address (main IP range). Departments like **Accounting** and **Marketing** can have their own internal addresses (subnets).  
If a hacker enters Marketing's subnet, they **cannot** automatically access Accounting’s subnet.

### Types of Subnets
- **Private Subnet** 🛡️ → No direct internet access (e.g., databases).
- **Public Subnet** 🌍 → Internet-accessible (e.g., web servers).

---

## 📏 CIDR (Classless Inter-Domain Routing)
CIDR specifies IP ranges in the format:

`xxx.xxx.xxx.xxx/yy`

- `/yy` → Prefix length (number of fixed bits).
- **Formula for IP count**: `2^(32 - yy)`

### CIDR Examples
| Required IPs | Bits for Hosts | Prefix Length | Example CIDR   | IP Range                          |
|--------------|---------------|--------------|----------------|------------------------------------|
| 256          | 8             | /24          | 172.43.29.0/24 | 172.43.29.0 → 172.43.29.255        |
| 2            | 1             | /31          | 172.43.32.0/31 | 172.43.32.0 → 172.43.32.1          |
| 65,536       | 16            | /16          | 124.23.0.0/16  | 124.23.0.0 → 124.23.255.255        |

---

## 🔐 Common Private IP Ranges

- 192.168.0.0/16
- 172.16.0.0/12
- 10.0.0.0/8


---

## 🔌 Ports
A **port** identifies a specific application on a device.  
An IP gets you to the device, and a port gets you to the **right application**.

💡 **Analogy**:  
- IP address → Apartment building address.
- Port number → Apartment number.

**Example**:
- 128.21.3.34:8086

Here, `8086` is the port for a specific application.

---

## 🗺️ OSI Model and Data Journey

When you access a website or send data, your request travels through the **OSI model layers** before reaching its destination. Each layer has a specific role.

### Stage 1: DNS Resolution
- Converts a domain name (e.g., `www.google.com`) into an IP address.
- Acts like the **phone book** of the internet.

### Stage 2: TCP Handshake
1. **SYN** → Your computer says: "I want to connect."
2. **SYN-ACK** → Server replies: "I’m ready."
3. **ACK** → Your computer confirms: "Let’s start."

---

### OSI Model Layers Table
| Layer | Name              | Function & Detailed Explanation                                                                                                                                                        | Emoji |
|-------|-------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------|
| 7     | Application       | **User-facing layer**. This is where applications like browsers or email clients interact. It uses protocols like HTTP, HTTPS, FTP, and SMTP to send and receive data.               | 💻    |
| 6     | Presentation      | **Translator layer**. It formats data for the application layer and handles encryption (SSL/TLS) and compression so data is secure and efficient to transmit.                        | 📜    |
| 5     | Session           | **Session manager**. Establishes, maintains, and terminates sessions. Keeps you logged in while navigating between pages, often using cookies and tokens.                           | ⏱️    |
| 4     | Transport         | **Data delivery layer**. Breaks data into segments, chooses TCP (reliable, ordered delivery) or UDP (faster, no guarantee), and ensures data is reassembled correctly.                | 📦    |
| 3     | Network           | **Routing layer**. Adds source and destination IP addresses to create packets. Determines the best path through the network using routers.                                            | 🗺️    |
| 2     | Data Link         | **Local delivery layer**. Packages packets into frames, adds MAC addresses (unique device IDs), and ensures delivery between devices on the same local network (LAN).                 | 🏡    |
| 1     | Physical          | **Hardware layer**. Converts frames into electrical, optical, or radio signals that physically travel through cables, fiber optics, or Wi-Fi to reach the next device.               | 🔌    |

---

📍 **Flow Summary**:
1. Browser sends request.
2. DNS finds server IP.
3. TCP handshake establishes connection.
4. Data passes through OSI layers **(7 → 1)**.
5. Server responds, reversing the process **(1 → 7)**.
