# CHI Passport

A conference passport for CHI 2027 in Pittsburgh. Scan a QR code, build a little block figure of yourself, find the people you came to meet, and collect a stamp every time you meet someone in person. After the conference the passport is archived as a keepsake.

Built for the CHI 2027 Digital Experience Competition. Mobile-first, runs in the phone browser, no install and no login.

## Try it

Open the live page on a phone and tap **Make my passport**. Example people marked *Demo* let you try the whole flow before CHI:

1. Build your figure: skin, hairstyle, top and bottom (pick a colour or photograph your real clothes), glasses or a cap, and optionally a selfie as the head block.
2. Add a name, a 4-digit PIN and how you feel about meeting people today. Your passport is issued.
3. Tap the cover to open it. Page 1 is your holder page; the next pages hold your stamps.
4. **Find people**, open a profile, and send a meet request with a place, a time and one line about why.
5. When they accept, you both get a small **bridge quest** as a reason to talk. Tap *We did it* and both passports get a stamp.
6. Waving at someone who has not arrived yet tells you when their passport is issued (Prof. Sam Okafor in the demo).
7. **Keepsake** saves the whole passport (cover, holder page, every stamp page and the full activity log) as one long image, and shows a QR code that reopens the passport. It also keeps a full log of everything you did, day by day: who you met, where and when, the quest you did together, the notes you sent, the stamps you gave and received. It also lists the people you met and makes a card you can save to your photos.

### Who you are at CHI

Roles stack: a student volunteer can also be an author, and an author can link several papers.

- **Author.** Find a paper by title or ID from the programme and pick which author you are. Verify that author once by email and every other paper by the same author is found and added automatically. A paper under a different author name needs its own verification. Others can then find you by your paper, even if your passport shows a nickname. To get a *Verified author* badge, a one-time code goes to the email the organisers hold for that author. Without it the link shows as *self-claimed*.
- **Here to explore.** For attendees without a paper, including visitors from industry or the city.
- **Student volunteer.** Unlocked with a code from the SV chairs. People can ask an SV for help in the app and thank them with a stamp, so each volunteer ends CHI with a record of everyone they helped.

### Stamps

Every moment becomes a stamp: passport issued, first chat with someone (*Said hi*), waving at someone not yet here, each in-person meet-up (*Bridge*), and sharing your CHI story. Anyone can also give anyone they talked to a stamp (*Thank you*, *Great chat*, *Great talk*, *Good luck*). Gifted stamps wait in the inbox, and the receiver chooses whether to add them to their passport. Skipping is silent.

### Feedback & your CHI story

A button on the passport opens an optional short form: how CHI is going, feedback for the organisers, and questions about past CHI submissions (full paper, Late-Breaking Work, other tracks) and what decided the format. Answers are anonymous, need explicit consent, can be withdrawn, and earn a stamp.

Tip: add the page to your Home Screen so it opens like an app.

## What works and what is mocked in this prototype

| Part | State |
|---|---|
| Figure builder, selfie head, fabric photos | Working |
| Passport with page-turn animation, stamps, keepsake card | Working |
| Meet requests, chat, bridge quests | Working against demo people, who reply automatically |
| Other attendees | Demo people only; there is no shared server yet |
| Sign in on another phone with name + PIN | Mocked; the passport lives on the phone that made it |
| Paper search and author linking | Working against six demo papers; the hosted version uses the official programme JSON |
| Author verification by email code | Mocked; the code is shown on screen. Needs organiser support to email authors |
| Student volunteer code | Mocked with a fixed demo code (SV2027) |
| Gifted stamps between real attendees | Working with demo people, who send stamps back |
| CHI story answers | Stored on the phone only in this prototype |
| Meeting times | Fixed gaps between sessions; the hosted version will read the official CHI programme JSON and live update API |
| Archive | Switches automatically after 14 May 2027; before that the keepsake is labelled Preview |

## Personal data

This prototype stores everything (name, PIN, figure, photos, stamps, messages) in the browser's local storage on the user's own phone. Nothing is sent to a server. Selfie and fabric photos are cropped to a small square (160 px and 96 px) before they are stored. *Start over* on the Keepsake page deletes it all.

## Accessibility

- Real buttons, links, labels and form fields throughout; works with VoiceOver and keyboard focus.
- Touch targets of at least 44 px; text contrast of at least 4.5:1.
- Every stamp, moment and status is also written in text, not shown by colour alone.
- Page turns and the stamp animation respect *Reduce motion*.
- Planned: larger text mode, alt descriptions of each figure, a list view of stamps.

## Technical notes

- One HTML file (`index.html`) with inline CSS and JavaScript, plus images in `assets/`. No build step and no framework.
- Third-party: Inter and Space Grotesk from Google Fonts; html2canvas 1.4.1 (MIT) for the long-image export and qrcode-generator 1.4.4 (MIT) for QR codes, both in `assets/vendor/`. No APIs or AI models are used in this version.
- The figure is drawn as SVG; photo fabrics are tiled with an SVG pattern.

## Deploy

Upload the folder to a public GitHub repository and turn on **Settings → Pages → Deploy from a branch → main / root**. The site appears at `https://<your-username>.github.io/<repository>/`.

## Licence

Code: MIT, see `LICENSE`.
The CHI 2027 logo in `assets/chi27-cover.png` and `assets/chi27-mark.png` belongs to ACM SIGCHI and is not covered by the MIT licence. It is used here for the CHI 2027 Digital Experience Competition.
