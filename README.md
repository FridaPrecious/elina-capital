# Eliana Capital website: design prototype (v20)

## What changed in v20 (fixes on top of v19)
Changed: `tools/home2.py`, `tools/build.py`, `css/v19.css` (block at the end), `js/phone-pop.js`, and all rebuilt pages.
- **One "We grow together" on the landing page**: the static tagline under the hero logo is gone. The one on the phone screen stays. The phone now keeps clear of the logo instead.
- **Same design on every screen**: the viewport meta in `tools/build.py` is now `width=1280`, so phones and tablets show the desktop layout scaled down instead of the stacked small-screen layout. Change `1280` to a smaller number to make everything bigger on phones. The hero height and phone positions are capped so the page keeps desktop proportions.
- **How we work**: the line icons on the four cards are removed.
- **Menu on short desktop windows**: the link list was centred taller than the screen, so "Home" slid up behind the header. The menu now starts below the header, the links shrink with screen height, and it scrolls if still too tall (end of `css/v19.css`).

# Eliana Capital website: design prototype (v19)

## What changed in v19 (small screens + homepage finish on every page)
New files: `css/v19.css`, `js/v19.js`. Changed: `tools/build.py` (links both, contact grid class). Remove the v19 links in `build.py` to go back to v18.
- **Small screens**: the contact page used a fixed two-column grid that never stacked, which squeezed the form and cut off the contact card. It now stacks under 900px. Menu, footer word, tabs and hero are sized for phones.
- **Menu**: serif links with hairlines that glide in one by one, a glow behind, and phone, WhatsApp and email as tappable glass pills.
- **Inner pages**: hero, mono labels with hairlines, serif headings with an italic green accent phrase, ruled fact tables, lifted cards, a proper pull-quote, and gentle scroll reveals. Accent words are added automatically by `js/v19.js`.
- **Contact**: the details card is now a dark glass panel with a tappable tile per channel; the form tabs scroll sideways on phones.

# Eliana Capital website: design prototype (v18)

## What changed in v18 (final touches)
New files: `css/v18.css`, `js/v18.js`. Changed: `tools/home2.py`, `tools/build.py`, `css/styles.css` (appended block at the end), `README.md`. Remove the v18 links in `build.py` to go back to v17.
- **Customer stories** (home): panels that open as you point at them. The open one shows the photo in full colour with the story title and a "Read story" button; the others stay narrow with a vertical label. When nobody is pointing they open one by one every 5.2s, with a progress line (`--dwell` in `css/v18.css`). Tab key works too. On phones they are a swipeable row.
- **How we work**: four cards that slide over each other as you scroll. The card underneath scales back and dims, the photo opens like a curtain and drifts, a line icon draws itself, and a glass chip fades in. The background has slow aurora colour, grain and a rotating "We grow together" badge. Edit icons and chips in `ART` and `TAGS` in `tools/home2.py`.
- **Clock removed** from the hero (and its code path is now unused).
- **Numbers removed**: the (01) labels, the left-edge 01/07 tab, numbers on the promise cards, the steps (now dots), the branch list, the process steps on How it works, and the story index on Customer stories.
- **Real icons**: WhatsApp logo, phone, mail and map pin (inline SVG, no files) in the Find us pills, the menu, the footer, the contact page card and the WhatsApp buttons. They are defined once as `[[I_WA]]`, `[[I_TEL]]`, `[[I_MAIL]]`, `[[I_PIN]]` near the top of `tools/build.py`.

# Eliana Capital website: design prototype (v17)

