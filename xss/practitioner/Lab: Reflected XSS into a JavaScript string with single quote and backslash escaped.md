Overview

In this lab, the search parameter is reflected inside a JavaScript string.
The application escapes single quotes (' → \') and backslashes (\ → \\), which prevents the usual string-breaking payloads.

What’s happening
The input ends up inside a script like this:
  var searchTerm = '<user input>';
Because the application escapes ' and \, normal payloads fail.
💡 Exploitation
</script><script>alert(1)</script>
The solution is to break out of the script entirely using HTML context:

Why it works

</script> closes the current script tag.

A new <script> tag is injected.

The browser executes alert(1) normally.

Result:

The injected script runs successfully, confirming the reflected XSS.
