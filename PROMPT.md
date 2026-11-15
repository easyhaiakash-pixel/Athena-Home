# Build "Athena's Home": a 3D website for the One Life series

Read this whole file before you start. The owner is not a developer, so make every decision yourself and write simple English in all notes.

## 1. What this is

**One Life** is a daily Instagram/YouTube cartoon series (@one_life_daily_you_choose). One day = one year of a girl's life. The viewers voted her a girl and named her **Athena**. She is turning **3** in the next episode.

Fans can "gift" Athena things through Amazon affiliate links (clothes, toys). When fans buy an item, it becomes part of her life: it shows up in the next video, and now **also in her home on this website**.

**The website:** a cute 3D house built with three.js. Visitors walk or tap through Athena's home, see her family, and see every item fans have gifted her in the room where it belongs (dress in the wardrobe, unicorn on the bed, doctor kit on the floor and so on). Tapping an item opens a card with a "Get one for your little one" button (Amazon USA or India).

**Goals, in order:**
1. Fans feel they are building her life → they come back and share it.
2. Every item is a shop button → affiliate sales.
3. It must be easy to add a new item in 2 minutes, by editing one file.

## 2. Read first
- `~/personal/one-life/SERIES_BIBLE.md`: series rules
- `~/personal/one-life/STYLE.md`: the look ("Style test 2: soft and cuter")
- `~/personal/one-life/style-tests/02-day1-cute-style.png`: **match this look**
- `~/personal/one-life/scripts/L1-D02-athena.md`: Athena's look (pink-cream hat with a small bow) and Mom
- `~/personal/one-life/videos/Day-02-Athena-thumbnail.png`: how she looks now

## 3. Look and feel (strict)
- **Soft kawaii style** like style test 2: pastel colours, warm-brown thin outlines (not heavy black), rounded shapes, big glossy eyes with sparkles and blush, warm sunlight through windows, gentle soft shadows.
- **Draw every object in code** (three.js shapes, toon/gradient materials, outline pass or inverted-hull outlines). **Never** use free kit models (Kenney, Poly Pizza, Sketchfab packs). Everything must look like it belongs to the same cartoon.
- Characters: **Athena (age 3)** and **Mom**. Same look as the videos. Gentle idle animation (breathing, blinking, Athena swaying or hugging her unicorn). No lip movement. Don't add a Dad or other family members unless they appear in a script; leave a clearly marked empty spot in `data/family.json` for later.
- It should feel like a real, warm home, not a game level: rugs, curtains, plants, family photos on the wall, toys on the floor.

## 4. The house
Start with **3 rooms**, connected:
1. **Athena's bedroom.** Bed, wardrobe, toy shelf, play rug, window. Most gifts go here.
2. **Living room.** Sofa, TV, family photo wall, Mom sitting here.
3. **Kitchen.** Mom's kitchen. Also a spot for a toy kitchen set.

Plan for more later (garden, bathroom, her school bag corner). Rooms come from `data/rooms.json` so new ones can be added.

**Moving around (phone first):**
- Tap a door or a room button at the bottom → the camera glides smoothly to that room (about 1 s ease, no jumps).
- Drag to look around a little inside a room (limited angle, never lose the room).
- Tap an item → the camera leans in a bit and the item card opens.
- Desktop: the same, with the mouse.

## 5. Gifted items (the important part)
All items live in **`data/items.json`**. Example:

```json
[
  {
    "id": "red-party-frock",
    "name": "Red party frock",
    "emoji": "👗",
    "status": "gifted",
    "giftedOnDay": 4,
    "room": "bedroom",
    "spot": "wardrobe",
    "model": "dress",
    "color": "#9b1c2c",
    "note": "She wore it on her 3rd birthday!",
    "links": {
      "in": "https://link.amazon/B04EufOyt",
      "us": ""
    }
  }
]
```

- `status: "gifted"` → shown as a real, full-colour object in the room, with a tiny ✨ sparkle and a "Gifted by you on Day 4" tag.
- `status: "wish"` → shown as a **soft see-through ghost** with a small 🎁 tag: "Not gifted yet. Gift it to her!" This is what makes people buy.
- `spot` → named places in each room (wardrobe, bed, shelf, rug, floor-left, kitchen-counter and so on), defined in `rooms.json`. Several items can share a spot; place them neatly side by side.
- `model` → a small set of **code-drawn item builders**: `dress`, `outfit-set`, `plush` (with `variant`: unicorn, elephant, teddy), `doctor-kit`, `makeup-trolley`, `toy-kitchen`, `doll`, `shoes`, `hair-bows`, `generic-box` (a pretty gift box, the fallback for anything new). Colour comes from `color`.