## What changed in v17 (smooth phone, clean hero, finishing layer)
New files: `css/v17.css`, `js/v17.js`. Changed: `js/phone-pop.js`, `css/home.css`, `tools/home2.py`, `tools/build.py`. Remove the v17 links in `build.py` to return to the v16 finishing layer.
- **Smooth phone**: every part of the phone's motion (position, size, turn) now follows its target through a critically damped spring, so it keeps its velocity and never jerks, even on a fast scroll or a touch fling. The turn between sections is one continuous, accumulating spin, and the screen swaps only while the back of the phone faces you. A graceful dip in size and a warm glow that brightens with scroll speed accompany each flight. Edit the spring stiffness in the `Spring(...)` lines in `phone-pop.js`.
- **Drop-in on load**: a soft spring with one gentle settle (no bounce), one full turn, starting about 3.2s in.
- **9:41 removed** from the phone screen (the battery icon went with it; the island stays).
- **Hero overlap fixed**: the hero phone anchor has `data-avoid=".h-tag"`, so the phone shrinks from the top to always stay 26px below "We grow together" on any screen size. The logo is a little smaller and sits higher to give the phone room.
- **Finishing layer**: scroll-progress line along the top, pointer depth in the hero (sky and logo drift against each other), and a staged entrance (tagline arrives with the sun, then the cue and clock).

# Eliana Capital website: design prototype (v16)

## What changed in v16 (sunrise hero + editorial type, home page)
New files: `css/v16.css`, `js/v16.js`, `assets/hero-nosun.jpg`, `assets/hero-nosun-m.jpg`. Changed: `tools/home2.py` (hero markup, italic accent words, numbering), `tools/build.py` (links the new files, adds the DM Mono font), `js/home.js` (headline split keeps italic words; blur bug fixed in css), `js/phone-pop.js` (phone now pops at first light, about 3.5s in). Delete the `v16` links in `build.py` to return to v15.
- **The sunrise**: the hero photo now has the baked-in sun removed (`hero-nosun*.jpg`). A real sun, glow, rays and drifting dust rise out of the skyline on load over about 7 seconds while the sky warms from blue hour (indigo, rose) to gold. The logo is white at first light and turns to full colour. A small clock (05:31 to 06:25 EAT) follows the sun. Everything is driven by one value, `--sr` (0 to 1), set on `.h-hero` by `js/v16.js`. Preview any stage with `index.html?sr=0.3`. Reduced motion shows the finished, sunlit scene at once.
- **Sun position**: `--sx`, `--sy` (where the sun settles) and `--hz` (horizon line) at the top of `.h-sky` in `css/v16.css`. If you swap the photo, change those three numbers; the photo must have no sun in it.
- **Text layout**: a hanging mono index label with a hairline that draws in ("(01) WHO WE ARE"), very large tight serif headlines with one italic green accent phrase, a full-width headline over the phone in the intro and loan sections, ruled fact and price tables with big numerals, steps as ruled rows whose titles light up as you reach them, staggered numbered promises, a numbered branch list, and a huge call to action with the sun coming up under it. A thin vertical tab on the left edge shows which section you are in (wide screens only).
- **Accent words** are the `<em>` tags in the headings in `tools/home2.py`.
- **Fix**: the paragraph that lights up as you read was permanently blurred by an old inner-page style. It is sharp now.
- Fonts load from Google Fonts (Fraunces, Outfit, DM Mono). Offline you will see fallback fonts, which looks plainer than the real thing.

# Eliana Capital website: design prototype (v15)

