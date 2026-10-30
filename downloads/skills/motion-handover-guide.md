# Motion handover skill: how to use

Turns a Figma prototype or a prototype video into a motion spec page for Android engineers. The page has a live phone reference, a scrubbable timeline, stamps, layers with Compose and Views APIs, rules and open items.

## Install

1. Click **Save skill** on the `motion-handover.skill` file card.
2. If the button doesn't appear, upload the file under Skills in Settings.
3. Make sure code execution is on.

## Input option 1: Figma screenshots (most accurate)

1. Export the flow's frames side by side in one image, left to right in play order.
2. Click each prototype arrow and screenshot it with the Interaction panel open. Trigger, Delay, Animation, Easing and Duration must be readable. Phone photos of the screen work.
3. Send everything in one message: "Motion handover for this, Android."

## Input option 2: Video

1. Screen-record the prototype, 60 fps if possible.
2. Start the recording on the first frame, keep the cursor still, one flow per clip.
3. Upload the mp4 or mov: "Motion handover from this video."

Video timings come back rounded to 50 ms and marked *confirm*. Send the Figma panels later if devs need exact values.

## What you get

- A published link with the live phone and a scrubbable timeline
- `index.html` plus a Netlify zip. Drop the zip on app.netlify.com/drop.
- The stamps table and open items in chat

## Iterating

| You want | Say |
|---|---|
| Answer open items | "Opens directly, scale is 1.04, offset not intended." They move to Resolved. |
| Add another flow | Send its frames and panels: "Add this as B." |
| Variant of an existing flow | "Same as A but skip the expand, keep timings." |
| Shorter copy | "Make it terser." |
| Hosting | "Give me the Netlify zip." |

## Tips

- One flow per message, labelled if you have several.
- If you already know the numbers, type them ("800 hold, 500 ease in out") and skip the panels.
- For springs, screenshot the panel with mass, stiffness and damping visible.
- Frames without timings get a layer breakdown and a request for the panels, not a page.

## Limits

- Android only (Compose and Views).
- The phone mock approximates the layout. Figma stays the source of truth for static geometry.
- Video analysis is less reliable under 30 fps or when two transitions overlap. Use Figma panels in those cases.
