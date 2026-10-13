# Georgian interface

> **Last reviewed:** 2026-10-13 · **Last updated:** 2026-10-13 · **Change:** minor (Georgian localization notes and terminology) · **Target:** Adobe After Effects 2026

Choose **Settings ▸ General ▸ Language ▸ ქართული** (in Georgian: **პარამეტრები ▸ ზოგადი ▸ ენა**),
or leave the language on **Match System** with a Georgian system display language (`ka`, `ka-GE`,
`ka_GE.UTF-8`). The catalog code is `ka`; `prefs.set` with `{"key": "general.language", "value":
"ka"}` selects it over the control channel or MCP, and the choice is saved with the other settings.
The browser build has no system locale, so there Georgian has to be chosen in Settings. Project
content, layer and composition names, command ids and CLI/MCP/control responses do not change.

The Georgian catalogs cover every fixed menu entry (`crates/ui-egui/src/i18n.rs`, `GEORGIAN`, 624
entries with the same (command, English label) keys as Japanese) and every panel, dialog, button
and tooltip string of the Chinese panel catalogs (`crates/ui-egui/src/i18n/ui.rs`, `GEORGIAN`, 506
rows in the same order). The macOS application menu (Services, Hide, Hide Others, Show All), Undo /
Redo with the history's action name (`დაბრუნება: Comp 1`) and the platform file manager in
"Reveal in …" are translated too. Effect names and their parameters, engine-generated text
(property names, errors, undo labels), strings no catalog has yet and documentation stay in
English, as in every language. Translations are written from the meaning of EffectCraft's English
labels; no proprietary translation resources, fonts or screenshots were used.

## Georgian script

- Mkhedruli has no letter case. Labels are never capitalised and never use Mtavruli; title-case
  and capitalise transforms leave Georgian as it is, while ALL CAPS (a text layer's All Caps)
  maps Mkhedruli to Mtavruli as Unicode `to_uppercase` defines.
- A noun stays singular after a numeral, and the catalogs have no plural forms, so counts use
  count-neutral wording: `{} minutes ago` is `{} წუთის წინ`, and `{} contributors · {} commits`
  reads `მონაწილე: {} · კომიტი: {}`.
- Commands are verbal nouns (masdar: *შენახვა*, *გახსნა*, *ფენის წაშლა*); prompts address the user
  politely (*დააწკაპუნეთ*, *გადაათრიეთ*). Product and format names (EffectCraft, Lottie, ProEXR,
  OpenEXR, Finder) stay Latin, with Georgian case endings after a hyphen (`Finder-ში`).
- Interface font: Inter has no Georgian, and the craft-fonts set has no Georgian face yet. The
  interface and text layers fall back to installed system faces: Sylfaen, SF Georgian, Arial
  Unicode MS, Noto Sans Georgian, DejaVu Sans (`crates/ui-egui/src/theme.rs`,
  `crates/text/src/fonts.rs`). The web build has no system fonts, so it needs a Georgian face
  bundled before Georgian renders there.
- EffectCraft has no per-language date or number formatting: timecode, frame numbers and
  percentages are the same in every language.

## Terminology

Follow this table when adding or changing Georgian strings.

| English source | Georgian |
|---|---|
| File / Edit / View / Window / Help | ფაილი / რედაქტირება / ჩვენება / ფანჯარა / დახმარება |
| Composition / New Composition… | კომპოზიცია / ახალი კომპოზიცია... |
| Layer | ფენა |
| Keyframe / Hold Keyframe | საკვანძო კადრი / ფიქსირებული საკვანძო კადრი |
| Easy Ease | რბილი შენელება |
| Footage / Interpret Footage | ვიდეომასალა / ვიდეომასალის ინტერპრეტაცია |
| Solid / Null Object | სოლიდი / ნულოვანი ობიექტი |
| Shape Layer / Adjustment Layer | ფიგურის ფენა / კორექციის ფენა |
| Pre-compose… | კომპოზიციაში მოთავსება... |
| Mask / New Mask | ნიღაბი / ახალი ნიღაბი |
| Track Matte / Alpha Matte / Luma Matte | ტრეკ-მატი / ალფა-მატი / ლუმა-მატი |
| Expression / Add Expression | ექსპრესია / ექსპრესიის დამატება |
| Timeline / Effect Controls / Project | დროის ხაზი / ეფექტის მართვა / პროექტი |
| Render Queue / Add to Render Queue | რენდერის რიგი / რენდერის რიგში დამატება |
| Preview | წინასწარი ნახვა |
| Essential Graphics | ძირითადი გრაფიკა |
| Lift / Extract Work Area | სამუშაო არის აწევა / სამუშაო არის ამოღება |
| Time Remapping | დროის გადანაწილება |
| Motion Blur | მოძრაობის გაბუნდოვნება |
| Keyframe Assistant | საკვანძო კადრების ასისტენტი |
| Purge | გაწმენდა |
| Character (panel) | სიმბოლო |
| Undo / Redo / Paste | დაბრუნება / ხელახლა შესრულება / ჩასმა |
| Settings / General… | პარამეტრები / ზოგადი... |
| Preset | პრესეტი |
| Stroke / Path | კონტური / ტრაექტორია |
| Hue | ფერის ტონი |
| Copy Frame to Clipboard | კადრის კოპირება გაცვლის ბუფერში |

## Maintenance

Add Georgian with every new English string: a `(command, English, Georgian)` row in `GEORGIAN` in
`crates/ui-egui/src/i18n.rs` for a fixed menu entry, and an `(English, Georgian)` row in
`GEORGIAN` in `crates/ui-egui/src/i18n/ui.rs` at the same position as in the Chinese catalogs for
a panel string. Keep `{}` placeholders and their order, `...` and `…`, `\n`, shortcut text and
leading or trailing spaces exactly as in the source. `cargo test -p effectcraft-ui-egui --lib
i18n` checks that the menu keys match Japanese, that the panel rows match the Chinese catalogs one
for one, that ellipses and placeholders survive, Georgian locale tags (`ka`, `ka-GE`,
`ka_GE.UTF-8`), Undo / Redo, Reveal labels and the Georgian font fallback; `native_menu` tests the
macOS application menu.

## Revision history

| Date | Change | Summary |
|---|---|---|
| 2026-10-13 | minor | Georgian localization notes and terminology; catalogs synced with upstream (624 menu entries, 506 panel rows) |
