# Module 07 - Quality of Service (QoS)

This module covers traffic shaping and bandwidth management on MikroTik RouterOS using Simple Queues, Bursting, and Per Connection Queues (PCQ).

## 1. Simple Queues & Bursting (Guest Network)

To prevent Guest network users from saturating the WAN link, we implemented a Simple Queue with burst capabilities. This allows guests to load web pages quickly (using the burst speed) but heavily throttles sustained downloads (like large files or video streams) to preserve bandwidth for corporate VLANs.

### Configuration Parameters

* **Target:** `192.168.40.0/24` (Guest Subnet)
* **Limit At (Guaranteed):** 128k Upload / 512k Download
* **Max Limit (Sustained Ceiling):** 512k Upload / 2M Download
* **Burst Limit:** 1M Upload / 4M Download
* **Burst Threshold:** 256k Upload / 1500k Download
* **Burst Time:** 16s / 16s

![Guest Queue Burst Settings](/screenshots/69-guest-queue-burst-settings.png)

### Testing the Burst Queue

We validated the queue using the RouterOS Bandwidth Test tool. By forcing UDP traffic from the Guest subnet to the router, we successfully triggered the burst limits. The router allowed the initial 4M burst, and once the 16-second average crossed the 1.5M threshold, it successfully clamped the traffic down to the 2M Max Limit.

![Guest Queue Traffic Test](screenshots/70-guest-queue-traffic-test.png)

## 2. Per Connection Queue (PCQ) (IT Network)

While a Simple Queue caps an entire subnet, it does not guarantee fairness *within* that subnet. For the IT Department (`vlan10`), we implemented PCQ to ensure that a shared 10 Mbps pool is divided equally among all active IT users dynamically.

### Step 1: Creating PCQ Types

We created custom Queue Types to classify the traffic streams:
* **PCQ-Download:** Classifies based on `Dst. Address`. This ensures every individual PC receiving data gets its own dedicated slice of download bandwidth.
* **PCQ-Upload:** Classifies based on `Src. Address`. This ensures every individual PC sending data gets its own dedicated slice of upload bandwidth.

![PCQ Types Created](screenshots/71-pcq-types-created.png)

### Step 2: Applying PCQ to the IT VLAN

We created a new Simple Queue targeting the IT interface (`vlan10`) with a 10M/10M Max Limit. On the Advanced tab, we applied our custom PCQ Types.

![IT Queue PCQ Applied](screenshots/72-it-queue-pcq-applied.png)

### Step 3: Verifying Dynamic Sub-Queues

To prove PCQ fairness, we generated simulated IT traffic. By analyzing the queue statistics during the test, we verified that the router dynamically spawned a dedicated sub-queue (`PCQ Queues: 1`) specifically for that unique source IP address. If more users join, the router will automatically create additional queues and divide the 10 Mbps evenly.

![PCQ Dynamic Queues Test](screenshots/73-pcq-dynamic-queues-test.png)