## What changed in v15 (home page rebuilt: real photos, one phone, no repetition)
The home page is now generated by `tools/home2.py` (called from `tools/build.py`). Inner pages are unchanged. Home-only files: `css/home.css`, `js/home.js`, `js/phone-pop.js`, `assets/hero-grade.jpg`, `assets/hero-grade-m.jpg`. The old `build_home()` is still in `build.py` for reference but no longer runs.
- **Hero = a real photo and the logo.** Nairobi at sunrise, graded toward the brand blue in the shadows, with a pale golden haze at the top so the blue and green logo reads. Nothing else on screen.
- **A 3D phone pops out of the photo** (`js/phone-pop.js`, three.js): it springs up out of the hero, overlaps the photo's edge, then flies between sections as you scroll. It spins a full turn between stops and swaps its screen while the back faces you. The screens show your real customer photos (`tailor.jpg`, `shop.jpg`, held as data in `js/imgdata.js`).
- **Each message appears once**, in this order: hero, who we are (3 key numbers), why Eliana (six assurances as callouts around the phone, over a real photo), the loan priced in plain words, five steps, four promises with the people who keep them, customer stories (the only place customer photos appear), branches and short FAQ, call to action.
- **Removed**: the duplicated feature cards and marquee, the four stacking service cards, the second "Know the price" block, the "Real people" arches repeated under the hero, the dark 3D "How we work" panels, the rail dots, the travelling hands, the giant text bands.
- **Motion** (hand-written versions of patterns from reactbits and motion.dev): word-by-word headline reveal, paragraph that lights up as you read, count-up numbers, tilting story cards, magnetic buttons, a spring-driven phone, scroll-linked step line, a Lenis-style smooth scroll, and a cursor ring that says "View" over stories. All off with reduced motion.
- **Photos**: all from `assets/`. The hero skyline source is only 720px wide, so it is slightly soft on large screens. Drop a 2400px+ sunrise photo over `assets/hero-grade.jpg` (keep the warm sky and a tall tower on the left) for the final polish.
- Edit the phone screens in `drawA`, `drawB` and `drawC` in `js/phone-pop.js`. Anchors are the `data-phone` boxes in `tools/home2.py` (`data-yaw` is the resting angle, `data-screen` picks the screen).

# Eliana Capital website: design prototype (v14)

## What changed in v14 (a real hero object, a real scene, smooth motion)
New files: `css/v14.css`, `js/hero-scene.js`, `js/phone3d.js`, `js/v14.js` (linked in `layout()` in `tools/build.py`; all pages rebuilt). Delete those links to return to v13.
- **Why v13 felt flat**: the hands mark was a flat vector with no light or depth, the hero photo was a soft 720px image, and cards, chips and rail dots all competed. MYLK works because there is one real object, one sharp scene, and air around them.
- **3D phone replaces the travelling hands** (`js/phone3d.js`, three.js, no extra files). Glossy blue frame, glass screen showing the Imaarika loan, branded back. It rides the same `.mk` flight path from `js/v10.js`, spins a full turn between sections, tilts toward the pointer. If WebGL is missing, the hands appear exactly as before. The hands stay as the logo in the header and footer.
- **Hero scene** (`js/hero-scene.js`): a Nairobi dawn drawn in code, in the brand blue, green and gold: sky, sun and soft rays, three skyline layers with the KICC tower, an acacia, tall grass. Seven depth layers move with the pointer and with scroll. Crisp at any size. The old photo files are still there but unused.
- **Calmer layout**: side rail dots hidden, hero chips now sit around the phone on dotted lines, the headline lifts away as you scroll.
- **Smooth scroll** (`js/v14.js`): a Lenis-style glide on the mouse wheel, in-page links glide, touch and keyboard stay native. Scroll speed leans the giant type band.
- **Cursor ring** that grows on links and reads "View" over photos (mouse only).
- Reduced motion: scene and phone are drawn once, no smooth scroll, no cursor.
- Edit the phone's screen text in `drawScreen()` in `js/phone3d.js`; edit the scene's colours in the gradients at the top of `build()` in `js/hero-scene.js`.

# Eliana Capital website: design prototype (v13)

