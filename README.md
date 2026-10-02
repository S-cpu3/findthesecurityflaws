This website is being used to show students how to find real world security flaws in websites.

https://s-cpu3.github.io/findthesecurityflaws/


Answer Key: 

Steps to Reproduce: 

Issue #1: Hardcoded Credentials

Step 1: Inspect the page by right clicking on the website 

Step 2: Click on <script>

Step 3: Find username and password for site

Hardcoded Secrets / Credential Exposure (CWE-798) and Information Disclosure (CWE-200)


XSS payload: <img src=x onerror=alert('XSS')>

