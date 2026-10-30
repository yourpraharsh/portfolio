# Figma → Project Website

Turn a design project in your Figma file into a clear project web page you can share as a pre-read. You get a shareable link and a zip you can host anywhere. Claude reads your Figma, asks for whatever only you know, writes the story with you and builds the page in your team's visual style.

---

## What you get

- **A single responsive web page** for one project. It works on phone and desktop, in light and dark mode.
- **Your real screens.** Exported at high resolution and shown as:
  - flows with arrows between screens
  - before/after comparisons
  - exploration groups marked chosen, dropped or merged
  - a full-screen image viewer
- **A clear story.** Problem → research → explorations → final design → impact → reflection.
- **A shareable link** (a Claude artifact) that's private until you share it.
- **A Netlify-ready zip**, so you can host it as a pre-read link for people outside Claude.
- **A list of open items.** Anything Claude didn't know is shown on the page as a yellow `TODO` marker, never made up.

---

## 1. Install the skill (one time)

**If a colleague shared it with you inside your Claude workspace:**
Install it from your organization's skill directory in Claude's settings.

**If someone sent you the `figma-project-site.skill` file:**
1. If you're on a Free, Pro or Max plan, go to **Settings → Capabilities** and turn on **Code execution and file creation**. On Team or Enterprise, your workspace owner controls this.
2. Click **+** → **Create skill** → **Upload a skill**, and choose the file. If the upload doesn't accept `.skill`, rename it to `.zip` and try again.

---

## 2. Before you start (recommended, 5 minutes)

**Connect Figma.** Go to **Settings → Connectors** and connect **Figma**. Without it, you can still upload exported PNGs or a PDF of your frames.

**Make a "for claude" page in your Figma file.** This is the biggest time-saver:
1. Add a new page and call it `for claude`.
2. Copy in the frames for this one project, **in the order you'd tell the story**.
3. Include your explorations and rejected directions. They're the most convincing part of a project story.
4. **Name each frame like a caption**, e.g. `Checkout - address prefilled`, `Explore B - map pin first`.
5. Hide any slide text sitting on top of screens.

**Have these answers ready.** Rough notes are fine:
- What was the problem, for whom, and why did the business care?
- What was *your* role? Who else was on the team? Roles are enough.
- Which directions did you try, and why did each one lose?
- What happened after launch: numbers and what they measured, or "under NDA / no numbers"?
- One thing you'd do differently.
- A style reference link (design system, brand page or an existing page), if you want the page to match it.

---

## 3. Make your project page

Start a new chat and paste something like:

> Make a project page from this Figma page: `https://www.figma.com/design/…?node-id=…`
> It's a pre-read for my pod mentors' review.

Claude will:

1. **Ask what's missing** in one message. Tap or type your answers. Unsure about something? Say so, and it becomes a TODO.
2. **Pull your screens and text from Figma.** If Figma downloads are blocked, Claude gives you step-by-step export instructions instead (select frames → Export → 2x PNG → upload the zip).
3. **Show an outline**: each section, the point it makes and which frames go in it. Reply "looks good" or adjust it.
4. **Build and publish the page**, then list every TODO left for you.

If Claude doesn't pick up the skill on its own, add: *"use the figma-project-site skill"*.

---

## 4. Review and refine

Open the link and read it the way your mentor will: cold, five minutes before the review. Then either:
- **Comment directly on the page** (select text or a section → comment → mention @claude), or
- **Tell Claude in the chat**, e.g. "move explorations before research", "the caption on screen 3 is wrong", "use a darker background".

Claude updates the **same link** each time, so you never juggle versions.

Fill in the TODOs by replying with the real values, e.g. "conversion went up 3.1% in a 2-week A/B test".

---

## 5. Share it as a pre-read

There are two ways to share the page. Pick by who needs to open it.

| Option | Best for | Who can open it |
|---|---|---|
| **Claude link** | Teammates on the same Claude workspace | Only people you share it with |
| **Netlify** | Pre-reads for anyone outside Claude: mentors, other pods, stakeholders | Anyone with the link |

> **Before hosting outside Claude:** a Netlify link is public to anyone who has it. Check your team's policy on hosting unreleased work externally, and ask Claude to blur or remove sensitive numbers and customer data first.

### Host on Netlify (free, about 3 minutes)

**First time**
1. In the chat, ask Claude: *"Give me the Netlify zip."* Download the `…-netlify.zip`.
2. **Unzip it.** You get a folder containing `index.html` and an `images/` folder.
3. Go to **app.netlify.com** and sign up or log in. Free, and Google or GitHub sign-in works. Logging in matters: sites dropped without an account are temporary.
4. Open **Sites**, scroll to the box that says **"drag and drop your site output folder here"** (or go to **app.netlify.com/drop**), and drag the **unzipped folder** onto it.
5. In about 10 seconds you get a live link like `https://random-name-123.netlify.app`.
6. **Give it a readable name:** Site configuration → **Change site name** → e.g. `checkout-concept-review`. Your link becomes `https://checkout-concept-review.netlify.app`.
7. Paste the link in your pod channel or review invite as the pre-read.

**Updating after feedback**
1. Ask Claude for the changes, then *"give me the updated Netlify zip."*
2. Unzip it, open your site on Netlify → **Deploys** tab → drag the new folder onto the drop area.
3. **Same link, new version.** Anyone who already has the link sees the update.

**Good to know**
- Several projects? Make one Netlify site per project, each with its own readable name.
- Password protection on Netlify needs a paid plan. On the free plan, only share the link with the people who should see it.
- To take a page down: Site configuration → **Delete this site**.

---

## Tips for a strong project page

- **Show the explorations that lost, and why.** That's where your judgment shows.
- **Give numbers with context**: what was measured, how (A/B, before/after) and over what period.
- **Be honest about ownership.** If you joined mid-project or owned one part, say so.
- **Under NDA?** Ask Claude to use relative numbers ("+12%"), hide real figures, or blur customer data in screenshots.
- **One project per chat** keeps things clean.

---

## Troubleshooting

| Problem | What to do |
|---|---|
| "Rate limit" or Figma errors | Free Figma plans have tight limits. Export the frames as 2x PNGs (or a PDF) and upload them; Claude carries on from there. |
| Claude can't open the file | Make sure the Figma file is shared with the account you connected. Or just upload exports. |
| Screens look blurry | Export at **2x**, not 1x. |
| A deck or PDF has several screens per slide | That's fine. Claude crops the screens out automatically, then checks the crops with you. |
| Fonts don't match your team's style | Your font may not be on Google Fonts. Claude picks the closest match; tell it if you'd prefer another. |
| The page is too large to publish | Claude shrinks images automatically. Long videos may only be included in the Netlify zip. |
| Netlify shows “Page not found” | You dropped the zip or a parent folder. Drag the unzipped folder that has `index.html` directly inside it. |
| Netlify link disappeared | The site was dropped without logging in. Log in and drop it again. |
| Claude invented something | It shouldn't. Point it out and it will replace it with your real info or a TODO. |

---

## What's inside this folder

| File | What it's for |
|---|---|
| `SKILL.md` | Instructions Claude follows |
| `README.md` | This guide |
| `references/` | Intake checklist, Figma extraction methods, page structure and writing rules |
| `scripts/build_site.py` | Builds the page and zip from the content file |
| `scripts/crop_screens.py` | Crops individual screens out of slides or PDFs |
| `assets/template.html` | The page design |
| `assets/example-content.json` | A complete example project page |
