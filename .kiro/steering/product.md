# Product

## Summary
Tweenaro is a free 2D animation editor based on the Flash and Adobe Animate workflow, with AI features that create editable keyframes. It runs on web, desktop (Windows, macOS, Linux) and mobile (iOS, Android), built from one monorepo.

## Why it exists
- Adobe ended Flash in 2020. In February 2026 Adobe announced it would discontinue Adobe Animate, then kept it available in maintenance mode with no new features planned.
- There is no free, cross-platform, actively developed editor that uses the timeline and symbols workflow from Flash and Animate.
- Current AI animation tools either generate video files that cannot be edited frame by frame, or focus on UI motion graphics (Lottie Creator, Rive) instead of character animation.
- Tweenaro provides the timeline and symbols workflow on every platform, with AI that edits the same timeline data the user edits.

## Target users
1. Former Flash and Adobe Animate users who know timelines, symbols and tweens.
2. Hobbyist and student animators who find Toon Boom or Adobe Animate too complex or too expensive.
3. Video creators (YouTube, Twitch, social media) who need short character clips, intros and lip-synced characters.

## Competitors
| Tool | What it does not have that Tweenaro has |
|---|---|
| Adobe Animate | New features, AI, web and mobile versions, free |
| Rive | Built-in AI (Rive only supports external AI tools through MCP, desktop only); Rive targets app UI, not character animation |
| Lottie Creator | Character animation, drawing tools, timeline with layers and symbols |
| Wick Editor | AI, active development |
| AI video generators | Editable output. They produce video files; Tweenaro produces timeline data |

## Product rules
1. AI features output timeline data (shapes, keyframes, symbols, tweens), never video files. Every AI change can be selected and edited by the user.
2. Every AI change is shown as a summary with Keep and Undo buttons, and is undone as a single step.
3. The layout follows the Flash and Animate layout: timeline at the bottom, tools on the left, stage in the center, properties on the right.
4. Web, desktop and mobile use the same document format, the same editor core and the same AI features. A project opens and plays the same way on every platform.
5. AI-generated motion follows the 12 principles of animation (see `animation-principles.md`).

## Glossary
Use these terms in the UI and in code.
- **Stage**: the canvas area that is exported.
- **Layer**: a row in the timeline that holds frames.
- **Frame, keyframe, blank keyframe**: same meaning as in Flash. A keyframe holds defined content. Frames after a keyframe hold that content or are tweened.
- **Tween**: interpolation between two keyframes. A motion tween changes transform properties. A shape tween changes path shape.
- **In-between**: a drawn frame between two key poses.
- **Symbol**: a reusable named asset (graphic or movie clip) with its own timeline. Copies placed on the stage are instances.
- **Onion skin**: a faded display of previous frames (red) and next frames (green).
- **Easing**: the timing curve applied to a tween.
- **Playhead**: the marker for the current frame.
- **AI assistant**: the side panel where the user types prompts and reviews AI changes.

## Editor features
- **Drawing**: brush with pressure, pen with bezier curves, rectangle, ellipse, polygon, fill bucket, eraser, eyedropper, text.
- **Selection and transform**: select, direct select (edit points), free transform with a movable pivot.
- **Timeline**: add, delete, reorder, lock and hide layers; layer folders; frames, keyframes and blank keyframes; frame spans; playhead scrubbing; frame rate setting (default 24 fps).
- **Onion skin**: adjustable frame range, red for previous frames, green for next frames.
- **Tweens**: motion tween and shape tween, easing presets and a custom easing curve.
- **Symbols**: convert a selection to a symbol, library panel, nested timelines.
- **Audio**: import an audio clip onto a layer, waveform shown in the timeline.
- **Playback**: play, loop, step forward and back, go to first or last frame.
- **Export**: MP4, GIF, HTML (self-contained player), Lottie JSON. Projects save as `.twn` files (JSON).
- **Undo and redo** for every action, including AI changes.

## AI features (in priority order)
1. **Prompt to keyframes**: the user types a description such as "bounce the ball and squash on landing", and Tweenaro adds keyframes and tweens to the selected layer or symbol.
2. **Text edits**: the user types changes such as "slow down scene 2" or "add a camera shake at frame 40".
3. **Lip sync**: an audio clip is converted into mouth shape keyframes using a standard mouth shape set.
4. **Auto rig**: a drawn character is split into body part symbols with pivot points.
5. **Sketch cleanup**: rough strokes are converted into clean vector paths.
6. **AI in-betweening**: two key poses are converted into editable vector in-betweens. Stretch goal, because current methods are not reliable.

After each AI change, the AI assistant panel shows a short summary (for example, "Added keyframes on Ghost at frames 1, 12 and 24") with Keep and Undo buttons.

## Platforms
| Platform | App folder | Scope |
|---|---|---|
| Web | `apps/web` | Landing page, accounts, dashboard and the full editor in the browser. Main platform and the hackathon demo. |
| Desktop | `apps/desktop` | Full editor as an installed app for Windows, macOS and Linux. Adds local `.twn` file open and save, offline use, native menus and keyboard shortcuts. |
| Mobile | `apps/mobile` | iOS and Android. Browse and play projects, start a project from a prompt, use the AI assistant, and draw with touch or stylus on a simplified timeline. Full timeline editing is on web and desktop. |

Platform rules:
- All apps use the same `.twn` format and the same shared packages for the document model, timeline, tweens, playback and export. Each app only adds its own window, input handling and file system code.
- Projects sync through the user's account, so a project started on one device opens on another.
- The document format and playback must work the same on every platform. The editing UI can be simpler on mobile.

## Screens
1. **Landing page** (web): hero section, editor preview, AI features, how it works, desktop and mobile download links, sign-up button.
2. **Dashboard** (web, desktop): sidebar (Home, Projects, Templates, Symbols, Shared with me, Trash), prompt box to start a project, grid of recent projects.
3. **Editor** (web, desktop): top bar (file name, save status, playback controls, Share, Export), tool bar on the left, stage in the center, properties and AI assistant on the right, timeline at the bottom.
4. **Mobile home**: prompt card, recent projects list, bottom tab bar (Home, Projects, New, Templates, Explore).
5. **Mobile editor**: stage fills the screen, floating tool palette, timeline in a collapsible bottom drawer, AI assistant in a bottom sheet.

## Kiroween 2026 scope
Deadline: December 4, 2026, 2:00 PM Pacific.

- **Must ship**: web app with drawing tools, timeline with layers, keyframes and onion skin, motion tweens with easing, symbols, playback, prompt to keyframes, text edits, MP4 and GIF export, landing page, dashboard. Shared editor core package used by all apps.
- **Should ship**: desktop app (full editor and local files), mobile app (home, playback, prompts, AI assistant edits), lip sync, shape tweens, HTML and Lottie export, auto rig.
- **Stretch**: mobile drawing editor, AI in-betweening, sketch cleanup, .fla import.

Judges test the project through a URL, so the web app is the demo. Desktop and mobile builds are shown in the demo video and linked from the repository.

## Out of scope
- 3D animation, raster painting, video editing, real-time collaboration.
- Generating finished videos from a prompt.

## Rules
- Do not use the word "Flash" in the product UI, marketing or the demo video. It is an Adobe trademark. Use "the classic 2D animation timeline" instead.
- Do not use third-party trademarks or copyrighted music in demo content.
- All sample and demo content is original (ghosts, pumpkins, bouncing balls).
