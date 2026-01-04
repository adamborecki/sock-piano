# sock-piano
musical piano based on "wrong" pattern of rainbow piano songs


## generated from prompt
You are a senior creative-coding engineer and sound designer. Build a single-page web app musical instrument based on “wrong piano keyboard socks.”

Core concept

A normal piano octave has white keys with black keys grouped 2 + 3. These socks are “wrong”: within one repeating unit (“sock octave”), the pattern is:

W B W B W B W  W B W B W B W B W
	•	This 16-key unit is one “sock octave.”
	•	The 17th key would repeat the 1st key’s pitch class one octave higher.
	•	There is exactly one WW gap, between positions 7 and 8 as written above.
	•	Visually, it should still look like a piano keyboard: white keys are full height; black keys are shorter and sit “between” adjacent whites (overlayed on top), even though the pattern is nonstandard.

Color system (very important)
	•	Black keys are black.
	•	White keys are each a single solid color (no stripes). Each white key has its own distinct color.
	•	Within one sock octave, the white-key colors should form a rainbow progression (ROYGBIV-ish stops), with hues distributed across the octave.
	•	The first note (position 1, which is C) is sky blue.
	•	The “octave” note (the 17th conceptual repeat of C) is the same sky blue.
	•	Use a palette that feels like a coherent rainbow but not uniform; allow strong variation in saturation/lightness (playful sock vibe), while still clearly reading as “rainbow.”
	•	Implement color selection by mapping each white key’s index to a hue path that returns to sky blue at the wrap point, but “anchored” to ROYGBIV-ish stops rather than a purely linear hue wheel.

Sound & mapping (dropdown modes)

Provide a dropdown that switches pitch mapping modes. Implement at least 4 modes:
	1.	16-EDO (Sock Equal Division):
Treat the sock octave as 16 equal divisions of the octave.
Key i maps to frequency = baseC * 2^(i/16), where i=0..15 for the 16 keys.
	2.	12-EDO “Nearest Piano-ish”:
Map the 16 sock keys onto the standard 12 chromatic pitch classes across one octave, by a deterministic method (e.g., distribute 16 keys across 12 steps with some repeats). Explain the mapping in a small help panel.
	3.	Near-Duplicate Microtonal Mode (requested):
Some keys should be near duplicates of others: pitches repeat but with small microtonal offsets (e.g., ±20–40 cents), creating a “woolly detuned sock” feel.
Keep it musical and repeatable (not fully random each press). For example, define a set of pairings and cents offsets that always apply.
	4.	Harmonic/Just-ish Mode (designer choice):
Use a coherent alternative mapping (e.g., a just-intonation-ish lattice around C, or a non-12 equal temperament) that still respects the 16-step sock octave concept. Keep it playable.

Base pitch / register
	•	The starting C (position 1) is C3 by default.
	•	Provide octave shift controls (+ / -).

Interaction
	•	Click/touch to play notes.
	•	Polyphony: at least 5 simultaneous voices.
	•	Optional computer-keyboard mapping (e.g., ASDF row) that follows the visual left-to-right order.
	•	No timbre difference between black and white keys (same synth), only pitch differences by mapping mode.
	•	Provide toggleable labels:
	•	Off by default or on by default is your choice, but must be toggleable.
	•	Labels may show index (1–16) and/or pitch name depending on mode.

Audio design

Use WebAudio (no libraries unless necessary).
	•	“Soft but bright” toy-piano/celesta vibe with a gentle attack and decay.
	•	Slight per-note randomness is ok (tiny variations), but mapping must remain stable.
	•	Light reverb or delay.
Controls:
	•	volume
	•	brightness/tone
	•	reverb amount
	•	mapping mode dropdown
	•	octave shift

Layout generation

Generate the 16-key unit procedurally from the W/B pattern string.
	•	White keys render in a row.
	•	Black keys render as overlayed shorter keys positioned between their neighboring whites, consistent with a piano look.
	•	Must be responsive for desktop and mobile.

Deliverables
	1.	Short spec (a few paragraphs) explaining:
	•	the 16-key sock octave pattern and how black keys are placed visually
	•	each mapping mode’s pitch logic (especially microtonal near-duplicates)
	2.	A complete single-file implementation: HTML + CSS + JS in one file that runs locally.
	3.	Code comments explaining:
	•	how you parse the pattern
	•	how you compute key positions
	•	how each mapping mode computes frequencies

Make it whimsical and coherent: the “wrong sock keyboard” visual should match the musical behavior.

⸻
