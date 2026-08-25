# AR Visiting Card — Setup Guide

How it works: someone opens a webpage in their phone browser, points the
camera at your printed card, and your name/title floats over it like a
hologram. No app to install — it's a normal camera-permission website.

## 1. Test it right now
Open `index.html` on your phone (see hosting step below) — it's pre-wired
to MindAR's demo card, so before you touch anything you can confirm AR
works on your phone.

## 2. Make YOUR card the trigger image
1. Take a clean, well-lit, straight-on photo of your card's **front**
   design (the side people will scan). Good contrast and detail = better
   tracking — avoid plain/blank cards.
2. Go to the compiler: https://hiukim.github.io/mind-ar-js-doc/tools/compile/
3. Drop your card photo in, click **Start**, then **Download** — this
   gives you a file called `targets.mind`.
4. Put `targets.mind` in the same folder as `index.html`.
5. In `index.html`, find this line:
   ```
   imageTargetSrc: https://cdn.jsdelivr.net/gh/hiukim/mind-ar-js@1.2.5/examples/image-tracking/assets/card-example/card.mind;
   ```
   and change it to:
   ```
   imageTargetSrc: ./targets.mind;
   ```

## 3. Customize the content
- Edit the two `<a-text>` lines (name / title) in `index.html`.
- Edit the phone number and email in `contact.vcf` and in the
  `#contact-bar` links at the bottom of `index.html`.
- Want more than floating text? Swap the `<a-text>` entities for an
  `<a-image>` (your logo) or a small `.glb` 3D model the same way.

## 4. Put it online (free, ~2 minutes)
Camera access requires HTTPS, so it needs to be hosted somewhere:
- **Netlify Drop**: https://app.netlify.com/drop — drag the whole folder
  in, get a live URL instantly. Easiest option.
- **GitHub Pages**: push the folder to a repo, enable Pages in Settings.

## 5. Add it to the physical card
Generate a QR code (e.g. https://www.qr-code-generator.com) pointing to
your hosted URL, and print it on the **back** of the card — small, one
corner is plenty. The front stays as your normal design; that's also the
image the AR locks onto.

## Notes
- Works in mobile Safari/Chrome — no install needed.
- If tracking feels jittery, use a higher-contrast/more-detailed card
  photo when compiling `targets.mind`.
- Everything here runs off free CDNs (A-Frame + MindAR) — no backend,
  no build step.
