## Case Scenario 
You investigated a phishing email that was sent to a user with malicious intentions.  You have analyzed the email content and collected artifacts. Now, it is time to write a report of your findings and recommend defensive measures. 

## Collected Artifacts
-----------------

## Email Artifacts

Sending Address:
securityteam@companya.com

Subject Line:
We have detected unusual activity. Please update your password NOW! 

Recipients:
alex.anderson@companya.com
josh.howen@companya.com
aleina.smith@companya.com

Sending Server IP:
294.142.185.121

Reverse DNS:
mail-mg3-d124.google.com (gmail)

Reply-To:
adil.byuk@gmail.com

Date and Time:
11:05 AM Thursday 20th July 2023

URL:
hxxps://gmail-security.alert(.)net/index/2023/OWA.php?

Root Domain:
hxxps://alert(.)net

Upon analysis, this email seems to have come from a spoofed email address of securityteam@companya.com. However, the reply-to is a Gmail address. The email is informing recipients that their email accounts has been hacked and used a sense of urgency to make them click on the malicious URL.  

-----------
## Analysis
-----------

A reverse DNS search was performed and the IP address was linked to a Gmail account and not from Companya address.
A URL search using Hybrid Analysis displayed that this url has been flagged as malicious activity.  
URL2PNG displays the URL direct users to an Outlook credential harvester page that is asking them to enter their email address and their new password.  

--------------------------------
## Recommended Defensive Measures
--------------------------------
The first defensive step that should be taken is to block the sender's Gmail address. This will prevent emails from this sender from getting through.  Therefore, an email block should be implemented on the address "adil.byuk@gmail.com"

Upon analysis, the domain hxxps://alert(.)net was found to be used for pure malicious intentions and employees have no business to visit this site.  Therefore, we can conclude that it would be best to block the domain hxxps://alert(.)net. 
