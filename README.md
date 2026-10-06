# riversidefamilyeyecare

> **Unofficial copy — not the website of Riverside Family Eye Care.** This repository is a development copy of
> a redesign, published for build review. It is not operated by, affiliated with, or endorsed by
> Riverside Family Eye Care. The practice's real site is https://www.riversidefamilyeyecare.com/.

**Preview: https://chris-sgen.github.io/riversidefamilyeyecare/**

A **total redesign** of **riversidefamilyeyecare.com** (Riverside Family Eye Care, an optometry practice in
Fort Myers, Florida): 142 pages, built by the `site-reforge` pipeline and changed for public
hosting as listed under *Hardening*. It is a static site with no build step, no dependencies and
no backend. Serve the folder, or use the preview link above.

> **Some of this copy's pictures, and all of its silent video loops, are AI-generated illustrations
> made for this redesign. They are not photographs of the practice.**

Two terms used below. The **handoff build** is the private build of this redesign that this copy
was made from, together with its documentation and audit files; it is not published ("handoff" is
the pipeline's name for its packaged output, and says nothing about a recipient). This **preview**
is that build with the changes listed under *Hardening*.

## What this is, and what it is not

This is **not** a pixel-faithful clone. It is a redesign:

|  |  |
| --- | --- |
| **Content, contact details, URLs** | All from `riversidefamilyeyecare.com`. Every sentence of the pages' body text comes from the practice's live site. The redesign's own words are interface text (menu-group labels, section labels such as "In this section", button labels such as "Read More", the messages of the search page), descriptions (alt text) of pictures, a title made from the heading of the 4 pages the live site leaves untitled, initials on a tile where a team portrait is missing, and the notes this preview adds (see Hardening). 15 short texts of the live site are left out or printed differently, each with a recorded reason: relative review dates ("2 weeks ago") printed as month and year, texts of the form platform, and a duplicate sitemap label. In 3 further texts an unfilled placeholder of the old platform is replaced by the practice's name or town. |
| **Generated imagery** | **30 still pictures and 5 silent video loops were generated for this redesign** on fal.ai and Higgsfield (models in `PROVENANCE.md`); 78 of the 144 pages show at least one. They show objects and light only (eyewear, lenses, water and everyday objects), never a person, the practice's premises, its staff or doctors, a clinical result or a named product. No page whose address names a brand, a product or a named programme (17 pages, found by the 9 words of the build's list) is led by a generated picture, and no card that leads to such a page shows one; on 1 of those pages (`/inmode-forma-and-lumecca-a-breakthrough-in-eye-care/`) one appears on the card of another article. Every generated picture has empty alt text (166 placements), so screen readers skip it, and every generated file is served from `assets/generated/`, kept separate from the live site's pictures in `assets/img/`. Nothing on the pages themselves labels them. |
| **Other imagery** | Every other picture was published on the practice's site (222 source pictures are used): the practice's logo and photographs, the stock photographs of its articles, and the frame-brand, contact-lens and insurance logos its pages show. 2 pages carry 3 films the practice published on its site, re-encoded smaller and served from `assets/media/`. Many of the generated stills stand where the live site showed a stock photograph that could not be downloaded (see Known limits). |
| **Navigation model and page anatomy** | Modelled on `eyetrendsclearlake.com`: a top bar, grouped menus, an "Hours & Location" band before the footer and a persistent appointment call to action. **No content or asset came from that site.** |
| **Visual design** | New. The navy and the teal are the practice's own (its logo and live stylesheet); a coral is added as an accent. Type is Jost for headings and Mulish for text. Pictures sit in frames with one long corner, and a two-stroke "river line" marks headings. |
| **Platform** | Removed: no WordPress, no EyeCarePro theme, no Beaver Builder, no Gravity Forms, no analytics or tag-manager scripts. The one third-party embed that loads by itself is the Google map (see Known limits). |

## Verification

