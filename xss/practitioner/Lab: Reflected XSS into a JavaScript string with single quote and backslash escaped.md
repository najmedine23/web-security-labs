# Reflected XSS into a JavaScript string (single quote + backslash escaped)
**Level:** Practitioner  
**Category:** XSS  
**Status:** Solved

## 🔍 Lab Description
The search input appears inside a JavaScript string.  
Single quotes (`'`) and backslashes (`\`) are escaped, so you cannot break the string normally.

## 🎯 Goal
Break the JavaScript string and run `alert(1)`.

## 🧠 What I Learned
- Simple XSS payloads fail when quotes are escaped.
- Sometimes the easiest way is to escape the whole `<script>` block.
- Injecting a new `<script>` tag avoids the escaping inside the string.

## 💡 Working Payload
</script><script>alert(1)</script> 

## 📝 Notes
Since the string escaping blocks simple injections, closing the `<script>` tag is the easiest bypass.
