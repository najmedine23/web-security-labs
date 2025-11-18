Level: Practitioner
Category: XSS
Status: Solved ✅

🔍 Lab Description
The search input is reflected inside a JavaScript template literal:
const result = `You searched for: ${input}`;
However, the application performs heavy escaping:
< and > are HTML-encoded
Single quotes ' and double quotes " are HTML-encoded
Backslashes \ are escaped
Backticks ` are escaped
This means you cannot break out of the template literal using the usual string-breaking XSS payloads.
🎯 Goal
Inject JavaScript inside the template literal syntax and trigger:alert(1)
🧠 What I Learned
Even when quotes and backticks are escaped, template literals remain vulnerable if ${} is not sanitized.
Template literals evaluate JavaScript expressions inside ${ ... }.
You don't always need to break the string—sometimes the vulnerability is inside the JavaScript expression context.
HTML-encoded characters like &#x27; are not decoded by JavaScript, so they cannot be used to break out.
💡 Working Payload:
${alert(1)}
This takes advantage of the fact that template literals treat ${ ... } as executable JavaScript.
The resulting code becomes:const result = `You searched for: ${alert(1)}`;
📝 Notes
Breaking out of the backtick string fails because all dangerous characters are escaped.
${} is the only unescaped vector → expression injection.
This is a common pattern in modern JavaScript applications:
secure strings, insecure expressions.

When you see a template literal, always test:${alert(1)}