## What changed in v13 (editorial finish, MYLK and Naturals level)
New files only: `css/v13.css`, `js/v13.js` (linked from `layout()` in `tools/build.py`; all pages rebuilt). Delete the two links to return to v12.
- **Serif headlines**: Fraunces (Google Fonts) for h1, h2 and the call-to-action; Outfit stays for body and UI.
- **Hero**: headline no longer collides with the hands mark; golden-hour glow, slow rotating sun rays and drifting pollen (canvas, pauses off screen). `hero-nairobi.jpg` and `-m.jpg` are sharpened, graded and grained; the untouched originals are saved as `*.orig.jpg`. A 2400px+ original photo is still the best upgrade.
- **Botanical line art**: ferns, acacia, aloe, sugarcane grass and a bloom, drawn in code (no image files). They draw themselves in when scrolled to, sway, and drift at a different speed from the page. Placement is the `PLAN` list at the top of `js/v13.js`.
- **Giant type band** before "Branches": Market traders, Tailors, Salon owners... slides with scroll, between two kitenge-inspired pattern strips (SVG made in code).
- Reduced motion: art stays visible and still, pollen and band movement are off.
- Photos: these are code-made graphics, not photographs. Replace the stock photos in `assets/` with your own real shoots for the final launch.


Static HTML, CSS and JavaScript. No build step needed to view it. Pages are generated by tools/build.py.

## What changed in v12 (a golden-hour photo hero on flat cream, MYLK-style)
Replaces the v11 "living background" (photo wash, colour orbs, dot grid, pointer glow, seeds, grain). `css/v11.css` and `js/v11.js` are gone; the new files are `css/v12.css` and `js/v12.js`.
- **Full-bleed hero photo**: the home hero sits on one photo of the Nairobi skyline at sunrise (`assets/hero-nairobi.jpg` for desktop, `assets/hero-nairobi-m.jpg` for phones, both made from `offer-3.jpg`). The headline and the hands mark are centred on top, a pale haze at the top keeps the headline readable, the photo drifts very slowly, and it melts into cream at the bottom.
- **Everything else is flat cream** (`#fefef1`): no gradients, textures or background photos. The old hero blobs, the giant "grow" word, the ripples and the glow behind the hands mark are off. Cream sections use solid cream and leaf tints.
- **Copy on the photo** sits on soft cream cards so it stays readable over the skyline.
- **Gooey blob buttons**: every `.btn` gets four blobs that rise on hover (JS adds them; a hidden SVG `goo` filter is added once).
- **Sharper photo**: the source (`offer-3.jpg`) is only 720px wide, so the hero photo is soft. Drop a larger photo (2400px+ wide, sun and skyline in the middle) over `assets/hero-nairobi.jpg` and it will just work. Photo height is `--photo-h` in `css/v12.css`; framing is `object-position`.
- Inner pages keep their dark rounded hero bands on the flat cream page.

## What changed in v11 (page source, MYLK Co style)
**Page source in the MYLK Co style.** Every page's `<head>` is now built by `head_block()` in `tools/build.py`, in labelled sections:
primary SEO meta (title, description, keywords, robots, canonical, geo), Open Graph, Twitter card, favicons and app icons, theme colours, preconnects, and JSON-LD structured data (Organization, FinancialService with the three branches and the Imaarika loan, WebSite on Home, WebPage, BreadcrumbList on inner pages, FAQPage on the FAQs page). The body has matching section comments.
New files: `og-image.png` (1200x630 share image), `favicon/` (ico, 16, 32, apple-touch, 192, 512), `site.webmanifest`, `robots.txt`, `sitemap.xml`.
**Before launch:** set `SITE_URL` at the top of `tools/build.py` to the real domain (it is `https://eliana-capital.com`, taken from the email address), then run `python3 tools/build.py`. Phone, email and branches come from `CONTACT` and `BRANCHES`. Facts that are not known yet (street address, opening hours, social links, founding year) are left out of the structured data on purpose; add them in `head_block()` when you have them. No star rating is included because there are no real reviews yet.

