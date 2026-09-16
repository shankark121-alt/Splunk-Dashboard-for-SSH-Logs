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

<img width="1393" height="601" alt="image" src="https://github.com/user-attachments/assets/48aee767-0616-41b5-a702-91d1071cdfe8" />

# **Authentication Overview Panels**

Goal: Give a quick summary of SSH activity.

1 Total SSH Events

Click on Add Panel

Under New, choose Single Value

Use Shared Time Picker time_range

Set Content Title to "Total SSH Events"

Enter the Search String as below

source="ssh_logs.json" host="LinuxServer" sourcetype="_json"
 | stats count AS "Total SSH Events"

<img width="1395" height="626" alt="image" src="https://github.com/user-attachments/assets/88ef7831-1d16-48e6-80d6-3cc8ad2adef3" />

2.Successful Logins

Click on Add Panel

Under New, choose Single Value

Use Shared Time Picker time_range

Set Content Title to "Successful Logins"

Enter the Search String as below:

source="ssh_logs.json" host="LinuxServer" sourcetype="_json" event_type="Successful SSH Login" 
| stats count AS "Successful Logins"

<img width="1404" height="638" alt="image" src="https://github.com/user-attachments/assets/f561da04-0f27-47f2-ae5e-dfb3b2245056" />

3.Failed Logins

Click on Add Panel

Under New, choose Single Value

Use Shared Time Picker time_range

Set Content Title to "Failed Logins"

Enter the Search String as below:

source="ssh_logs.json" host="LinuxServer" sourcetype="_json" event_type="Failed SSH Login"
| stats count AS "Failed Login"
   
<img width="1389" height="638" alt="image" src="https://github.com/user-attachments/assets/840c8846-9a0b-4ad9-be99-c7d733447349" />

4. Connection without Authentication
   
 Click on Add Panel

Under New, choose Single Value

Use Shared Time Picker time_range

Set Content Title to "Invalid User Attempts"

Enter the Search String as below:

index=auth "sshd" "invalid user"
| stats count AS "Invalid User Attempts"

<img width="1403" height="709" alt="image" src="https://github.com/user-attachments/assets/f0c9302f-8885-4490-b708-01344457720c" />


# **Login Activity Trends**

Goal: Visualize login behavior over time and detect spikes.

1. Failed Logins by username
   
Click on Add Panel

Under New, choose Bar Chart

Use Shared Time Picker time_range

Set Content Title to "Failed Logins by username"

Enter the Search String as below:

source="ssh_logs_new.json" host="LinuxNew" sourcetype="_json" event_type="Failed SSH Login" | top username

<img width="1404" height="604" alt="image" src="https://github.com/user-attachments/assets/a52d1b6f-0afd-4480-b846-b8ee558ec9e1" />

2. Possible Brute Force
   
Click on Add Panel

Under New, choose Statstics Table

Use Shared Time Picker time_range

Set Content Title to Possible Brute Force b IP Address

Enter the Search String as below:

source="ssh_logs_new.json" host="LinuxNew" sourcetype="_json" event_type="Multiple Failed Authentication Attempts" | top id.orig_h

# **Visualizing Brute Force attack in geo-location**

Click on Add Panel

Under New, choose Choropleth Map

Use Shared Time Picker time_range

Set Content Title to Brute Force attack with geo-location

Enter the Search String as below:

source="ssh_logs_new.json" host="LinuxNew" sourcetype="_json" event_type="Multiple Failed Authentication Attempts" 
| table id.orig_h
| iplocation id.orig_h
| stats count by Country
| geom geo_countries featureIdField="Country"

<img width="1479" height="681" alt="image" src="https://github.com/user-attachments/assets/376be176-5eed-4a64-9d4f-5fdee7c719d5" />

<img width="1459" height="654" alt="image" src="https://github.com/user-attachments/assets/b39d6de9-b631-4ecf-877e-ed69e540c11d" />

# **Final Dashboard**

<img width="1384" height="697" alt="image" src="https://github.com/user-attachments/assets/5340eb4a-9ad9-474b-be2d-57ee3759dc58" />









