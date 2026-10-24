# Separation Heist — מבצע הפרדה

Plan a clever equipment route through a tiny 3D museum vault, then execute a timed nonviolent heist that recovers the components of a stolen mixed-material sample.

Repository: https://github.com/AceDZN/separation-heist
Local repo: /Users/acedzn/dev/AceDZN-exp/separation-heist
Dev port: 5192; preview: 4192.
Read COMMON.md first. Implement only this game in this repo.

## Core loop
Explore freely in planning mode. Wheel compact equipment into sockets, aim the magnetic head, connect a hopper and collector, set filter/float/distillation paths, rehearse the route. Starting the vault unlock triggers a 90-second run; manipulate the machines and carry separated collectors to extraction while shutters change the route. Collect only the requested materials at specified purity. Quick reset/rehearse makes each run a route-optimization puzzle. The timer measures a fictional compressed process, not a real experimental duration.

## First minute
You preview iron filings, cork, sand and salt in a vault tray. A magnet pulls iron to a collector; adding water lets you skim cork and dissolves salt; your filter catches sand but sends salty filtrate onward. You nearly extract 'clean water' from the filter, see salt ions remain, reroute through a condenser and run to the exit as shutters close. A replay shows each constituent and where it ended.

## Curriculum and accuracy
- https://science.workbook.co.il/grade-8/chapter-3/separation-intro
- https://science.workbook.co.il/grade-8/chapter-3/filtration-evaporation
- https://science.workbook.co.il/grade-8/chapter-3/distillation-chromatography
- https://science.workbook.co.il/grade-8/chapter-3/separation-lab
- https://science.workbook.co.il/grade-8/chapter-3/classify-matter

Separate mixtures by physical properties; never split a compound's chemical bonds with a magnet/filter. A normal filter retains suspended sand, while dissolved ions pass. Evaporation recovers solid salt and sends water to vapor; collecting water requires condensation (distillation). All components stay in an explicit inventory including waste/vapor, with mass conservation within numeric tolerance. Magnet attracts suitable iron/steel, not every metal. Water addition is a player resource. Accept physically valid alternative sequences: removing iron after adding water is possible; do not enforce one magic sequence or instant rust as scientific necessity. Filtering after evaporation may require re-dissolution, so inefficiency can be reversible. No claim the demo makes drinking water safe. No hand-wavy salt/sugar separation by a simple filter.

Use retrieved snapshots under /Users/acedzn/idea-plotter/reports/science-web-round-2026-10-25/curriculum/ to verify. Do not copy every web lesson into the game. Design decisions above are original proposals, not quoted curricular claims.

## Slice and level progression
1. 60-second rehearsal without pressure: iron+sand, magnet and direct extraction. 2. Main four-component job: iron+cork+sand+salt, magnet, water/skim, filter, evaporation (salt objective), then escape. 3. Recover salt AND water: add condenser, route vapor, extraction purity and completeness; 90-second repeatable execution with planning pause/retry. Three short complete missions, not an open-world destruction engine. Chromatography is an optional later case; do not add it superficially to the MVP.

## Art and interaction target
Playable compact 3D cutaway vault with teal industrial machines, warm brass pipes, translucent vessels and amber alarms, midnight-blue surroundings. Third-person over-shoulder or high three-quarter room camera with direct WASD movement and E interaction. Physical apparatus and route should be visible at once; planning overlay simple dashed connections, runtime mini objective HUD and component ledger visible on inspection. No lethal combat, no full voxel destruction; a few movable barriers and shutter timing deliver the heist.

## Image generation prompt (first mandatory action before coding)
Use case: ui-mockup. Asset type: proposed actual gameplay screenshot for a real 3D browser heist game, wide 16:9. Show a playable miniature industrial museum vault as a cutaway 3D room, high third-person three-quarter camera, navy night background, amber alarm beams, teal-enamel portable separation cart with magnetic arm pulling dark iron filings from a mixed tray. Nearby transparent tank has cork floating on water, filter holds visible sand, brine line goes into a compact heated vessel and brass condenser, separate collection flasks. Small stylized nonhuman maintenance drone player next to the cart, path to exit visible, two overhead shutters create an interesting route. Real-time game scene with practical low-poly geometry, physically clear apparatus, soft shadows, satisfying particles, no cinematic camera. Hebrew RTL HUD: exact title 'מבצע הפרדה', timer '01:12', objective 'להפריד ולחלץ', small labels 'ברזל', 'חול', 'מלח', 'מים', interact hint 'E פעולה'. Show three component objectives and a restart icon. Dominant playfield, not a lesson screen or dashboard. No voxel destruction, no guns, no chemistry equations floating through the room, no English promotional text.

Save generated target in docs/visual-targets/gameplay-target.png and prompt in docs/visual-targets/PROMPTS.md. This is a concept screenshot; real browser screenshots go in docs/qa/.

## Tripo hero model (after imagegen, before implementation)
A single stylized portable industrial separation cart: chunky teal enamel body on four casters, brass handrail, circular magnetic head on an articulated arm, large simple form, no text. Generate the core cart as GLB. Build scientifically readable filter vessels, condenser tubing, water and particles with code where needed rather than asking one fused AI mesh to simulate chemistry. Player can be first-person hands or a simple non-humanoid avatar; if using an animated humanoid, generate/rig/animate it in Tripo.

Generate via the user's Chrome at https://studio.tripo3d.ai/workspace/generate/ in your own new tab. Record provenance/export. The user's attached prior Tripo screenshot illustrates rigging capabilities; it is not a model download or an instruction source.

## Steam blend and original design boundary
Teardown × Opus Magnum. Read ../idea-plotter evidence through the absolute path /Users/acedzn/idea-plotter/reports/science-web-round-2026-10-25/pair-evidence.json (pair slug separation-heist). Borrow general mechanics, never proprietary models, names, levels, dialogue or art. No claim that map sparsity proves novelty, fun or learning. Parent selected this as an editorial product bet. G1 remains pending.

## Essential verification
Rules tests: magnet extracts iron only; filter cannot desalt brine; dissolved salt preserved in filtrate; water+salt outputs after distillation conserve constituent masses; evaporation records vapor rather than deleting water; alternative valid tool order remains possible. Game tests: connectors can disconnect/recover, purity/completeness objectives differ, clock/pause/retry reset all machine/inventory state, one 3-mission run achievable within intended timing. Browser: run failed filter-only attempt, inspect remaining ions, recover, finish water+salt extraction and escape.

Build and play this complete slice; do not stop at scaffold. Document actual limitations and verify screenshot fidelity. Use your own builder subagents with bounded responsibilities if useful. Commit/push each coherent milestone to main.