## What changed in v10 (the hands travel with the text, inspired by mylk-co.com)
On mylk-co.com the cup is the star and it moves down the page with the words. Here the star is our logo, the four hands. Everything is in `css/v10.css` and `js/v10.js`, plus the home page markup in `tools/build.py`. Remove the `v10.css` link in `layout()` to see v9 again.
- **One hands mark that travels from section to section** (home page). On load the four hands fly in, spin and lock together in the hero, then keep gently reaching and swaying. As you scroll, the mark opens up, turns a quarter turn and lands in a reserved spot next to the text of each section, so it never sits on top of the words: above "Why Eliana", beside "Who we are", beside "One clear loan", as a sticker on the pricing receipt, beside "How we work" (white hands on the dark band), beside "Questions", and beside "Ready when you are" (white and blue on the green band).
- **Stations**: each landing spot is a `<div class="mk-slot" data-mk-stop data-mk-theme="light|dark|green">` in `tools/build.py`. Add or move one and the mark will include it. The hero spot is `.hero-slot`. `data-mk-theme` sets the hands' colours at that spot.
- **Far-apart stations** (the stacking service cards) get no flight: the mark stays with the spot it left and the next spot picks it up, so it never floats over the cards.
- **Hero**: headline, then the mark in the middle with the intro text on the left and the buttons on the right, a giant soft "grow" word behind it, ripples growing out, two floating chips, morphing background blobs, and a green swoosh drawn under "trap."
- **Big hands behind the dark "How we work" band and the call-to-action band** turn slowly as you scroll. The 3D wave in the home call-to-action band was replaced by the mark (inner pages keep their 3D scenes).
- **Phones**: the same journey, with the spots in the normal flow above or below the text.
- **Reduced motion**: the mark is still and simply sits at the nearest spot; ripples, chips, blobs and spinning decorations are off.
- To tune the feel in `js/v10.js`: `HOLD` (how long it stays at a spot before setting off, `.3` = 30% of the way), `FLY_MAX` (how far apart two spots can be and still get a flight), and the `* 90` quarter turn. Spot sizes are `--s` in `css/v10.css`.

## What changed in v9 (design refresh, inspired by Naturals and MYLK Co)
The whole look moved from "dark blue with 3D" to a warm, rounded, editorial style. Brand blue, brand green and the typeface are unchanged.
All of it lives in two new files, `css/v9.css` (loaded after `styles.css`) and `js/v9.js`, plus changes to the home page in `tools/build.py`. Delete the `v9.css` link in `layout()` to see v8 again.
- **Floating pill header** on every page (Naturals): a rounded cream bar with the logo, "Apply for support" and Menu. The Menu overlay opens from the button inside the pill.
- **Warm cream paper** (MYLK Co) replaces the cool lavender tint, with bigger radii everywhere and big rounded bands (dark "How we work", the brand band, the call-to-action and the footer) inset from the page edges.
- **Home hero**: centred headline on cream, a "Now lending in..." chip, and three arch-shaped customer photos that float gently (the WebGL photo effects still run on them), a rotating "We grow together" badge, and the loan facts in a rounded card. The 3D hands mark that used to sit in the home hero is gone; the 3D scenes remain on every inner-page hero and call-to-action band.
- **"Why Eliana" feature cards** scroll by themselves (Naturals "more than beauty" row). They pause on hover or focus, and become a swipeable row if the visitor prefers reduced motion.
- **"What we offer" is now four service cards that stack as you scroll** (Naturals "expertly made, with care"). Each card keeps the photo-backed scene from v7.1, plus tags and a button. The card underneath settles back as the next one slides over. On phones the cards simply stack.
- **Section labels** are written ( like this ), as on Naturals.
- **Stat cards**, soft FAQ cards, pill chips for "People we back", and arch-shaped photos for the home customer stories (still swipeable on phones).
- Rail dots no longer turn white over the (now light) home hero.

