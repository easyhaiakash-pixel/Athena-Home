# Athena's Home 🏠

A cute 3D house for the **One Life** series. Fans walk through Athena's home (bedroom, living room, kitchen) and see every gift they sent her. Every gift opens a card with Amazon buttons (USA and India).

- Gifted items (`"status": "gifted"`) are real, full-colour objects with ✨ sparkles.
- Wishes (`"status": "wish"`) are soft see-through ghosts with a 🎁 tag.
- Everything is drawn in code (three.js). No downloaded 3D models and no Amazon photos.
- No login, no tracking, no cookies.
- Visitors tap anything (34 things: bed, ball, teddy, TV, lamp, fridge, plants…) and Athena walks over and plays with it: she talks in a speech bubble and the thing reacts (the ball rolls, the TV and lamp switch on/off, plants wiggle, she naps on the bed).
- Drag to turn the view all the way around, pinch (phone) or mouse wheel (computer) to zoom. "🎯 Reset view" brings the normal view back.
- Visitors tap any spot on the floor and Athena walks there, around furniture and through the doors into every room. The camera follows her. Tapping Mom or Dad makes her run to them.
- The Amazon line ("As an Amazon Associate I earn from qualifying purchases.") is inside every gift card and the gift wall, not at the bottom of the screen.

## Files
| File | What it is |
|---|---|
| `data/items.json` | all gifts and their Amazon links (**the only file you edit day to day**) |
| `data/athena.json` | her age, the day, the life number, the Instagram link |
| `data/rooms.json` | the rooms, their colours and the spots where items go |
| `data/family.json` | who is in the house (Athena, Mom, Dad) and where they sit or stand |
| `src/` | the code: `main.js` (app), `walk.js` (where Athena can walk), `rooms.js` (house), `items.js` (gift drawings), `people.js` (Athena, Mom), `kit.js` (drawing tools), `textures.js` (wallpaper, photos) |
| `vendor/` | three.js (copied in, so the site needs no outside servers) |
| `fonts/` | the round title font (Lilita One) |
| `checks/` | screenshots from the last test |

Guides: `HOW-TO-ADD-ITEM.md` (add or flip a gift) and `HOW-TO-PUBLISH.md` (put it online).

## Run it on your computer
The site needs a tiny local web server (opening `index.html` by double-click will not load the data).

```
cd ~/personal/one-life/athena-home
python3 -m http.server 8080
```
Then open http://localhost:8080 in Chrome. Stop it with Ctrl+C.

## Handy links
- `index.html#living` or `#kitchen` opens straight in that room.
- `index.html?item=glitter-unicorn` opens straight on that item's card (good for an Instagram story link).
- `index.html?debug` shows the frame rate.

## Every new day
1. Update `data/athena.json` (`age`, `day`).
2. Flip bought items to `"gifted"` in `data/items.json` (see HOW-TO-ADD-ITEM.md).
3. Publish again (HOW-TO-PUBLISH.md).
