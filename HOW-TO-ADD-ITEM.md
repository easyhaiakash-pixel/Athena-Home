# How to add a gift (2 minutes)

Everything about gifts lives in **one file: `data/items.json`**. You never touch the code.

## A. Add a new item

1. Open `data/items.json`.
2. Copy this block and paste it **before the last `]`**. Put a comma `,` after the `}` of the item above it.

```json
  {
    "id": "pink-water-bottle",
    "name": "Pink water bottle",
    "emoji": "🍼",
    "status": "wish",
    "giftedOnDay": null,
    "room": "kitchen",
    "spot": "kitchen-counter",
    "model": "generic-box",
    "color": "#ffb3c8",
    "note": "A little bottle for her school bag.",
    "links": {
      "in": "PASTE THE INDIA LINK HERE",
      "us": ""
    }
  }
```

3. Change the words:
   - `id`: short name, small letters and dashes, no spaces. Must be different from every other item.
   - `name`, `emoji`, `note`: what people read on the card.
   - `links`: paste the Amazon link **exactly** as Amazon gives it. Leave `""` if there is no link for that country. The site only shows the buttons that have a link.
4. Save. Reload the site. The item is there as a see-through "wish" with a 🎁 tag.

## B. When fans bought it (wish → gifted)

Change two lines of that item:

```json
    "status": "gifted",
    "giftedOnDay": 5,
```

Reload. It becomes a real, full-colour object with ✨ sparkles and the tag "Gifted by you on Day 5".

## Where can it go? (`room` + `spot`)

| room | spots |
|---|---|
| `bedroom` | `wardrobe` (clothes hang here), `bed`, `shelf`, `rug`, `floor-left`, `floor-right` |
| `living` | `sofa`, `coffee-table`, `floor-left`, `floor-right` |
| `kitchen` | `toy-kitchen`, `kitchen-counter`, `table`, `floor-left` |

Several items can share a spot; they line up side by side. Keep it to about 3 per spot so they stay easy to tap.

## What does it look like? (`model`)

| model | looks like | extra |
|---|---|---|
| `dress` | a dress on a hanger | `"variant": "tutu"` or `"knit"` |
| `outfit-set` | "Birthday Girl" top + pom-pom tutu | |
| `plush` | soft toy | `"variant": "unicorn"`, `"elephant"` or `"teddy"` |
| `doctor-kit` | pink doctor case + stethoscope | |
| `makeup-trolley` | little trolley with a mirror | |
| `toy-kitchen` | play kitchen | |
| `doll` | small doll | |
| `shoes` | pair of shoes | |
| `hair-bows` | card of 3 bows | |
| `generic-box` | a pretty gift box | use this for anything new |

`color` is the main colour, like `"#ff8fb0"` (pink). Pick colours at https://htmlcolorcodes.com.

## If it does not show up
- The file must stay valid. Paste it into https://jsonlint.com: it shows the exact line with a missing comma or quote.
- Check the `room` and `spot` words against the table above (small letters).
- Hard-reload the page (on a phone: close and reopen the tab).
