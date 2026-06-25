# PickleBlocks

© 2026 wpd2012. All rights reserved.

> [!IMPORTANT]
> **PickleBlocks** is a proprietary web-based 2D game creation engine and editor. 
> This repository hosts only the compiled runtime demo and assets for playtesting and evaluation purposes. 
> You are not permitted to copy, modify, distribute, reverse-engineer, or host this software, in part or in whole, without explicit written permission from the copyright owner.

---

# PickleBlocks

**Version:** 0.5.2

PickleBlocks is a web-based, 2D-only game creation engine and editor. The current focus is a Blockly-first authoring flow where game logic is created visually, compiled into a structured event model, and previewed immediately in a Canvas 2D runtime.

## Live Demo

GitHub Pages deployment:

- https://wpd2012.github.io/PickleBlocks/

## Current Checkpoint

PickleBlocks v0.5.2 introduces a new Animation Mockup tab inside the Sprite Editor, featuring a live timeline player with compact settings-row play/pause controls, onion skinning visual overlays (enabling independent previous and next toggles, custom colors, and adjustable depth from 1 to 3 frames), interactive frame duration stretching (clicking and dragging card stretch handles), looping configurations (Loop, Once, Ping-Pong), and a marquee pixel selection tool with canvas context clipboard/rotation menu actions. It also adds a Rotate 90° button to the Sprite Card sidebar context menu. Additionally, it integrates visual animations into the Blockly editor and standalone runtimes, and implements a robust timeline clipboard supporting copying and pasting frames as "linked" (shared sprite assets) or "cloned" (duplicated sprites) with context menu insertion operations. It supports **timeline multi-selection** (using Shift-click for range select and Ctrl/Cmd-click for individual select) to perform **batch frame operations** including batch drag-and-drop reordering, batch inter-animation frame movement, batch duration setting, batch copying/pasting, and batch removal. It upgrades drag-and-drop frame reordering between different animations directly in both the timeline cards and sidebar tree rows with precise indicators, displays link badges for shared frames and special styles for foreign frames, preserves persistent frame identifiers (`id`), integrates **garbage collection safeguards** for shared sprite assets, protects shared sprite names, enables double-clicking sprite rows/cards to jump to sprite edit mode, introduces a Timeline Start Index setting, adds show/hide layout controls to editor pane context menus, overhauls the stage actor context menu with space-saving side-by-side button pairs and a new **Reset** command to revert custom properties to default settings, refines status console log toggle checkbox styling, integrates native dark mode color schemes automatically, adds browser Gamepad API and low-level WebHID controller fallback support for Switch, PlayStation, Xbox, and generic controllers (decoding D-Pads, analog axes, and button report inputs with unit tests), overhauls native checkboxes with antialiased CSS styles to prevent pixelation in dark mode, and adds a character dashing mechanic to the Collect Coins sample project.

The previous v0.5.1 checkpoint introduced a comprehensive visual UI system (supporting UI entity kinds, custom font size, text colors, text alignments, interactive click states, transparent HUD labels, pointer-down click/tap condition triggers, and Sprite Editor UI filters), upgrades both the Dodge Enemies and Collect Coins sample projects to utilize visual UI HUD text overlays, and implements dynamic standalone project screen resolutions rather than a hardcoded 16:9 aspect ratio. It also implements a searchable Add Block popup menu in the logic editor, custom dual-tone green styled condition blocks, fixes context menu selection inspector options to support props and UI elements, and implements follow-camera target tracking, separated Scene Map Sizes, global variable drag-sorting, density header updates, unified decorative Props under Entity schemas (`kind: 'prop'`) with automatic migrations, `.pickleblocks` project saving file formats, custom default active tabs, dynamic sidebar filters, and spacing layout density polish. In addition, it adds a visual value expression row editor featuring nested operator operands and variables/actors/props/UI/groups dropdown selectors, supports editing generic expression conditions in the Event Inspector and Event Sheet card inline editors, implements desktop global variable drag-and-drop workspace spawning, introduces an Enable Editor Sounds preference setting, adds repeat loop action support inside the compiler and standalone runtimes, builds dedicated visual loop action container boxes inside the Event Sheet, introduces unified dropdown action select pickers, supports updateVariable math-based actions, integrates stage and actor context camera target settings with real-time feedback, and implements inspector focus lock overrides for newly created elements.

The previous v0.5.0 checkpoint introduced comprehensive custom audio support (including file category auto-inference, duplicate import protection, cached HTML5 Audio playback, and an integrated workspace mini/expanded player with loop controls, animated level meters, and waveform visualizers), a consolidated Workspace Assets panel grouping images, audio, sounds, and synthesizers, a unified drag-and-drop file import dropzone, image asset deletion with linked sprite verification popups, a "Ping Sprite" tool for image assets to locate linked sprite definitions instantly, a camera focus context menu for scene actors, an upgraded 4D virtual joystick overlay supporting 4-way, 8-way, and full circular analog controls, a new Project settings and configuration tab in the Workspace tray, solo pane viewport layout scroll locking, Blockly editor viewport stability improvements, enhanced drag-and-drop pointer reordering for Workspace scenes, functions, and audio files, a sidebar toggle for the logic blocks toolbox, double-click and context menu controls to solo editor panes, right-click toolbar customization settings, editor-wide browser context menu prevention with overlay-free auto-dismissal, a dedicated context options dropdown for the application title header, a congruent premium tab panel redesign across settings and inspectors, and built-in scene tagging support with compiled scene conditions.

## What Works Now

### Editor Workspace

