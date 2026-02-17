# SOC Alert Investigations

This repo shows a real phishing alert investigation I completed using Splunk (SIEM).
 
The goal of this project was to practice how SOC analysts triage alerts, validate whether they are real threats, and document their findings.

---

## Project: Phishing Email Investigation

A security alert was triggered for a suspicious inbound email coming from an external domain.  
My task was to investigate the alert in Splunk and determine if it was a True Positive or False Positive.

---

## What Happened

The security system flagged an email as suspicious because it came from an external domain using an unusual top-level domain (.me).

Basically, the system said:
"Hey… this email looks sketchy. Someone should check it."

So I investigated it using Splunk.

---

## Investigation Workflow (SOC Triage Process)

### 1. Search the correct log source
I started by searching email logs in Splunk:

index=* datasource=email

This filtered the data down to only email activity.

---

### 2. Fix the time range (common SOC step)
Initially, no logs appeared because Splunk was only searching the last 6 hours.

I expanded the time range to include the alert timestamp.

This is a very common real-world SIEM troubleshooting step.

---

### 3. Narrow down to the affected mailbox
I filtered logs to the recipient mailbox:

recipient="support@tryhatme.com"

This reduced the data from all company emails → emails sent to the affected user.

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

**TRUE POSITIVE — Confirmed phishing attempt**

Meaning the alert correctly identified a real threat.

---

## Recommended Remediation (What a SOC would do)

• Block the sender domain at the email gateway  
• Search for similar emails across the environment  
• Notify the recipient not to interact with the message  

---

## Skills Demonstrated

• Splunk SIEM searching  
• Log filtering and time range troubleshooting  
• Email threat investigation  
• Alert triage (True Positive vs False Positive)  
• Basic incident documentation  

---

This project simulates the type of investigation performed by an entry-level SOC analyst.
