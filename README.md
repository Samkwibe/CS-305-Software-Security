# CS 305 Software Security – Artemis Financial Portfolio

Demonstrating secure software development practices, including vulnerability assessment, 
dependency analysis, HTTPS implementation, and cryptographic hashing for a financial services client.

---

## Table of Contents

- [About the Project](#about-the-project)
- [Artifacts](#artifacts)
- [Journal Reflection](#journal-reflection)
- [Tools and Technologies](#tools-and-technologies)
- [Contact](#contact)

---

## About the Project

This repository contains portfolio artifacts completed during CS 305: Software Security 
at Southern New Hampshire University. The projects involved working with a fictional 
client, Artemis Financial, to assess software vulnerabilities and implement secure 
coding practices in a Java-based Spring Boot web application.

---

## Artifacts

- **Artemis Financial Vulnerability Assessment Report** – A detailed report identifying 
security vulnerabilities in the client's web application, including dependency analysis 
using the OWASP Dependency-Check tool and recommended mitigation strategies.

- **Artemis Financial Practices for Secure Software Report** – Documentation of secure 
coding implementations, including HTTPS configuration via SSL, SHA-256 cryptographic 
hashing for data integrity, and post-refactor vulnerability verification.

---

## Journal Reflection

### Briefly summarize your client, Artemis Financial, and its software requirements. Who was the client? What issue did the company want you to address?

Artemis Financial is a financial consulting company that specializes in helping 
individual clients build personalized and comprehensive financial plans. Their services 
cover a wide range of financial needs, including savings accounts, retirement planning, 
investment strategies, and insurance coverage. Because the nature of their business 
involves handling highly sensitive personal and financial information on a daily basis, 
security is not just a feature for them — it is a fundamental requirement for operating 
responsibly and maintaining the trust of their clients.

The company came to us because they were looking to modernize their software and 
strengthen the overall security of their web-based application. While they had an 
existing system in place, they recognized that it had not been thoroughly evaluated for 
security vulnerabilities and that as technology evolves, so do the threats that target 
it. They wanted a professional assessment that would help them understand where their 
weaknesses were, how serious those weaknesses were, and what steps they should take to 
address them. Specifically, they were concerned about protecting data in transit, 
ensuring the integrity of the information moving through their system, and making sure 
that any third-party libraries or dependencies they were using did not introduce known 
vulnerabilities into their application.

My role in this project was to step into the position of a software security consultant 
and take a close, methodical look at their application. That meant examining the 
codebase, running vulnerability scans, researching the results, and producing a report 
that communicated the findings in a way that was both technically accurate and 
understandable to people who may not have a deep background in cybersecurity. The goal 
was not just to find problems but to help Artemis Financial understand the risks they 
were facing and feel confident moving forward with a more secure system.

---

### What did you do well when you found your client's software security vulnerabilities? Why is it important to code securely? What value does software security add to a company's overall well-being?

I think one of the things I did well was being thorough and not just skimming the 
surface. I used the OWASP Dependency-Check tool to scan the project's dependencies and 
took the time to actually read through the results rather than just noting how many 
vulnerabilities were flagged. I looked up individual CVEs to understand what they meant 
in the context of Artemis Financial's application specifically. I also tried to 
communicate my findings clearly, which I think is just as important as finding the 
vulnerabilities in the first place — if you can't explain the risk in a way that makes 
sense to stakeholders, the information doesn't lead to action.

Coding securely matters because the consequences of not doing so can be devastating. 
For a financial company especially, a data breach doesn't just mean a technical problem 
— it means real people's money, personal information, and trust are on the line. Beyond 
the human impact, there are serious legal and regulatory consequences that come with 
failing to protect client data. Things like GDPR, PCI-DSS, and other compliance 
standards exist precisely because the stakes are so high. Software security adds 
enormous value to a company's overall well-being because it protects the business from 
financial losses, legal liability, and reputational damage. A company that prioritizes 
security is a company that clients can trust, and trust is everything in the financial 
industry.

---

### Which part of the vulnerability assessment was challenging or helpful to you?

Honestly, the most challenging part was working through the OWASP Dependency-Check 
report and figuring out which vulnerabilities were actually relevant and which ones were 
false positives. The report generates a lot of output, and not every flagged item is 
necessarily a real risk in the context of the specific application you are working with. 
I had to do a lot of research on individual CVEs to understand the nature of each 
vulnerability — things like how it could be exploited, whether the affected functionality 
was even being used in the project, and how severe the potential impact would be.

That process was frustrating at times because it was time-consuming, but it was also the 
most educational part of the whole assignment. It pushed me to actually understand what I 
was looking at rather than just running a tool and copying the output. Going through that 
process gave me a much better sense of how to think critically about security findings 
rather than treating every flag as equally urgent. I walked away from that part of the 
project with a skill set that I know will carry into real professional work.

---

### How did you increase layers of security? In the future, what would you use to assess vulnerabilities and decide which mitigation techniques to use?

To increase the layers of security in the application, I implemented HTTPS by generating 
a self-signed certificate and configuring the Spring Boot application to use SSL. This 
ensured that data in transit between the client and server would be encrypted rather than 
sent in plain text. I also added a checksum verification feature using the SHA-256 
hashing algorithm, which allows the application to verify the integrity of data and 
detect if anything has been tampered with. These two additions worked together to address 
both confidentiality and integrity, which are two of the core principles of information 
security.

In the future, I would continue using the OWASP Dependency-Check tool as a baseline for 
identifying known vulnerabilities in third-party libraries and dependencies. I would also 
incorporate static code analysis tools like SonarQube to catch issues in the code itself, 
not just in the dependencies. Beyond automated tools, I think regular code reviews and 
penetration testing are important practices that help catch things automated scanners 
might miss. When it comes to deciding which mitigation techniques to prioritize, I would 
use a risk-based approach — looking at the severity of the vulnerability, how likely it 
is to be exploited, and what the potential impact would be if it were. Not every 
vulnerability needs to be fixed immediately, but having a clear process for deciding what 
gets addressed first is essential.

---

### How did you make certain the code and software application were functional and secure? After refactoring the code, how did you check to see whether you introduced new vulnerabilities?

To make sure the application was functional after my changes, I ran the application 
locally and tested the endpoints to verify they were responding correctly and that the 
HTTPS configuration was working as expected. I also checked that the checksum 
functionality was producing the correct hash output for given inputs. After refactoring 
the code, one of the most important steps I took was running the OWASP Dependency-Check 
report again and comparing the results to the report I had generated before making 
changes. This side-by-side comparison helped me confirm that I had not introduced any new 
vulnerable dependencies or made changes that would create new exposure.

I also reviewed my own code carefully to look for common mistakes like hardcoded 
credentials, improper error handling, or anything that might unintentionally expose 
sensitive information. Testing and verification are not steps you can skip when working 
on security-focused code, because a change that fixes one problem can easily introduce 
another if you are not paying close attention.

---

### What resources, tools, or coding practices did you use that might be helpful in future assignments or tasks?

There were several tools and resources I relied on heavily throughout this project that I 
think will continue to be useful going forward. The OWASP Dependency-Check Maven plugin 
was essential for identifying vulnerable dependencies, and it is something I would add to 
virtually any Java project I work on in the future as a standard part of the build 
process. I also used the National Vulnerability Database and the CVE database to research 
individual vulnerabilities, and being comfortable navigating those resources is a valuable 
skill in itself.

On the coding side, working with Java's `MessageDigest` class for hashing and Spring 
Security for configuring HTTPS gave me hands-on experience with security implementation 
that I had mostly only read about before. Going forward, I also want to keep building the 
habit of running security checks early and often rather than treating it as something you 
do at the end of a project. Security is much easier to build in from the beginning than 
to bolt on after the fact, and this project really drove that lesson home for me.

---

### Employers sometimes ask for examples of work that you have successfully completed to show your skills, knowledge, and experience. What might you show future employers from this assignment?

I would be proud to show a future employer the Vulnerability Assessment Report from this 
project. I think it demonstrates a few things that are genuinely hard to show without 
concrete examples. First, it shows that I know how to use industry-standard tools like 
OWASP Dependency-Check to identify real security risks, not just what I have heard of 
them. Second, it shows that I can think critically about findings rather than just 
regurgitating tool output — I had to analyze each vulnerability in context and make 
judgment calls about relevance and severity. Third, and maybe most importantly, it shows 
that I can communicate technical findings clearly and professionally to an audience that 
may not have a deep technical background. A lot of security work ultimately comes down to 
convincing people to take action, and that requires clear communication.

I would also point to the secure coding work I did in Project Two, which shows that I can 
move from identifying problems to actually implementing solutions — things like enabling 
HTTPS and building checksum verification into the application. Together, I think these 
artifacts give a well-rounded picture of both the analytical and hands-on sides of 
software security work, and I believe they reflect the kind of careful, thoughtful 
approach that employers in this field are looking for.

---

## Tools and Technologies

- Java / Spring Boot
- OWASP Dependency-Check Maven Plugin
- SSL / HTTPS (Self-Signed Certificate)
- SHA-256 Cryptographic Hashing (Java `MessageDigest`)
- National Vulnerability Database (NVD)
- CVE Database
- Maven

---

## Contact

**Your Name**  
Southern New Hampshire University  
GitHub: https://github.com/Samkwibe  
Email: samuel.kwibe@snhu.edu
