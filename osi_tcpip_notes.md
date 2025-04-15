
# OSI Model & TCP/IP Suite – My Notes

## What’s a Networking Model?

A networking model is basically a blueprint. It helps organize how different network protocols and standards work together.  
_(BTW, a protocol is just a set of rules for how devices and apps talk to each other over a network.)_

---

## OSI Model – Open Systems Interconnection

The OSI model is a conceptual framework created by ISO (International Organization for Standardization).  
It breaks down network functions into **7 layers**, each with a specific job. These layers work together to make communication happen.

### Important terms:
- **Encapsulation**: When data goes from the top layer down to the bottom.
- **De-encapsulation**: When data travels from the bottom layer back up.
- **Same-layer interaction**: Communication between the same layer on two different devices.

---

## 7 Layers of OSI (from top to bottom):

### 7. Application Layer
- Closest to the end user.
- Interacts with software applications (like web browsers).
- Examples: **HTTP**, **HTTPS**.
- Main roles: identify communication partners, sync communications.

### 6. Presentation Layer
- Translates data between app formats and network formats.
- Think: data encoding, compression, encryption.

### 5. Session Layer
- Manages sessions (connections) between apps on different devices.
- Establishes, maintains, and terminates sessions.

> *Note: Network engineers don’t usually deal much with layers 5–7. These are more relevant for app developers.*

### 4. Transport Layer
- Handles end-to-end communication.
- Breaks large data into smaller chunks (segments), then reassembles them on the other side.
- Adds the **Layer 4 Header** to the data → called a **Segment**.

```
Segment = Data + L4 Header
```

### 3. Network Layer
- Routes data between devices on different networks (outside your LAN).
- Handles logical addressing (like IP addresses).
- Routers work here.
- Adds the **Layer 3 Header** → now it’s a **Packet**.

```
Packet = Data + L4 Header + L3 Header
```

### 2. Data Link Layer
- Manages direct device-to-device connections (PC to switch, switch to router, etc).
- Defines how data is packed for the physical medium (like UTP cables).
- Uses MAC addresses.
- Switches operate at this layer.
- Adds **Layer 2 Header** and **Trailer** → this forms a **Frame**.

```
Frame = L2 Trailer + Data + L4 Header + L3 Header + L2 Header
```

### 1. Physical Layer
- The actual physical stuff: cables, signals, voltages, connectors, etc.
- Converts data into electrical or wireless signals.
- Devices like hubs or anything hardware-related belong here.

---

## Encapsulation & De-encapsulation Flow

When sending data:
1. It starts at Layer 7 and goes down → **Encapsulation**.
2. At each layer, headers (and sometimes trailers) are added.
3. Finally, it’s transmitted as bits over the wire (or wirelessly).

When receiving data:
1. It travels up from Layer 1 to 7 → **De-encapsulation**.
2. Each layer removes its corresponding header and processes the data.

---

## OSI Model & PDU (Protocol Data Units)

| OSI Layer | PDU Name | What’s Added |
|-----------|----------|--------------|
| 7–5       | Data     | Nothing yet  |
| 4         | Segment  | L4 Header    |
| 3         | Packet   | L3 Header    |
| 2         | Frame    | L2 Header + Trailer |
| 1         | Bits     | Just 1s and 0s |

---

# TCP/IP Suite – The Real World Model

The TCP/IP model is what we actually use today in real networks, like the Internet.

- Developed by the US Department of Defense (DARPA).
- Fewer layers than OSI, but similar concepts.
- Named after **TCP** and **IP**, two core protocols.

Although OSI is great for learning and understanding, TCP/IP is the practical model used in modern networking.

---

## Layer Interactions

### Adjacent-Layer Interaction
- Happens between layers on the **same device**.
- Example: Layer 6 gives data to Layer 5 → Layer 5 adds its header.

### Same-Layer Interaction
- Happens between the **same layer on two different devices**.
- Example: Your browser (Layer 7) talks to YouTube’s web server (also Layer 7).

---

> These notes are written to help me understand and explain the OSI Model and TCP/IP Stack clearly and simply.
