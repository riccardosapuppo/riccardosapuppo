# Riccardo Sapuppo

Full-stack developer in Catania. Most of what I build ends up in a clinic, a
radiology archive, or somebody's back office — places where being approximately
right is worse than being obviously wrong, because nobody notices.

I rebuild that work here, from scratch, with invented data. Not to show that it
runs: to show what it took to be sure it was right.

---

## Every project makes a claim, and its own CI can prove it false

That is the one thing these have in common, and it is the point of them. Each
repository opens with a sentence that could be wrong, and each has a command
that goes red if it becomes wrong. Not a badge — a measurement.

**[pacs-maintenance-tasker](https://github.com/riccardosapuppo/pacs-maintenance-tasker)** — a job that deletes medical images it cannot get back.

> *A dry run and a real run choose the same studies.* Written as its own branch —
> the way it usually is — the dry run failed to mention **9** of the 255 studies
> it was about to delete.
>
> *Nothing is deleted because the record system said nothing.* An empty result set
> is an ordinary return value, so it falls through to whatever the last line of
> the function happens to be. That cost **23** patients' studies, on a run where
> nothing errored and every total looked plausible.
>
> *When the second of two deletions fails, the next run can finish it.* Removing
> the catalogue row first leaves **25** folders that nothing will ever look for
> again. Same failure, same frequency, and one of them is permanent.

**[dynamic-form-builder](https://github.com/riccardosapuppo/dynamic-form-builder)** — a form is authored as a tree and asked about as a table.

> The same 120 submissions, stored three ways, asked the same eight questions.
> Not speed: **whether the answer is right, and whether a wrong answer announces
> itself.** A pile of JSON documents is quietly wrong three times and cannot
> express three of the questions at all. Flattening fixes all but one — the
> rename — and that one needs an id, which is the whole finding.

**[pacs-analytics-monitoring](https://github.com/riccardosapuppo/pacs-analytics-monitoring)** — analytics over an archive whose schema you do not own and that differs at every installation.

> Six installations holding the same studies. The side that reads the schema
> first gets every question right on all six. The side with the SQL written
> straight gets **7 answers wrong with nothing to show for it** — not errors,
> numbers, four times too high, because a one-to-many join took the storage with
> it.

---

## The work

**Medical imaging** — [DICOM viewer, web](https://github.com/riccardosapuppo/medical-dicom-viewer-web)
· [DICOM viewer, desktop](https://github.com/riccardosapuppo/medical-dicom-viewer-desktop)
· [archive analytics](https://github.com/riccardosapuppo/pacs-analytics-monitoring)
· [archive maintenance](https://github.com/riccardosapuppo/pacs-maintenance-tasker)

**Healthcare, patient-facing** — [multi-tenant booking](https://github.com/riccardosapuppo/multi-tenant-booking)
· [a booking agent that knows when to hand over](https://github.com/riccardosapuppo/conversational-booking-agent)

**Documents** — [OCR as an internal service](https://github.com/riccardosapuppo/document-ocr-service)
· [questions about a document set](https://github.com/riccardosapuppo/document-chat-assistant)
· [rebuilding an order from a folder of email](https://github.com/riccardosapuppo/order-email-extraction)
· [forms as a relational schema](https://github.com/riccardosapuppo/dynamic-form-builder)

**Desktop and devices** — [teaching somebody a Windows application](https://github.com/riccardosapuppo/windows-app-guided-tour)
· [printer meters over SNMP](https://github.com/riccardosapuppo/printer-meter-collector)

**The rest** — [campaigns that cannot write to somebody who said stop](https://github.com/riccardosapuppo/campaign-automation)
· [a TOTP authenticator](https://github.com/riccardosapuppo/totp-authenticator)

---

## What is underneath

Where a standard was the interesting part, it is implemented rather than
installed. SMTP is spoken by hand, one line at a time, so the conversation is
visible. SNMP is decoded from ASN.1/BER on the standard Printer MIB, not
through a vendor's own interface. MIME is parsed with its own byte counts
because a `{n}` in IMAP is bytes and not characters, and getting that wrong
gives you mojibake and no error. DICOM dates are `VARCHAR(8)` and sort
lexicographically, which is the one gift that format gives you.

The Node projects have **no runtime dependencies at all** — `node:sqlite`,
`node:http`, `node:fs` — and no build step: they are TypeScript that Node runs
directly, with `erasableSyntaxOnly` set so the type check is also the proof that
they still run without one.

`TypeScript` · `Node.js` · `Angular` · `React` · `Electron` · `Python` ·
`PostgreSQL` · `SQL Server` · `SQLite` · `Docker`

---

## A note on the originals

Every one of these was built for a client and lives in a private repository.
What is here is an independent reimplementation, written from scratch, with
data that is invented in the repository itself — no clinic, no patient, no real
archive, no customer list. Each README says what the original did, what this
does differently, and why.

The limits are in the READMEs too, in their own section, and they are real ones.
A portfolio piece without them is a brochure.
