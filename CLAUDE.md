# Speed skydiving school presentation

A school presentation (spreekbeurt) about speed skydiving for Marre Anne, a girl of about 9. It is written in Dutch, in simple language for children of that age. Thomas (her uncle, a speed skydiver who builds FlySight Insights) asks for the changes.

**Commits:** no `Co-Authored-By:` trailer and no "Generated with Claude Code" line, in commit messages or anywhere else (Thomas's rule from the flysight-insights repo, applied here too). Commit straight to `main`.

## Files

- `index.html`: the presentation itself (named `index.html` so GitHub Pages opens it at https://tderaat.github.io/presentatie-speedskydiven-ma/): inline CSS, inline SVG, a little vanilla JS. It needs no network, so it runs from a USB stick at school, as long as the files it loads sit next to it: `flysight.png` and the two videos.
- `flysight.png`: photo of a FlySight (the original, black with the FlySight sticker) with the white background cut out to transparency and cropped to the device. Currently unused: the "Wat heb je nodig?" slide that showed it was removed at Thomas's request.
- `spreektekst.html`: the speaker text per slide, printable, plus presenting tips at the top.
- `mockups-*.html`: design variants that were shown to choose from. They are not used by the presentation and may be deleted.

**Keep the two main files in sync.** Each slide's speaker text lives twice: in the slide's `data-notes` attribute (shown on screen with N) and in `spreektekst.html`. Change both. When a slide is added or removed, renumber the slides in `spreektekst.html` and check the duration estimate in the tips (now about 5 minutes for 10 slides, plus the two videos).

## Controls

Click anywhere (except the nav buttons) or press Right/Space/Enter for the next slide. Left/Backspace goes back. F toggles fullscreen, N shows the speaker text at the bottom (N is deliberately not mentioned in the on-screen hint). The counter and a dark-blue progress bar (`#061a40`) show where you are. A short controls hint sits bottom right on the title slide only; `show()` hides it on every other slide.

## Slides (current order)

1. **Titel:** the head-down `flyer-head` skydiver with white speed streaks of different lengths shooting up past and above it (style B of `mockups-luchtstroming.html`, `.streak` animation), then "Speed skydiven", "De snelste sport zonder motor" and "Door Marre Anne" (no colon, smaller and semi-transparent, hard-coded).
2. **Wat is skydiven?** Infographic of four panels in a row (option C of the mockups): 1 omhoog to 4 km (about 20 min), 2 springen uit de open deur, 3 vrije val (about 1 min, 200 km/u), 4 parachute en landen (about 5 min). Dotted lines connect them; white for the climb, yellow for jump and freefall, green for the canopy. All four number circles are white. Panel 4 combines mockup options from `mockups-landen.html`: the canopy of B (the yellow skydiver hanging under it, seen from the front, both hands on the toggles) and the landing of D (standing side-on next to the folded-down canopy, waving). Both figures are drawn inline in that panel, not as symbols. The infographic is sized `min(1500px, 97vw)` wide and at most `74vh` tall so it fits under the heading.
3. **Video:** plays `hugo.mp4` from the same folder, filling the slide (see "Video slides" below).
4. **Wat is speed skydiven?** A belly-to-earth skydiver with a slow animated arrow down, next to a head-down skydiver with a fast animated arrow.
5. **Hoe snel gaat dat?** Animated bars: fiets 25, auto 120, snelle trein 300, Max Verstappen 350, speed skydiver 500+ km/u.
6. **Video speed:** plays `speed.mp4`, a speed jump.
7. **Hoe hoog spring je?** Silhouettes of a house (8 m), the Eiffeltoren (330 m), the Burj Khalifa (828 m) and the Cessna 208 at 4000 m. The towers are to scale against the 4000 m; only the house is drawn bigger than scale so it stays visible.
8. **Waarom als een pijl?** White belly skydiver with pink arrows (air pushing back, langzaam) next to the yellow head-down skydiver with airflow lines (snel). Below the cards: the faster you go, the more unstable it gets and the harder it is to hold the arrow position.
9. **Hoe win je?** Three cards: a competition has 8 sprongen, per jump the 3 fastest seconds count, the fastest on average over all jumps wins. Below them: the fastest GPS jump ever.
10. **Einde:** only the speed figure with streaks, larger (`.title-diver.solo`), no text at all. The presenter says "Zijn er nog vragen?" (in the speaker text).

### Video slides

A video slide is a `<section class="slide">` holding only `<video class="slide-video" src="..." controls playsinline preload="auto">`; `show()` plays the video of the active slide and pauses every other one. On a video slide Space toggles play/pause instead of advancing, and clicking the video does not advance (clicking beside it does). Both videos are H.264 MP4s next to `index.html` and are committed (`hugo.mp4` 38 MB, `speed.mp4` 26 MB), so GitHub Pages can play them. Keep each under GitHub's 100 MB file limit: the first `hugo.mp4` was 494 MB and had to be replaced. Note that Pages is public, so the videos are too. A missing file shows as an error box or an empty black slide.

## Drawing conventions

All artwork is inline SVG `<symbol>`s in the hidden `<svg>` at the top of `index.html`, reused with `<use>`:

- `plane`: Cessna 208 Caravan side view, nose right (high wing with strut, fixed gear, cargo pod). Use this for every aircraft.
- `flyer-belly`: belly-to-earth skydiver side view, **head on the right**, rig on the back, legs only slightly bent.
- `flyer-head`: head-down skydiver, arms swept back along the body, rig on the back.
- Both skydivers are "style 1, silhouet": one colour with smooth rounded strokes, far-side limbs a shade darker, rig darker still. Colours come from CSS variables on the `<use>`: `--fig`, `--fig-shade`, `--fig-rig` (default yellow `#ffd23f` / `#d6a21c` / `#b07f00`; white variant `#fff` / `#c3cfdf` / `#8fa3bf`).
- `eiffel`, `burj`, `house`: the remaining pictures. The FlySight is a real photo (`flysight.png`), not a drawing. (The old white stick-figure `canopy` and `lander` symbols were removed; do not bring stick figures back.)
- The title and end slides share the same inline `.title-diver` SVG (the `flyer-head` figure plus eight `.streak` lines); the markup is duplicated in both slides, so change both. The old FlySight Insights logo silhouette (`diver-shape`) and its straight speed lines were removed.

## Thomas's preferences (learnt from the feedback)

- Speaker text is neutral and informative: no "ik", "mijn", "jullie", no "Hallo allemaal" or "Bedankt voor het luisteren", and no personal references (such as whose jump the first video shows). The presenter adds any personal touch herself.
- Not too childish: no "WOW!", no quiz, no "Supersnel", no "Probeer maar" experiment. Plain, friendly wording.
- Figures must look smooth and well drawn, not angular stick figures. He chose from mockups each time; for a bigger visual change, show a few mockups first and let him pick.
- Use real, recognisable references: Max Verstappen (no "Formule 1" label under the name), the Eiffeltoren rather than the Euromast, and silhouettes rather than coloured blocks.
- Navigation buttons are bare chevrons without the light circle behind them.
- Cards, bar tracks and the four infographic panels are opaque (`--card`: a white 14% wash over solid `#2f78c6`; the panels use the same colours as SVG rects), so the drifting clouds pass behind them and never show through the text.
- Removed at his request, do not bring back without being asked: the "Wat heb je nodig?" slide (helm, pak, parachute, hoogtemeter, FlySight), the quiz slide, "Is het niet gevaarlijk?", "Leuke weetjes" (including the peregrine falcon comparison), "Wie het snelst valt, wint!", "Bedankt!".

## Facts used, and their sources

- **Fastest GPS-measured jump:** 542.65 km/u (shown as 542), Niklas Daniel (USA), National 2026 Meeting, Perris, September 2026. It is the top of the ISSA GPS Eternal Ranking: https://www.issa.one/speed-skydiving-eternal-ranking-gps/ . It was a national meeting, so the slide says "Snelste sprong ooit (GPS)", not "officieel wereldrecord". Check this page again before the presentation in case the ranking has changed.
- The older 601 km/u (Henrik Raimer, 2016) was measured with a barometric device and does not count as a GPS record (https://fai.org/node/190020).
- Competition format: a competition is planned as 8 rounds. Each jump's score is the fastest 3-second average speed. The ranking uses all completed rounds, so the slide says "gemiddeld het snelst" (true whether the rules sum or average the rounds, and also if bad weather cuts rounds).
- Rounded figures for children: exit about 4 km, normal freefall about 200 km/u for about 1 minute, canopy ride about 5 minutes, climb about 20 minutes.
