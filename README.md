# Tendesai Muyambo — Profile & Mini-Portfolio

A one-page, semantic HTML5 profile site built for CIS2103 (Web Technologies). Assignment 1 built the page; Assignment 2 adds responsive styling.

## AI-Assisted Content

See [PROMPT_LOG.md](./PROMPT_LOG%20(1).md) for the prompt used to draft the About Me section,
the AI's raw output, my edited final version, and my reflection on the changes.

## Accessibility

- All images use meaningful `alt` text (or `alt=""` for decorative images, if any are added).
- Every form input has a properly associated `<label for="...">`.
- Text and background colors were checked for readable contrast.

**Peer review issue found (Thursday's session):**
My peer reviewer pointed out that the text on the page had poor color contrast against
its background in places, making it harder to read — most noticeably the light grey
placeholder text inside the contact form's inputs, which was close to the white
background color and hard to see at a glance.

**Fix applied:**
I added an explicit darker grey placeholder colour (`#5a6b64`, now applied with the
Tailwind utilities `placeholder:text-[#5a6b64] placeholder:opacity-100`) that meets the
WCAG AA minimum contrast ratio (4.5:1) against the white input background, and set
explicit text colour on the inputs themselves. I also made
sure every field has a persistent, always-visible `<label>` (not just placeholder
text), so the field's purpose is still clear even before the low-contrast placeholder
text is read.

## Notes

- Built on top of the practical-session starter file.
- Styled with a standalone stylesheet (`tendesai.css`) plus Tailwind utilities (see below).
- Contact form uses native HTML5 validation only — no JavaScript.

## Responsive Notes (Assignment 2)

**Breakpoints tested.** I tested the page in the browser's device toolbar at **375px
(mobile)**, **768px (tablet)** and **1280px (desktop)**. At each width there is no
horizontal scrollbar, no overlapping text, and the navigation stays usable.

**Mobile-first approach.** The base rules in `tendesai.css` are written for a ~375px
phone. Larger screens are layered on with two hand-written `min-width` media queries
(`768px` and `1280px`) that scale the type, widen the section containers and add padding.
Design tokens (colours, type and spacing scale) live in `:root` so spacing and colour
stay consistent.

**Flexbox vs. Grid, and why.**
- **Flexbox** is used for one-dimensional layouts: the header (picture and text stack in a
  column on mobile and sit in a row from `md`), the nav links (`flex-wrap`, `gap`,
  `justify-center` / `md:justify-start`), and the contact form field groups (`flex-col`,
  `gap`, with name and email side by side from `md:flex-row`).
- **CSS Grid** is used for the Skills section, because the cards form a two-dimensional
  layout. `repeat(auto-fit, minmax(min(100%, 280px), 1fr))` with `gap` gives one column on
  mobile and a 2 x 2 grid on tablet and desktop without needing a media query.

**Where Tailwind is used, and the split with my own CSS.**
- **Tailwind utilities:** the header and nav, and the contact form (including the
  responsive variants `md:`, `lg:` and `sm:`). Tailwind is loaded from its browser (Play)
  CDN script, so there is no build step.
- **My own CSS (`tendesai.css`):** the page-level base styles, design tokens, the content
  sections, the skills grid and the footer. I kept these in plain CSS so the split is
  intentional: components I rebuilt for this assignment use utilities, and everything that
  was already working stays in the stylesheet. Rules for the header and form were removed
  from `tendesai.css` once they were converted, so nothing is styled twice.
- Tailwind's reset removes default link styling, so `tendesai.css` restores an underlined
  link style for links inside the content sections.

**Code quality.** The semantic HTML5 structure and accessibility work from Assignment 1
(landmarks, labels, alt text, visible focus, placeholder contrast) are unchanged.
