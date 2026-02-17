# SOC Alert Investigations

This repo shows a real phishing alert investigation I completed using the SIEM Tool Splunk. 
 
The goal of this project was to practice how Tier 1 SOC analysts triage alerts, validate whether they are real threats, and document their findings.
In this project, the alert I investigated was a phishing email. Below I will provide the steps I used to triage the alert and what 
what my observations were about the alert.

---

## Project: Phishing Email Investigation

A security alert was triggered for a suspicious inbound email coming from an external domain.  
My task was to investigate the alert in Splunk and determine if it was a True Positive or False Positive.

---

## What Happened

The security system flagged an email as suspicious because it came from an 
external domain using an unusual top level domain (.me).



---

## SOC Triage Process 

### 1. Search the correct log source
Logs are the timeline a SOC uses to investigate what happened on a system or network.
They record things like logins, errors, process activity, and network connections, 
and analysts use them in a SIEM to detect alerts, investigate incidents, and figure 
out if something malicious is going on.

I started by searching email logs in Splunk:
index=* datasource=email

This filtered the data down to only email activity.

---

### 2. Fix the time range 
Initially, no logs appeared because Splunk was only searching the last 6 hours.

I expanded the time range to include the alert timestamp which was a crucial step 
because initially I had an issue finding the time due to so many alerts at that time. 

### 3. Narrow down to the affected mailbox
I filtered logs to the recipient mailbox:

recipient="support@tryhatme.com"

This reduced the data from all company emails down to emails sent to the affected user.

---

### 4. Filter to the suspicious sender
Next I filtered using the sender email:

sender="eileen@trendymillineryco.me"

This located the exact email that triggered the alert.

---

### 5. Analyze the email content
After reviewing the event, I identified multiple phishing indicators:

• External sender domain  
• Financial inheritance scam language  
• Request for sensitive banking information  
• Generic non-personalized message  

---

## Alert Classification

After reviewing the evidence, the alert was classified as:

**TRUE POSITIVE - Confirmed phishing attempt**

Meaning the alert correctly identified a real threat.

---

## Recommended Remediation 

In this phishing attempt, I recommend that:

• Block the sender domain at the email gateway  
• Search for similar emails across the environment  
• Notify the recipient not to interact with the message  

---

## Skills Demonstrated

• Splunk SIEM searching  
• Log filtering and time range troubleshooting  
• Email threat investigation  
• Alert triage   
• Basic incident documentation  



