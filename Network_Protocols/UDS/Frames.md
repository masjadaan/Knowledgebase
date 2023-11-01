# Frames
* * *
Unified Diagnostic Services (UDS) operates within a client-server architecture, wherein a client (tester's tool) initiates requests and the server (ECU) provides responses, with each request being associated with a unique Service ID (SID).



## Frame Format

### Request Frame Format

|  SID | Sub-Function ID (optional) | Data Parameters |
| ------------- | ------------- | ------------- |

- For UDS on CAN

| CAN ID | PCI | SID | Sub-Function ID (optional) | Data Parameters |
| ------ | --- | --- | -------------------------- | --------------- |

### Response Frame Format
#### - Positive Response Frame
- The ECU has processed the requested service and responds to the client 
- If the response is positive, then the 6th bit of the SID should be 1, or in another way the positive response = SID + 0x40

| SID + 0x40 | Sub-Function ID (optional) | Data Response Code |
| ---------- | -------------------------- | ------------------ |


- For UDS on CAN

| CAN ID | PCI | SID + 0x40 | Sub-Function ID (optional) | Data Response Code |
| -------| --- | ---------- | -------------------------- | ------------------ |
	
#### - Negative Response Frame
- The ECU has detected an error and it sends a Negative response code(NRC)

| 0x7F| Service ID | Negative Response Code |
| --- | ---------- | ---------------------- |

- For UDS on CAN

| CAN ID | PCI | 0x7F | Service ID | Negative Response Code |
|------- | --- | ---- | ---------- | ---------------------- |




#### Notes
- Protocol Control Information (PCI)
  - it ranges from 1 to 3 bytes long and contains information about the transmission of messages that do not fit withi a single CAN frame.
- Negative Response Code
