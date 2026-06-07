# Accessibility

## Target

- **WCAG 2.1 Level AA** minimum for customer-facing experiences unless legal specifies stricter.

## Keyboard

- All interactive controls reachable in logical order.
- **No keyboard traps** in modals/menus; **Escape** closes overlays.

## Focus

- Visible **focus ring** using `focus.ring` token; never `outline: none` without replacement.

## Color and contrast

- Text and UI components meet **4.5:1** for normal text; **3:1** for large text and critical graphics.
- **Do not rely on color alone** for status — pair with icon or text.

## Forms

- Labels associated with inputs; errors in text, not color alone.

## Images and media

- Meaningful **alt text**; decorative images marked decorative.
- **Captions** for spoken audio when relevant.

## Motion

- Honor **prefers-reduced-motion**; avoid auto-play background motion.

## Testing expectations

- **Design:** annotates focus order and hit targets in handoff.
- **Engineering:** automated checks + keyboard pass per feature.
- **Accessibility champion:** spot audits on high-risk flows.

## Assistive technology smoke set

- Screen reader path for **sign-in**, **pay or commit**, **destructive action**, **primary task loop**.