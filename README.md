Detection Lab

Objective
The purpose of this lab was to simulate the role of a security analyst by monitoring network traffic with Suricata, configuring and testing custom detection rules, and analyzing Suricata’s output logs. The activity involved working with pre-supplied packet capture (PCAP) data and rule files to trigger alerts, examine Suricata’s fast log format for quick checks, and review the more detailed JSON output for in-depth analysis.

Skills Learned
Configuring and testing custom intrusion detection system (IDS) rules in Suricata.

Using packet capture (PCAP) files to simulate network traffic for analysis.

Interpreting Suricata’s fast.log output for quick alert validation.

Parsing and analyzing Suricata’s eve.json log for detailed telemetry.

Extracting and filtering JSON log data using the jq command.

Understanding IDS rule components: action, header, and rule options.

Tools Used
Suricata – for network traffic monitoring and alert generation.

sample.pcap – packet capture file containing test network traffic.

custom.rules – file for defining and modifying Suricata rules.

fast.log – Suricata’s quick alert output log.

eve.json – Suricata’s standard, detailed JSON log format.

jq – command-line JSON processor for querying log data.

Linux Bash Shell – for executing Suricata commands and log queries.

Steps
1. Examine a Custom Rule in Suricata

Located and viewed the custom.rules file using cat custom.rules.

Broke down the rule into its action, header, and rule options.

Identified how the rule alerts on HTTP GET requests from $HOME_NET to $EXTERNAL_NET.

2. Trigger a Custom Rule

Verified /var/log/suricata directory before execution (empty at start).

Ran Suricata with:

bash
Copy
Edit
sudo suricata -r sample.pcap -S custom.rules -k none
Observed the creation of fast.log and eve.json after Suricata processed the PCAP file.

Used cat /var/log/suricata/fast.log to confirm that alerts were triggered and recorded.

3. Examine eve.json Output

Displayed raw eve.json content with cat, then reformatted with jq . /var/log/suricata/eve.json | less.

Located the severity property of the first alert (value: 3).

Extracted key fields with:

bash
Copy
Edit
jq -c "[.timestamp,.flow_id,.alert.signature,.proto,.dest_ip]" /var/log/suricata/eve.json
Identified:

Destination IP for last event: 142.250.1.102.

First alert signature: "GET on wire".

Queried all logs for a specific flow using:

bash
Copy
Edit
jq "select(.flow_id==X)" /var/log/suricata/eve.json
Conclusion
This lab provided hands-on experience with Suricata IDS, from creating and understanding detection rules to running them against simulated traffic and interpreting the results. The workflow demonstrated:

How to define and test custom IDS rules.

How to use PCAP files for repeatable detection testing.

How to read and analyze both quick alert logs and comprehensive JSON event logs.



*Ref 1: Network Diagram*
