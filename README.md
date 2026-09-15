# Tendesai Muyambo — Profile & Mini-Portfolio

A one-page, semantic HTML5 profile site built for CIS2103 (Web Technologies), Assignment 1.

## AI-Assisted Content

See [PROMPT_LOG.md](./PROMPT_LOG.md) for the prompt used to draft the About Me section,
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
I added an explicit `::placeholder` style in `tendesai.css` with a darker grey
(`#5a6b64`) that meets the WCAG AA minimum contrast ratio (4.5:1) against the white
input background, and set explicit text color on the inputs themselves. I also made
sure every field has a persistent, always-visible `<label>` (not just placeholder
text), so the field's purpose is still clear even before the low-contrast placeholder
text is read.

## Notes

- Built on top of the practical-session starter file.
- Styled with a standalone stylesheet (`tendesai.css`).
- Contact form uses native HTML5 validation only — no JavaScript.