These figures were measured by the pipeline and filled in from the measurement files. The first
eight rows come from the handoff build's audit. The others were re-read from this tree. The
browser figures (rendering, video loops, forms) were measured at the public URL (https://chris-sgen.github.io/riversidefamilyeyecare/). The tree has 144 pages: the 142 rebuilt ones plus `/404.html` and `/search/`, which the build makes itself. Tested in Chrome only.

| Check | Result |
| --- | --- |
| Every text unit of the live pages looked for on its rebuilt page (sentences, headings, list entries, labels) | **5,793 checked: 5,778 found, 15 left out or corrected with a recorded reason, 0 missing; 0 sentences of eight or more words in the handoff build, other than its interface labels, that are not the live site's** |
| Content recall vs the live source (`sr-parity`) | **99.79% mean** over 142 pages; threshold 95%; 2 pages below it (`/contact-us/appointment-request-form/` at 89.6%, `/contact-us/contact-form/` at 88.1%, explained under C17) |
| Pages mapped | **142 / 148** at their original URLs; the 6 not rebuilt are explained below (C16) |
| Claims traced to the live site (`sr-fabrication`) | 857 claims checked, 2 flagged; they are phrases of the live site (explained below, C20) |
| Platform decontamination | **CLEAN: 0 findings across 150 files** |
| Responsive sweep, 390 / 768 / 1024 / 1440 px | **0 blocker · 0 major introduced by the redesign** across 568 page × width sweeps (1,084 minor, 8 nit) |
| Forms of the handoff build against the live forms (2 forms) | 26 checks, 1,019 assertions, 0 failed. (In this preview the forms are disabled; see Hardening.) |
| Gate (`sr-gate.mjs`) | 22 PASS · 7 FAIL · 0 UNPROVEN. The verdict is NOT-READY, and the handoff build was packaged with a recorded override. Each red is explained below |
| Preview hardening, re-read from the shipped bytes | **144 / 144 pages**; 2 practice forms inert; 157 search forms that send a GET to `/search/` (one query was run in the browser); 143 map frames, each carrying `referrerpolicy="no-referrer"`; every link-card title begins "Unofficial preview:" |
| Reference audit: every local `href` / `src` / `srcset` / `url()` / video-loop source / search-form address | **26,795 local references resolved when this tree was built: 0 name no file, 0 leave the site root**; read again from the shipped pages: 0 root-relative outside `404.html`, whose 168 references are absolute by design (GitHub Pages serves it at any depth) |
| Binary files read for metadata | 8 woff2, 13 mp4, 898 webp: no EXIF, XMP, IPTC or C2PA; the WebP files carry at most the encoder's stock sRGB colour profile |
| Rendering under `/riversidefamilyeyecare/`, every page except `404.html` at 1440 and 390 px | **286 page loads: 0 failed requests on this site, 0 requests on this host outside `/riversidefamilyeyecare/`, 0 script errors, 0 broken pictures, 0 sideways scroll at 390**; `404.html` loaded at depth with its stylesheet and pictures |
| Video loops | **5 loops played** (`/contact-lenses/eye-exams-for-contact-lenses/`, `/eye-care-services/dry-eye-disease-and-treatment/`, `/eye-care-services/management-of-ocular-diseases/glaucoma/`, `/eye-care-services/nearsighted-myopia/`, `/`), each from inside `/riversidefamilyeyecare/`, muted, without controls |
| Practice forms, each tried with scripts on and off | **2 forms. As shipped (4 trials): Enter pressed in a field of every form and the form's button clicked where one is shown (4 trials) sent nothing and went nowhere.** Two reduced configurations were also tried: only the form attributes (`method="dialog"` / `action=""` / `onsubmit`) left, with a live submit button added (4 trials); and those attributes taken off with a real address put back, leaving the disabled buttons and the hidden field (4 trials). Nothing was sent in either. With every safeguard taken off (4 control trials) every form was seen to submit, so the trials can see a submission |

**Why the red gate checks are red:**

- **C04 Content captured for every page** (1 page(s) with under 50 chars of body text: /cherry-payment-plan). One page of the live site has almost no text of its own: the payment-plan page, which there is filled by the payment company's widget.
- **C06 SEO inventory captured** (4 source page(s) had no title). Four pages of the live site (three category listings and one tag listing) have no title. The rebuild gives each a title made from its heading.
- **C07 Image inventory completed with real dimensions** (1 same-origin image(s) never downloaded). One background picture named only in the old theme's stylesheet sits on the web platform's own server, which refused the request. The redesign does not use it.
- **C16 Every source page exists in the rebuild** (6 missing: /template/footer, /template/footer-2, /template/header, /template/header-2…). The six addresses that are "missing" are the live platform's own header and footer fragments (`/template/...`). They are not pages.
- **C17 Content survived the rebuild** (2 content-loss finding(s)). The only words not carried are those of the two forms' anti-robot fields (a CAPTCHA label and the text of a hidden trap field), which were never meant for a visitor.
- **C20 No invented content** (0 blocker + 2 major unsourced claims). Two phrases of the live site that contain "best" are flagged. Both are the live site's own words: one ends its page, and the tracer reads fifty characters past such a word into the next part of the rebuilt page; in the other the live page splits the word "your" across two tags and the rebuild joins it. The sentence check (above) finds no sentence in the build that is not the live site's.
- **C22 Design matches the source pixel-for-pixel at every breakpoint** (worst drift 98.362% on sitemap.390.png). This is a redesign. The check asks whether the rebuild is pixel-identical to the live site; it is not meant to be.

## Hardening applied to this public copy

`PROVENANCE.json` gives the counts.

1. **`noindex, nofollow, noarchive, nosnippet, noimageindex` on every page.** This is the only control here that search engines honour. It
   is a request; the major ones follow it. A `robots.txt` with `Disallow: /` is also shipped,
   but it has **no effect** here: crawlers read `robots.txt` only at the host root
   (`chris-sgen.github.io/robots.txt`, which only a separate repository for that host could provide), not under
   `/riversidefamilyeyecare/`. GitHub Pages cannot send an `X-Robots-Tag` header either. That leaves
   the non-HTML files (the pictures, the videos, the search index) with no index control of
   their own; `noimageindex` asks search engines not to index the pictures a page shows, and those
   files are linked only from pages marked `nofollow`. The repository itself is public, and
   github.com shows its files like any public repository's.
2. `og:url` points at this preview, `og:description` / `twitter:description` carry the
   disclosure, `og:site_name` reads "Unofficial preview (not Riverside Family Eye Care)", and `og:title` / `twitter:title` begin
   "Unofficial preview:" (144 pages). `og:image` and `twitter:image` are removed (196 tags), and
   the practice's logo is not this copy's tab or home-screen icon (288 icon links removed). The
   `<title>` of a page is the live page's own and names the practice.
   What a link card shows depends on the app: apps that take a link's description or site name
   from these tags show the disclosure; apps that read none of these tags show the page's own
   title with the `chris-sgen.github.io` address; apps that pick a picture from the page itself
   may show one of its pictures.
3. **JSON-LD removed** (1,163 blocks). Most asserted the practice's identity, address, telephone and opening hours; the rest described pages, breadcrumbs and articles.
4. **Both practice forms made inert, with or without JavaScript** (the appointment request form and
   the "Email Us" form). Three safeguards are layered:
   - **A hidden, disabled submit button is placed first in each form**, followed by a hidden,
     disabled text field. A form whose default button is disabled is not submitted when Enter is
     pressed in it; a browser that skips a disabled button decides by counting the form's
     single-line fields, and the hidden field keeps that count above one.
   - Each **submit button is replaced by a disabled `type="button"`** (2 buttons).
   - Each form gets `action=""`, `onsubmit="return false"`, `method="dialog"` and
     `data-preview="inert"`, and the hooks by which the handoff build's script finds a form are
     removed, so that script does not touch these forms at all.

   A visible notice at the top of each form page and again above the form says that it is disabled
   and gives the practice's phone number; a line at the end of the form says it once more. The
   fields can still be typed in; nothing typed leaves the browser. **Site search still works**: its 157 forms
   send the query only to this site's own `/search/` page, as part of that page's address.
5. **The payment-plan widget is not loaded** (1 page, `/cherry-payment-plan/`). On the live site
   that page is a widget drawn by the payment company for the practice's own account, and an
   application made through it would be a real one. Here its loader script and the font sheet it
   asks for are removed, and a note with a link to the practice's page stands in its place.
   Likewise, 2 links that carried the practice's own dealer or referral code do not carry it here:
   the credit "Apply now" link on `/insurance/carecredit/` leads to the practice's own page, and the
   skincare maker's link on the home page is left without its code.
6. `<meta name="referrer" content="no-referrer">`, so outbound clicks don't reveal this URL to
   third parties. The one video hosted on YouTube (`/eye-care-services/eye-emergencies-pink-red-eyes/`; nothing is requested from YouTube until play is pressed, then the player loads from `www.youtube-nocookie.com`) gets
   `referrerpolicy="strict-origin"` on its frame, because the player refuses to play when it is
   sent no origin at all; the frame is then sent only this site's bare origin, never the page address.
   The 143 map frames carry `referrerpolicy="no-referrer"` themselves, because an attribute on a frame
   overrules the page's tag.
7. **No on-page disclosure banner.** The disclosure is carried by the link-preview tags (in apps
   that show them; see 2) and by this README. Apart from those notes a page looks like a page of
   the practice: its logo, address, phone number and words. On the pages themselves there are three kinds of
   note: each practice form page says that the form is disabled, the payment-plan page says its widget is not
   loaded, and the 3 pages whose own text speaks about "this website"
   (`/disclaimer/`, `/website-accessibility-policy/`, `/privacy-policy/`) say that the text is the live site's and describes the live site.
8. `sitemap.xml` and `llms.txt` are not shipped, because both advertise the practice's real
   URLs and invite crawlers. The `_redirects` file is not shipped either, since GitHub Pages ignores it.
9. **The map embed uses no API key.** It is Google's keyless embed of the practice's name and address.
10. `<link rel="canonical">` is **kept** pointing at the practice's real page. That is the usual signal for a
   duplicate, and deliberately different from `og:url`. The two pages the build makes itself
   (`/404.html` and `/search/`) have no live counterpart, so their canonicals name addresses the
   live site does not have. 4 page descriptions matched by a word list (online form, HIPAA, forms online, paperwork, book online...) (`/contact-us/appointment-request-form/`, `/contact-us/contact-form/`, `/contact-us/`, `/contact-us/patient-forms/`) are replaced by the disclosure; other descriptions, and sentences of the pages themselves that invite booking online, are kept as the live site writes them.
11. **Files left out.** 1 document of the practice (a PDF form) is not shipped: the link on `/contact-us/patient-forms/` leads to the page of the live site that offers it. 94 files of the handoff build that no page, stylesheet or script of this copy names are not shipped (mostly renditions of pictures that only the link-preview tags, the structured data or the icon links named).

## Known limits

- **The two practice forms do not submit.** This is deliberate (see 4 above). In the handoff build
  the forms are complete but not connected to a receiver.
- **The words on the pages are the live site's, and some of them speak about the live site.** The
  pages named in 7 carry a note saying so. Elsewhere the practice's words ("our website",
  "fill out the form") are carried as written.
