# Case Scenario 
You investigated a phishing email that was sent to a user with malicious intentions.  You have analyzed the email content and collected artifacts. Now, it is time to write a report of your findings and recommend defensive measures. 

----------------------
# Collected Artifacts
----------------------
## Email Artifacts

Sending Address:
service@paypal.com

Subject Line:
Your PayPal account has been used to purchase Google Pixel for $589 It will be deducted by automated system in next 24hrs. Call us +1(844) 583-2828 to cancel & claim a refund.

Recipients:
t-------@aol.com

Originating IP:
52.102.139.16

Resolve Host:	
mail-centralusazhn15012016(.)outbound(.)protection(.)outlook(.)com

Reply-To:
JanetHiroshima567@outlook(.)com

Date and Time:
28 Mar 2023 6:33 PM

URL:
hxxps://w(.)w(.)w.paypal.co(.)m/invoice/payerView/details/INV2-4FN7-9YPZ-YUHA-H6CE?cc-email=true%3Flocale.x%3Den_US&v=1&utm_source=unp&utm_medium=email&utm_campaign=RT000274&utm_unptid=1597ff18-cd7e-11ed-8041-3cfdfef08b90&ppid=RT000274&cnac=US&rsta=en_US%28en-US%29&cust=&unptid=1597ff18-cd7e-11ed-8041-3cfdfef08b90&calc=f5977839a3fca&unp_tpcid=invoice-buyer-reminder&page=main%3Aemail%3ART000274&pgrp=main%3Aemail&e=cl&mchn=em&s=ci&mail=sys&appVersion=1.156.0&xt=104038%2C124817

Upon analysis, this email seems to have come from a spoofed email address of PayPal. This email was a well designed email with great styling and no grammatical errors.  However, the reply-to is an Outlook address. The email is informing recipient that their someone access their PayPal account to purchase a Google Pixel for $589 and a link to view the invoice.  Attached to the email is a questionable link to is will supposedly direct the recipient to a page to the invoice.  

Spoofed PayPal Invoice Email
![FakePayPal Email](https://i.imgur.com/C3RWNaw.jpg)

Raw Data From Email
![Email Artifacts](https://i.imgur.com/CsL4snn.jpg)

![Email Artifacts](https://i.imgur.com/ijoo1xc.jpg)


-----------
# Analysis
-----------

A lookup using Mxtools display DMARC, SPF, and DKIM errors. 
A reverse DNS search was performed and the IP address was linked to a outlook account and not from PayPal. 
URL2PNG displays the URL direct users to a page that notifies us that the invoice was a scam.  
A URL search using VirtualTotal and URLBrowser came back clean.  However, a url sandbox using Hybrid Analysis indicate that this url is suspicious. 

DMARC Error - Suspcious since DMARC acts like security guard for recipent's mailbox to check and ensure emails originate from the source is who the the sender claims to be and prevent fake emails.  

![Analysis](https://i.imgur.com/Hs6Rfx8.jpg)

SPF Alighment Error - Suspicious since SPF alignment verify the legitimacy of the email by checking that the email orginated domain matches the domain of the actual sending server.

![Analysis](https://i.imgur.com/XSBZr7l.jpg)

DKIM Authentication Error - Supicious since DKIM authentication allow email servers to verify a digital signature ensure email was not tampered.  

![Analysis](https://i.imgur.com/qkQtdKZ.jpg)

Performed a reverse DNS lookup using domain tools to investigate sender's originating IP address and the source resolved host. 

![Analysis](https://i.imgur.com/YpFhAtH.jpg)

Utilized URL2PNG to visulize the page users will be directed to when they click on the link to determine the safety and legitimacy of the URL. 

![Analysis](https://i.imgur.com/baE3v3y.jpg)

Utilized Hybrid Analysis to sandbox the URL.  

![Analysis](https://i.imgur.com/sU9jhNU.jpg)

![Analysis](https://i.imgur.com/xjnnew5.jpg)

## Summary 
This email was flagged as a phishing email within the environment.  Throughout the investigation, domain tools, sandbox, email records, URL scanners were utilized to analyze the level of maliciousness in this email. The investigation analysis results display that this was a true positive and this email was not legitimate. Pending peer review from fellow analysis.

The next section will highlight recommend defensive measures.

<details close>

<div>
  
--------------------------------
# Recommended Defensive Measures
--------------------------------
## If user interacted with malicious link or attachment that contained a malware

Recommeded step include adhering to the Malware Incident Response Playbook:

Preparation:
- Determine the members of the Cybersecurity Incident Response Team (CSIRT).
- Identify escalation paths.
- Evaluate and confirm that backups are secure and not impacted by the incident.

Idenitification:
- Isolate infected systems.
- Preserve affected systems for forensic investigation.
- Analyze malware to determine characteristics in a sandboxed environment and monitor for any network connectivity attempts, any files that has been created or modified by malware, the location malware is located, preserve a copy of the malware file, retrieve all revalent hashes for malware files and documents these as Indicator of Compromise (IOCs).
- Analyze all information and IOCs to determine additional hosts, determine if malware is associated with further attacks, and inital point of entry.

Containment: 
- Utilize information on intial entry point to close any gaps, such as, firewall misconfiguration and email rules misconfiguration.
- If additional hosts were found to be infected, then appropriate measure to isolate associated systems to these hosts must be taken.
- Submit hash value to community sources, such as, VirusTotal.

Eradication: 
- Preserve artifacts, systems, and relevant backups.
- Preserve collected volatile data.  

Recovery:
- Restore affected systems from clean backups that was before the infection. 
- Rebuild machines that were not restorable from backups.
- Remediate any vulnerabilities and gaps that were found during the investigation.
- Reset all passwords for affected accounts.
- Monitor malicious activity related to the incident.

Lesson Learned:
- Answer the following questions
    What went well during the investigation?
    What could be improved during the investigation?
    What vulnerabilities or security gaps i that were identified?
    How will or were these vulnerabilities or gaps be remediated?
    What actions can be taken to prevent similar incidents in the future?

## If user click on just a general phishing link
- Check network event logs or organization's VPN logs to document which users click on the link and when they click on the link.
- If the logs show no user interaction, then escalate to tune out the sender.  
- If the logs show the user clicked on the link, then escalate to analyze the system to determine the type of phisphing attack.
- After the investigation, suggest users who clicked on the link or open attachment for additional phishing awareness training.  
  
