#Detection Lab

##Objective
The purpose of this lab was to simulate the role of a security analyst by monitoring network traffic with Suricata, configuring and testing custom detection rules, and analyzing Suricata’s output logs. The activity involved working with pre-supplied packet capture (PCAP) data and rule files to trigger alerts, examine Suricata’s fast log format for quick checks, and review the more detailed JSON output for in-depth analysis.

###Skills Learned
Configuring and testing custom intrusion detection system (IDS) rules in Suricata.

Using packet capture (PCAP) files to simulate network traffic for analysis.

Interpreting Suricata’s fast.log output for quick alert validation.

Parsing and analyzing Suricata’s eve.json log for detailed telemetry.

Extracting and filtering JSON log data using the jq command.

Understanding IDS rule components: action, header, and rule options.

###Tools Used
Suricata – for network traffic monitoring and alert generation.

sample.pcap – packet capture file containing test network traffic.

custom.rules – file for defining and modifying Suricata rules.

fast.log – Suricata’s quick alert output log.

eve.json – Suricata’s standard, detailed JSON log format.

jq – command-line JSON processor for querying log data.

Linux Bash Shell – for executing Suricata commands and log queries.

##Steps
*1️⃣ Launching Suricata Lab Environment*
The terminal window shows Suricata installed and ready to run. This step ensures the system has the required dependencies and tools for packet capture and rule testing.
(Screenshot: Suricata command line initialized
<img width="931" height="317" alt="Suricata 1" src="https://github.com/user-attachments/assets/a9c1cd03-0a7c-4571-abc4-2c1ecc98ef8a" />


*2️⃣ Creating Custom Suricata Rule File*
A custom.rules file is created and opened for editing. This file contains user-defined detection signatures to be tested against network traffic.
(Screenshot: nano editor with rule creation)
<img width="935" height="435" alt="Suricata 2" src="https://github.com/user-attachments/assets/d6fda8cf-7a00-4efa-ae7f-47c6934e1a20" />


*3️⃣ Adding an HTTP GET Detection Rule*
A rule is added to trigger on HTTP traffic containing a specific keyword in the request URI. The rule specifies the alert action, protocol, source/destination, and matching content.
(Screenshot: Suricata rule syntax inside custom.rules)
<img width="938" height="476" alt="Suricata 3" src="https://github.com/user-attachments/assets/61ffddcc-3039-4ea2-8820-496578fc9466" />


*4️⃣ Running Suricata Against a Packet Capture File*
The command runs Suricata with the -r option to process sample.pcap using the custom rules. This simulates real network traffic and allows testing of detection accuracy.
(Screenshot: Suricata executing with a PCAP file)
<img width="935" height="157" alt="Suricata 4" src="https://github.com/user-attachments/assets/5c85236c-4bc5-4076-9c46-470f576e74fe" />


*5️⃣ Reviewing Alerts in fast.log*
The fast.log file is opened to verify rule matches. Each line corresponds to an alert triggered by the custom rule. This quick-reference log helps confirm initial detection success.
(Screenshots: fast.log content showing alert entries)
<img width="776" height="599" alt="Suricata 5 part 1" src="https://github.com/user-attachments/assets/1044bce9-a79c-4a16-a08e-ab39e15ed075" />
<img width="510" height="251" alt="Suricata 5 part 2" src="https://github.com/user-attachments/assets/be0c6ccd-5de4-4ccd-9a29-ab9c3a6b4188" />



*6️⃣ Analyzing Detailed Alerts in eve.json*
The eve.json file is examined to view structured, JSON-formatted event data, including timestamps, source/destination IPs, and matched rule content.
(Screenshot: eve.json event output)
<img width="934" height="159" alt="Suricata 6" src="https://github.com/user-attachments/assets/9324f589-9ad3-46a7-aa69-b79060275310" />


*7️⃣ Filtering JSON Output with jq*
Using jq, specific alert fields are extracted for cleaner review, making it easier to focus on key data points from Suricata’s logs.
(Screenshot: jq command extracting fields from eve.json)
<img width="938" height="96" alt="Suricata 7" src="https://github.com/user-attachments/assets/a0d8b7d2-0c69-44e5-a431-882c472a6b0e" />


*8️⃣ Final Validation of Detection Workflow*
The successful correlation of the packet capture, rule match, and log output confirms that Suricata is detecting the intended traffic patterns.
(Screenshot: summary of detection results in terminal)

##✅ Outcome:
This lab demonstrated the complete process of creating a Suricata rule, applying it to recorded network traffic, and validating alerts through both quick and detailed log formats. The results confirmed the rule’s accuracy and the ability of Suricata to detect specific traffic patterns effectively.
