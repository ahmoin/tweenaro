# Structure

```
apps/
  web/            Next.js: landing page, dashboard, editor
  desktop/        Electron
    src/main/       main process: windows, menus, file system, IPC
    src/preload/    preload script exposing safe IPC functions
    src/renderer/   React app that mounts packages/editor-ui
  mobile/         Expo + React Native Skia
    app/            screens (Expo Router)
    renderer/       Skia implementation of the renderer interface
packages/
  editor-core/    document model, commands, tweens, playback, serialization
  renderer/       renderer interface and Canvas 2D implementation
  editor-ui/      editor React components for web and desktop
  ai/             prompt to editor-core commands
  ui/             shadcn/ui components
```

## Import rules
- Apps can import from any package.
- `editor-core` imports from no other package.
- `renderer` and `ai` import only from `editor-core`.
- `editor-ui` imports from `editor-core`, `renderer`, `ai` and `ui`.
- `apps/mobile` must not import `editor-ui` or `ui`, because they depend on the DOM.

## Naming
- Files: kebab-case (`timeline-row.tsx`, `tween-math.ts`).
- React components: PascalCase.
- Tests sit next to the file they test: `tween-math.test.ts`.
- Property-based tests end in `.property.test.ts`.
