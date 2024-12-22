# Network Intrusion Detection System (NIDS)

A Python-based Network Intrusion Detection System that monitors network traffic in real-time, detects potential security threats, and generates alerts for suspicious activities.

## Features

- Real-time packet capture and analysis
- Multiple protocol support (TCP, UDP, ICMP)
- Threat detection mechanisms:
  - Rule-based detection for command injection attempts
  - Framework for statistical anomaly detection
  - Placeholder for ML-based threat detection
- Comprehensive logging system
- Alert generation for detected threats

## Prerequisites

- Python 3.7+
- Scapy library
- Administrative/root privileges (required for packet capture)
- Network interface in promiscuous mode

## Installation

1. Clone this repository:
```bash
git clone https://github.com/yourusername/network-ids
cd network-ids
```

2. Install required dependencies:
```bash
pip install scapy
```

3. Ensure you have the necessary permissions to capture packets on your system.

## Configuration

Before running the system, you need to:

1. Modify the network interface in `main()` function:
   - Replace `"Wi-Fi"` with your network interface name (e.g., 'eth0', 'wlan0')
   - You can find your interface name using:
     - Windows: `ipconfig`
     - Linux/Mac: `ifconfig` or `ip addr`

2. Configure logging settings in the logging setup section if needed:
   - Default log file: `nids_logs.log`
   - Current logging level: INFO

## Usage

Run the script with administrative privileges:

```bash
# Linux/Mac
sudo python3 nids.py

# Windows (Run PowerShell as Administrator)
python nids.py
```

## Code Structure

- `capture_packet(packet)`: Processes captured network packets
  - Extracts protocol information
  - Parses packet metadata
  - Triggers threat detection

- `detect_threat(protocol, src_ip, dst_ip, payload)`: Implements threat detection logic
  - Rule-based detection
  - Placeholder for anomaly detection
  - Placeholder for ML-based detection

- `generate_alert(alert_type, src_ip, dst_ip, protocol)`: Handles alert generation and logging
  - Formats alert messages
  - Logs to file
  - Console output

## Logging

The system generates two types of logs:
1. Regular packet captures (INFO level)
2. Threat alerts (WARNING level)

Log format: `timestamp - message`

Example log entries:
```
2024-12-21 10:15:23 - Packet Captured: Protocol=TCP, Src=192.168.1.100, Dst=192.168.1.1
2024-12-21 10:15:24 - ALERT: Command Injection Attempt Detected | Src=192.168.1.100 | Dst=192.168.1.1 | Protocol=TCP
```

## Extending the System

### Adding New Detection Rules
Add new rules in the `detect_threat()` function:
```python
if <your_condition>:
    generate_alert("New Threat Type", src_ip, dst_ip, protocol)
```

### Implementing ML Detection
Replace the ML placeholder in `detect_threat()` with your trained model:
```python
model = load_your_model()
if model.predict(payload) == "Malicious":
    generate_alert("ML-Based Threat Detected", src_ip, dst_ip, protocol)
```

## Security Considerations

- Run with minimal required privileges
- Regularly update detection rules
- Monitor false positive rates
- Secure log files appropriately
- Consider network performance impact

## Known Limitations

- Basic command injection detection
- No persistent storage for threat intelligence
- Limited to packet-level analysis
- Requires root/admin privileges

## Contributing

Feel free to submit issues, fork the repository, and create pull requests for any improvements.

## License

[Your chosen license]

## Author

J.Wiggins

## Acknowledgments

- Scapy documentation and community
- [Any other acknowledgments]
