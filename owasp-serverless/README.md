# Protect your Serverless App against OWASP Top 10

OWASP Top 10 Security Risks

1. Broken access control
2. Cryptography failures
3. Event Injection
4. Insecure design: application design flow.
5. Security misconfiguration: over permissive lambda function.
6. Vulnerability and outdate components
7. Identification and authentication failures
8. Software and data integrity failures
9. Security logging and minoring failures
10. Serviside request forgery

### Broken access control

What are the risks:

- Data can be modified
- Data leakage
- Execution of unauthorised functions

How do we make sure our app is using the right access control?

How can we solve broken access control?

- Strong Auth
- Least privilege
- Regular access log audit.

Remediations:

- AWS IAM Access Analyser
- GuardDuty for AWS Lambda
- OSS tools: cloud tracker, police setry, repokid

### Event Injection

What are the risks: 

- Resource exhaustion
- Privilege escalation
- Execution of unauthorised code

Remediations:

- Validate & sanitise data input in your function handler
- Ensure your function is running with least privilege
- Monitoring

Example: We have a lambda querying dynamodb. The lambda has FirstName and LastName as parameter. If we don’t validate them and the bad actor user FirstName: * and LastName: *  the lambda could return all items in the dynamodb table. (Similar to SQL Injection)

### Security missconfiguration

What are the risks?

- Unauthorised access
- Denial-of service
- Malware ransomware
- Data leakage

How to prevent?:

- Proper functions configuration
    - Max concurring
    - Timeout
    - Iam roles

For example if you use a large lambda timeout. If a bot attack you. You will end up paying a lot. And all lambda will be reserved to these attackers. Defining parameter is very important for a lambda

Always ask, what happen if a lambda will over run? Do I really need a big timeout?

Tool we can use:

- Amazon Inspector
- guard duty
- security hub
- CloudWatch
- OSS tools (KICS, prowler)

## Supply chain attack

When you have vulnerable and outdate components.

It can allow malicious code to sneak into your environment.

Risks: 

- Denial-of-service attacks.
- Malware ransomware attacks
- Data breaches.

How to prevent:

- Don’t use dependencies with known vulnerabilities.

Remediations:

- OSS SCA tools
- Npm audit
- Owasp dependency check

## Security logging

There is an attack but not enough logs to see the attack.

Remedies:

- Make sure you log everything.
- We should also log for infrastructure not just business logic.
- Have an incident process.
- You can use log insight to search for ip invoking in api gateway.From there you can see if there is a specific IP malicious.
- Amazon Detective
- Clouwatch Logs

Main takeaway:

- Security it’s a journey. It has to be continuously improved.
- Embrace continuously monitoring.