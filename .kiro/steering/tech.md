# Technology

## Monorepo
- pnpm workspaces with Turborepo.
- TypeScript in strict mode everywhere.
- Shared code lives in `packages/`. Apps in `apps/` only contain platform code.

## Apps
| App | Stack | Notes |
|---|---|---|
| `apps/web` | Next.js, React, Tailwind, shadcn/ui | Landing page, accounts, dashboard, full editor |
| `apps/desktop` | Electron, React, Vite | Full editor using `packages/editor-ui` and `packages/renderer`. Main process handles windows, native menus, keyboard shortcuts, and local `.twn` file open and save through IPC |
| `apps/mobile` | Expo, React Native, React Native Skia | Uses `packages/editor-core` and its own Skia renderer. Does not use `packages/editor-ui` or shadcn |

## Shared packages
| Package | Contents | Rules |
|---|---|---|
| `packages/editor-core` | `.twn` document model (layers, frames, keyframes, symbols, tweens), command system for undo and redo, tween interpolation and easing, playback timing, serialization | Pure TypeScript. No DOM, React, Node or React Native APIs, so it runs on web, Electron and Expo |
| `packages/renderer` | Renderer interface plus a Canvas 2D implementation | Everything that draws goes through the interface, so the Canvas 2D implementation can be replaced later (for example with WebGL) without changing other packages |
| `packages/editor-ui` | Editor React components for web and desktop: stage, timeline, tool bar, properties panel, AI assistant panel | Uses `packages/ui` components and Phosphor icons |
| `packages/ai` | Converts prompts into document commands | Output is always a list of `editor-core` commands, never images or video |
| `packages/ui` | shadcn/ui components | Already created by the shadcn monorepo template |

## Rendering
- Web and desktop: Canvas 2D through `packages/renderer`.
- Mobile: React Native Skia, implementing the same renderer interface inside `apps/mobile`.
- The renderer only reads the document. It never changes it.

## AI
- Model and provider: [decide]
- The model returns structured output (JSON) that is validated and converted into `editor-core` commands.
- Each AI response is applied as one command group, so one undo reverses the whole change.

## Data rules
- The document is plain, serializable JSON. It is the single source of truth.
- Every change to the document goes through a command in `editor-core`, so it can be undone.
- `.twn` files include a format version number. Changes to the format need a migration.

## Testing
- Vitest for unit tests.
- fast-check for property-based tests on `editor-core`. Required properties:
  - A tween at its start and end frames returns exactly the values of its keyframes.
  - Undo followed by redo returns an identical document.
  - Serializing and then loading a document returns an identical document.
  - Exported frame count equals duration multiplied by frame rate.
- Playwright for end-to-end tests of the web editor.
