## Goal
Ship a single self-contained HTML launch page for **TOCK**, a two-screen clamshell handheld, that makes a jaded phone-user feel a small physical pang of want — and put down a $5 reservation.

## Medium and deliverables
One self-contained HTML page (inline CSS/JS, one variable font, no build step, no external JS beyond a CDN GSAP + Lenis), published as a live URL. Proof: 1440 px and 390 px full-page captures, plus a 20 s screen recording of the cartridge-insert moment. Nothing else.

## Concept
TOCK is a handheld that **cannot reach you** — no Wi-Fi, no accounts, no notifications, just two screens, real cartridges and a lid that closes. The page is built like a piece of product packaging from a better decade: warm paper stock, stamped type, spec tables set like a service manual, the device photographed like a tool, not a gadget. The point of view is that attention is the product, and TOCK gives yours back. Copy is dry and a little deadpan; nothing is "revolutionary."

**Alternative:** a fold-out field-manual concept where the whole page is newsprint instructions and the device appears only in exploded diagrams.

**Style:** warm industrial packaging. **Mood:** tactile, trustworthy, dryly funny, slightly nostalgic, calm.
**References:** Teenage Engineering (product honesty, exposed detail, spec typography), Panic's Playdate site (warm humor, real hardware photography, one idea per screen), Analogue Pocket (restraint, material close-ups, no hype).

## Content
**Facts:** TOCK. Two 3.2″ 400×320 LCDs, clamshell, 118 g, 14 h battery, USB-C, 3.5 mm jack, no wireless. Cartridge slot takes 8 MB flash carts ($12–$28). 12 launch titles. $149, ships March 2026, $5 refundable reservation. Colorways: Tomato, Bone, Moss.

**Voice:** flat, confident, no exclamation marks, occasional dry aside. Lowercase eyebrows, sentence-case body.

**Sections in order:** 01 Hero · 02 The case against the feed · 03 Two screens, one folded lid (interactive hinge demo) · 04 Cartridges are back (four tilted cart cards) · 05 **The Slot** (signature) · 06 Specs, set as a manual page · 07 Three colors, one of them wrong on purpose · 08 Reserve / price / ship date · footer.

**Copy — headline:** "Two screens. No feed."
**Sub:** "A clamshell handheld with real cartridges, 14 hours of battery, and no possible way to notify you."
**Key lines:** "You already have a device that wants you. This one doesn't." · "It closes. That's a feature." · "8 megabytes. That's a whole game." · "No accounts. No updates. No dark patterns, no light patterns." · CTA: "Reserve one — $5" · Footer: "TOCK is made by eleven people in Lisbon. We ship when it's right."

## Signature moment
**The Slot.** A large CSS-drawn TOCK sits lid-open, centre stage. A cartridge rests in a tray at 12°, tilted. Drag it (or press Enter / tap) and it springs into the slot: 120 ms snap, 6 % overshoot, a thin light line runs the cart's edge, the lid's hinge gives a tiny settle. Top screen boots a 3-frame pixel logo, then loads a real, playable canvas paddle-and-ball game at 320×240 — arrow keys, touch, or drag — running at 60 fps on the bottom screen stats while the top screen shows the score. After 30 seconds of play, a quiet line fades in under the device: *"Nothing has interrupted you."* That's the whole pitch, delivered by doing.

## Look
**Palette:** paper `#F3EBDD` (bg) · ink `#17150F` (type) · tomato `#E0512B` (device body, CTAs) · moss `#6F7F5C` (cart labels, secondary) · buttermilk `#F2C14E` (tags, highlights) · screen `#B8D98A` (LCD glow).
**Type mood:** grotesk-expressive — one tight, wide-charset grotesk, headlines at -3 % tracking, a single oblique accent for asides, mono for specs.
**Layout:** 12-col editorial grid on paper, left-aligned, generous outer margins, numbered 01–08 eyebrows, device photography bleeding off the right edge; spec section breaks the grid into a two-column manual table with hairline rules. No centred stacks, no cards-on-gradient.
**Imagery:** device rendered in CSS/SVG — flat fills, one soft shadow, visible seams, screws and hinge; grain overlay at 4 %; speckled-paper texture behind hero. Cartridges as chunky SVG with label art.
**Motion:** mechanical and springy — lid closes like a real hinge, sections slide up 24 px with a 90 ms stagger, the slot snaps. Full motion plays even when the OS reports reduced motion; a visible **"Reduce motion"** toggle in the header kills springs and parallax but keeps fades.
**Sound:** silent by default. Opt-in "sound" toggle in the header enables two SFX only: cartridge click and boot chime. No voiceover.

## Toolchain
`oneshot-page.sh` for the concept draft, a second draft with `minimax` and keep the better hero; `font-pick.sh` for the grotesk + mono pair; build in the kit web-editorial structure; GSAP + ScrollTrigger + Lenis for the hinge and section reveals; 21st.dev only for the reservation input pattern. Plain canvas for the game (no three.js — it would slow the load and add nothing). `qa.sh`, vision review of both captures, `publish-pages.sh`.

## Acceptance
1. `qa.sh` clean: 0 text leaks, 0 line clashes, no 390 px overflow, a11y AA.
2. Full motion plays when the OS reports reduced motion; the toggle is visible and works.
3. Cartridge inserts by drag, click and Enter; game is playable and holds 60 fps.
4. "Nothing has interrupted you" appears only after 30 s of play.
5. No websafe fallback flash; one font family loads, FOUT under 200 ms.
6. Page weight under 400 KB total, LCP under 1.8 s.
7. Zero purple-blue gradients, glass cards or centred hero stacks.
8. A fresh designer reviewer scores it ≥ 8.5/10 against Teenage Engineering and Playdate.

## Assumptions
Name, specs, price, ship date, team size and city are invented. Two screens + cartridges chosen over a single-screen brick because it gives the signature moment a physical action. Warm paper palette chosen deliberately against the studio's recent dark/neon work. Reservation flow is a fake form with a success state — no backend. Sound is opt-in and minimal.