- Blockly scripting workspace with customizable light and dark theme modes
- Color-separated logic blocks: Hue `340` (pink/reddish) for nested `if` and `if/else` conditional action blocks, separating them visually from the blue-colored event blocks (`215`)
- Toggle for hiding and showing the Blockly grid dots/crosses
- Hide/Show Logic Blocks Sidebar: new action button in the pane header (visible in logic tab) and custom context menu items (Hide/Show Logic Blocks sidebar) on blocks/workspaces to collapse or expand the toolbox, triggering automatic SVG workspace resizing
- Congruent Tab Panel Designs: unified styling for Inspector tabs, Blocks Inspector mode selection tabs, and Settings tabs using a premium, congruent glassmorphic design with custom hover transitions and active drop shadows
- Workspace Audio Player: integrated player at the bottom of the Audio tab with Mini (single row controls) and Expanded (featuring an interactive waveform visualizer with timeline click/drag scrubbing, elapsed time formatting, and dynamic level meter animations) views, toggleable via settings or player context menus
- Image Asset Ping Sprite Context Menu: right-click any image asset and select "Ping Sprite" to automatically locate and focus the first linked sprite inside the Sprites tab of the Blockly Editor pane
- Double-Click & Context Solo: double-click Editor, Preview, Inspector, or Workspace view toggles (or right-click/double-click the panel header surfaces directly) to instantly solo/maximize that pane, or configure solo states from their right-click context menus
- Topbar Toolbar Hiding Context Menu: right-click Sample picker, project action buttons, history controls, or theme toggle to select "Hide from Toolbar", instantly updating general preferences to hide those buttons
- Overlay-Free Context Dismissal: window-level pointerdown, scroll, and resize listeners automatically dismiss open context menus on clicking outside, scrolling panels, or resizing the window, removing the transparent backdrop layer
- Application Title Header Context Menu: right-click the "PickleBlocks" header logo to open a custom app actions menu enabling reloading the application, opening Settings to the General tab, resetting the editor pane visibility layout and dimensions, or copying console logs to the clipboard
- Status Console Log Checkbox Toggle: redesigned the footer's console log toggle with custom borders, hover/checked styles, a clean checkmark SVG animation to match the engine editor's theme, and toned down label text brightness in dark mode
- Antialiased Checkbox Styling: custom antialiased CSS overrides for native checkboxes across Settings, Colliders, Inspector rows, Event Sheet tables, Onion setups, Group checklists, and Scene tags to prevent border/corner pixelation in dark mode
- Color Scheme Dark Mode Integration: added native CSS `color-scheme: dark` declarations to dark mode styles to ensure form inputs, scrollbars, and browser interfaces render with dark themes automatically
- Editor-Wide Browser Right-Click Prevention: disabled browser default context menus globally, automatically dismissing any custom context windows when empty area right-clicks occur
- Pointer Drag-to-Reorder for Audio Assets: upgraded audio list sorting to a custom pointer-capture event handler system with movement thresholds, avoiding native HTML5 drag-and-drop quirks
- Workspace Draggable Tab Strip: scroll the bottom project workspace tabs (Assets, Scenes, Functions, etc.) horizontally on desktop by clicking and dragging them with the mouse, utilizing pointer-capture event handlers
- Workspace Scene Ping: selecting a scene card or triggering a locator flashes the scene card inside the Scenes list with a pulsing border and shadow glow animation (`scene-card-ping`), and panning focuses targets cleanly
- Workspace Variable & Group Migration: moved Global Variables and Variable Groups tabs from the Inspector panel to the bottom Workspace dock panel to simplify inspector panels
- Logic Blocks Default Drag Mode: choose between dragging a Single Block (default, leaves children behind unless Cmd/Ctrl/Alt is held) or a Full Stack of blocks (drags attached blocks together unless Cmd/Ctrl/Alt is held), configurable under General Settings
- Searchable Add Block context menu: right-click empty workspace or blocks to open a custom search popup (`.add-block-popup`) with category grouping, and use arrow keys/Enter to quickly spawn blocks at coordinates
- Blockly Text Input Context Menu: right-click inside editable block text inputs (variable/actor names) to open a custom clipboard actions menu (Cut, Copy, Paste, Select All) bypassing default context menu prevention
- Hybrid Dropdown Pickers: dropdown selection pickers (`▾`) inside actor, prop, UI, group, and variable reference blocks to easily select existing assets or manually enter custom text values
- Pure CSS Zelos Highlights: styled condition blocks and active selection highlights using pure CSS rules, fixing selection highlight outlines with yellow/gold strokes (`#facc15` / `#fde047`)
- Global Variable Drag-to-Workspace: drag a global variable row from the Workspace Variables list and drop it directly onto the Blockly logic canvas to instantly spawn a variable reference block configured with that variable name
- Enable Editor Sounds Setting: toggle audio feedback and block click sounds in the logic editor via the "Enable Editor Sounds" checkbox under general settings
- Project Save Hotkey & `.pickleblocks` format: global Cmd/Ctrl+S keyboard shortcut saves the project immediately as a `.pickleblocks` file instead of launching browser HTML save dialogues
- Compact Workbench Spacing Layout: layout spacing padding, gaps, and panel borders adjusted from `14px` to `10px` globally to optimize screen real estate
- Left Editor (with Logic Blocks & Scene placeholder tabs), center Preview, and right Inspector layout
- Collapsible Editor, Preview, and Inspector panes
- Show/Hide Panel Controls: toggle panel visibility (Blockly, Preview, Inspector, and bottom Workspace dock tray) directly from any right-clicked header View Control context menu
- Timeline Start Index Setting: configure whether animation frame indices and timeline items start at index 0 or index 1 using a dropdown preference in General Settings
- Show Frame Duration Toggle: toggle the visibility of frame duration badges (`X ms`) on individual timeline cards using a General Settings preference checkbox
- Horizontal edge resize handles on all panel boundaries: drag the right edge of the Editor, both edges of the Preview (left/right), or the left edge of the Inspector
- Workspace docking system supporting top, bottom, left, or right positions, adjustable via Settings or a header quick-select dropdown
- Resizable Workspace tray and Status footer with persisted heights, supporting side-dock resizers with custom dimensions stored in local storage
- Drag-and-drop reordering for scene cards in the Workspace Scenes tab with pointer-driven drag handles and insertion previews, including locator targets
- Workspace assets tab consolidation combining Images, Audio, Sounds (retro sound presets), and Sound Synth sub-tabs for a cleaner asset management workflow
- Unified drag-and-drop file import dropzone supporting dragging files into lists with sleek inline list rows (`.asset-list-import-row`) and file verification checks (`isDraggingFiles`)
- Workspace Project settings tab grouping project name editing, startup scene configuration, active scene screen resolution presets, collision outline preferences, and Project Load/Save/Export actions, featuring a configurable Default Tab Selection preference
- Relocated asset statistics summary chips to the Project workspace tab
- Custom mouse/pointer context menus with modern three-dot icon buttons and backdrop wrappers on resource list rows for rapid asset actions (including Copy ID, rename, and Delete commands)
- Solo Workspace panel support stretching the tray to full viewport in solo layout mode
- Tablet height clamping configurations and Solo viewport size overrides to stabilize workspace tray layouts
- Scroll-locked solo layouts (`.has-solo-pane`) for desktop/tablet viewports, with dynamic height overrides for mobile stacking to maintain native scrolling behavior
- Desktop and pointer-capture drag-and-drop reordering for workspace functions and audio assets in resource list sidebars
- Blockly Editor viewport state preservation (scroll/scale zoom tracking) to eliminate visual canvas jumps and prevent infinite compile loop cycles
- Active scene auto-expansion: selecting a scene automatically expands its entry inside the Workspace Scenes list
- Solo Pane layout mode: maximize the Logic Editor, Preview, Actor Inspector, or Workspace Tray using the `[.]` circle button or the backtick/tilda (`` ` ``) hotkey
- Target locator/ping buttons next to Event and Function dropdowns in the Inspector, on each Event Card header inside the Event Sheet, and next to function definitions in the sidebar resource list, allowing users to quickly switch tabs and center/flash the block in the logic editor
- Floating Actors panel resizing: drag from any of the 4 corners of the floating Actors panel (`Top-Left`, `Top-Right`, `Bottom-Left`, `Bottom-Right`) to scale and position it, with standard clamping limits (`160px` width, `120px` height) and container boundary locks, plus a `ResizeObserver` listener to snap/scale the panel if the main canvas shrinks
- Actor clone sidebar tree view cleanup: indentation and expand/collapse icons are only shown if the actor actually has instantiated clones, removing unnecessary padding and whitespace
- Phone view sizing refinements: Actor selection dropdown stretches to `100%` width on mobile to prevent coordinate/metadata wrapping early, with the scrollable sprite sidebar vertical height doubled to `150px - 220px` to optimize asset editing workspace
- Expanded Desktop Mode setting (General Settings tab): toggles between locked `100vh` viewport size (default) and standard vertical page scrolling, removing browser height constraints and letting you scroll down to see the project tray and status footer
- Custom right-click context menu options on all Blockly blocks: `Inspect` selects the block and opens the Inspector panel; `Copy` copies block configurations to the clipboard; and `Paste` pastes blocks at the exact right-clicked mouse coordinates (supports both block context menu and workspace background context menu)
- Responsive layout that keeps the editor usable on narrow screens

### Event Sheet & Event Model

- Canvas 2D game preview with run, stop, and restart controls
- Top-bar Play button for launching the current project in a separate playable window
- Play mode stops the embedded Preview and shows that the external player is open
- Standalone player window includes Restart and Close controls plus automatic canvas focus
- Space is treated as a gameplay key in Preview and standalone Play mode, preventing browser page scrolling while playing
- Auto toggle in the Game preview header for live apply versus pending edits
- Event-only edits can hot-swap into the running preview without resetting the scene
- Center Preview workspace with collapsible Game and Event sections
- Vertical resize handle for balancing Game and Event inside Preview
- Collapsed Event section retracts to its header so the Game preview can reclaim space
- Event Sheet and JavaScript tabs for inspecting/editing the compiled event model
- Interactive card-based Event Sheet: toggle event enabled, rename event inline, delete events, and reorder event cards using HTML5 drag-and-drop (with drag handles, opacity reduction, and animated drop-line indicators)
- Automatic Blockly workspace block repositioning: reordering event cards in the Event Sheet automatically repositions and snaps their corresponding blocks vertically in the Blockly workspace to match
- Multiple conditions per event card: `If` headers map multiple conditions, with selectable AND (all) and OR (any) logical operators
- Interactive condition pills inside Event Sheet `If` cards with drag-and-drop support, secondary sorting buttons (▲/▼), and delete controls
- New triggers and conditional blocks: `timerEvery` (every X seconds), `timerAfter` (after X seconds), `cooldownReady` (checks timer cooldown), `variableChanged` (triggers on variable edit), `actorVisible` (checks visibility), `actorOutsideScene` (out of bounds check), `distanceBetween` (proximity trigger), `randomChance` (probabilistic trigger), `sceneHasTag` (current scene tag evaluation), and `sceneIs` (current scene ID matching)
- Advanced condition groups (`all` AND / `any` OR) rendered recursively as condition trees in the inspector and editing panels
- Mathematical variable update actions supporting `add`, `subtract`, `multiply`, `divide`, and `remainder` operators
- Event card locator target button next to the delete button in each card header to center and flash-highlight the event block on the Blockly workspace
- Auto-ping on event creation: adding an event from the Event Sheet automatically focuses the logic blocks tab (opening the pane if closed) and triggers a ping highlight with an asynchronous retry handler to wait for loading completion
- Workspace block payload mapping: associates `eventBlock.data = event.id` immediately during seeding to support locator resolutions before compile cycles run
- Compiler block evaluation sorting: sorts existing project events before new ones during compilation to preserve stable event names/IDs and avoid shifting or duplicate key crashes
- Collapsed event summary details (e.g., "1 condition • 2 actions") when event cards are minimized
- "Minimize Events" / "Expand Events" toolbar toggle to collapse/expand all cards at once
- Interactive popup configuration modals for adding, editing, and deleting conditions and actions (independent of the Inspector panel)
- Drag-and-drop action and sub-action reordering, with secondary side-by-side Up/Down arrows for quick adjustments
- Nested conditional branches (`if`/`then`/`else` layout structure) rendered visually inside the action column
- Nested `If` actions can be added, selected, edited, reordered, and deleted inside Then/Else branches
- Branch-level `+ Action` and `+ If` controls make deeper event logic editable directly in the Event Sheet
- Toggleable tabbed Blocks Inspector with Simple and Advanced views: Simple view renders plain-English summary descriptions of event conditions and actions; Advanced view shows all configurable block parameters and details
- Repeat & For Each Loop Actions: compile and execute loop structures visually using `repeat` and `forEachActor` action blocks, rendering them as nested container boxes with drag-and-drop branches, dedicated Block Inspector field inputs, and built-in safety execution limits
- Visual Value Expression Editor: visually construct nested operator expressions and references using a recursive dropdown/input interface supporting variables, actors, props, UI elements, groups, and parameters
- Generic Expression Conditions: edit and evaluate boolean-valued operator expressions directly in the Event Inspector and Event Sheet inline editors as `expressionCompare` ("Expression") conditions
- Update Variable Math Actions: modify global variables using arithmetic operators (`Add`, `Subtract`, `Multiply`, `Divide`, `Remainder`) with dynamic value expressions in the Event Sheet and Block Inspector
- Unified Action Dropdown Creators: choose and insert any action type using search/selection dropdowns (`.inspector-add-select`) at any nested level of the Event Sheet
- Blockly Animation Blocks: visual blocks under the "Animation" toolbox category to switch, play once/loop/ping-pong, or control the playback speed of sprite animations at runtime, complete with an animation finished event trigger

### Sprite Asset Editing

- Dedicated "Sprites" panel inside assets sidebar with list view and item counts
- Action controls to add new sprites (+ Add) and delete sprites (- Del)
- Paint Canvas editor for drawing 16x16 pixel art sprite frames
- Segmented tools: Pencil, Eraser, and Paint Bucket (flood fill) with custom SVGs
- Full-width Color presets ribbon featuring 16 color swatches with micro-animations and custom color picker input
- Canvas clear and assign-to-actor controls relocated to the sidebar below sprite list to declutter workbench
- Draggable sidebar resizer to dynamically customize the Sprite Editor layout width
- Container-query based pixel grid canvas scaling automatically using custom CSS aspect ratios
- Dynamic aspect ratio constraints for sprite thumbnails to prevent visual distortion (squishing/stretching) in actor lists and previews
- Persistent green circle Default Sprite restored automatically when the asset list becomes empty
- Collapsed grid rendering fix for left list sidebar and inspector icon previews
- Drag-and-drop sprite list reordering: drag and drop sprite items inside the Sprite Editor left-hand list to reorder them, complete with dashed dragover highlights
- Drag-and-drop asset list reordering: drag and drop imported image files inside the Workspace Assets list to rearrange them
- Dark mode checkerboard background pattern support for sprite images and previews to maintain visibility for transparent assets
- Standardized `"No Sprite"` warning placeholder badge (`.sprite-thumbnail-missing`) to replace broken thumbnails when a sprite's linked image asset is deleted
- Marquee Pixel Selection Tool: drag-select rectangular regions of pixels on the drawing grid, showing selected cells with highlight outlines and translucent overlays
- Selection Clipboard & Rotation Actions: copy selected pixels, paste them at different grid cells, or rotate them 90° clockwise directly via the canvas context menu, and rotate the entire sprite asset 90° clockwise directly from the Sprite Card sidebar context menu
- Animation Mockup timeline player: visual animation tab with frames timeline strip, playback controls (Play, Pause, Step Backward, Step Forward), frame duration inputs, loop modes (Loop, Once, Ping-Pong), and an animation preview height drag-resizer to adjust the settings panel height in the sidebar
- Interactive Duration Stretching: toggle interactive stretching from the timeline header to click and drag the right edge of any timeline card (`.frame-stretch-handle`) to scale its duration between `20ms` and `5000ms` with the card width resizing proportionally in real time
- Compact Settings Play Control: integrated a play/pause button (`.animation-sidebar-play-btn`) utilizing custom SVG icons directly inside the sidebar settings row next to loop and speed dropdowns, replacing the larger bottom play buttons
- Timeline Frame Multi-Selection: select multiple animation frames in the timeline using standard keyboard modifiers (**Shift-click** for range selection, **Ctrl-click** or **Cmd-click** for individual toggles), styling selected cards with a distinct outline highlight (`.is-selected`) and displaying a dashed overlay (`.is-active-frame`) on the active frame
- Timeline Frame Drag Reordering & Inter-Animation Movement: reorder animation frames inside the timeline strip by clicking and dragging frame index badges horizontally (safeguarded to prevent touchscreen scrolling conflicts), or drag single/multiple frames between different animations of the same owner sprite directly in both the timeline strip and left-hand sidebar tree list, with precise insertion drop indicators (`.is-drop-before` / `.is-drop-after`) and end-sequence append targets (`.is-frame-drop-target`)
- Animation Clipboard & Copy-Paste: copy single or multiple selected frames to a central clipboard, and paste them either as **linked** frames (referencing/sharing the same sprite asset) or **cloned** frames (creating duplicate copies of the sprite canvas to edit separately), with precise menu options for **Link Before/After** and **Clone Before/After** insertion
- Batch Context Menu Actions: apply operations to all selected frames in a single batch via the frame context menu, including shifting indices left/right together (preserving relative sequence), changing durations simultaneously, copying frames, pasting links/clones, and removing frames from the timeline
- Advanced Timeline Actions: a comprehensive context menu on the timeline title enabling users to reverse the frame sequence, double playback speed (halve frame durations), halve playback speed (double frame durations), set a uniform frame duration, clear all drawing canvases to transparent, or delete all timeline frames and their associated sprite assets
- Customizable Onion Skinning: toggle previous and next onion skins independently, select custom overlay colors, and adjust onion depth from 1 to 3 frames with staggered opacities (`0.28`, `0.18`, `0.1`), with a dedicated header toggle button and long-press/right-click quick action menu
- Shared & Foreign Frame Indicators: displays a chain-link badge icon on timeline cards and sidebar tree rows when a sprite asset is referenced multiple times in the timeline, and applies special styles/tooltips (`.is-foreign`) to frames that reference sprites from a different sprite group
- Garbage Collection & Reindexing Safeguards: checks and preserves sprite assets upon frame removal, ensuring they are only deleted from the project if not referenced by *any* animation timeline, protects shared sprites from being automatically renamed/reindexed to match sequence names, and auto-assigns persistent frame identifiers (`id`)
- Auto-generated Sprite Animations: automatically creates Mock Run and Mock Idle animations from the selected sprite assets by shifting pixel structures dynamically
- Natural Alphanumeric Sprite Sorting: sorts sprites and frame groups alphabetically and numerically using a natural alphanumeric ordering algorithm (e.g. `Sprite_2` before `Sprite_10`) via locale-aware comparison rules
- Double-Click Sprite Row Select: double-clicking a sprite tree row or a timeline frame card automatically selects the sprite and switches the active editor mode to `'sprites'` for instant editing
- Framed Tree Disclosure Buttons: restyled tree list expand/collapse arrows into modern border-framed buttons (`.sprite-asset-disclosure-btn`) with smooth transition animations and ARIA attributes for accessibility

### Entity Editing & Scene Layout

- Fully interactive Konva 2D scene editor tab for visual layouts
- Zoom, pan, and fit controls on the scene designer viewport, with full mobile touch-based panning and navigation support
- Mobile touch navigation gestures: multi-pointer pinch-to-zoom (calculates distance and center offsets between pointers to scale stage) and double-touch quick zoom
- Mobile touch action triggers: long-press touch gestures open context menus for actors and empty stage grid areas, enabling full mobile utility on touchscreen devices without physical mice
- Toggleable "Auto Pan on blank space drag" setting to pan viewport using touch/pointer drag on empty canvas background
- Global copy-paste clipboard hotkeys (Ctrl/Cmd + C / V) for duplicating actors instantly
- Backdrop-covered Stage Context Menu triggered on empty workspace right-click or touch-hold to "Paste" the copied actor at scene coordinates or "Add Actor Here" (creates default actor)
- Extended Actor Context Menu Overhaul: reorganized stage actor right-click context menu options into clean, space-saving side-by-side button pairs (Inspect & Focus, Copy & Clone, Reset & Delete) using a custom divided row layout (`.actor-context-button-row.has-divider`), and added a **Reset** command (marked as `is-info`) to revert all custom properties back to default settings after a confirmation prompt
- Glitch-free canvas resizing: keeping the Konva Stage always mounted prevents canvas recreation glitches during drag-resizing, while docked left/right actor lists use standard percentage/min-width constraints and the Sprite Editor uses Flexbox-based proportional shrinking to protect canvas and workspace viewport areas
- Snap-to-grid alignment with configurable grid size (4 / 8 / 12 / 16 / 24 / 32 / 48 / 64 px), selectable from Scene Settings
- Right-side entity inspector for adding, deleting, and editing scene objects
- UI Entity Customization: added UI entity kind (`kind: 'ui'`) with custom font size (6-128 px), text color picker, text alignment options (left, center, right), and interactive click toggle to configure buttons and overlays in the Inspector. Added target filtering in the Sprite Editor to support UI elements, and right-click context menu options in the scene stage to support quick inspection of both props and UI elements
- Decorative Props System: integrated decorative props system unified directly with entities (`kind: 'prop'`) under `EntitySchema`, featuring automatic schema preprocess migration from legacy formats. Built a dedicated Props tab in the Inspector to modify prop properties (x/y position, size, scale, rotation, color, opacity, visibility, image/sprite references, and sorting layer/order)
- Collapsible Scene Outline Sidebar: reorganized the sidebar entity list into collapsible sections (Actors, Props, UI Elements) with toggle carats (`▸` / `▾`), visual dividers, hover highlight states, and tab bar filtering (All, Actors, Props) to easily view and manage scene hierarchies
- Sprite Editor Assignment Filters: assign target filters (Show: All, Show: Actors, Show: Props, Show: UI) in the Sprite Editor to easily find and map sprites, and clear canvas quickly using the drawing toolbar's Trash Icon button
- Slottable actor icon preview: drag sprites from the Sprite Editor list or images from Workspace Assets and drop them onto the Inspector's actor preview slot (with glowing dragover highlights, scaling hover states, and smooth border animations in light/dark modes) to assign them directly
- Drag-and-drop actor list reordering: drag and drop actors/clones inside the Scene Editor's sidebar list to sort them, supporting clone-level and group-level (parent-to-parent) rearranging
- Dedicated highlight styles for selected actor clones in the sidebar list in both light and dark mode views
- Built-in Scene Tagging support: assign multiple semantic tags (e.g. gameplay, menu, combat, boss, cutscene, victory, gameover) to scenes, displaying them as metadata badges inside the scenes workspace tray, and toggling them via an interactive checklist inside the scene property panel
- Actor Focus Camera Shortcut: right-click any actor clone in the Scene Editor list or stage to select "Focus", which centers/fits the Konva editor camera viewport on that actor clone's position, opens the Preview panel if hidden, and selects the Scene layout preview tab
- Interactive Camera Viewport Follow: right-click any actor clone to select "Set as Camera Target", or right-click empty stage coordinates to select "Clear Camera Target", triggering real-time success/info toast notifications on tracking adjustments
- Inspector Focus Lock Bypass: newly added props, UI elements, and cloned/pasted actors automatically ignore block inspector lock toggles to focus their properties tabs in the inspector panel immediately for rapid editing
- Editable entity name, position, size, color, and rotation (in degrees)
- Actor group tags in the Actor Inspector for grouping actors such as enemies, hazards, bullets, and collectibles
- Action and collision target dropdowns can select individual actors or actor groups
- Inspector lock state (persisted across sessions) with minimal locked/unlocked lock SVGs
- Entity changes restart the preview cleanly so the game view stays in sync

### Runtime And Engine Foundation

- Canvas 2D runtime split into dedicated engine modules
- Scene/entity modeling for game state
- Input handling for keyboard-driven movement and pointer clicks (capturing mouse/touch positions in world-space for actors and screen-space for UI components)
- Collision helpers, including `collisionStarted` for one-shot overlap events
- Renderer module supporting rotated entities, interactive UI button backgrounds/borders, and transparent non-interactive text HUD overlays
- Blockly compiler and standalone exporter updated for entity rotation, UI button drawing, click event handlers, and dynamic motion action target values
- Event interpreter and standalone runner translating events into runtime behavior, supporting dynamic motion targets and value expressions (resolving variables, entity instances, and group targets at runtime)
- Actor group target selectors, allowing actions like destroy, move, hide/show, set text, set color, and clamp to apply to all actors in a group
- Group-aware collision checks, allowing a condition like `Player starts touching group enemies`
- Runtime project hot-swapping for event-only changes
- Additional game actions: set color, show sprite, hide sprite, set text, clamp to scene, restart scene, and play sound (with volume controls, custom HTML5 Audio resolve, and retro synthesizer fallbacks)
- Seamless audio import and resolver engine supporting `.mp3`, `.wav`, `.ogg`, `.webm`, and `.m4a` file categories with duplicate asset checking (analyzing names and binary data url content)

### Gamepad Controls & Key Bindings

- Fully customizable physical keyboard key bindings for D-Pad directions, buttons A/B/X/Y, Select, and Start buttons
- Dynamic layout customizability: independently show/hide D-Pad, A/B buttons, X/Y buttons, and Select/Start buttons via checkbox settings
- Keyboard rerouting that maps custom configurations (e.g. WASD, Space, Backspace, Enter) to their canonical Blockly runtime action triggers
- Cross-browser touch responsiveness: delegated touch event listeners (`touchstart`, `touchend`, `tou-chcancel`) with active scroll-prevention `{ passive: false }` options ensure continuous, cancellation-free tap-and-hold controls on mobile devices
- Upgraded virtual gamepad direction controls supporting 4-way, 8-way, and full circular analog joystick modes, customizable via settings
- Beautiful pointer-capture dragging visual ring/thumb UI overlay elements on touchscreens, also bundled into exported standalone builds
- Cleaner retro aesthetic for Start/Select buttons, replacing text labels with clean SVG icons (+ and -) and fully collapsing the controls frame when disabled
- Settings persistence in localStorage, synced in real-time
- WebHID Gamepad Fallback Support: low-level controller support to read raw HID input reports from Switch, PlayStation (DualShock 4), Xbox, and generic gamepad controllers, decoding analog axes, D-Pad hat switches, and button mappings
- WebHID API Fallback Routing: prioritizes requesting WebHID gamepad connections inside secure contexts and standalone PWAs when standard browser Gamepad APIs are restricted
- Controller Diagnostic Tools: sidebar display showing HID gamepad connection states, and exports detailed report mappings (`__pickleblocksControllerReport`) to inspect connected device bytes

### Progressive Web App (PWA)

- Mobile/Desktop installation support (Add to Home Screen) utilizing `vite-plugin-pwa`
- Standalone app shell display mode hiding browser URL/navigation panels for native look-and-feel
- Service Worker registration (`sw.js`) utilizing workbox to support offline caching and launch
- Custom high-resolution brand icons (`icon-192.png`, `icon-512.png`) and iOS bookmark icons (`apple-touch-icon.png`)
- Custom textless pixel-art favicon (`favicon.png`) configured across creator app and website landing page
- Zero-latency theme flash prevention: inline `<style>` and synchronous blocking `<script>` inside `index.html`'s `<head>` resolve white background flashes during page loads before external CSS or JS bundles load, matching React's synchronous state initialization
- Native PWA user-select restriction: global `user-select: none` on `body` prevents accidental highlights and double-tap zooms, while preserving `user-select: text` for input fields, textareas, Blockly input fields, and editing elements
- Dynamic status bar colors synchronizing browser/PWA interfaces automatically using fallback media queries and runtime `theme-color` meta updates

### Samples, Save/Load, And Export

- Built-in Collect Coins and Dodge Enemies sample projects, upgraded to support visual UI HUD text overlays, multi-scene gameplay loops, and a keyboard-triggered dash ability (using Space or Z) in Collect Coins
- Save and load project JSON
- Dynamic Standalone Project Resolution: Exported standalone HTML and ZIP builds automatically respect and scale to the active project's screen resolution and aspect ratio (e.g., 256x240 for NES) rather than hardcoding a 16:9 ratio
- Export a standalone game ZIP bundling custom image and audio assets, resolving asset references dynamically at runtime

## Changelog Summary

### v0.5.2 - Animation Mockup Timeline, Onion Skinning, Pixel Selection, Blockly Integration, Timeline Clipboard, Frame Dragging & Reordering Settings

- **Animation Mockup Timeline & Preview**: Created a new Animation Mockup tab inside the Sprite Editor featuring a live animation preview panel with play, pause, step forward/backward, and custom frame duration controls, supporting standard Loop, play-once Once, and reversing Ping-Pong playback. Added customizable onion skinning overlays to display adjacent frames on the drawing canvas, auto-generated Idle/Run mockups via pixel-shifting calculations, and added a vertical resizer handle to customize the animation sidebar preview height between `120px` and `400px`.
- **Customizable Onion Skinning Controls**: Added previous and next onion skin toggle checkboxes, color selectors, and depth settings (1 to 3 frames) with staggered alpha opacities. Integrated a timeline header onion skin toggle button with a long-press/right-click quick action context menu.
- **Timeline Clipboard & Linked/Cloned Copy-Paste**: Built an in-memory frame clipboard supporting copying individual frames or all animation frames, and pasting them as **linked** frames (referencing/sharing the same sprite asset) or **cloned** frames (creating duplicate sprite canvas copies to edit separately). Added context menu options for **Link Before/After** and **Clone Before/After** insertion.
- **Advanced Timeline Title Context Menu**: Added options to reverse frame sequence, double playback speed (halve frame durations), halve playback speed (double frame durations), set a uniform duration across all frames, clear all timeline drawing canvases, and delete all timeline frames and their associated sprite assets.
- **Inter-Animation Frame Dragging & Movement**: Upgraded drag-and-drop frame reordering to support dragging and dropping frame cards between different animations of the same owner sprite directly in both the timeline strip and the left-hand sidebar tree list. Added precise drop target indicators (`.is-drop-before` / `.is-drop-after`) and append zones (`.is-frame-drop-target`).
- **Shared & Foreign Frame Badges**: Added a chain-link badge icon on timeline cards and sidebar tree rows when a sprite asset is referenced multiple times in the timeline, and applied special styles/tooltips (`.is-foreign`) to frames referencing a sprite belonging to a different sprite group.
- **Persistent Frame IDs & Schemas**: Upgraded the project schema and parser to assign and preserve persistent frame identifiers (`id`) for stable rendering keys during reordering.
- **UI & Workspace Refinements**: Redesigned the tree disclosure expand/collapse buttons into framed buttons with smooth transitions. Enabled double-clicking sprite rows or timeline cards to jump to sprite edit mode. Added an auto-switch guard to prevent unwanted animation jumps when selecting sprites inside the active sequence.
- **Interactive Duration Stretching**: Added a stretchy duration toggle button to the timeline header. Toggling it enables **interactive frame duration stretching**: users can click and drag the right edge of any timeline card horizontally (`.frame-stretch-handle`) to dynamically scale its duration between `20ms` and `5000ms`, with the timeline card width resizing proportionally in real time.
- **Compact Settings Play Control**: Integrated a play/pause button (`.animation-sidebar-play-btn`) using clean SVG icons directly inside the sidebar settings row next to loop and speed drop-downs, decluttering the bottom of the assets panel.
- **Actor Workspace & Context Actions**: Added a Reset command to the stage actor right-click context menu to revert all custom properties of a scene entity back to default settings, and reorganized context menu options into clean side-by-side button pairs (Inspect & Focus, Copy & Clone, Reset & Delete) using a custom divided row layout.
- **Console Log Toggle Styling**: Redesigned the PWA status console log toggle under the footer with custom checkbox borders, hover/checked styling, and a clean checkmark SVG animation to match the engine editor's theme.
- **Color Scheme Dark Mode Integration**: Added native CSS `color-scheme: dark` declarations to dark mode styles to ensure form inputs, scrollbars, and browser interfaces render with dark themes automatically.
- **Browser Gamepad & WebHID Switch Support**: Added a complete frame-by-frame browser gamepad polling subsystem to the preview runtime and standalone exported builds. Integrates standard USB/Bluetooth controller button-to-keyboard mapping and a specialized WebHID backend (`joy-con-webhid`) for Nintendo Switch Joy-Cons and Pro Controllers.
  - **Dynamic Layout Mapping**: Split button configurations into two layouts: Nintendo-style (physical button labels match A/B/X/Y literally) and Standard-style (Xbox/PlayStation controllers physically map the bottom button to Action A/Space/Jump and right button to Action B/Z, maintaining standard console ergonomics).
  - **Compatibility & Diagnostics**: Wrapped Gamepad API and WebHID calls in `try...catch` safeguards to handle insecure context blocks (HTTPS required) or iframe Permissions Policy restrictions without crashing the engine. Enhanced the editor UI status header to explicitly show `Gamepad blocked (HTTPS required)` if the browser restricts the API on non-secure origins.
  - **Safari Performance Optimization**: Removed redundant 8ms background polling intervals in favor of strictly frame-driven updates, resolving input lag and stuttering for macOS Safari Pro Controller bluetooth connections.
- **WebHID Gamepad Fallback Support**: Added low-level fallback WebHID controller support to interface with Switch, PlayStation (DualShock 4), Xbox, and generic gamepad controllers, reading raw HID input reports to decode analog axes, D-Pad hat switch coordinates, and buttons. Prompts for WebHID authorization in secure contexts and standalone PWAs when standard browser Gamepad APIs are restricted, displaying gamepad state in the Preview sidebar and exporting detailed report mapping logs (`__pickleblocksControllerReport`).
- **Antialiased Checkbox Styling**: Overrode default native checkbox appearances with custom antialiased CSS overrides across Settings, Colliders, Inspector rows, Event Sheet, Onion configurations, and Scene tags to prevent border/corner pixelation in dark mode.
- **Dashing in Collect Coins**: Upgraded the Collect Coins sample project to support character dashing: press the Spacebar or `Z` key while moving to dash in the player's active direction (speed `4320`) with a `0.18s` cooldown timer.
- **Previous Features**: Redirected mouse wheel scroll events over the timeline horizontally. Added a General Settings toggle preference to show/hide frame duration labels on timeline cards. Implemented a rectangular Marquee Selection tool, canvas context menu copy/paste/rotate 90° actions, a Rotate 90° button on the Sprite Card sidebar context menu, Blockly animation blocks, a Timeline Start Index option, pane visibility header toggles, and natural alphanumeric sprite sorting.


### v0.5.1 - UI System, Follow-Camera, Separate Map Sizes & Drag-Sorting

- **UI System, Pointer Clicks & Filters**: Introduced a new UI entity kind (`kind: 'ui'`) with custom font size, text color, and alignment options. Interactive UI buttons render with border/background outlines while text labels remain transparent to support HUD meters. Added `pointerDown` triggers in the interpreter, and added the `when [TARGET] is clicked` event block and `[TARGET] is clicked` condition block in Blockly. Supported filtering UI targets in the Sprite Editor (Show: UI filter dropdown option) and quick inspection of UI elements via the stage right-click context menu.
- **Standalone Project Resolution**: Configured the standalone exporter to configure canvas dimensions and CSS styles using the active project's screen resolution and aspect ratio (e.g., 256x240 for NES) rather than hardcoding a 16:9 ratio.
- **Sample Projects Upgrades**: Upgraded the **Dodge Enemies** sample project into a multi-scene loop (`main` level, `level2` level, `gameover` screen, `victory` screen) displaying HUD overlays and a clickable "Retry" button. Upgraded the **Collect Coins** sample project to display the running score utilizing the new UI entity text overlay HUD elements.
- **Searchable Add Block Popup**: Added an "Add Block" context menu option to the Blockly workspace and blocks. It opens a custom overlay search popup (`.add-block-popup`) containing all available blocks grouped by category, with arrow key and Enter navigation to spawn the selected block at the cursor's location.
- **Blockly Condition Block Outlines**: Implemented custom dual-tone green styling for condition blocks (blocks starting with `phase_condition_` or the OR condition separator) to clearly differentiate them from event and action blocks in both light and dark modes.
- **Logic Blocks Default Drag Mode**: Added a "Default Drag Mode" user setting to choose between dragging a single block (default) or dragging the full stack of blocks together, with Ctrl/Cmd key modifiers to invert the drag behavior.
- **ESLint & Codebase Cleanups**: Disabled several React/TS lint rules globally to streamline hooks development. Unified entity logic by removing obsolete prop wrapper functions, added missing dependencies to React Konva hooks, cleaned up unused arguments/variables, and converted helper callback variables into named functions.
- **Dynamic Action Targets & References**: Upgraded `setPosition`, `setVelocity`, and `moveBy` actions to accept a dynamic value expression (`ValueExpression`) as their target instead of a hardcoded target string. Introduced new Blockly block definitions under a new "References" category to retrieve variable values (`get variable`) and references to actors (`actor`), props (`prop`), UI elements (`ui`), and groups (`group`), with full compiler, interpreter, and standalone runtime support to resolve these references dynamically at runtime.
- **Collapsible Entity List Sidebar**: Reorganized the scene outline sidebar list into collapsible/expandable sections for **Actors**, **Props**, and **UI Elements**, with toggle carats (`▸` / `▾`), visual dividers, and hover highlight states in both light and dark modes.
- **Blockly Drag Performance Optimization**: Deferred workspace compilation and block styling updates during active `BLOCK_DRAG` events in the logic editor, running compile operations only after block release to prevent UI lag.
- **Logic Operators & Generic Expressions**: Added Zod schemas and runtime support for nested `OperatorExpression` values (performing math operations `+`/`-`/`*`/`/`/`%`, comparisons `==`/`!=`/`<`/`<=`/`>`/`>=`, and logical `and`/`or` operations). Created `valueOperatorMath` and `valueOperatorCondition` Blockly blocks, along with `conditionExpression` ("Expression Check") and updated `actionIf` / `actionIfElse` to support dynamic condition sockets.
- **Reference Dropdown Arrow Pickers**: Added dropdown pickers (`▾`) inside entity reference blocks (actor, prop, UI, group) and variable blocks to choose existing names dynamically or write custom values manually.
- **Blockly HTML Text Input Context Menu**: Registered a custom context menu (Cut, Copy, Paste, Select All) on editable block text fields (`.blocklyHtmlInput`) to enable clipboard actions.
- **CSS-Based Zelos Block Styling & Selection outlines**: Refactored condition block green styling to pure CSS rules, and styled zelos selected block outlines using custom gold/yellow highlights (`#facc15` / `#fde047`) to resolve visual glitches.
- **Camera Tracking & Lerping**: Integrated target follow-camera tracking into preview and standalone runtimes, supporting customizable camera targets and smooth movement interpolation (lerping values from `0.01` to `1.0`). Added a "Camera" category with `set camera follow target` and `set camera position` blocks.
- **Scene Map Size Separation**: Split scene width and height into individual, scrollable map sizes separate from the project resolution configured in settings. Added `MapSizeInput` and `ProjectResolutionInput` components for clean inputs.
- **Global Variable Drag-and-Drop**: Enabled click-drag reordering for global variables inside the Workspace Variables tab, letting users adjust their index order sequence.
- **Workspace Density Improvements**: Redesigned tab headers for Scenes, Functions, and Variables to place search bars, warning diagnostics, and counters side-by-side with actions to save vertical space.
- **Scene Group Double-Clicks**: Programmed double-clicks on scene names inside Project tag lists to automatically locate and ping the scene card in the Scenes dock tab.
- **Props & Unified Entities**: Refactored the Props implementation to merge `Props` with `Entities` under `EntitySchema` via `kind: 'prop'`, including automatic schema preprocess migration from legacy formats. Simplified the Canvas renderer (`Renderer.ts`), standalone exporter (`standalone.ts`), and Konva scene layout builder (`SceneEditor.tsx`) by drawing/transforming props as entities directly.
- **Project Save Extension & Hotkey**: Changed project file saves from `.json` to `.pickleblocks` extension, and updated global key shortcut (Cmd/Ctrl + S) to save the project `.pickleblocks` JSON file instead of launching browser HTML save dialogues.
- **Workspace Default Tab Settings**: Added a new `Default Tab Selection` user preference setting under Workspace Settings to specify which workspace tab is active by default.
- **Sprite & Actor List Filters**: Added a filter tab bar ("All", "Actors", "Props") in the Scene Editor's Sidebar list and a target filter select dropdown in the Sprite Editor to filter lists.
- **Sprite Editor Clear Canvas Button**: Replaced the text "Clear Canvas" button with a modern Trash Icon SVG button inside the Sprite Editor drawing toolbar.
- **Workbench Gap & Margins Spacing**: Tightened the global workspace margins, gaps, and panel borders layout padding from `14px` to `10px` for a more compact and elegant alignment on desktop and mobile.
- **Workspace Variable Migration**: Relocated the **Variables** and **Groups** (Variable Groups) management tabs from the Inspector panel to the bottom Workspace dock panel to declutter the layout and improve the editing flow.
- **Draggable Workspace Tabs**: Enabled desktop click-drag scrolling for the project workspace tab strip. Users can click and drag horizontally on the tab strip to scroll smoothly, using pointer-capture event handlers.
- **Panel Header Solo Mode & Double Click**: Added support for maximize/solo actions directly on editor panel headers (Blockly editor, Preview, Inspector, and Workspace). Double-clicking a header solos the pane, and right-clicking it triggers the pane visibility context menu.
- **Scene Ping Animation**: Programmed a locating "ping" animation on workspace Scene cards. Selecting or triggering a scene locator flashes the scene card with a smooth border pulse and shadow glow animation (`scene-card-ping`).
- **Codebase Lint Fixes**: Resolved a variety of syntax constraints, TypeScript type assertions, and ESLint rule warnings across multiple files.

### v0.5.0 - Custom Audio Waveform & Level Meter, 4D Joysticks, Sidebar Toggle, Pane Soloing, App Header Context, Toolbar Customization, Scene Tagging & Viewport Stability

- **Logic Blocks Sidebar Toggle**: Added a header button and context menu options (Hide/Show Logic Blocks sidebar) on blocks/workspaces to collapse or expand the toolbox, triggering automatic SVG workspace resizing.
- **Congruent Tab Panel Designs**: Restyled the Inspector tabs, Blocks Inspector mode selector tabs, and Settings panel tabs into a premium congruent glassmorphic design featuring hover transition effects and drop-shadow active states.
- **Scene Tagging & Scene Conditions**: Added built-in scene tagging (e.g. gameplay, menu, combat, boss, cutscene, victory, gameover) with inline scene card badges and an interactive properties checklist. Introduced new compilation, interpreter, and exporter support for conditional `sceneHasTag` and `sceneIs` checks.
- **Image Asset Deletion & Verification**: Built a workspace image deletion workflow confirming deletions via a popup (`window.confirm`) listing linked sprites that will be affected and fall back to placeholders, with warning notifications and counts metadata previews.
- **Solo Layout & Viewport Height overrides**: Implemented `.has-solo-pane` height constraints locking desktop/tablet viewport scrolling to prevent duplicate scrollbars, while letting mobile/tablet solo views bypass locks for stacked touch scrolling.
- **Unified Drag & Drop Import Dropzone**: Replaced the large full-width dropzone overlay with a sleek, interactive inline import row (`.asset-list-import-row`) inside both image and audio lists. Added a file check guard (`isDraggingFiles`) to verify that drag events contain actual files, avoiding collision with internal row reordering. Batch-processes images, audio, and unsupported formats in parallel, with content/name duplicate checking and summary toast notifications.
- **Restructured Workspace Assets Tabs**: Restructured bottom Workspace tabs: split the Synth tab into Sounds (Retro presets list) and Sound Synth (the Synthesizer playground controls). Added SVG icon indicators next to all tab labels, metadata badges (`.asset-meta-badge` and `.uppercase-badge`), and modern three-dot SVG context menu triggers.
- **Custom Dock position Dropdown**: Replaced the native select dropdown for dock positioning with a custom, sleek dropdown list UI (`.workspace-dock-dropdown-menu`) showing status checkmarks, active states, and layout outline previews.
- **Workspace Search Filters**: Added search bar inputs (`.workspace-search-input`) inside the Images, Audio, Sounds, Scenes, and Functions workspace tabs, enabling instant real-time filtering of items with styled empty search state feedback blocks.
- **Theme-Aware Scrollbars & SVG Buttons**: Added styled custom modern scrollbars (`::-webkit-scrollbar`) across workspace list grids to match light/dark themes. Replaced emoji actions and counts stats chips with visual SVG icons.
- **Workspace "Project" Settings Tab**: Introduced a dedicated Project tab in the Workspace tray, housing inline project name editing, startup scene configuration, active scene screen resolution presets, editor collision outline visibility and color picker settings, and data load/save/export actions. Also relocated the global asset counts chip dock to this tab.
- **Audio Player Improvements (Waveform & Level Meter)**: Added an **Expanded Audio Player** view mode featuring an interactive **Waveform Visualizer** displaying 72 sample amplitude bar heights with keyboard/mouse scrubbing, and a multi-band animated **Audio Level Meter** pulsing dynamically during playback. Also supported loop configuration and view settings.
- **Image Asset Ping Sprite Tool**: Added a context menu action "Ping Sprite" for image assets to automatically locate the first linked sprite inside the Sprites tab of the Blockly Editor pane.
- **Actor Focus Camera Utility**: Integrated a **Focus** button inside the Scene Editor's actor clone context menu that immediately centers the stage editor camera viewport on the selected actor, reveals the Preview panel, and activates the Scene layout preview tab.
- **Pane Soloing via Double-Click & Context**: Enabled view controls (Editor, Preview, Inspector, Workspace) to be soloed via double-click actions or right-click context menus.
- **Topbar Toolbar Custom Hiding**: Added right-click context menu options to primary toolbar modules, allowing them to be hidden from the topbar workspace. Suppressed default browser menus across the header background.
- **Overlay-Free Context Auto-Dismissal**: Replaced full backdrop layers with window-level pointerdown, scroll, and resize events to auto-close open context windows.
- **Global Browser Context Menu Prevention**: Configured an `onContextMenu` handler globally on the editor wrapper, disabling native browser menus and auto-dismissing active custom menus.
- **Application Title Context Menu (App Options)**: Added a custom right-click context menu to the **PickleBlocks** logo header to quickly reload the app, open general preferences settings, reset the view layout and weights, or copy internal logs.
- **Sprite Editor & Canvas Previews**: Implemented dark mode checkerboard pattern background support for custom sprite images and previews (`.sprite-image-preview-wrapper` and `.sprite-image-preview-img`) to preserve contrast for transparent assets. Added `"No Sprite"` placeholder tag renderers inside the inspector when a sprite's underlying image is missing/deleted.
- **Scene Editor Sidebar List**: Added CSS highlight styling for selected actor clones (`.scene-actor-list-item.is-clone.is-selected`) in both light and dark mode views.
- **4D Virtual Joystick Overlay**: Upgraded the virtual gamepad D-Pad with new 4-way, 8-way, and circular analog joystick modes. Rendered dynamic pointer-captured joystick thumb dragging overlay UI, fully integrated into standalone game builds.
- **Workspace Dock Solo & Tablet Fit**: Supported solo Workspace window styles (`.is-soloed`) to stretch the tray fluidly when in solo layout mode. Configured tablet-view workspace height clamping controls and Solo viewport height calculations.
- **Blockly Viewport Preservation & Compilation Order**: Added viewport scroll/scale locking during compiling to prevent jumping/flickering Blockly layouts. Preserved drag-and-drop workspace functions ordering during compile cycles to prevent Blockly index overrides.
- **Drag-to-Reorder Enhancements**: Added drag-and-drop support for reordering Workspace functions (using pointer-down capture click-suppression guards to prevent accidental clicks) and audio assets. Migrated Scene card reordering to native HTML5 drag-and-drop events with insertion highlight borders.
- **Refactored Audio Drag-to-Reorder**: Upgraded audio list sorting to a pointer-capture event handler system with movement thresholds, avoiding native HTML5 drag-and-drop quirks and distinguishing select clicks.

### v0.4.9 - Scene Editor Toolbar Streamlining, Workspace Docking, & Slottable Preview

- **Workspace Docking System**: Added support for docking the bottom Workspace tray to the top, bottom, left, or right margins, selectable via a quick-access header dropdown or in settings. Includes custom CSS layouts, pointer boundary resizers for side docks, and persisted localStorage dimensions.
- **Drag-and-Drop Reordering**: Implemented drag-and-drop sorting for:
  - **Scenes**: Drag handles in the Scenes tab to rearrange scene sequences.
  - **Event Cards**: Drag handles in the Event Sheet to reorder game events.
  - **Sprites**: Interactive drag-and-drop reordering inside the Sprite Editor list, styled with active dashed-border outlines.
  - **Image Assets**: Drag-and-drop reordering inside the Workspace Assets resource list.
  - **Actors/Clones**: Sidebar drag-and-drop sorting in the Scene Editor list, supporting clone-level and group-to-group reordering.
- **Slottable Actor Icon Preview**: Drag sprites from the Sprite Editor or images from Workspace Assets onto the actor preview slot in the Inspector (which highlights with glowing borders and a scale-up animation on dragover) to assign assets directly.
- **Blockly Workspace Synchronization**: Reordering events in the Event Sheet automatically repositions their corresponding logic blocks vertically in the Blockly editor to mirror the Event Sheet layout.
- **Select/Pan Tool Removal**: Removed the explicit Select and Pan toggle buttons from the Scene Editor toolbar. Panning is now handled entirely by blank-space drag (autoPan), Spacebar hold, or middle-mouse button — keeping the toolbar clean and unambiguous.
- **Scene Name in Toolbar**: Added a `scene-title-label` span at the far left of the Scene Editor toolbar showing the active scene's name, with separator border, ellipsis overflow, and dark mode support.
- **Configurable Grid Size**: Replaced the hardcoded `16px` grid with a `gridSize` prop wired through all snap calculations and major-gridline logic. A Scene Grid Size dropdown in Scene Settings (inside the Settings modal) offers 4 / 8 / 12 / 16 / 24 / 32 / 48 / 64 px options persisted in `localStorage`.
- **Constraints & Snapping Group**: Merged Lock Ratio, Grid, and Snap buttons into a single unified **Constraints and Snapping** toolbar group. Zoom buttons now use compact SVG magnifying-glass icons with accessible `title`/`aria-label` attributes.
- **Workspace improvements & adjustments**: Selecting a scene auto-expands its details row in the sidebar, scene actor counts are standardized to "X actor" or "X actors", long resource lists are truncated with ellipsis, sprite thumbnails are aligned center-center, clone index indicators (e.g. `Player (1)`) are displayed across all inspector lists and picker controls, duplicated or pasted clones are automatically placed adjacent to their sibling clones in the entities array, and a unique name generator ensures conflicts are avoided on "+ Add".
- **Accessibility & Markup Fixes**: Replaced nested `<button>` tags inside Scene Editor actor lists with keyboard-friendly `role="button"` elements to conform to ARIA guidelines.

### v0.4.8 - Assets Integration, Notifications, Sprite Editor & Dark Mode

- **Global Notification System**: Created a new React context and provider in [NotificationSystem.tsx](file:///Users/wpd/GameEngine2D/src/app/NotificationSystem.tsx) with a `useNotification` hook to allow any component to spawn alerts. Supports four severity types (`success`, `info`, `warning`, `error`) with bespoke icons, glassmorphic styles, auto-dismiss, and queue limit capping. Integrated intelligent notification deduplication and timer-refreshing to extend active toast durations rather than spawning duplicate items. Integrated toasts into key actions: asset imports, project saving/loading, previews, undos/redos, and entity creations/deletions.
- **Image Asset Integration**: Added support for selecting and importing multiple image files simultaneously, resolving them in parallel with accurate file loading counts and success/error status toasts. Added `ImageAssetSchema` and a project-level `assets[]` array for imported images. Refactored `SpriteAssetSchema` into a discriminated union (`kind: 'pixel' | 'image'`), with legacy sprites auto-defaulting to `pixel`. Updated the Renderer to draw image-kind sprites from cached `HTMLImageElement` objects, and the standalone exporter to bundle image assets into exported ZIPs.
- **Sprite Editor Dual-Mode Support**: Extended the Sprite Editor to display a full image preview with linked asset metadata for `image`-kind sprites, while preserving the pixel grid workbench for `pixel`-kind sprites. Disabled inapplicable tools (clear, pencil, eraser, bucket, eyedropper, flip, mirror, color pickers) when editing image sprites. Integrated persistent `displayScale` settings on sprite assets (defaulting to `100` for images and `200` for pixel-art) to scale entities dynamically during creation and assignments, and completely removed redundant "Updated sprite" notifications on name edits, scale adjustments, and drawing pixel changes to eliminate input typing toast noise.
- **Workspace Assets Tab Restructure**: Moved imported image assets to the top of the Assets tab as the primary content, with the project stats grid replaced by compact inline chip summaries at the bottom.
- **Expandable Scenes Management**: Made scene items in the Workspace Scenes tab expandable inline. Integrated a live **Background Color** picker (using the custom `ColorPicker`) to update scene color tags dynamically in the Scene Editor and Game Preview. Displayed read-only size dimension and actor count metadata. Added "Add Scene" toolbar action, active scene switching focus controls, and safety-validated "Delete Scene" options.
- **Populated Game Samples**: Populated default projects (`Collect Coins` and `Dodge Enemies`) with playable multi-scene level progressions (Level 2, victory, game over screens).
- **Condition Sequence Editor**: Added styled condition sequence layout with AND/OR operator pills (green/orange), hover lift animations, and dark mode support.
- **Blockly Dark Mode Widget Theming**: Comprehensive dark mode overrides for Blockly context menus, dropdown divs, widget menus, menu items, and inline inputs using the slate dark palette.
- **Mobile Preview Scene Editor Layout**: Aligned the Preview's Scene Editor with the Editor's scene tab on mobile viewports for consistent full-height behavior.

### v0.4.7 - Timers, Logical Grouping, Resizing & Touch Gestures

- **Logical AND/OR nested conditions**: Supported recursive logical operators (`all` / `any`) and arrays of conditions, with interactive headers, drag-and-drop/arrows reordering, and sub-condition modal management.
- **Timers, Cooldowns & Trigger Blocks**: Added condition blocks for `timerEvery` (Every X seconds), `timerAfter`, `cooldownReady`, `variableChanged`, `actorVisible`, `actorOutsideScene`, `distanceBetween`, and `randomChance`.
- **Mathematical Variable Update Actions**: Supported operators `add`, `subtract`, `multiply`, `divide`, and `remainder` in variable updates.
- **Scene Editor Mobile Touch Gestures**: Programmed pinch-to-zoom, double-touch quick zoom, and long-press touch triggers to open context menus for actors and empty stage grid areas on mobile/tablet viewports.
- **Context Menus & Keyboard Shortcuts**: Built Ctrl/Cmd + C / V copy-paste shortcuts for actors, empty workspace context menus, and expanded the actor context menu with "Inspect" and "Copy" options.
- **Actor Clone Hierarchy Indentation**: Refined the sidebar list to only show indentations and expand toggle buttons if an actor has instantiated clones, saving valuable horizontal space.
- **Floating Actor Panel Multi-Corner Resizing**: Added `panelSize` state to track custom dimensions, rendered absolute-positioned handles for all 4 corners (`tl`, `tr`, `bl`, `br`), and implemented 2D resizing formulas to update position (`x`/`y`) and size (`width`/`height`) relative to the opposite anchor corner.
- **Default Preview Tab Selection Configuration**: Added a new setting `preview.defaultTab` (options: Standard, Scene Editor, Event Sheet) in the Settings modal under the "Preview Settings" tab, dynamically initializing the active tab on launcher startup.
- **Mobile Solo Height Fix**: Configured responsive styling overrides so that when the Logic Blocks Editor is soloed on mobile viewports, the Blockly workspace container expands dynamically to full screen viewport height (`calc(100vh - 40px)`) instead of staying locked to `480px`.
- **Mobile Preview Scene Editor Height Adjustment**: Aligned Preview's Scene Editor styling with the Editor's Scene tab under the `@media (max-width: 860px)` breakpoint. Configured `.preview-pane.is-tab-scene` to occupy `calc(100vh - 40px)` / `calc(100svh - 40px)` with a minimum height of `540px` and enabled all intermediate wrapper containers (pane body, tab container, and scene editor) to use `height: 100% !important; overflow: hidden !important` with `flex: 1 1 auto !important`. This ensures the canvas stage expands fluidly to fill the available height and shares space proportionally with the Actors list on mobile vertical stacks.

### v0.4.6 - Block Locator Navigation & Tablet Alignment

- **Block Locator & SVG Ping Navigation**: Added target locator buttons (`.locate-function-btn`) next to "Event" and "Function" dropdown selectors in the Inspector and Event Card headers to center the Blockly workspace on the target block, applying a custom flash animation (`.block-ping-flash`) on the block group elements.
- **Mobile/Tablet Viewport Sizing & Layout Fixes**: Configured dynamic CSS class overrides to keep the stage canvas stable at `360px` height on mobile/tablet viewports, and enabled active panels and Blockly Editor container bodies to stretch and scale fluidly to fill the screen layout space.

### v0.4.5 - Preview Panel Tabs & Synchronized Clones

- Added tab buttons `[ Standard | Scene Editor | Event Sheet ]` inside the Preview pane header, controlled by a new state `previewTab`.
- Implemented the **Scene Editor** tab showing a cloned instance of the `<SceneEditor>` component, fully synchronized in real-time with selections and updates from the parent App context.
- Implemented the **Event Sheet** tab showing a solo Event Sheet view utilizing the `renderEventSheetViewer` helper with `showJavaScriptToggle = false` to render only the pure interactive event sheet cards.
- Configured Actors Panel visibility controls to work independently per pane (Editor vs. Preview), using separate visibility state parameters.
- Restored the original beautiful two-column event list layout containing the `conditions-column` and `actions-column` styling to align with the application's default theme design.
- Added layout and tab containment CSS styles inside `src/App.css`.

### v0.4.3 - Actor Scaling & Aspect Ratio Lock

- Added `scaleX` and `scaleY` parameters to the `EntitySchema` defaulting to `1`.
- Added a **Lock Ratio** toggle button next to the **Select** and **Pan** tool buttons in the Scene Editor toolbar.
- Enabled aspect ratio locking inside the Konva `Transformer` resizing boundary controls when the Lock Ratio tool is active.
- Configured Konva `<Group>` containers representing entities in the Scene Editor to use `scaleX` and `scaleY` dynamically, scaling all actor elements, colliders, and borders.
- Updated `handleTransformEnd` to read Konva node scales, snap them to the grid, and write `scaleX` and `scaleY` directly into the entity updates while preserving base `width`/`height` variables.
- Added **Scale X** and **Scale Y** input fields underneath Width and Height in the Actor properties tab, allowing manual control over rendering scales. These inputs automatically adjust the actor's coordinates to scale from the center by default.
- Added scaling preprocessors inside `createRuntimeEntities` (both preview and standalone game player) and `createSprite` event sheet actions. This applies scaling factors directly to `width`, `height`, and collider dimensions/offsets prior to entering the physics engine, guaranteeing physics compliance without breaking existing runtime gameplay logic.
- Updated the entity resolution mechanism (`findEntities`) in both the preview runner and the exported standalone script. If a target name doesn't match an individual actor name/ID, it falls back to matching by group names directly. This allows actions (like `destroy "players"`) to target all actors belonging to the group.

### v0.4.2 - Play Mode Gamepad & Groups Manager

- Added a touch/mouse controller in external Play Mode windows, styled below the canvas, with settings configuration and custom gamepad keybindings integration.
- Added a dedicated **Groups** tab in the Inspector panel.
- Implemented a list display showing all unique actor groups in the active scene alongside their member actor count, with support for selecting a group to rename it, manage member actor checkboxes, and delete custom groups.
- Provided an **Add Group** action button to register new custom groups, pre-populating five locked default groups (`enemies`, `hazards`, `items`, `players`, `obstacles`) by default.
- Replaced the quick-edit Groups text field on the individual Actor page in the Actors tab with a simplified select dropdown and interactive tags (chips with ✕ remove button).
- Formatted target dropdown selections and card details to render clean, friendly group names.
- Optimized JSON and JavaScript code generation by integrating `stringifyWithCollapsedPixels` in the standalone exporter to collapse the multi-line pixel color arrays inside the exported `project.json` file.
- Replaced the text-based "Expand" and "Collapse" buttons in the Game and Event sections of the Preview panel with compact, space-saving SVG Chevron icons, and added a **Solo** button to expand one section and collapse the other.
- Added a new option **Default Blocks Inspector Mode** under the Inspector Settings tab (options: `Simple Mode`, `Advanced Mode`).

### v0.4.1 - Settings Popup & PWA

- Added a Settings popup modal covering General, Editor, Preview, Bindings, Inspector, and Workspace preferences.
- Added **General Settings** toggles to show/hide Undo/Redo buttons and the Dark Mode button.
- Implemented **Theme Mode** selection (`Auto`, `Light`, `Dark`). `Auto` mode dynamically tracks system color preferences.
- Added **Editor Settings** to configure default visibility, default tab selection on startup (`Logic Blocks`, `Scene Editor`, `Sprite Editor`), and default grid visibility.
- Moved the **Actors Panel Dock Position** dropdown selector from the Scene Editor header to a new **Scene Settings** tab inside the Settings modal.
- Moved the **Auto-Apply** (Auto On / Auto Off) toggle button from the Game Preview panel header to a new checkbox option "Automatic preview apply" inside the **Preview Settings** tab.
- Added **Inspector & Workspace Settings** to configure default visibilities.
- Implemented a **Reset to Defaults** button in the Settings modal footer to restore all options back to factory configuration.
- Integrated PWA capabilities using `vite-plugin-pwa` to enable installation on mobile and desktop home screens.
- Generated PWA assets including `icon-192.png` and `icon-512.png` matching the official logo.
- Configured a Service Worker (`sw.js`) to cache core HTML/JS/CSS assets for offline availability.
- Replaced the temporary SVG favicon with the new official textless logo PNG file (`favicon.png` and `apple-touch-icon.png` for iOS home screen bookmarks) across the creator app and landing page templates.
- Eliminated white background flashes on initial reload/refresh by introducing synchronous inline theme-initialization script inside `index.html`'s `<head>`.

### v0.4.0 - Actor Groups & Group Targeting

- Added `groups` to actor schema data, defaulting existing actors to an empty group list for backward compatibility.
- Added a Groups field and visual group chips to the Actor Inspector.
- Added group-aware target dropdowns in the Blocks Inspector and Event Sheet modal for actions and collision conditions.
- Implemented `group:name` target selectors in the runtime so one action can affect every matching actor.
- Added group-aware collision checks so collision and collision-started conditions can match any actor in a target group.
- Updated standalone exported games with the same group target and group collision behavior as the editor preview runtime.
- Added tests covering actor group schema validation, group destroy actions, group collision conditions, and standalone exporter coverage.
- Decoupled the bottom Workspace tray's preferred height state from layout clamping constraints, calculating bounds dynamically on render to prevent the panel from getting permanently stuck at its minimum height (80px).
- Added an auto-stretch CSS layout rule to let the Workspace tray fill the viewport height when the three main editor panels are closed on desktop and tablet, pushing the Status footer to the bottom.
- Added auto-migration to automatically upgrade old default or shrunked stored heights (`<= 140px`) to `200px` on startup.
- Fixed Blockly controls clipping on pane resizing by letting the Blockly host scale down to `min-height: 0`.

### v0.3.5 - Retro Audio Synthesizer, Workspace Function Definitions, Deep Parameters & Diagnostics, and Sprite Upgrades

- Implemented programmatically generated 8-bit retro sound synthesis (`coin`, `jump`, `laser`, `hit`, `explosion`, `powerup`) powered by the Web Audio API with zero external file asset overhead.
- Built a **Retro Synthesizer Playground** in the Sounds tab, complete with sliders for waveform selection, base/target frequencies, and duration, alongside a copy action to copy generated synth strings to the clipboard.
- Added a **`synth:` Protocol** (`synth:waveform:startFreq:endFreq:duration`) supporting dynamically synthesized frequency sweeps in the preview runtime and standalone exported HTML games.
- Updated the Blockly `playSound` block and the inspector action pane to offer preset dropdown selectors, with a custom text field fallback for pasting raw `synth:` codes.
- Added a visual **Define Function** block (`phase_function_definition`) to allow layout and creation of custom reusable function action stacks on the Blockly workspace.
- Upgraded the **Call Function** block to use a dynamic dropdown selector (`FunctionDropdown`) populated from functions currently defined on the workspace.
- Added support for custom functions to take dynamic arguments/parameters.
- Supported configuring parameters (names, types, default values) in the function inspector, allowing events and functions to pass arguments on call.
- Integrated parameter reference compilation in the compiler and standalone interpreter, evaluating variables/arguments correctly at runtime.
- Re-architected and moved function diagnostics into a dedicated analysis engine ([functionAnalysis.ts](file:///Users/wpd/GameEngine2D/src/app/functionAnalysis.ts)).
- Implemented static analysis checkups for function parameters and call arguments:
  - `missing-argument`: Warnings when a declared parameter is omitted in a call.
  - `stale-argument`: Warnings for arguments that are no longer declared on the function.
  - `argument-type`: Warnings when argument types do not match parameter declarations.
  - `unused-parameter`: Warnings when declared parameters are not used inside the function body.
  - `parameter-reference`: Warnings for referencing missing/deleted parameters.
- Extended trace logging to track exact call-site locations including nested conditional statements (e.g. `action 1 / then 1 / else 2`).
- Wrote full unit test coverage for analysis warnings in [functionAnalysis.test.ts](file:///Users/wpd/GameEngine2D/src/app/functionAnalysis.test.ts).
- Added an **Eyedropper Tool** to the Sprite Editor to sample active colors directly from any pixel in the drawing canvas.
- Added **Mirror X (Horizontal Symmetry)** and **Mirror Y (Vertical Symmetry)** options for pixel-drawing and bucket flood-fills in the Sprite Editor.
- Upgraded the target actor dropdown selection with live thumbnails and color previews next to actor names.
- Displayed diagnostics badges next to function names in the left-hand assets list panel.
- Added an **Open** button next to the `callFunction` block in the Event Sheet to quickly jump to the function definition in the inspector workspace.
- Implemented `resizeEntityCollider` to scale offsets, width/height, and radius values automatically when resizing actors visually in the Scene Editor.
- Updated schema definitions to make custom collider offsets/dimensions optional rather than defaulting to hardcoded values, preventing default dimensions from populating on all actors.


### v0.3.4 - Custom Colliders, Color Pickers, & Visual Fixes

- Extended the Actor Schema with custom collider fields: type (`box`, `circle`, or `none`), offset values (X/Y), dimensions (Width/Height), and Circle Radius.
- Built a **Collider Settings** section in the Actor Inspector panel supporting dropdown switching, and contextual input layouts (e.g., hiding offsets and size adjustments when `None` is selected to keep layouts clean).
- Upgraded the physics engine's `areEntitiesColliding` intersection logic (and the standalone exporter template) to check **Box vs Box**, **Circle vs Circle**, and **Box vs Circle** geometries, using squared-distance checks to optimize execution.
- Added a **None** collider option that completely disables visual collider outlines and bypasses all collision checks, allowing decorative background actors to be passed through.
- Configured the **Colliders** checkbox in the scene view to default to `true` (checked) at startup.
- Cleaned up inline styles on the collider select dropdown and text fields to inherit global theme classes, making them adapt natively to dark mode.
- Upgraded the custom color picker panel to support HSVA coordinates with rainbow Hue and checkerboard Alpha transparency range sliders.
- Replaced native browser/OS color dialogs with the custom floating HSVA `<ColorPicker>` popover across both the Actor Inspector and the Scene Editor toolbar.
- Relocated collider debug outline rendering from the canvas game preview (`Renderer.ts`) directly into the interactive Scene Editor stage (`SceneEditor.tsx`).
- Connected collider borders inside each actor's Konva group container to automatically scale, rotate, and move in sync with edits, rendering as a `<Rect>` or `<Circle>` based on shape.
- Replaced the heavy `#0f172a` unselected border around all canvas actors with a transparent outline for sprite assets and a light placeholder border for sprite-less shapes.
- Fixed a color picker parsing bug where invalid/empty input strings would reset the panel value and lock it to green.

### v0.3.3 - Sprite Editor Upgrades, Fixes, & Inspector Modes

- Relocated dedicated Color presets section to the top of the workbench as a full-width ribbon below the toolbar.
- Refactored swatches and custom picker to compact 24px x 24px rounded squares with flex-shrink to prevent stretching/squashing.
- Fixed empty grid previews on list thumbnails in the sidebar and inspector by explicitly adding gridTemplateRows and styling child spans as block-level elements filling 100%.
- Prevented sub-pixel thumbnail grid collapsing by separating text labels into `.sprite-asset-metadata` and setting `gap: 0` on the thumbnail.
- Implemented a Paint Bucket (flood fill) tool powered by BFS, and styled tools with Pencil, Eraser, and Paint Bucket SVG icons.
- Added a persistent green circle Default Sprite restored automatically when the asset list becomes empty.
- Added Simple and Advanced toggle tab modes to the Blocks Inspector, displaying a plain-English event summary or detailed parameter forms.
- Configured TypeScript to tolerate unused locals for smoother dev builds.

### v0.3.2 - Actors Docking, Tablet Layouts, & Rebranding

- Renamed the project from PickleBlocks to PickleBlocks.
- Added Actors panel docking dropdown selector in the Scene Editor supporting Left, Right, Top, and Bottom options.
- Added tablet CSS grid layout stack overrides to dynamically balance Stage, Preview, and Inspector panels.
- Optimized mobile top header layout button spacing and padding to fit narrow viewport widths.
- Polished Blocks Inspector layout to display the Selected Block card at the top, side-by-side with the Enabled checkbox.

### v0.3.1 - Play Window Polish & Nested If Editing

- Added a top-bar Play workflow that opens the current project in a separate playable browser window.
- Stopped the embedded Preview automatically when Play mode launches so editor preview and player mode do not compete.
- Reused the named Play window on repeated launches, refreshing it with the latest project data.
- Added editor-side tracking for the external Play window so the Game panel can show "Play window open".
- Added standalone player header polish with Play Mode labeling, Restart, Close, and automatic canvas focus for keyboard controls.
- Prevented Space from scrolling the standalone player page and tightened the player window chrome so the game canvas gets more room.
- Added recursive Event Sheet editing for nested `If` actions inside Then/Else branches.
- Added branch-level `+ Action` and `+ If` controls for building deeper event logic visually.
- Updated nested action selection, editing, reordering, and deletion so the popup editor can target actions at deeper branch paths.
- Updated the default editor ready status and project metadata to `v0.3.1`.

### v0.3.0 - Event Sheet System & Blockly Multi-Condition Support

- Upgraded the Event Sheet to a fully interactive card-based editor supporting enabled toggles, inline renaming, and deletions.
- Implemented dedicated centered popup configuration modals for editing conditions and actions, removing reliance on the Inspector.
- Added nested visual layout rendering for conditional If blocks, supporting sub-action lists for both Then and Else branches.
- Enabled HTML5 drag-and-drop reordering for actions and sub-actions, alongside compact side-by-side Up/Down arrows.
- Added a "Minimize Events" / "Expand Events" toolbar toggle to collapse/expand all cards at once and moved the "+ Add Event" button to the tab header to optimize vertical layout space.
- Deprecated individual event-hat blocks in favor of a single generic `when [CONDITIONS] do [ACTIONS]` event block in Blockly.
- Added stackable condition blocks (Start, Update, Key Down, Collision, Collision Started, Variable Compare) that snap together vertically inside the conditions slot of the generic event block.
- Updated the compiler, workspace factory seeding, and editor selection listener to compile, rebuild, and synchronize multiple conditions per event.
- Added diagnostic compile warning messages for event blocks containing zero conditions.
- Updated the unit tests suite to compile multiple chained conditions and verified all 20 tests pass.

### v0.2.0 - Phase 3 Scene Editor, Rotation, and UI Optimizations

- Integrated `react-konva` for a visual 2D scene editor tab supporting entity selection and transform controls.
- Added Select (transform) and Pan tools to navigate the editor viewport.
- Added canvas grid rendering and 16px snapping toggle controls.
- Added viewport zoom-in, zoom-out, and fit-view controls.
- Added a `rotation` property to entity schema and supported rotated rendering in the Canvas 2D runtime and standalone exporter.
- Added **Undo / Redo** history controls to the top toolbar.
- Renamed all user-facing occurrences of **Entities** and **Entity** to **Actors** and **Actor** (in inspector tabs, dropdown selectors, empty status placeholders, and resource counts).
- Unified and shrunken all utility panel buttons, collapse toggles, top toolbar actions, and dropdown selections to a cohesive **26px** height (and inner tab buttons to **20px** height).
- Repositioned the **Game**, **Event**, and **Inspector** subtitles horizontally next to their headers to reclaim vertical space and simplified their styles.
- Added conditional sibling margin spacing to ensure proper gaps between panels when the main editor workspace is completely hidden.
- Implemented a split canvas selection lock so inspector focus locking doesn't block visual canvas transformations (drag, resize, rotate).
- Replaced the Inspector locked/unlocked text toggle button with minimal, color-coded SVG lock icons.
- Centered the `[Run, Stop, Restart]` buttons in the Game preview header using CSS Grid.
- Added a "Hide" button to the bottom Workspace panel header.
- Added white, gray, and black to the Actor Inspector color preset swatches (11 presets total); fixed swatch shapes to render as perfect circles.
- Fixed all three main panels (Editor, Preview, Inspector) to be fully horizontally resizable: horizontal resizer handles are now direct layout siblings in the workspace gap, enabling drag on the Editor's right edge, both Preview edges, and the Inspector's left edge.

### v0.1.4 - Primitive Variables, Console Logging, Workspace Renames, and Resizable Layout

- Added support for typed global variables (number, boolean, string) with dynamic input controls, type badges, and creation dropdowns in the Inspector.
- Fixed sizing issue in Globals Inspector to allocate proper space to variable name inputs.
- Renamed "Project" to "Workspace" across top navigation menu toggles and the bottom panel.
- Added a toggleable, clearable, auto-scrolling log console in the Status footer for runtime events and diagnostics.
- Added persisted resizing for the main editor panes, Workspace tray, and Status footer.
- Changed main pane resizing to use invisible pane-edge grab targets while preserving visible spacing between Editor, Preview, and Inspector.
- Added persistent Locked/Unlocked state for the Blocks Inspector selection behavior.
- Introduced a new "print to console" Blockly block for runtime message logging.
- Fixed event interpreter double-execution bug where startup events were running twice during preview start.
- Enhanced the Blockly compiler and standalone exporter to correctly support primitive variable types and template string escaping.

### v0.1.3 - Theme, Spacing, and Cleanups

- Added persistent dark and light theme options, toggled by an icon-only button in the top-right header.
- Cleaned up the Inspector panel by removing redundant read-only event and block ID fields.
- Integrated "Event ID" into the "Selected Block" summary details list.
- Made the "Selected Block" summary collapsible and hidden by default, moved to the bottom of the Blocks Inspector.
- Styled Inspector detail suffixes (e.g., "- X globals") to render lighter (non-bold) and italic.
- Renamed "Blocks" to "Editor" in navigation controls, and added "Logic Blocks" and "Scene" placeholder tabs to the Editor header.
- Simplified the Preview section header by removing the subtitle.
- Fixed dark mode overrides on Blockly category flyout colors (preventing block shape color loss).
- Restored and styled Blockly grid dots in dark mode, and added a toolbar toggle to show/hide the grid.

### v0.1.2 - Live Editing And Sync

- Added the Game preview Auto toggle for live apply versus pending manual restart.
- Split editor draft state from the running preview snapshot.
- Added runtime hot-swapping so event-only changes can apply while the game keeps running.
- Preserved running entities, variables, input, and collision state during event-only updates.
- Synced Event Sheet `On` checkboxes with Blockly's native disabled block state.
- Greyed disabled event blocks in Blockly using Blockly's built-in disabled styling.
- Updated the compiler so disabled Blockly event blocks compile to `enabled: false`.
- Tightened the Event Sheet `On` column so checkbox controls use less space.
- Added tests for runtime hot-swapping and disabled block compilation.

### v0.1.1 - Editor And Runtime Depth

- Reworked the editor into left Blocks, center Preview, and right Inspector panes.
- Added collapsible Game/Event sections and vertical Preview resizing.
- Added desktop pane resizing for open editor views.
- Split the runtime into focused modules for game orchestration, scenes, entities, input, collision, rendering, and event interpretation.
- Added Event Sheet and generated JavaScript tabs.
- Added Inspector add/delete/edit workflows for scene entities.
- Added Dodge Enemies as a second built-in sample.
- Added more sprite/game actions and `collisionStarted`.

### v0.1.0 - First Phase 1 Checkpoint

- Added Blockly-first event scripting.
- Added the structured PickleBlocks project/event model.
- Added Canvas 2D runtime preview.
- Added Collect Coins sample project.
- Added JSON save/load and standalone ZIP export.
- Added responsive, collapsible first-pass editor panes.

## Development

Install dependencies:

```bash
npm install
```

Start the local dev server:

```bash
npm run dev
```

Run checks:

```bash
npm run lint
npm test
npm run build
```

Build the GitHub Pages version locally:

```bash
GITHUB_PAGES=true npm run build
```

## Project Structure

- `src/app` - React editor components
- `src/blocks` - Blockly block definitions, toolbox, and workspace loading
- `src/compiler` - Blockly to PickleBlocks project compiler
- `src/engine` - Canvas 2D runtime, scene/entity logic, input, collision, rendering, and event interpretation
- `src/examples` - built-in sample projects
- `src/exporter` - standalone ZIP export support
- `src/schemas` - project schema and validation

## Versioning And Progress

This project started at `v0.1.0` as the first public development checkpoint.

Current release:

- `v0.5.2` - Sprite Editor Animation Mockup preview player tab, onion skinning visual overlays, pixel marquee selection tool, context clipboard/rotation canvas menu actions, interactive duration stretching, compact sidebar settings play controls, stage entity reset actions, side-by-side context button layouts, footer console log checkbox styling refinements, dark mode color scheme integration, browser Gamepad API and low-level WebHID controller fallback support (Switch, PS4, Xbox), custom antialiased native checkbox styling, and Collect Coins character dashing

Recent checkpoints:

- `v0.5.1` - Dynamic motion action targets & value references, collapsible entity list sidebar sections, Blockly drag performance optimization, Searchable Add Block popup menu, custom dual-tone green condition blocks styling, Logic Blocks Default Drag Mode (single block or full stack dragging options), ESLint config rules alignment & codebase cleanups (obsolete prop wrappers removal, named event handlers conversion), UI system implementation (interactive buttons & transparent labels), pointer click input & events, Dodge Enemies & Collect Coins sample upgrades, custom standalone project screen resolution, camera target tracking & lerp smoothness, separate scene map size scroll limits, global variable drag-sorting, Workspace tab layout spacing optimizations, Project scene tags double-click locating, unified decorative Props under Entity schema (`kind: 'prop'`), legacy prop migration, `.pickleblocks` file saves & Ctrl/Cmd+S shortcut, default workspace tab preferences, Scene Editor sidebar filters, Sprite Editor target filters (supporting UI entities) & Trash Icon canvas clearing, compact spacing adjustments, Global Variables/Groups workspace migration, draggable workspace tabs, panel header solo/maximize controls, visual value expression field selectors (nested operator operands and variables/actors/props/UI/groups dropdowns), generic `expressionCompare` Condition type ("Expression Check") editing, global variable drag-and-drop workspace spawning, Enable Editor Sounds preference setting, repeat loop action support in compiler and standalone game builds, visual loop action container boxes inside the Event Sheet (repeat & forEachActor), unified dropdown action select pickers, updateVariable arithmetic actions, stage and actor context camera target settings with toast feedback, and inspector lock overrides for newly created objects

- `v0.5.0` - Custom audio import & HTML5 audio library, workspace audio player with waveform/level meter, image asset "Ping Sprite" tool, actor focus camera utility, upgraded 4D joystick system, blocks toolbox sidebar toggle, double-click/context solo controls, topbar toolbar context hiding, app header context menus, editor-wide context prevention, congruent premium tab panel redesigns, built-in scene tagging & conditions, Workspace Assets consolidation, and Blockly viewport stability improvements

- `v0.4.9` - Workspace docking system, slottable actor previews, comprehensive drag-and-drop reordering (scenes, events, sprites, images, actors), grid and constraints updates, accessibility enhancements, and workspace improvements
- `v0.4.8` - Full image asset integration, global notification & toast system, improved Sprite Editor, Workspace Assets tab restructure, condition sequence editor, and Blockly dark mode widget theming
- `v0.4.7` - Timers, logical AND/OR grouping, floating panel resizing, and mobile touch gestures
- `v0.3.5` - Retro Audio Synthesizer, visual function definitions, custom function parameters, deep diagnostics, and Sprite Editor upgrades
- `v0.3.4` - Custom colliders, color pickers, centered box collider fixes, and visual cleanup
- `v0.3.3` - Sprite Editor upgrades, Paint Bucket, full-width color ribbon, list thumbnail collapse fix, and simple/advanced Blocks Inspector mode
- `v0.3.2` - Actors panel docking, tablet layout stack priorities, mobile top bar optimizations, and PickleBlocks rebranding
- `v0.3.1` - Play Window polish, separate playable browser launch, and nested Event Sheet If editing
- `v0.3.0` - Event Sheet System and Blockly multi-condition support
- `v0.2.0` - Phase 3 Scene Editor, rotation support, and UI layout optimizations
- `v0.1.4` - Primitive variables, debug console log, workspace rename, and resizable layout pass
- `v0.1.3` - Theme customizations, layout enhancements, and inspector simplifications pass
- `v0.1.2` - Phase 1 live-editing and Event Sheet synchronization pass
- `v0.1.1` - Phase 1 editor/runtime depth pass
- `v0.1.0` - First public development checkpoint

Future work should continue updating `CHANGELOG.md` so progress is easy to review over time. Each checkpoint should make it clear what changed in the engine foundation, editor UX, event model, runtime behavior, and sample projects.

## Near-Term Direction

- Keep improving the visual event workflow without hiding the generated model
- Expand entity and scene editing beyond the first inspector fields
- Add Planck physics behind a `PhysicsWorld` adapter so the runtime can support richer 2D physics without coupling project logic directly to a third-party API
- Add Capacitor export templates for iOS and Android builds from the existing standalone web runtime
- Add Tauri export templates for macOS, Windows, and Linux desktop builds from the same standalone web runtime
- Add more actions and conditions to make small games possible faster
- Improve runtime correctness around collisions, scoring, restart behavior, and scene bounds
- Continue tightening the editor layout so it feels stable during resizing and pane collapse

## Product Name

The product name is **PickleBlocks**.
