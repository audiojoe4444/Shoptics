# Shoptics 🛒👓
**See it. Say it. Sorted.** A voice-first shopping list for Meta Ray-Ban Display glasses.

## Using it
| Do this | Neural Band / touchpad |
|---|---|
| **Add items** | Press **Say it!** → press **Press & speak** (it stays selected after each add) → the glasses' dictation opens → say e.g. *"two pineapples, six beers and some toilet rolls"*. It splits them up, sorts them into aisles and shows "Added!". You stay on this screen, so each extra item is one press. |
| **Add without speaking** (e.g. in a meeting) | On the Say it! screen, swipe down to **Type it instead** → Shoptics' own keyboard (never voice) → pick a suggestion or tap **Next ›** → "How many?" keypad → **Add ✓** (leave blank for just one) |
| **Open the list** | Swipe down to **My List**, press |
| **Move around the list** | Swipe up / down |
| **Tick an item (into the basket)** | Press → it greys out and stays on the list |
| **Un-tick (re-shop it)** | Press a greyed item → "Put it back on the list?" → Yes |
| **Delete a mistake** | Swipe right on an item → Remove (already selected, so just press) |
| **Leave the list** | Back gesture (or the ‹ Back button) → "Clear the ticked items?" (Yes is already selected) Yes removes them; No keeps them greyed |

- After 15 seconds with no input the app dims. The next press only wakes it up, so you can't tick something by accident.
- The app makes no sound and never touches audio, so music from your phone keeps playing.
- Your list is saved on the glasses (local storage) and still opens with poor signal in the shop (offline cache).

Aisles: Produce · Dairy & Eggs · Pantry & Dry Goods · Meat & Seafood · Household & Cleaning · Personal Care · Treats (+ "Other" for anything it doesn't recognise).

## Putting it on GitHub Pages
1. Create a new repository (e.g. `shoptics`) on github.com.
2. **Add file → Upload files** → drag in everything from this folder (`index.html`, `sw.js`, `manifest.json`, `icon-96.png`, `icon-192.png`, `icon-512.png`, `apple-touch-icon.png`, `README.md`) → Commit.
3. **Settings → Pages** → Source: *Deploy from a branch*, Branch: `main`, folder `/ (root)` → Save.
4. After a minute your app is at `https://<your-username>.github.io/shoptics/`. Open/install that URL on the glasses the same way as your other apps.

**Updating:** upload the changed files, then change `CACHE_NAME` in `sw.js` (e.g. `shoptics-v2`) so the glasses pick up the new version.

## Automatic GitHub backup
Glasses software updates can wipe web apps' saved data. Shoptics keeps an encrypted copy of your list (and your typed-item suggestions) in a private gist in your own GitHub account and restores it automatically.

1. Use the same GitHub key as GlassCast (a classic token with only the `gist` permission). Shoptics saves to its own gist, `shoptics-backup.json`, so it never touches GlassCast's.
2. In the Meta AI app, add `?sync=YOUR-KEY` to the end of the Shoptics address, e.g. `https://<your-username>.github.io/Shoptics/?sync=ghp_...` (use `&sync=` if the address already has a `?`).
3. Open Shoptics. The bottom of the home screen shows **Backed up to GitHub · just now**.

Changes are saved within a few seconds. After a wipe, the list comes back the next time you open the app. The key lives only in the app address, never in the code. A backup made with a different key is never overwritten.

## Customising the aisles
Open `index.html` and find `var KEYWORDS`. Each aisle has a comma-separated list of words. Add a word to move items into that aisle (e.g. add `, oat bar` to `treats`).
