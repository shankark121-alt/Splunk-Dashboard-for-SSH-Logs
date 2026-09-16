# **1.OBJECTIVE**

The objective of this project is to collect, ingest, search, and analyze SSH authentication logs using Splunk Enterprise.

The project focuses on identifying:

Successful SSH login attempts

Failed SSH authentication attempts

Multiple failed login attempts

Suspicious login activity

Source IP addresses

Login usernames

Authentication patterns

Potential brute-force attacks

This project demonstrates practical SIEM, Log Analysis, Security Monitoring, and Threat Detection skills.

# **2.LAB ENVIRONMENT**

Component	Details

SIEM	Splunk Enterprise

Operating System	Kali Linux

Splunk IP	192.168.227.128

Splunk Web	http://192.168.227.128:8000

Log Type	SSH Authentication Logs

Log Format	JSON

Sourcetype	_json

Hdostost	kali

Index	ssh

<img width="1382" height="576" alt="image" src="https://github.com/user-attachments/assets/70390bc2-86ad-40b3-9c0d-716183791040" />

<img width="1399" height="628" alt="image" src="https://github.com/user-attachments/assets/b35de15b-eff7-4dd7-a983-b159c2d609d4" />

<img width="1202" height="528" alt="image" src="https://github.com/user-attachments/assets/6c8e61f7-14f3-40a8-b469-e53ad425a016" />


# **Setting up Time Range**

Add Time Range Button

Click on Add Input

Select Time and click on pencil icon

Set Label to Time Range and Token time_range

Again Add Input

Select Submit
Note: For all future panel, set the time to time_range for consistency.