- **The generated pictures and loops are illustrations, not the practice's photographs.** No
  caption or frame on the pages tells them apart; `PROVENANCE.md` lists each one.
- **The video loops have no pause control.** They are silent, ignore clicks, taps and keys, and
  play only on or near the screen. When the device asks for reduced motion or data saving they do not
  play at all, and the still picture shows instead. WCAG 2.2.2 (Pause, Stop, Hide) asks for a way
  to pause moving content that starts by itself and lasts more than five seconds; this design does
  not provide one.
- **The 3 films the practice published (on 2 pages) have no captions here.** They play only when a visitor presses play.
- **143 of the 144 pages carry a Google Maps frame** (in the "Hours & Location" band before the
  footer). It loads when it nears the screen (on a short page that can be at once), and the browser
  then talks to Google's servers. The frame carries `referrerpolicy="no-referrer"` (see 6), so the
  request for it names no page address; the frame's own requests were not measured for this file.
  **A visitor's browser contacts two third parties:** Google (this map frame) and YouTube (one
  page, only after play is pressed). Fonts, scripts and pictures are served from this site. A
  search sends its words to this site's own `/search/` address, so they reach GitHub's servers like any page address.
- **Links that lead to live services.** The phone links dial the practice (`239-500-2020`) and the
  e-mail links open a message to it (`info@riversidefamilyeyecare.com`, `optician@riversidefamilyeyecare.com`). Links leave this copy for `google.com`, `youtube.com`, `facebook.com`, `yelp.com`, `maps.app.goo.gl`, `builder.eyeglassguide.com`, `infantsee.org`, `alumiermd.com`, `carecredit.com`, `longafamilyeyecare.com`, `get.adobe.com`, and for the practice's own site (the payment-plan note, the credit application link and the document link):
  the practice's review, map and social pages, the makers and programmes its pages name, one
  doctor's other practice, and a document reader's download page. What a
  visitor does there reaches those services, not this copy. "Request Appointment" leads to the
  disabled form of this copy.
