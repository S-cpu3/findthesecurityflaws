This website is being used to show students how to find real world security flaws in websites.


Answer Key: 

Steps to Reproduce: 

 Exercise 1: Credential Exposure
1. [ ] Load the page and click "Reveal Configuration"
2. [ ] View page source (Ctrl+U)
3. [ ] Locate the SECRET_CONFIG object
4. [ ] Copy one credential value into a notebook

 Exercise 2: XSS Injection  
1. Submit: Your name → Note the output
2. Submit: `<b>BOLD TEXT</b>` → Observe HTML formatting
3. Submit: `<script>alert('hacked')</script>` → Observe execution
4. Submit: `<img src=x onerror=alert(document.cookie)>` → Record cookie value shown
