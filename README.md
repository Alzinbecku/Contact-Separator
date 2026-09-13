# Contact-Separator

A lightweight, single-file web tool for untangling merged contact lists. Upload two exported `.vcf` files, and it matches contacts by name, phone number, and email to flag overlaps—letting you review, adjust, and export a clean list with only the contacts that belong.

**No installs, no accounts, no server. Everything runs locally in your browser, and no data is ever uploaded or stored anywhere.**


## Why this exists

Contact lists get merged more easily than people expect — signing out of iCloud, restoring a backup onto someone else's device, or syncing two phones to the same Apple ID can quietly combine two people's contacts into one list. Untangling that by hand, contact by contact, isn't realistic once you're past a couple hundred entries.

This tool automates the comparison so you can separate two merged lists in minutes instead of hours.

## How it works

1. **Export both contact lists as `.vcf` files**
   - On a Mac: open Contacts, select the relevant contacts (or all), then **File > Export > Export vCard**.
   - On iCloud.com: sign in, select contacts, and export vCard from the settings gear icon.
2. **Upload both files** into the tool — one as the "reference" list, one as the list you want to clean.
3. **Click Compare.** Contacts found in both files are flagged as likely overlaps.
4. **Review the flagged contacts.** Uncheck any false positives; check any the matcher missed.
5. **Export the cleaned list** as a new `.vcf` file, ready to import back onto the intended device.

## Matching logic

Contacts are compared using:
- Normalized full name
- Phone number (last 10 digits, formatting stripped)
- Email address

A contact is flagged as an overlap if it matches on **any** of these; you can review and adjust every flag before exporting.

## Privacy

This tool does not use a server, an API, or any external storage. All parsing, comparison, and file generation happen client-side in your browser using JavaScript's `FileReader` and `Blob` APIs. Closing the tab clears everything; nothing persists.

## Limitations

- Matching is name/phone/email based; contacts with no name, phone, or email in common won't be flagged automatically and will need manual review.
- Currently supports `.vcf` (vCard) format only.
- Large files (several thousand contacts) may take a moment to parse and render.

## License

MIT — free to use, modify, and share.
