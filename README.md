# Do copy-paste "HTML contact form code" snippets deliver a message?

A small, pre-registered check of the snippets that rank for "html contact form code" and three similar searches
(2026-10-13). **Result: 9 pages judged, 4 of 9 snippets send nothing as pasted, 0 of 9 pass all six checks.**

By [Formgong](https://formgong.com). Disclosure: we make a form backend, so we have an interest in forms that work.
The method was written down before any page was fetched (section 1), every failure quotes the exact line (section 4),
and the limits are in section 5. You can run the same kind of check on any page with the free
[form checker](https://formgong.com/en/tools/form-checker/).

Text: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Quoted code lines belong to their authors and are
quoted for review; follow the source URLs for the full pages.

---


## 1. Pre-registration (written before any page was fetched)

Question: for the queries "html contact form code", "html contact form", "contact form html css",
"simple contact form html", how many of the top 10 unique pages with copy-paste form code give a
snippet that would actually deliver a message, and what do they miss?

Sample rule: top 10 unique pages across the four queries (WebSearch, US results) that contain
copy-paste form code. Skipped and logged: videos, forum questions without code, form-builder
product pages that hide the code. Pages owned by form-backend companies (Formspree, Web3Forms,
Getform/Forminit, Basin, FormSubmit, etc.) are kept and labelled "backend vendor".
Main snippet = the first complete `<form>` the page presents as the thing to copy (if a page
offers a backend file for that form on the same page, it is judged together with it).

Read-only: nothing is submitted to any endpoint; judgement is by reading code only.
A page that cannot be fetched = UNKNOWN, not fail.

| Code | Criterion | Pass | Fail | n/a |
|---|---|---|---|---|
| C1 | Sends somewhere | `action` points at a working endpoint (a real backend URL, or a PHP/Node file whose code is in the snippet/page), or JS posts to such an endpoint | `action="#"`, empty/missing action, JS that only shows "Thanks" without a request, action pointing at a file the page never gives. `mailto:` gets its own label **mailto** (not counted as sends) | - |
| C2 | Every visible input/textarea has an associated `<label>` (for/id match or wrapping) | all have one | any field placeholder-only or label without for/id match | - |
| C3 | Email field is `type="email"` | yes | `type="text"` or no email field | no email field at all |
| C4 | `required` on the fields that must be filled (name/email/message) | all three (or whichever exist) | any missing | - |
| C5 | `autocomplete` on name and email | both | either missing | - |
| C6 | Any spam protection (honeypot, captcha, server-side check) | present | none | - |
| C7 | If JS submits: shows an error when the request fails | handles failure | no failure branch / always "Thanks" | no JS submit |
| PHP | If PHP `mail()` with visitor email in From/Reply-To without sanitising: header-injection risk | note | | |

Evidence: every fail gets the exact attribute/line quoted.
Totals: reported as "k of N" where N = pages fetched and judged; unknowns listed separately.

## 2. How the sample was drawn

- Search: Claude Code `WebSearch` tool (US results), 2026-10-13, four queries:
  `html contact form code`, `html contact form`, `contact form html css`, `simple contact form html`.
  This is the tool's search backend, not a logged-in Google SERP; ranks may differ from Google.
- Merge rule: round-robin by rank across the four queries (all rank-1 results, then rank-2, ...),
  duplicates dropped, skips logged, until 10 pages with copy-paste form code.
- Fetch: curl with a desktop Chrome UA. Four pages returned HTTP 403 to curl and to WebFetch
  (Medium x2, TemplateMonster, Web3Forms); those were read in a real Chrome tab (read-only, no
  form touched, no challenge solved; TemplateMonster passed its bot check on the second load by itself).

### Skipped (not in the 10)

| Candidate order | Page | Why skipped |
|---|---|---|
| 1 | scribd.com/document/583929158/Contact-Us-Form-HTML-CSS-Code | 5-page PDF in Scribd's viewer; no selectable code (`<form` not in page text); download needs sign-in |
| 6 | medium.com/@gogaelisabeth21/how-to-create-a-contact-form-with-html-and-css-79c3d0ae0d91 | Code shown only as images (6 figures, 0 `<pre>` blocks); nothing to copy |
| 7 | paperform.co/blog/html-contact-form/ | 301 -> paperform.com/blog/... -> 301 -> paperform.com/tools/free-html-form-creator/ : a form-builder tool page, no code on the page |

Next candidates not needed (sample filled at candidate 13): vserver-backup.adiscon.com/?p=28539 (looks like a spam/scraper site), hackmd.io note, 123contactform.com (form builder), quackit.com template (has `action="#"`, not judged).

## 3. Results (10 pages: 9 judged, 1 unknown)

Owner type: **vendor** = page owned by a form-backend company; **indep** = everyone else.
We saved each page's snippet on 2026-10-13 as `<n>-<site>.html` (+ `.php`/`.js` when the page gives a backend/script). Those copies are third-party code, so they are not published here; their SHA-256 hashes are in [evidence-sha256.txt](evidence-sha256.txt), and every failing line is quoted below. To check a finding, open the source URL in the table.

| # | Site | URL | Owner | C1 sends | C2 labels | C3 type=email | C4 required | C5 autocomplete | C6 spam | C7 JS failure | Blocking defect as shown (extra, not pre-registered) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | Formspree | https://formspree.io/library/html/contact/ (code: /library/contact/simple-contact-form/) | vendor | pass (needs signup, replace `{FORM_ID}`) | pass | **fail** | **fail** | **fail** | fail in snippet (vendor-side filter claimed) | n/a | - |
| 2 | Medium / Cwrcode (2023-06-08) | https://medium.com/@cwrworksite/how-to-create-contact-form-using-html-and-css-5bb88866eee4 | indep | **fail** | **fail** | pass | **fail** | **fail** | **fail** | n/a | name/email/phone inputs have no `name` |
| 3 | GeeksforGeeks | https://www.geeksforgeeks.org/php/simple-contact-form-using-html-css-and-php/ | indep | pass (contact.php given) | **fail** | pass | **fail** | **fail** | **fail** | n/a | hard-coded `CC: somebodyelse@example.com` |
| 4 | TemplateMonster Help (2011-11-15) | https://www.templatemonster.com/help/how-create-contact-form-html.html | indep | pass (contact.php given) | **fail** | **fail** | **fail** | **fail** | **fail** | n/a | `<textarea>` never closed: Send button disappears |
| 5 | freeCodeCamp | https://www.freecodecamp.org/news/how-to-create-a-contact-form-with-css/ | indep | **fail** | **fail** | pass | pass* | **fail** | **fail** | n/a | - |
| 6 | filipchabik.ghost.is | https://filipchabik.ghost.is/html-contact-form | indep | UNKNOWN | UNKNOWN | UNKNOWN | UNKNOWN | UNKNOWN | UNKNOWN | UNKNOWN | HTTP 402 "Site unavailable" (curl and Chrome) |
| 7 | TutorialsPoint | https://www.tutorialspoint.com/article/how-to-create-a-contact-form-with-css | indep | **fail** | pass | pass | pass | **fail** | **fail** | n/a | - |
| 8 | awabrao.lovable.app | https://awabrao.lovable.app/blog/create-simple-contact-form-html-css-javascript | indep | **fail** | pass | pass | pass | **fail** | **fail** | **fail** | - |
| 9 | Web3Forms | https://web3forms.com/platforms/html-contact-form | vendor | pass (needs signup, replace access key) | **fail** | pass | pass | **fail** | fail in snippet (vendor-side filter claimed) | n/a | - |
| 10 | Formcarry | https://formcarry.com/blog/how-to-create-a-simple-html-contact-form/ | vendor | pass (PHP given, or own endpoint) | pass | pass | **fail** | **fail** | **fail** (PHP path) | n/a | PHP rejects valid emails and non-ASCII names |

\* freeCodeCamp marks the textarea `required`, but the textarea ships with a space as its content (`required> </textarea>`), so the browser treats it as filled (checked in Chrome: `validity.valueMissing === false`). It passes C4 by the pre-registered letter; in practice an empty message goes through.

### Totals (denominator = 9 pages judged; 1 unknown)

- **C1 sends: 5 of 9.** mailto: 0 of 9. Of the 5, 3 are form-backend vendors selling the endpoint (Formspree, Web3Forms, Formcarry).
  - Independent pages: **2 of 6** send, and one of those two (TemplateMonster) cannot be submitted as displayed. So **1 of 6** independent pages gives code that would deliver a message as pasted (GeeksforGeeks, and only on a PHP host with working `mail()`, and it CCs example.com).
  - All 4 non-sending snippets are from independent pages. 3 of those 4 say nothing about the form not sending (freeCodeCamp, TutorialsPoint, Cwrcode); 1 of 4 (lovable) says data "must be sent to a server".
- **C2 labels: 4 of 9** (Formspree, TutorialsPoint, lovable, Formcarry).
- **C3 type="email": 7 of 9** (fails: Formspree, TemplateMonster).
- **C4 required: 4 of 9** (freeCodeCamp*, TutorialsPoint, lovable, Web3Forms).
- **C5 autocomplete on name/email: 0 of 9.** No snippet has a single `autocomplete` attribute.
- **C6 spam protection in the snippet: 0 of 9.** No honeypot, no captcha, no server-side check in any PHP. The 3 vendor endpoints claim server-side filtering on their side (not verified here).
- **C7 JS failure handling: 0 of 1** applicable (lovable is the only snippet with JS; it never sends a request and always says thanks).
- **All of C1-C6 pass: 0 of 9.**
- PHP header handling: 3 of 9 pages give PHP. 1 of 3 (TemplateMonster) puts an unsanitised, actually undefined variable in From/Reply-To; 1 of 3 (Formcarry) puts the visitor's address in From after a regex check; 1 of 3 (GeeksforGeeks) uses a fixed From.

## 4. Evidence for every fail (quotes from the saved snippets)

**1 Formspree** (1-formspree.html)
- C3: `<input class="fs-input" id="email" name="email" required />` (no `type`, defaults to text)
- C4: `<textarea class="fs-textarea" id="message" name="message"></textarea>` (message not required)
- C5: no `autocomplete` anywhere. C6: no honeypot/captcha field in the snippet.

**2 Medium / Cwrcode** (2-medium-cwrcode.html)
- C1: `<form enctype="multipart/form-data" method="POST">` (no `action`: posts back to the static page itself).
  Worse: name, email and phone inputs have **no `name` attribute** (`<input type="text" size="33" placeholder="Enter Your Name" id="firstname" autofocus />`). Checked in Chrome with `new FormData(form)`: the only fields that would be sent are `telcode` and `msag`. Even with a backend, the owner would never get the visitor's name or email.
- C2: placeholder-only (`placeholder="Enter Your Email"`), no `<label>`.
- C4: no `required` on any field. C5: none. C6: none.

**3 GeeksforGeeks** (3-geeksforgeeks.html, .php)
- C2: `<input type="text" class="form-control" id="name" placeholder="NAME" name="name" value="" />` (placeholder-only)
- C4: no `required` on any field. C5: none.
- C6: PHP sends whenever email is non-empty: `if($email != NULL) { mail($to, $subject, $txt, $headers); }`
- Also: `$headers = "From: noreply@demosite.com" . "\r\n" . "CC: somebodyelse@example.com";` (copy it unchanged and every message is also CC'd to example.com). No header injection: From is fixed.

**4 TemplateMonster** (4-templatemonster.html, .php)
- Blocking: `<textarea name="cf_message"><br>` has no `</textarea>` in the displayed code (10 numbered lines). Parsed in Chrome with DOMParser: the textarea swallows the rest, `input[type=submit]` count = 0, and the textarea's default text becomes `<br> <input type="submit" value="Send"> ...`. With two text fields and no submit button, Enter does not submit either. (Probably the page's syntax highlighter dropped the closing tag; the downloadable package was not fetched.)
- C2: `Your name<br>` / `Your e-mail<br>` (plain text, no `<label>`). C3: `<input type="text" name="cf_email">`. C4/C5/C6: none.
- PHP: `$headers = "From: $cf_email\r\n"; $headers .= "Reply-To: $cf_email\r\n";` while the code only defines `$field_email`. On PHP >= 5.4 `$cf_email` is undefined, so From and Reply-To are empty; on PHP <= 5.3 with register_globals (the norm in 2011) it was the raw POST value: a classic header-injection hole. No sanitising either way.

**5 freeCodeCamp** (5-freecodecamp.html)
- C1: `<form action="#" name="contact_form">`; the article never mentions a backend.
- C2: `<label for="first_name">` but the input is `<input name="first_name" type="text" ...>` with no `id`. Checked in Chrome: every `label.control` is `null`.
- C4*: `<textarea name="message" cols="30" rows="10" placeholder="Enter your message here ..." required> </textarea>` (the space defeats `required`).
- C5/C6: none.

**7 TutorialsPoint** (7-tutorialspoint.html)
- C1: `<form>` (no `action`, no `method`: a GET back to the same page, the message lands in the URL). No backend mentioned.
- C5/C6: none.

**8 awabrao.lovable.app** (8-awabrao-lovable.html, .js)
- C1/C7: `event.preventDefault();` then, when valid, only `console.log(...)` and `alert('Thank you for your message! We will get back to you shortly.');` followed by `contactForm.reset();`. No request is made; the visitor is told it worked. The prose does say a server is needed ("In a real-world application, this is where you would send the data to a server").
- C5/C6: none.

**9 Web3Forms** (9-web3forms.html)
- C2: `<input type="text" name="name" required>`, no label and no placeholder: three unlabelled boxes.
- C5: none. C6: nothing in the snippet (the hidden input is the access key, not a honeypot).

**10 Formcarry** (10-formcarry.html, .php)
- First snippet: `<form action="#" method="POST" class="formcarry-form">`; the page then gives `form-process.php` and its own endpoint as replacements (judged together, C1 pass).
- C4: `<textarea name="message" id="message" cols="30" rows="10"></textarea>` (not required). C5: none. C6: PHP has no spam check.
- PHP: `$headers = 'From: ' . $email . "\r\n" . 'Reply-To: ' . $email ...` The address is checked first with `/^[A-Za-z0-9._%-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,4}$/`, which blocks CRLF injection, so this is not a header-injection hole. But:
  - From = the visitor's domain, so the message fails SPF/DMARC alignment at the receiving side (likely rejected or spam-foldered when the visitor uses Gmail/Outlook etc.).
  - The regex rejects real addresses (tested with the same pattern in Python `re`): `o.brien+site@gmail.com` (plus sign), `ann@studio.agency`, `ann@firm.photography` (TLD > 4 letters) are all "Email address does not seem valid."
  - The name check `/^[A-Za-z .'-]+$/` rejects `José García`, `Zoë Kim`, `Олена Коваль`: the visitor gets "Name does not seem valid." and the script `die()`s.

## 5. Limits

- One search backend, one day, US results. Rank order is the tool's, merged by a fixed round-robin rule.
- Judged by reading code only; no snippet was run against a real endpoint, so "pass" on C1 means "points at something that can send", not "delivered in a test".
- Vendor-side spam filtering (Formspree, Web3Forms, Formcarry) is the vendors' claim, not checked.
- Medium and TemplateMonster were read through Chrome's rendered text; Medium's text view loses indentation (attributes unchanged).
