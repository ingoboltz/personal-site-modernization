# Personal Site Modernization Plan

This is a modernization of a personal website originally built in 1997. The goal is to preserve the look, feel and vibe while fixing broken things and making it work on mobile.

---

## Decisions

### 1. Navigation
Every page gets a consistent nav with three items: **Home**, **I-Files**, **Guestbook**.

### 2. Responsiveness
- **Hub pages** (homepage, i-files.html, guestbook.html): full responsive treatment
- **All inner pages**: viewport meta tag fix only

### 3. Guestbook
- Keep the TV graphic
- Remove broken links
- Add humorous fossil text (acknowledging the page's age)
- Add bot-proof email

### 4. Retired Pages
`my_cv.html` and `manager.html` to be retired/deleted.

### 5. Academic Archive
Diplomas and thesis move into I-Files as a new **Academic Archive** section.

### 6. All Inner Pages
- Fix broken links
- Fix malformed HTML
- Remove old tracking scripts (Google Analytics urchin.js, StatCounter)
- Add viewport meta tag

### 7. VenCredRally.jpg
Keep exactly as-is. Add a README explaining it hosts a C2PA credentialled image.

### 8. Gate5 Flowchart
Keep as an illustration for a new **Sporadic Musings** entry about Palm V era location services.

### 9. Phase 2 (Later)
Export Buenos Aires blog and Argentina photos from Blogger.

---

## Cleanup Notes

- **buch.html**: Content area has absolute image/PDF paths (`/img/buch.gif`, `/buch/jeremiah.pdf`, `/buch/jeremiah.rtf`) and two dead `cgi07.puretec.de` guestbook links — needs a content cleanup pass. *(Fixed in cleanup pass.)*

---

## Future Sections

- **buch.html → I-Files museum section**: Integrate buch.html into I-Files as its own museum section — Ingo's unfinished novel attempt from the early 2000s. Currently exists as a standalone root page. Should become part of the i-files archive alongside Africa, Australia etc.