## What changed in v7.1 (contact details and "What we offer")
- **Menu contact details fixed on every page**: the "Talk to us" panel still showed the old placeholders (`+254 7XX XXX XXX`, `hello@eliana-capital.com`) on 11 pages because those pages had not been rebuilt after `CONTACT` was edited. All pages are rebuilt, so the menu, footer, WhatsApp links and FAQ button now use `+254 721881177` and `support@eliana-capital.com`.
- **What we offer**: each of the four panels now has a photo behind its graphic (`assets/offer-1.jpg` to `offer-4.jpg`): market trader, handshake, Nairobi skyline, harvest. A colour wash keeps the bars, receipt and labels readable, and the photo drifts slowly while its panel is showing (off for reduced motion).
- **Kept your edit**: the hidden "Six more / Branches planned" row on Home was only commented out in `index.html`, so a rebuild would have brought it back. It is now commented out in `tools/build.py` too.
- **Typo fixed**: `index.html` had `fgitont-weight` in the last offer panel (stray text); the rebuild corrects it to `font-weight`.

## What changed in v7 (phones and touch)
Phones have no hover, so the effects a mouse triggers are now driven by scrolling, swiping and tapping (`js/touch.js`):
- **Services**: the animated scene is back on phones as a card pinned under the header; it changes as you scroll through the services.
- **How we work**: the box for the part of the page you are on opens by itself, smoothly. Tapping a box still works and pauses this for a few seconds.
- **Customer stories**: a swipeable 3D carousel (neighbouring cards turn away, dots show where you are). The index list shows a photo on every row and the row in the middle of the screen lights up.
- **Cards** tip up into place in 3D as they scroll in. **Photos** tilt as they pass and ripple when tapped. Cards light up where you tap.
- **3D scenes** are larger on phones, follow your finger, and tilt with the phone on Android.
- **Bug fix**: `body{overflow-x:hidden}` was silently breaking `position:sticky` everywhere (services stage, story page photo, footer reveal). It now uses `overflow-x:clip`.

## What changed in v6
- **New pages**: `terms.html` (Terms of use) and `accessibility.html` (Accessibility statement), linked from the footer. The text is placeholder copy and must be reviewed by a lawyer and confirmed by a real accessibility audit before launch.
- **Fixed the "page refreshes twice" feel**: the page-transition curtain was created by JavaScript at the end of the page, so the new page flashed, the curtain popped over it, then lifted. The curtain is now in the HTML and covers from the first paint.
- **Motion engine** (`js/motion.js`), using ideas from Motion (motion.dev), React Bits, OriginKit and the react-three-fiber examples:
  - spring physics for magnetic buttons, card tilt and button press (replaces CSS easing)
  - rolling-text buttons and a light sweep on hover
  - scroll word reveal on intro paragraphs
  - scroll-velocity marquee bands (speed and direction follow your scrolling)
  - hero copy drifts and fades on scroll; footer "Eliana" word rises
  - text scramble on page labels
  - footer reveal: the page lifts away to uncover the footer
  - spring-style overshoot on scroll reveals
- **3D scenes**: pointer following now uses damped spring physics, and the page-hero pieces spread apart as you scroll (bars, orbiting cards, rings).
- Everything in the motion engine is switched off when the visitor's device asks for reduced motion.

## What changed in v4
- **WebGL photos on every page** (`js/gl-images.js`): each photo is a shader-driven 3D plane. It bends and splits colour as you scroll, ripples and tilts under the cursor, wipes in with a slow zoom-out, and has parallax inside its frame. Photo data is embedded in `js/imgdata.js` so this works from a plain folder; if WebGL is unavailable the normal image shows.
- **Customer stories redesigned** in an editorial style: a large featured story, a staggered gallery, and an index list where a floating photo follows the cursor and tilts with its speed. The 3D hero cards now carry the real photos.
- **Page feel** (`js/flow.js`): curtain page transitions, eased scrolling (set `SMOOTH = false` at the top of the file to turn it off), and a cursor follower that says "Read" over stories.
- The category filter chips on the stories page were replaced by the index list.