- **42 picture files of the live site could not be downloaded** (several are sizes of the same
  picture): 36 were refused (HTTP 403) by the live site's image host and 1 by its platform's
  server, 4 timed out at the image host (HTTP 504), and 1 video thumbnail on YouTube's image
  host returned HTTP 404. The pipeline does not retry past a refusal. Several are team portraits:
  wherever one of those people is shown, the page shows a tile with the person's initials instead
  (45 placements). Where the missing file was a stock photograph that only illustrated a topic,
  a generated still may stand in its place.
- **This copy republishes people's names and pictures as the live site shows them**: the
  practice's doctors and staff (names, biographies, portraits, one staff film) and patient reviews
  signed with a first name and an initial.
- **17 of the rebuilt pages are `noindex` on the live site itself**; here every page is `noindex` anyway.
- **The search index is the handoff build's file with two changes.** The entries of the 2 practice-form pages keep only their titles, and the summary of 2 other pages (`/contact-us/`, `/contact-us/patient-forms/`) matched by the same word list is blanked; the page text in the index is otherwise the live site's.
- **Tested in Chrome only.** The checks above ran in headless Chrome; Firefox and Safari were not run.
- **Commit metadata is public**: the author's name and e-mail address, and the commit times.

## Licence / ownership

This repository is an unaffiliated development artifact and asserts no rights over any of its
content.
- The writing, photographs and films the practice published, and the Riverside Family Eye Care name and
  logo, remain the practice's or their respective owners'. Patient reviews quoted on the site
  belong to their authors.
- The practice's site also shows third-party material, and this copy carries it as found: stock
  photographs in its articles, and frame-brand, contact-lens and insurance logos. The owners'
  rights remain theirs; the trademarks among them belong to their owners.
- The generated pictures and loops were made for this redesign with the models named in
  `PROVENANCE.md`. None shows a person or a legible brand mark; 3 carry a blurred mark noted in `PROVENANCE.md`.
- The typefaces are Jost and Mulish (both SIL Open Font License 1.1), self-hosted.
