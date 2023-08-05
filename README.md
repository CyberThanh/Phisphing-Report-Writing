
# Case Scenario 
You investigated a phishing email that was sent to a user with malicious intentions.  You have analyzed the email content and collected artifacts. Now, it is time to write a report of your findings and recommend defensive measures. 

# Collected Artifacts
-----------------
## Email Artifacts

Sending Address:
service@paypal.com

Subject Line:
Your PayPal account has been used to purchase Google Pixel for $589 It will be deducted by automated system in next 24hrs. Call us +1(844) 583-2828 to cancel & claim a refund.

Recipients:
t-------@aol.com

Sending Server IP:
52.102.139.16

Resolve Host:	
mail-centralusazhn15012016.outbound.protection.outlook.com

Reply-To:
JanetHiroshima567@outlook.com

Date and Time:
28 Mar 2023 6:33 PM

URL:
hxxps://w(.)w(.)w.paypal.co(.)m/invoice/payerView/details/INV2-4FN7-9YPZ-YUHA-H6CE?cc-email=true%3Flocale.x%3Den_US&v=1&utm_source=unp&utm_medium=email&utm_campaign=RT000274&utm_unptid=1597ff18-cd7e-11ed-8041-3cfdfef08b90&ppid=RT000274&cnac=US&rsta=en_US%28en-US%29&cust=&unptid=1597ff18-cd7e-11ed-8041-3cfdfef08b90&calc=f5977839a3fca&unp_tpcid=invoice-buyer-reminder&page=main%3Aemail%3ART000274&pgrp=main%3Aemail&e=cl&mchn=em&s=ci&mail=sys&appVersion=1.156.0&xt=104038%2C124817

Upon analysis, this email seems to have come from a spoofed email address of PayPal. This email was a well designed email with great styling and no grammatical errors.  However, the reply-to is a Outlook address. The email is informing recipient that their someone access their PayPal account to purchase a Google Pixel for $589 and a link to view the invoice.  

![FakePayPal Email](https://i.imgur.com/C3RWNaw.jpg)

![Email Artifacts](https://i.imgur.com/CsL4snn.jpg)

![Email Artifacts](https://i.imgur.com/ijoo1xc.jpg)


-----------
# Analysis
-----------

A lookup using Mxtools display DMARC, SPF, and DKIM errors. 
A reverse DNS search was performed and the IP address was linked to a outlook account and not from PayPal. 
URL2PNG displays the URL direct users to a page that notifies us that the invoice was a scam.  
A URL search using VirtualTotal and URLBrowser came back clean.  However, a url sandbox using Hybrid Analysis indicate that this url is suspicious. 

![Analysis](https://i.imgur.com/Hs6Rfx8.jpg)

![Analysis](https://i.imgur.com/XSBZr7l.jpg)

![Analysis](https://i.imgur.com/qkQtdKZ.jpg)

![Analysis](https://i.imgur.com/YpFhAtH.jpg)

![Analysis](https://i.imgur.com/baE3v3y.jpg)

![Analysis](https://i.imgur.com/sU9jhNU.jpg)

![Analysis](https://i.imgur.com/xjnnew5.jpg)

--------------------------------
# Recommended Defensive Measures
--------------------------------
The recommended defensive step to combat this phishing email is to block the sender's Outlook address. This will prevent emails from this sender from getting through.  Therefore, an email block should be implemented on the address "JanetHiroshima567@outlook.com"
