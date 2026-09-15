# The OSI Model

The **Open Systems Interconnection (OSI) model** is a conceptual framework created by the International Organization for Standardization (ISO) that describes how data travels from a software application on one computer across a network to a software application on another computer.

The model divides computer networking communications into **seven distinct layers**. Each layer serves the layer above it and is served by the layer below it, allowing different hardware and software technologies to interoperate reliably.

---

## The 7 Layers of the OSI Model

The layers are traditionally ordered from Layer 7 (closest to the user) down to Layer 1 (closest to the physical transmission medium):

```
Layer 7: Application
Layer 6: Presentation
Layer 5: Session
Layer 4: Transport
Layer 3: Network
Layer 2: Data Link
Layer 1: Physical
```

A common mnemonic to remember the order from 7 to 1 is: **"All People Seem To Need Data Processing"**.

---

### Layer 7: Application Layer

The **Application Layer** interacts directly with software applications that implement a communicating component. It provides network services directly to end-user applications.

- **Key Functions**: Identifies communication partners, determines resource availability, and synchronizes communication.
- **Protocols & Services**: HTTP/HTTPS (web browsing), DNS (name resolution), SMTP/IMAP (email), FTP/SFTP (file transfer), SSH (secure shell).
- **Data Unit**: Data / Message.

**Example**: When you enter a URL into your web browser, the browser uses the HTTP protocol at Layer 7 to formulate a request for the page.

---

### Layer 6: Presentation Layer

The **Presentation Layer** ensures that data is in a usable format and is where data encryption and formatting occur. It acts as a translator between the application and the network.

- **Key Functions**: Data translation (character code translation such as ASCII to EBCDIC), data compression, and cryptographic encryption/decryption (e.g., TLS/SSL).
- **Formats & Standards**: JPEG, PNG, GIF, ASCII, UTF-8, TLS.
- **Data Unit**: Data.

**Example**: When viewing a secure website, TLS operates here to encrypt outgoing user inputs and decrypt incoming server responses so the application layer can read them.

---

### Layer 5: Session Layer

The **Session Layer** manages connections between applications. It establishes, coordinates, maintains, and terminates communication sessions between local and remote applications.

- **Key Functions**: Session establishment, maintenance, and teardown; dialog control (half-duplex or full-duplex); checkpointing and synchronization.
- **Protocols & Standards**: NetBIOS, RPC (Remote Procedure Call), PPTP, Sockets.
- **Data Unit**: Data.

**Example**: During a file transfer, the session layer can place checkpoints into the stream. If the connection drops midway, the transfer can resume from the last checkpoint rather than starting over.

---

### Layer 4: Transport Layer

The **Transport Layer** coordinates data transfer between end systems and hosts. It handles flow control, error detection and correction, and ensures data arrives reliably and in the correct sequence.

- **Key Functions**: Segmentation and reassembly of data, port-based addressing (multiplexing), connection-oriented communication (acknowledgments, retransmissions), and flow control.
- **Protocols**: 
  - **TCP (Transmission Control Protocol)**: Reliable, connection-oriented, ordered delivery.
  - **UDP (User Datagram Protocol)**: Lightweight, connectionless, low-latency, best-effort delivery.
- **Data Unit**: Segment (for TCP) or Datagram (for UDP).

**Example**: TCP breaks down large files into numbered segments before sending them and waits for acknowledgments (ACKs) from the receiver to guarantee nothing was lost.

---

### Layer 3: Network Layer

The **Network Layer** provides routing and logical addressing. It determines the best physical path for data to travel across interconnected networks from source to destination.

- **Key Functions**: Logical addressing (IP addresses), path determination (routing algorithms), packet forwarding, and fragmentation.
- **Protocols & Hardware**: IPv4, IPv6, ICMP, OSPF, BGP; Routers and Layer 3 switches.
- **Data Unit**: Packet.

**Example**: When your computer requests a resource from a server across the globe, routers examine the destination IP address in the Layer 3 packet header to determine the next hop along the route.

