# Module 5 – Wireless (Theory)

**Scope:** theory only. The lab runs on Hyper-V CHR virtual routers, which have no radio, so none of this module was configured or tested in the lab. Hands-on practice needs real MikroTik wireless hardware.

---

## 1. How wireless works

- Wi-Fi sends data as **radio waves**. All devices on a channel **share** the same airspace, so only one can transmit at a time.
- Devices listen before they transmit and wait if the channel is busy. More devices and more nearby networks on the same channel means slower speeds.

---

## 2. Frequency bands

| Band | Strengths | Weaknesses |
|---|---|---|
| **2.4 GHz** | Longer range, passes through walls better | Slower, crowded (neighbouring Wi-Fi, Bluetooth, microwave ovens) |
| **5 GHz** | Faster, less crowded | Shorter range, weaker through walls |

Newer standards also use a 6 GHz band (Wi-Fi 6E and later), which offers more room but the shortest range of the three.

**Choosing a band:** use 2.4 GHz where coverage through walls matters, and 5 GHz where speed matters and many other networks are nearby.

---

## 3. Channels and channel width

- Each band is divided into **channels**, like lanes on a road.
- Two access points on the same or overlapping channels interfere with each other and slow each other down.
- In the 2.4 GHz band, with 20 MHz-wide channels, only channels **1, 6 and 11** do not overlap, so they are the usual choices.
- **Channel width** (20, 40, 80 MHz and so on) is how much spectrum a channel uses. A wider channel gives higher speed but leaves fewer non-overlapping channels and picks up more interference.
- The allowed channels and power levels depend on the **country**, so the country setting on a device must match where it is used.

---

## 4. 802.11 standards

| Standard | Common name | Band | Notes |
|---|---|---|---|
| 802.11b | – | 2.4 GHz | Oldest, up to 11 Mbps |
| 802.11a | – | 5 GHz | Up to 54 Mbps |
| 802.11g | – | 2.4 GHz | Up to 54 Mbps |
| 802.11n | Wi-Fi 4 | 2.4 and 5 GHz | Introduced multiple antennas (MIMO) |
| 802.11ac | Wi-Fi 5 | 5 GHz | Gigabit-class speeds |
| 802.11ax | Wi-Fi 6 / 6E | 2.4, 5 (and 6 GHz for 6E) | Better in crowded environments |

Rates are theoretical maximums. Real throughput is much lower and depends on signal quality, interference and the number of clients.

---

## 5. Key terms

| Term | Meaning |
|---|---|
| **AP** (access point) | The device clients connect to |
| **Station / client** | A device that connects to an AP |
| **SSID** | The network name |
| **BSSID** | The MAC address of an AP's radio |
| **Signal strength** | Measured in dBm. The closer to 0, the stronger (for example, -50 is very good and -85 is poor) |
| **Noise floor** | Background radio noise. The gap between signal and noise matters more than signal alone |
| **Roaming** | A client moving from one AP to another with the same SSID |

---

## 6. Wireless security

| Method | Notes |
|---|---|
| Open | No encryption |
| WEP | Broken. Do not use |
| WPA / WPA2 | WPA2 with AES (CCMP) is still widely used |
| WPA3 | Newest, stronger protection |
| **PSK** vs **Enterprise** | PSK uses one shared password. Enterprise (802.1X) gives each user their own login through a RADIUS server |

Hiding the SSID and filtering by MAC address are not real security. A MAC address can be copied, and a hidden SSID is still visible to anyone scanning.

---

## 7. MikroTik wireless concepts

- **Wireless interface** (for example `wlan1`): the radio, configured with a band, channel, SSID and mode.
- **Modes:** an interface can act as an access point (such as `ap-bridge`) or as a client (such as `station`). The exact mode names and the wireless menu differ between RouterOS versions, so check the documentation for the version in use.
- **Security profile:** holds the authentication type and passwords for an interface.
- **Access list:** an AP-side list that decides which clients may connect.
- **Connect list:** a client-side list that decides which APs a station may join.
- **Registration table:** shows the clients currently connected to an AP, with signal strength.
- **Bridging:** to put wireless clients on the same network as wired devices, the wireless interface is added to a bridge, the same idea as `bridge1` in Module 3.

---

## 8. Practising wireless

No free virtual platform lets you practise MikroTik wireless, because it needs radio hardware. Options:
- Free video courses (for example the Wireless Netware MTCNA course on YouTube, and the Network Berg MTCNA course on Class Central) to watch a real setup.
- Two inexpensive MikroTik wireless routers for a full hands-on lab (optional).

---

## 9. Self-check questions

1. Which band gives better range through walls, and which is faster?
2. Why do channels 1, 6 and 11 matter on 2.4 GHz?
3. What is the difference between an access list and a connect list?
4. Why is hiding the SSID not a security measure?
5. Why must the country setting be correct?
6. How do you put wireless clients on the same network as wired devices?

---

## 10. Still to do
- Hands-on configuration on real MikroTik wireless hardware.
