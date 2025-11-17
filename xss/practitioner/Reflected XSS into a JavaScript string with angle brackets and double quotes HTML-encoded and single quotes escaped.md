# Reflected XSS into a JavaScript string (HTML‑encoded angle brackets and escaped single quotes)
**Level:** Practitioner  
**Category:** XSS  
**Status:** Solved

## 🔍 Lab Description
The server reflects the search parameter inside a JavaScript string.  
In this context:
- Angle brackets `< >` and double quotes `"` are HTML‑encoded.
- Single quotes `'` are escaped (`\'`).
- Backslashes `\` are **not** escaped.

This mix prevents normal string‑breaking with `'` but leaves a bypass using `\`.

## 🎯 Goal
Break out of the JavaScript string and execute arbitrary JavaScript (alert).

## 🧠 What I Learned
- How HTML encoding affects script injections.
- How escaped single quotes behave inside JS strings.
- How an unescaped backslash can break sanitization.
- How to comment out the rest of a JS line to avoid syntax errors.

#Solution:
\'-alert(1)//
