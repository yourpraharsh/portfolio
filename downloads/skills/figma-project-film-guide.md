# Figma → Project Film

Turn a design project in your Figma file, slides or PDF into a short **problem → solution film** (20 s, 30 s or 60 s). It shows the final design, then the other directions you explored and the research (LODs) that ruled them out. Use it to open a review, as an async update for your pod and mentors, or at the top of a project page.

The film shows the problem happening in your real UI, lands the key number, brings your fix into the *same* screen, shows the result, and ends on the full project page or your ask. It's built from your screens and your words, and it works with the sound off.

---

## What you get

- A **30-second film by default**, including an explorations beat after the final design: each rejected direction shown with the LOD or user research insight that ruled it out. There's also a 20 s cut, and a 60 s walkthrough that gives each exploration its own moment.
- **Your real UI**, recreated from Figma so it can scroll, highlight and change on screen.
- **Your team's look**: fonts, colours, end card.
- A **link** you can scrub through and comment on, plus an **MP4 export**.
- A **web-ready version** (2–4 MB) for your site, if you want one.
- An **original background score** (on the Motion route), muted by default.

Every number, quote and result comes from you. Anything Claude had to invent as an example, such as sample review text or product names, is listed for you to replace.

---

## 1. Install the skill (one time)

**Shared with you inside your Claude workspace:** install it from your organization's skill directory in Claude's settings.

**Someone sent you `figma-project-film.skill`:**
1. On Free, Pro or Max: **Settings → Capabilities** → turn on **Code execution and file creation**.
2. Click **+** → **Create skill** → **Upload a skill** and choose the file. If `.skill` isn't accepted, rename it to `.zip`.

---

## 2. Before you start (5 minutes)

**Connect Figma.** Go to **Settings → Connectors** and connect **Figma**. If you can't, exported PNGs, slides or a PDF work too.

**Point to the right frames.** You need only a few screens:
- the screen where the problem happens ("before"),
- the moment it goes wrong, if it's a different screen,
- the same screen with your fix ("after"), at the **same size** as the before screen,
- optionally, the new component on its own,
- the **explored directions** that didn't make it (one frame each).

Putting them on a Figma page called `for claude` makes this fastest.

**Have these ready.** One line each is enough:
1. **The moment it breaks.** What does the user *do* on screen when it goes wrong?
2. **The number.** The stat that made it matter, and what it measured.
3. **The fix.** What's new, and where it sits on the screen.
4. **The result.** After launch, or in testing. Real numbers only.
5. **Explorations and why they lost.** The frames of other directions you tried, and what LODs/user research showed for each (e.g. "5 of 8 users lost track of the steps"). A direction with no research reason can be shown with the honest reason ("dropped for scope") or left out.
6. **A style reference link** (design system, brand page or an existing project page), or a film you made before, so they match.
7. **Where it will live.** Opening a review, posted in a channel, or at the top of a project page. This decides the end card: your ask, a link, or "scroll down".

---

## 3. Make your film

Start a new chat and paste something like:

> Make a 30-second project film from this Figma page: `https://www.figma.com/design/…?node-id=…`
> It's for a review with my pod mentors.

Then:

1. **Claude asks what's missing** in one message. Answer roughly; it shapes the words.
2. **You get a storyboard**, including the explorations beat: a short table of beats, seconds, what's on screen and the text. Change anything here. This is the cheapest place to get it right.
3. **Claude builds the film** and gives you a link. You may get a quick picks form for style, colours and length; your earlier answers are pre-filled where possible.
4. **Watch it** with the sound on and off.

If Claude doesn't use the skill on its own, add: *"use the figma-project-film skill"*.

---

## 4. Refine

- **Comment on the film at a moment** (e.g. at 0:12: "circle should be on the price") or **tell Claude in chat**.
- Common fixes: text on screen too long, a highlight in the wrong place, end-card wording, music mood.
- Claude updates the **same film**, so there's no version juggling.

---

## 5. Use it

- **MP4.** Open the film and use **Export**.
- **On your website.** Ask Claude for the *web version*. You'll get a small H.264 file and a poster image, plus the embed code:
  `<video src="film-web.mp4" poster="film-poster.jpg" autoplay muted loop playsinline></video>`
- **Social.** Ask for a **9:16** (Reels/Shorts) or **1:1** (LinkedIn) version. That's a separate film laid out for that shape, not a crop.

**Making a series?** Keep the link to your first film and give it to Claude next time. Every film will share the same look and end card.

---

## Tips for a film that works

- **Show, don't tell.** The problem should be something the viewer *watches* happen, not a sentence.
- **One number.** The single stat that made the problem matter.
- **Same screen, before and after.** The change should be obvious without reading.
- **Short words on screen.** Headlines of 8 words or fewer. If it doesn't fit, cut words, not seconds.
- **Back every rejection with research.** "LODs: users read the toggle as a filter" convinces; "felt cluttered" doesn't.
- **"LOD" is fine for internal reviews.** For anything shared outside the team, Claude says "user research" instead.
- **Not launched yet?** Show what testing found, labelled as testing.
- **Employer's product?** Make sure you're allowed to show it publicly. Ask Claude to blur or replace real customer data.

---

## Troubleshooting

| Problem | What to do |
|---|---|
| Figma rate limit or access error | Export the frames at 2x PNG (or the deck as PDF) and upload them |
| The UI in the film looks slightly off | Claude recreates your UI so it can animate. Point out what's wrong, or share the exact Figma frame for that screen |
| Text flashes by too fast | Ask to cut words in that beat, or add a second |
| Wrong font | Your font may not be on Google Fonts; Claude picks the closest. Name the one you'd prefer |
| No "Motion" film option on your account | Claude renders the MP4 directly instead (no music unless you provide a track you have the rights to). It takes a few minutes |
| Something on screen isn't true | Tell Claude. It replaces it with your real info or removes it |

---

## What's inside this folder

| File | What it's for |
|---|---|
| `SKILL.md` | Instructions Claude follows |
| `README.md` | This guide |
| `references/intake.md` | What Claude asks, and the defaults it uses |
| `references/storyboard.md` | Beat templates for 20, 30 and 60 s, motion patterns, on-screen text rules, end card |
| `references/look.md` | Matching a style reference, keeping a series consistent, web export |
| `references/figma-ui.md` | Getting your UI out of Figma so it can animate |
| `references/offline-render.md` | The film format and render pipeline used when no Motion type is available |
| `assets/film-template.html`, `assets/example-film.json` | Offline film engine and a complete example |
| `scripts/build_film.py`, `scripts/render_film.py` | Build the film page; render stills or the MP4 |
| `scripts/crop_screens.py` | Cuts individual screens out of slides or PDFs |
