# Changelog

## 1.10 - 2026-10-17

Packaging only, no gameplay changes. Releases now ship this hand-written
changelog instead of one assembled from commit messages.

## 1.9 - 2026-10-17

First public release.

Renamed from WhitePlayerHealth, which described the default color rather than
what the addon does.

- Slash commands are now `/hp`, with `/arpg` and `/arpghealth` as aliases.
  `/hp` was checked against Blizzard's built-in commands and against every way
  an addon can register one before being claimed; the aliases are there in case
  another addon on your setup contests it.
- The settings panel is listed as **ARPG Health**.
- Declares support for interface versions `120100` and `120105` (patches 12.1.0
  and 12.1.5), so it no longer shows as out of date on a current client.

**Upgrading from an earlier version:** WoW ties saved settings to the addon
folder name, so they do not follow the rename on their own. To keep your
position, size and colors, open
`WTF/Account/<your account>/SavedVariables/`, copy `WhitePlayerHealth.lua` to
`ARPGHealth.lua`, and change the single `WhitePlayerHealthDB` at the top of the
copy to `ARPGHealthDB`. Skip this and the bar simply starts at its defaults.

1.8 was never released; the rename landed before it shipped.

## 1.7 - 2026-09-03

- Lower CPU cost in combat. Health and shield updates now each do only the work
  that actually changed, where previously every health tick also redid the full
  shield update.
- A saved **Left to Right** shield fill direction now reliably survives a
  reload. It had worked only as a side effect of the startup sequence.
- Removed the unlock diagnostics added in 1.6. The addon now prints to chat only
  in response to something you did.

## 1.6 - 2026-08-29

- The **Unlock Bar** checkbox is gone, replaced by a note pointing at the slash
  command. Its state was read from the bar's mouse state, so it went stale
  whenever the command or a combat auto-lock changed the bar behind an open
  panel.
- The bar is locked on login and on zone change.
- A queued edit-mode request that opened after a fight used to unlock the bar
  with no message, which looked like the bar unlocking itself. It now says so.

## 1.5 - 2026-08-27

- The settings color preview was being rebuilt on every combat health tick. It
  now refreshes only when a color or the fill direction changes.
- Edit mode and the settings panel close when a fight starts, and neither opens
  mid-fight. A request made during combat is queued and honored once the fight
  ends.
- `unlock` dropped as a separate command, having become identical to the bare
  command.
- `reset` restores position *and* size, matching the panel buttons.
- Help output rewritten, with numeric arguments shown as `#`.

## 1.4 - 2026-08-26

Development snapshot: color picker with live preview row, combat-deferred
settings, snap-to-center, corner-bracket resize grip, and confirmation on both
reset buttons.
