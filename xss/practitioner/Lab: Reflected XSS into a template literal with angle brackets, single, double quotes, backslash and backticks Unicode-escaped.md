Reflected XSS into a JavaScript Template Literal (heavy escaping)

Level: Practitioner
Category: XSS
Status: Solved
🔍 Lab Description

The search input is reflected inside a JavaScript template literal (backticks).

The application performs heavy escaping:

< and > are HTML‑encoded

Single quotes ' and double quotes " are HTML‑encoded

Backslashes \ are escaped

Backticks are escaped

Because of this, it’s impossible to break out of the template literal using quotes, backticks, or special characters.

🎯 Goal

Inject JavaScript inside the template literal expression and trigger alert(1).

🧠 What I Learned

Template literals execute whatever is placed inside ${ ... }.

Even when quotes and backticks are escaped, ${} can still allow code execution if not sanitized.

HTML entities like &#x27; do not act as quotes inside JavaScript.

When inside a template literal, the vulnerability is often expression injection, not string breaking.

💡 Working Payload:
${alert(1)}
This injects a JavaScript expression directly into the template literal and executes it.

📝 Notes

Breaking the template literal is impossible because all dangerous characters are escaped.

${} is the only unescaped vector → expression injection is the correct path.

In any template literal, always test ${alert(1)} first.