## What changed in v3
- **3D on every page**: each inner page hero has its own three.js scene (mark, rising bars, step path, orbiting story cards, torus knot, globe, gyroscope rings) plus an aurora glow. Every call-to-action band has the cursor-reactive wave.
- **Customer stories are clickable**: cards, and the home page photos, open their own story pages (`story-*.html`). Stories can be filtered by business type.
- **Motion layer** (`js/fx.js`): split-text blur reveals, scroll reveals, spotlight cards, count-up stats, magnetic buttons, 3D card tilt, scroll-lit steps, scroll progress bar, page transitions, FAQ search.
- Removed the "Design prototype for review" footer text.

## What changed in v2
- **Official logo**: extracted as vector from pages 2 to 4 of the brand guideline (`assets/logo-white.svg`, `logo-color.svg`, `logo-green.svg`, `logo-mark.svg`, `logo-mark-white.svg`). The header uses the white version over the dark hero and the full-colour version once it turns solid.
- **Your photos**: `tailor.jpg`, `shop.jpg`, `farmers.jpg`, `couple.jpg` (resized for the web) are used on Home, About, Services, How it works and Customer stories.
- **3D layer** (three.js, bundled in `assets/vendor/`, works from a plain folder):
  - Hero: the real hands mark extruded in 3D, floating, rotating, reacting to the cursor and the scroll, with glossy orbs and sparkles.
  - Call-to-action band: an instanced wave of bars that rises toward the cursor.
  - Photos, the price receipt and the services panel tilt in 3D with a light glare.
  - Techniques follow the react-three-fiber / drei ecosystem (Float, Environment, MeshDistortMaterial, Sparkles, ScrollControls, instancing), rebuilt in vanilla three.js. For the real Next.js build, the same scenes port directly to `@react-three/fiber` and `@react-three/drei`.
  - Respects "reduce motion" (shows a still frame), pauses off-screen, and lowers quality on slow devices.

## Still placeholder
- **Typeface**: Outfit stands in for Sofia Pro. Add licensed files and the `url(...)` hints at the top of `css/styles.css`.
- **Phone, WhatsApp, email**: edit `CONTACT` at the top of `tools/build.py`, then run `python3 tools/build.py`.
- **Customer story text**: sample copy; replace with real, consented stories.
- **Director portraits**: photo slots on About.
- **Privacy notice**: draft, needs legal review.
- **Forms**: validated in the browser but not stored. The build phase saves to Supabase first, then notifies staff.

## Editing
Pages are generated by `tools/build.py` (run it after changes). Styles: `css/styles.css`. Interactions: `js/main.js`. 3D: `js/scene3d.js`.
Three.js is MIT licensed (`assets/vendor/three-LICENSE.txt`).

## What changed in v4.1 (How we work)
- Each of the four panels now carries a photo from the ECL introduction deck (`assets/how-*.jpg`). Photos are tinted when collapsed and full colour when open.
- Panels open on hover (short intent delay so they don't flicker). Click, tap and keyboard (Tab, Enter) still work.
- The custom ring cursor is hidden over the panels, so the normal pointer shows there.

## What changed in v8
- **Swipeable stories on phones**: the home page photos and the customer stories page are now carousels. Swipe, tap the arrow buttons, tap a dot, or (on a narrow desktop window) drag with the mouse. Code: `js/swipe.js`; styles at the end of `css/styles.css`.
- **Director portraits**: `assets/ayoti.jpeg` is used on the About page. Add `assets/faith.jpeg` (any square-ish photo) and it appears automatically; until then Faith's initials show in the circle.
- **Scrolling brand band** redesigned: solid white text on deep blue with room for descenders (g, p, y were being clipped), no outline text.
- **Cleaner copy**: removed all "prototype", "design placeholder", "sample story" and "draft for legal review" notes. Customer stories have short written copy for each story (see `STORY_COPY` in `tools/build.py`); replace it with real, consented stories before launch.
