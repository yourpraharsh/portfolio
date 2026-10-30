# figma-to-prototype — how to install and run

Turns Figma links (or screenshots of app screens) into a clickable prototype you can switch
between **Android**, **iPhone (iOS Liquid Glass)** and **iPhone Duo** (all six postures,
side rail, fold animation).

---

## 1. Before you start

| You need | Why | How to check |
|---|---|---|
| Claude (desktop app or Claude Code) | runs the skill | — |
| **Node.js 18 or newer** | builds and runs the prototype | `node -v` in a terminal |
| **Figma connector, signed in** | reads your Figma screens | Desktop app: Settings → Connectors → Figma. Claude Code: run `/mcp` and authorise Figma |
| Access to the Figma file | the connector can only read files your account can open | open the link in your browser |

Screenshots-only prototypes don't need the Figma connector.

---

## 2. Install the skill

**Claude desktop app / claude.ai:** open `figma-to-prototype.skill` and click **Save skill**.

**Claude Code (terminal):** unzip it into your skills folder:

```bash
unzip ~/Downloads/figma-to-prototype.skill -d ~/.claude/skills/
```

You should now have `~/.claude/skills/figma-to-prototype/SKILL.md`. Start a new session so
it is picked up.

---

## 3. Ask for a prototype

Just describe what you want — you don't need to name the skill. Examples:

> Here's our checkout flow in Figma: https://www.figma.com/design/…?node-id=12-345 — make a
> clickable prototype of the cart and payment screens so I can see it on Android, iPhone and
> the Duo. Put it in a new folder called checkout-proto.

> Make a prototype from these two screenshots (attached) — home feed and profile.

Tips:
- Link the **page or section** that holds the screens (a link with `node-id`). Mention any
  screens on other pages.
- Say where the project should go (a new folder name), or Claude will ask.

---

## 4. What Claude will ask you (answer in one go)

1. **Font** — "Should the app use a particular font (e.g. your brand font)? If it's not a
   free Google font, where are the files?" Point to a folder with the font files if it's a
   licensed font.
2. **Real content** — "Do you have real pictures and content (product photos, profile
   pictures, names, prices, copy)?" Send files or a folder; until then it uses realistic
   placeholders.
3. **iOS tab bar** (only if your screens have a bottom tab bar) — should it stay visible, or
   shrink to a small button while scrolling (the iOS 26 behaviour)?
4. **Figma icons** (only if your file uses a design system with Code Connect) — permission
   to fetch the real icon files.

Then it builds: reads the Figma, sets up the project, builds every screen, adapts them to
the three skins, checks them in the browser and gives you a summary plus a Netlify zip.

---

## 5. Run a prototype yourself

Claude starts it for you, but you can always run it from its folder:

```bash
cd ~/path/to/your-prototype
```

```bash
npm install
```

```bash
npm run dev
```

Open the address it prints (usually http://localhost:5173).

To run the production build instead (what gets deployed):

```bash
npm run build
```

```bash
npm run preview
```

### Switching skins

- Use the floating switcher at the bottom: **Android · iOS · Duo**. In Duo, pick a posture
  (Folded, Stand, Open, Book, Portrait, Laptop) and, in Open/Book, Full screen / App left /
  App right.
- Or add these to the address bar:

| Want | Add to the URL |
|---|---|
| Android phone | `?ui=android&layout=phone` |
| iPhone (Liquid Glass) | `?ui=ios&layout=phone` |
| iPhone Duo, folded | `?layout=duo&posture=folded` |
| Duo, other postures | `?layout=duo&posture=stand` · `landscape` (Open) · `book` · `portrait` · `laptop` |
| Duo split view | add `&split=left` or `&split=right` (Open / Book) |

The choice is remembered for that browser tab.

---

## 6. Share it

Claude gives you a `…-netlify.zip`. To make your own:

```bash
bash ~/.claude/skills/figma-to-prototype/scripts/package_netlify.sh ~/path/to/your-prototype
```

Then drag the zip onto **https://app.netlify.com/drop** — you get a public link in seconds.
Deep links (e.g. `/checkout`) work because the zip includes the redirect rule.

Don't publish prototypes that contain other people's photos, or a third party's logos.

---

## 7. Changing things later

Talk to Claude in the same project: "make the sheet in Folded take the full width",
"swap in these product photos", "add the order success screen from this Figma link". It
applies feedback as a rule across all screens and rebuilds.

---

## 8. Troubleshooting

| Problem | Fix |
|---|---|
| "It's still not fixed" after a change | Refresh the browser tab — an open tab keeps the old build until reloaded |
| Claude can't read the Figma link | Sign in to the Figma connector (step 1) and make sure your account can open the file |
| Icons look different from Figma | Your file's icons come from a design-system package — allow Claude to fetch them with Code Connect off, or give it the icon folder |
| Wrong or fallback font | Tell Claude which font and where the files are |
| `npm` / `node` not found | Install Node.js 18+ from https://nodejs.org |
| The fold animation looks frozen while Claude tests | Normal when the browser pane is hidden — open the prototype yourself and switch Folded ↔ Open |