---

### Layer 2: Data Link Layer

The **Data Link Layer** provides node-to-node data transfer across a single physical network segment. It detects and potentially corrects errors that may occur in the physical layer.

- **Sublayers**:
  - **LLC (Logical Link Control)**: Synchronizes frames, identifies network layer protocols, and manages flow control.
  - **MAC (Media Access Control)**: Controls how devices on a shared transmission medium gain access to data and permission to transmit it; handles physical hardware addresses (MAC addresses).
- **Protocols & Hardware**: Ethernet (802.3), Wi-Fi (802.11), PPP, ARP; Switches, Bridges, and Network Interface Cards (NICs).
- **Data Unit**: Frame.

**Example**: An Ethernet switch reads the destination MAC address within the incoming frame to deliver the data directly to the correct computer on the local office network.

---

### Layer 1: Physical Layer

The **Physical Layer** conveys raw bit streams over physical transmission media. It defines electrical, mechanical, optical, and functional interfaces to the physical transmission medium.

- **Key Functions**: Encoding bits into electrical voltages, radio frequencies, or light pulses; cable pinouts, connector types, signaling standards, and physical topologies.
- **Standards & Media**: Twisted pair copper cables (Cat 5e/6/6a), fiber optic cables, coaxial cables, radio waves (Wi-Fi/cellular), RJ45 connectors, hubs, repeaters.
- **Data Unit**: Bit.

**Example**: When an Ethernet cable transmits electrical pulses representing 1s and 0s between a laptop port and a network switch port, the physical layer is in operation.

---

## Summary of the 7 Layers

| Layer # | Layer Name | Protocol Data Unit (PDU) | Primary Function | Common Examples |
|---------|------------|--------------------------|------------------|-----------------|
| **7** | Application | Data / Message | User network services | HTTP, HTTPS, DNS, SSH, SMTP |
| **6** | Presentation | Data | Translation, encryption, compression | TLS/SSL, UTF-8, JPEG |
| **5** | Session | Data | Session management & sync | RPC, NetBIOS, Sockets |
| **4** | Transport | Segment / Datagram | End-to-end transport & reliability | TCP, UDP |
| **3** | Network | Packet | Logical addressing & routing | IPv4, IPv6, ICMP, Routers |
| **2** | Data Link | Frame | Node-to-node hop & MAC addressing | Ethernet, Wi-Fi, Switches |
| **1** | Physical | Bit | Physical signal & transmission | Cables, Fiber, Radio, Hubs |

---

## Data Encapsulation and De-encapsulation

As data travels down the OSI stack from the sender (encapsulation), each layer adds its own header (and in Layer 2, a trailer). When data reaches the recipient, it moves up the stack (de-encapsulation), and each layer inspects and removes its respective header until only the original payload reaches the application:

```
Sender Application
       ↓
[Layer 7]  Data
       ↓
[Layer 6]  Data (Formatted / Encrypted)
       ↓
[Layer 5]  Data (Session synchronized)
       ↓
[Layer 4]  [TCP Header | Data]                         ← Segment
       ↓
[Layer 3]  [IP Header | TCP Header | Data]             ← Packet
       ↓
[Layer 2]  [MAC Header | IP Header | TCP Header | Data | FCS] ← Frame
       ↓
[Layer 1]  01001000 01100101 01101100 01101100 01101111...   ← Bits on wire
```

---

## Why the OSI Model Matters

Although modern networks, including the Internet, are practically built on the **TCP/IP model** (which consolidates Layers 5–7 into an Application layer and Layers 1–2 into a Network Access layer), the OSI model remains the universal standard for:

- **Troubleshooting**: Systematically isolating issues (e.g., "Is this a physical cable issue at Layer 1 or an IP routing problem at Layer 3?").
- **Design & Standardization**: Allowing hardware and protocol designers to develop modular systems where changes at one layer do not require redesigning other layers.
- **Education & Communication**: Providing a common, vendor-neutral vocabulary across software engineers, network administrators, and security analysts.
