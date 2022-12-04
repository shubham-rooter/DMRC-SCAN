# DMRC-SCAN
# dmarcscan
Bulk **Domain-based Message Authentication, Reporting and Conformance** scanner.

## Background

### What is DMARC?

DMARC also known as Domain-based Message Authentication Reporting and Conformance is a free and open technical specification that is used to authenticate an email by aligning SPF and DKIM mechanisms. By having DMARC in place, domain owners large and small can fight business email compromise, phishing and spoofing.

During my last year bug hunting activity, missing DMARC on email domain is vulnerability that worth to be reported to program owners. According to [Bugcrowd VRT](https://bugcrowd.com/vulnerability-rating-taxonomy), this finding has **P4** Priority.
```
Server Security Misconfiguration > Mail Server Misconfiguration > Email Spoofing to Inbox due to Missing or Misconfigured DMARC on Email Domain
```
Example of valid finding on Bogcrowd:
![Missing DMARC](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEifRzuXQbLKDfIsIiwH_DP-I85iZvAzhP1J_S0QTBgDrFj3XLivjHlW9PhE2SHLhATLzWuZ2Hk05JxZePeu3urVg9Xrcc5wwr9xbc4_CCPwTGz-YbzrD6ZYqcz7CZJ9CcLLSLy48hOzsjA0R6QmeXtlCOrXCpN9btZF03JwICZhi10PN-11QYhka63YRA/s700/dmarc%20not%20enabled.png "Missing DMARC")

So, i create this tool to check is DMARC enabled or missing from domain.

## How to Use
Print Help
```
┌──(shubham㉿Rooter)-[~/dmarcscan]
└─$ bash dmarcscan.sh 
░██████╗██╗░░██╗██╗░░░██╗██████╗░██╗░░██╗░█████╗░███╗░░░███╗  ██████╗░░█████╗░░█████╗░████████╗███████╗██████╗░
██╔════╝██║░░██║██║░░░██║██╔══██╗██║░░██║██╔══██╗████╗░████║  ██╔══██╗██╔══██╗██╔══██╗╚══██╔══╝██╔════╝██╔══██╗
╚█████╗░███████║██║░░░██║██████╦╝███████║███████║██╔████╔██║  ██████╔╝██║░░██║██║░░██║░░░██║░░░█████╗░░██████╔╝
░╚═══██╗██╔══██║██║░░░██║██╔══██╗██╔══██║██╔══██║██║╚██╔╝██║  ██╔══██╗██║░░██║██║░░██║░░░██║░░░██╔══╝░░██╔══██╗
██████╔╝██║░░██║╚██████╔╝██████╦╝██║░░██║██║░░██║██║░╚═╝░██║  ██║░░██║╚█████╔╝╚█████╔╝░░░██║░░░███████╗██║░░██║
╚═════╝░╚═╝░░╚═╝░╚═════╝░╚═════╝░╚═╝░░╚═╝╚═╝░░╚═╝╚═╝░░░░░╚═╝  ╚═╝░░╚═╝░╚════╝░░╚════╝░░░░╚═╝░░░╚══════╝╚═╝░░╚═╝ 
   Domain-based Message Authentication, Reporting and Conformance Scanner

Example: bash dmarc-multiprocess.sh -l domain.txt -t 30
options:
-l     Files contain lists of domain.
-d     Single domain check
-t     Adjust multi process. Default is 15
-h     Print this Help.

```
Bulk DMARC check from the lists.
```
bash dmarcscan.sh -l domains.txt -t 30
```
Single domain check
```
bash dmarcscan.sh -d linuxsec.org
```

Basicly, this tool will run **dig** command to check DMARC existence on target. 
- If DMARC exist on target, you will get **Found** result. 
- If DMARC exist but using **p=none**, you will get **p=none Found** result. 
- And if there is no DMARC record on target, you will get **Not Found** result.

This is good write up about exploiting this kind of vulnerability and reporting to program owners.
## Screenshot
![image](https://user-images.githubusercontent.com/94091556/205486349-7b45cc87-ff8c-4df1-abeb-00fac93021f3.png)

Feel free to contribute if you want to improve this tools.
