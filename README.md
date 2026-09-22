This website is being used to show students how to find real world security flaws in websites.


Answer Key: 

Steps to Reproduce: 

Issue #1: Hardcoded Credentials

Step 1: Open the CloudSync Pro webpage in your browser.

Step 2: Right-click anywhere on the page and select "View Page Source" (or press Ctrl+U).

Step 3: Press Ctrl+F to open the search box at the top of the source code window.

Step 4: Type "apiKey" or "APP_CONFIG" in the search field and press Enter.

Step 5: The search will jump to a JavaScript object containing sensitive credentials near the bottom of the HTML file.

Step 6: Look for the constant named APP_CONFIG which contains an apiKey value starting with "cs_live_sk_".

Step 7: Scroll slightly down from there and find the LEGACY_CREDENTIALS object which contains database host information.

Step 8: Copy the full API key value: cs_live_sk_9KjH8mNpQrStUvWxYzAbCdEfGhIj.

Step 9: To verify the credentials are accessible, press F12 to open Developer Tools.

Step 10: Click on the "Console" tab in the Developer Tools panel.

Step 11: Type "console.log(APP_CONFIG.apiKey)" and press Enter.

Step 12: The console will display the full API key, proving it is exposed in the browser memory.

Step 13: Record this finding in your lab report with the exact location where you discovered the credentials.

Issue #2: Cross-Site Scripting (XSS)

Step 1: Navigate to the Contact form section at the bottom of the CloudSync Pro page.

Step 2: Clear all fields in the form and prepare to test the Name input field.

Step 3: In the Name field, paste the following payload: <script>alert('XSS')</script>

Step 4: Leave the Email and Message fields empty or fill them with normal text.

Step 5: Click the "Send Message" button to submit the form.

Step 6: An alert dialog box should pop up displaying the text "XSS".

Step 7: Close the alert dialog to continue testing.

Step 8: Now try a different payload that accesses cookies: <img src=x onerror=alert(document.cookie)>

Step 9: Submit the form again with this payload in the Name field.

Step 10: Another alert dialog will appear showing your browser's session cookie value.

Step 11: Press F12 to open Developer Tools and click the "Elements" tab.

Step 12: Look for the div element with id="response-message" in the HTML structure.

Step 13: Notice that your injected HTML tags appear unescaped in the DOM tree.

Step 14: Switch to the "Sources" tab in Developer Tools to find the JavaScript file.

Step 15: Search for "innerHTML" using Ctrl+F in the Sources panel.

Step 16: You will find one match in the handleSubmit() function around lines 160-170.

Step 17: Read the vulnerable code where user input is inserted directly into innerHTML without sanitization.

Step 18: Optionally test a defacement payload like: <h1>HACKED BY STUDENT NAME</h1>

Step 19: Submit the form and observe how your HTML renders in the response area.
