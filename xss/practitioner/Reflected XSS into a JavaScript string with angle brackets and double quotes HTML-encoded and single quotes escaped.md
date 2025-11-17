Overview

In this lab, the search input is reflected inside a JavaScript string.
The application applies the following transformations:

< and > are HTML‑encoded

Double quotes are HTML‑encoded

Single quotes are escaped (' → \')

Backslashes are not escaped*

Because of this behavior, only some characters are usable for breaking out of the JavaScript string.

Context

The reflection looks like this:var query = '<user input>';
If you try:test'payload
the single quote becomes \', so the string does not break.
But if you try:test\payload
the backslash stays as \ — this becomes the entry point for exploitation.
Approach
Use the unescaped backslash to cancel the escaping and inject JavaScript that closes the string and triggers code execution.
Payload:\'-alert(1)//
Why it works
\ prevents the following ' from being escaped.
' then closes the JavaScript string.
-alert(1) executes immediately.
// comments out the rest of the line to avoid syntax errors.
Result
The alert box appears, confirming successful exploitation of the reflected XSS.