**Item card** (opens on tap), soft white rounded card:
- Item name and emoji, the note, "Gifted by fans on Day X" (or "Gift it to her 🎁")
- Buttons: **🇺🇸 Get it (USA & world)** and **🇮🇳 Get it (India)**. Show only the buttons that have links. Put the visitor's likely country first: India first if the time zone is `Asia/Kolkata` or the language is `en-IN`/`hi`, USA first otherwise.
- Links open in a new tab. **Use the link exactly as written. Never change or strip the link** (it carries the affiliate tag).

## 6. Amazon rules (must follow)
- Footer on every view: **"As an Amazon Associate I earn from qualifying purchases."**
- **No prices** on the site (Amazon prices change; showing old prices breaks their rules).
- **No Amazon product photos.** Only our own drawn 3D items.
- No login and no data collection. The site is for parents (adults). Don't speak to children ("ask your mom to buy").

## 7. Other parts of the page
- **Top bar:** "Athena's Home 🏠", her AGE chip (from `data/athena.json`, for example `{"age": 3, "day": 4, "life": 1}`), and a button to the Instagram page.
- **"Gift wall"** button: a simple 2D list of all items (gifted and wishes), for people who don't want to explore in 3D. Same cards and buttons.
- **Loading screen:** Athena waving + a progress bar. The site must start within **3 seconds on a normal phone in the Instagram in-app browser**.

## 8. Tech
- Plain **three.js + Vite** (or no build step with ES modules from a CDN; pick whichever is simpler to host). No React needed.
- Total download under **3 MB**. Aim for 60 fps on a mid phone: keep draw calls low, merge static furniture, no real-time shadows on phones (use baked/fake soft shadows).
- Works in the **Instagram and YouTube in-app browsers** (test with a small phone screen size, 390×844).
- Hosting: make it ready for **free static hosting** (Netlify drop or GitHub Pages). Write the exact steps in `HOW-TO-PUBLISH.md`. **Do not publish it yourself**; the owner decides.

## 9. Folder
Everything in `~/personal/one-life/athena-home/`:
```
athena-home/
  PROMPT.md            (this file)
  README.md            (what it is, how to run it locally)
  HOW-TO-ADD-ITEM.md   (2-minute guide for the owner, with a copy-paste example)
  HOW-TO-PUBLISH.md
  data/items.json, rooms.json, athena.json, family.json
  src/...
  checks/              (screenshots)
```

## 10. Starting items (the current gift shop)
Put these in `items.json`. All start as **`"wish"`** (nobody has ordered yet). The owner flips them to `"gifted"` after checking Amazon reports.

| id | name | model | room / spot | India link | USA link |
|---|---|---|---|---|---|
| red-party-frock | 👗 Red party frock | dress (deep red, tutu) | bedroom / wardrobe | https://link.amazon/B04EufOyt | |
| knit-birthday-dress | 🎂 Knitted birthday dress | dress (knit) | bedroom / wardrobe | https://link.amazon/B09VEpOSE | |
| glitter-unicorn | 🦄 Glitter unicorn | plush / unicorn | bedroom / bed | https://link.amazon/B06wk48lI | |
| pink-doctor-kit | 👩‍⚕️ Pink doctor kit | doctor-kit | bedroom / rug | https://link.amazon/B04u0Mmtd | |
| beauty-trolley | 💄 Beauty trolley | makeup-trolley | bedroom / floor-left | https://link.amazon/B08Ffu05N | |
| birthday-tutu-set | 🎂 Birthday Girl tutu set | outfit-set (pink, pom-poms) | bedroom / wardrobe | | https://link.amazon/B07qTS02Q |
| musical-elephant | 🌈 Glowing musical elephant | plush / elephant (rainbow, soft glow) | bedroom / bed | | https://link.amazon/B0e0zZa6Q |

## 11. Checks before you say "done"
1. Screenshot every room plus an open item card at **phone size (390×844)** and at desktop size. Save them in `checks/` with numbers (`01-bedroom.png` …) and open each image so the owner sees it.
2. Compare them with `style-tests/02-day1-cute-style.png`. Is it the same cute, warm, pastel look? If any object looks plain, grey, blocky or "programmer art", redraw it before moving on.
3. Tap every item: does the card open, and does every button go to the exact link in `items.json`?
4. Flip one item from `wish` to `gifted` in `items.json`, reload: does it turn into a real object with the sparkle tag?
5. Add a brand-new item using only `HOW-TO-ADD-ITEM.md` with `model: "generic-box"`: does it appear correctly?
6. Check the loading time and fps with phone throttling in Chrome DevTools.
7. Footer disclosure visible, no prices, no Amazon photos.

When everything passes, write a short report in simple English: what was built, the screenshot paths, and anything the owner must decide.
