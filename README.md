# HA Desktop Widget

A semi-transparent desktop widget for Home Assistant that provides quick access to your smart home devices from your desktop.

[![CI](https://github.com/Robertg761/HA-Desktop-Widget/actions/workflows/ci.yml/badge.svg)](https://github.com/Robertg761/HA-Desktop-Widget/actions/workflows/ci.yml)
[![Release](https://github.com/Robertg761/HA-Desktop-Widget/actions/workflows/release.yml/badge.svg)](https://github.com/Robertg761/HA-Desktop-Widget/actions/workflows/release.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Downloads](https://img.shields.io/github/downloads/Robertg761/HA-Desktop-Widget/total?color=blue&label=downloads)](https://github.com/Robertg761/HA-Desktop-Widget/releases)

- Download: https://github.com/Robertg761/HA-Desktop-Widget/releases

- [![GitHub Sponsors](https://img.shields.io/badge/Sponsor-me-orange)](https://github.com/sponsors/robertg761)

![Main View](images/Main_View.png?v=20260601) ![Edit View](images/Edit_View.png?v=20260601) ![Light Adjust](images/Light_Adjust.png?v=20260601)

## Settings: Personalization

![Personalization Tab](images/Personalization_Tab.png?v=20260601)

The Settings modal is organized into General, Personalization, Hotkeys, Alerts, and Advanced. Personalization covers color themes, window effects, weather animations, primary cards, custom entity icons, and media tile selection. General includes Home Assistant connection, window behavior, language packs, profile sync, and update checks.

## Weather Effects

![Rain Effect](images/Rain_Effect.png?v=20260601) ![Snow Effect](images/Snow_Effect.png?v=20260601)

## Features

### Smart Home Control

- **Real-time Updates**: WebSocket connection for instant entity state changes
- **Quick Access Dashboard**: Customizable grid of your most-used entities
- **Entity Management**: Add, remove, rename, and reorder entities with drag-and-drop
- **Desktop Pins**: Pin selected Quick Access entities as movable, resizable desktop tiles
- **Custom Names & Icons**: Rename entities and override entity icons without changing Home Assistant
- **Tile Options**: Adjust selected Quick Access readout sizing for dense or prominent tiles
- **Camera Tile Previews**: Opt into a visibility-scoped authenticated HLS stream or snapshots, then click the tile to grow that same feed into a larger view and reconnect a stale camera session when needed
- **Interactive Controls**: Toggle lights, switches, scenes, and more with a single click

### Modern Interface

- **Rainmeter-style Design**: Clean, transparent desktop widget aesthetic
- **Responsive Layout**: Auto-sizing tiles that adapt to content
- **Dark/Light Themes**: Automatic theme switching based on system preferences
- **Color Personalization**: Built-in and custom accent/background colors with live preview
- **Weather Effects**: Optional subtle rain, snow, clouds, sun, and storm animations when frosted glass is enabled
- **Smooth Animations**: Fluid drag-and-drop and hover effects
- **Toast Notifications**: Real-time feedback for all actions

### Entity Support

- **Lights**: Toggle on/off, brightness control, and desktop-pin brightness presets
- **Switches, Fans & Input Booleans**: Simple on/off controls, with fan speed controls where available
- **Covers & Locks**: Open/close and lock/unlock controls
- **Sensors & Binary Sensors**: Real-time value display with units and state-aware icons
- **Timers**: Live countdown displays for active timers
- **Cameras**: Optional Quick Access snapshots plus live feed viewing with snapshot fallback
- **Climate**: Temperature display and control
- **Media Players**: Play/pause, previous/next, artwork, seek bar, and 10-second rewind/fast-forward where supported
- **Scenes, Scripts & Buttons**: One-click scene activation, script running, and button/input-button pressing
- **Automations**: Trigger, toggle, enable, or disable from configured hotkeys

### Advanced Features

- **Updates**: Automatic installation for Windows installer and Linux AppImage builds; portable, macOS, and Linux deb builds use a GitHub Releases download flow
- **System Tray**: Minimize to tray with quick access menu
- **Start at Login**: Optional OS login startup control
- **Configuration**: Native Home Assistant browser authorization; legacy access-token setup remains available as an advanced fallback
- **Performance**: Optimized rendering and memory management
- **Cross-Platform**: Windows x64, universal macOS (Intel and Apple Silicon), and Linux x64 support with transparency effects where available
- **Personalization**: Accent/background themes, custom colors, window opacity, frosted glass, weather effects, custom icons, and desktop pins
- **Localization**: Auto/system language mode with downloadable offline language packs
- **Hotkeys**: Global entity hotkeys and popup hotkey to bring the window to front
- **Alerts**: Desktop notifications for entity state changes
- **Primary Cards**: Configure the top two cards (weather/time or any entity)
- **Comparison Graphs**: Plot several entities on one 24-hour chart to compare them at a glance (e.g. every room temperature against the outside temperature)
- **Media Tile**: Choose a primary media player or hide the tile
- **Profile Sync (Opt-in)**: Keep personalization/settings in sync across devices via a shared cloud-folder JSON file

## Roadmap

Planned for a future release:

- **HA Assist voice**: A microphone button wired to Home Assistant's Assist pipeline (speech-to-text → intent → text-to-speech) so you can talk to your smart home from the desktop. Deferred as a standalone update because it needs the full HA server-side audio pipeline and real device testing.

## Quick Start

### Download & Install

1. Go to the [Releases](https://github.com/Robertg761/HA-Desktop-Widget/releases) page and download the latest available build for your OS.
2. Windows: run the `.exe` installer or portable build. macOS: open the universal `.dmg` or `.zip` (older releases may be Apple Silicon-only). Linux: use the `.AppImage` or install the `.deb` package.
3. Run the app and click the Settings button to configure your Home Assistant connection.

> **macOS Gatekeeper notice:** Current macOS artifacts are universal, but they are
> temporarily not Apple Developer-ID signed or notarized. macOS may block the first launch
> because it cannot verify the developer. For a copy downloaded from this project's official
> GitHub Releases page, Control-click the app and choose **Open**; if needed, go to **System
> Settings > Privacy & Security** and choose **Open Anyway**. The package's ad-hoc integrity
> signature is not a substitute for Developer-ID signing. Do not bypass Gatekeeper for copies
> obtained elsewhere.

### First-Time Setup

1. **Get your Home Assistant URL**: Use the exact address you normally open in your browser, such as `http://homeassistant.local`, a legacy `http://your-ha-ip:8123` address, or `https://your-ha-domain.com`
2. **Connect the widget**: Enter that URL and click **Connect**. The app opens Home Assistant in
   your system browser so you can sign in and approve it; your Home Assistant password never enters
   the desktop app.
3. **Return to the widget**: Authorization finishes through a temporary loopback callback on this
   computer and live updates start automatically. If you change your mind, **Cancel** next to the
   connect button stops waiting and closes the loopback callback.
4. **Add entities**: Click the "+" button to add your favorite entities to Quick Access.

The legacy long-lived access-token form remains under **Settings > Legacy access token
(advanced)** for compatibility. New setups should use browser authorization.

### Home Assistant Companion Integration

The optional `HA Desktop Widget Companion` custom integration makes registered desktops visible as
native Home Assistant devices and supports `show`, `hide`, `toggle`, `switch_page`, and
`apply_profile` actions. The desktop uses the same authenticated Home Assistant WebSocket
connection for registration, state reporting, command delivery, and acknowledgements. It never
accepts arbitrary shell commands, JavaScript, file access, URLs, or generic Electron IPC from
Home Assistant.

`apply_profile` applies a named profile authored in Home Assistant: a bounded configuration
document covering appearance (theme, accent, background, opacity, frosted glass), primary cards,
Quick Access pages and tiles, comparison graphs, custom icons, and tile options. Profiles never
carry credentials, hotkeys, window geometry, desktop pins, or file-sync settings; those stay
local to each machine. The desktop reports which profile revision it last applied so Home
Assistant can flag out-of-date desktops.

> [!NOTE]
> A Home Assistant profile overwrites the sections it contains. If the folder-based profile sync
> feature is also enabled for the same sections, whichever mechanism writes last wins — avoid
> managing the same settings with both at once.

## How to Use

### Quick Access Management

- **Add Entities**: Click the "+" button to search and add entities to your dashboard
- **Reorder**: Click the Reorganize button to enter reorganize mode, then drag and drop to reorder
- **Rename**: In reorganize mode, click the edit icon to set custom display names
- **Camera Previews**: Edit a camera tile to choose an HLS live feed or a 30-second, 10-second, or 5-second snapshot cadence; previews pause while the app or tile is hidden, clicking expands the current feed without restarting it, and the expanded live view includes a Reconnect action for stale sessions
- **Remove**: In reorganize mode, click the remove button to remove entities
- **Pin to Desktop**: In reorganize mode or the tile context menu, pin supported Quick Access entities as standalone desktop tiles

### Comparison Graphs

- **Create**: Click the "+" button, then **Add comparison graph**
- **Pick entities**: Add up to 7 numeric sensors. Weather and climate entities can be graphed too — a weather entity contributes the **outside temperature** (search "outside" to find it, even though it is usually named after the integration, e.g. "Forecast Home")
- **Read it**: Series share one time axis and one value scale, so the curves are directly comparable. Hover anywhere to get a crosshair and a readout of every series at that moment
- **Units**: Entities sharing a unit share a scale. Adding a different unit (e.g. humidity next to temperature) warns and scales it separately
- **Width**: Choose 2, 3 or 4 tiles wide in the graph's editor
- **Edit / remove**: In reorganize mode, click the edit icon on the graph tile (or the remove button)

### Entity Interactions

- **Lights**: Click to toggle, long-press for brightness slider
- **Fans**: Click to toggle, long-press for speed controls
- **Covers**: Click to open/close, long-press for open/stop/close controls
- **Climate**: Long-press for target temperature and mode controls
- **Media Players**: Use the media tile controls or long-press a media player for details and seek controls
- **Cameras**: Click to view live feed in popup window
- **Sensors**: Display real-time values with automatic unit formatting
- **Timers**: Show live countdown when active
- **Scenes, Scripts & Buttons**: Click to activate, run, or press instantly

### System Integration

- **Minimize to Tray**: Click the minimize button to hide to system tray
- **Updates**: Windows installer and Linux AppImage builds can update in app; portable, macOS, and Linux deb builds offer a GitHub Releases download
- **Start at Login**: Enable or disable startup from Settings > General
- **Settings**: Access via the Settings button or right-click the tray icon

### Settings Highlights

- **General**: Configure Home Assistant connection, always-on-top, startup behavior, language packs, profile sync, and updates
- **Themes**: Choose built-in or custom accent and background colors
- **Window Effects**: Adjust opacity, toggle frosted glass, and enable subtle weather effects
- **Primary Cards**: Pin weather/time or any entity to the top two cards
- **Custom Entity Icons**: Search or paste emoji/glyph overrides for entity icons
- **Media Tile**: Select the primary media player or hide the tile
- **Hotkeys**: Configure global entity hotkeys, action-specific shortcuts, and a popup hotkey (hold/toggle on macOS and Windows; press/toggle on Linux)
- **Alerts**: Enable desktop notifications for entity state changes or target states
- **Advanced**: Open logs and enable detailed interaction diagnostics when troubleshooting

## Advanced Usage

### Build from Source

```bash
git clone https://github.com/Robertg761/HA-Desktop-Widget.git
cd HA-Desktop-Widget
npm install
npm run dev   # Development mode (opens DevTools)
npm run dev:climate-demo # Isolated simulated Fahrenheit air-conditioner demo (no HA required)
npm start     # Regular run (builds the renderer, then starts Electron)
npm run lint  # Run ESLint
npm test      # Run Jest tests
npm run native:rebuild # Build native Electron modules such as uiohook-napi
npm run dist        # Build Windows NSIS and portable artifacts
npm run dist:win    # Build Windows NSIS installer artifacts
npm run dist:mac    # Build macOS distribution artifacts
npm run dist:linux  # Build Linux AppImage and deb artifacts
```

### Build workflow

The repository intentionally separates ordinary dependency installation from native Electron rebuilding. `npm ci` installs the dependency tree without requiring a local MSVC toolchain. The `native:rebuild` script is used when packaging the desktop application and is invoked automatically by the `dist*` scripts and the CI packaging jobs.

This keeps linting, tests, renderer builds, and other normal development workflows independent from platform-specific native build tooling while preserving explicit native compilation for release artifacts.

### Climate UI Demo (Development Only)

Run `npm run dev:climate-demo` to launch a simulated **Demo Air Conditioner** without a Home
Assistant server. The demo starts with a Fahrenheit AC entity in Quick Access and advertises
its HVAC, fan, and preset modes plus a 60–86°F target range with 1°F steps. Click the tile to
toggle it; press and hold it to exercise the target-temperature, mode, fan, and preset controls.

This command only works with the development `--dev` launch path. It creates a fresh temporary
Electron profile for that run, blocks all real Home Assistant service calls, and never reads or
writes the normal app configuration, token, desktop pins, or profile-sync data. Remove the
`dev:climate-demo` script and `development/dev-climate-demo.js` when the fixture is no longer useful.

To test the card alongside a real Home Assistant connection, run
`npm run dev:climate-overlay`. This development-only mode leaves the normal Electron profile and
Home Assistant connection intact, then places a renderer-local **Demo Air Conditioner** card at
 the start of Quick Access for the current session. Its fake state and climate service calls stay
in memory and are intercepted before the WebSocket layer; the card is not saved as a favorite,
cannot be edited/removed in Quick Access, and is never written into the normal configuration or
sent to Home Assistant. The existing `npm run dev:climate-demo` remains the fully isolated mode.

Because the overlay uses the normal Electron profile, and only one widget runs per profile, it
cannot start while a copy of the widget is already running — quit that one first. The isolated
`dev:climate-demo` gets its own temporary profile and runs alongside the real widget.

### Release Channels

- **Stable releases**: Push a tag like `v3.5.4`. GitHub Actions publishes a normal release. Windows installer and Linux AppImage users can receive it through the in-app updater; portable, macOS, and Linux deb users download it from GitHub Releases.
- **Tester prereleases**: Push a SemVer prerelease tag like `v3.5.4-beta.1`. GitHub Actions marks it as a prerelease. Only users who enable **Receive beta updates** in Settings -> Application Updates are offered these builds.
- **Nightly betas**: At 07:17 UTC, GitHub Actions checks `main` against the last successfully published beta in the active series. When unreleased changes exist, it creates the next `vX.Y.Z-beta.N` tag and runs the normal release workflow. The job can also be started manually from the Actions tab.
- **Manual-update builds**: Portable, macOS, and Linux deb users update from GitHub Releases. The update checker shows the appropriate stable or prerelease download when beta updates are enabled.

The minimum planned beta version is stored in `.github/beta-target`. It is currently set to
`3.9.0`, so the active series starts at `v3.9.0-beta.1`. Once `v3.9.0` is stable, the workflow
automatically moves to `v3.9.1-beta.N`; increasing the file starts a future minor series instead.

Release builds align their package version from the tag. Manually prepared betas commit matching
prerelease metadata before tagging; automated nightly betas align it only inside the build.
Stable releases continue to sync `package.json` and `package-lock.json` after publishing.

New GitHub releases automatically generate notes from merged pull requests and contributors. A beta compares against the previous published prerelease in the same version series, falling back to the latest stable release for the first beta. A stable release compares against the previous stable release so its notes cover the complete release cycle rather than only the changes since the last beta.

### Configuration

- **Config Location**: Stored as `config.json` in Electron's userData directory.
  - **Windows (packaged)**: `%AppData%/Home Assistant Widget/config.json`
  - **macOS (packaged)**: `~/Library/Application Support/HA Desktop Widget/config.json`
  - **Linux (packaged)**: `~/.config/HA Desktop Widget/config.json`
  - **Development builds**: typically use `home-assistant-widget` as the folder name
- **Config Contents**: `homeAssistant` (url and auth method; encrypted token fields only for legacy-token authentication), `desktopCompanion` (a random installation ID), `favoriteEntities`, `customEntityNames`,
  `desktopPins`, `customEntityIcons`, `quickAccessTileOptions`, `tileSpans`, `selectedWeatherEntity`, `primaryMediaPlayer`,
  `globalHotkeys`, and notification preferences. Syncable personalization is kept separate from sensitive connection state.

### Security & Credentials

- **Browser Authorization (default)**: New setups use Home Assistant's browser authorization flow so the desktop app never receives your Home Assistant password.
- **Legacy tokens**: For older setups, long-lived access tokens are encrypted at rest using the operating system's keychain facilities (when available) and are never sent to third-party services.
- **Companion commands**: Commands from Home Assistant are handled through an explicit, allow-listed command protocol. The integration never accepts arbitrary shell commands, JavaScript, or generic Electron IPC payloads.
- **Camera feeds**: HLS/snapshot access uses authenticated Home Assistant endpoints. Media payloads are held in memory and not written to disk by the widget.
- **Profile sync**: Sync settings exclude credentials, tokens, hotkeys, window geometry, desktop pins, and file-sync configuration. The sync file itself contains only bounded personalization state.

### Troubleshooting

- **Home Assistant won't connect**: Make sure the URL is reachable from the computer running the widget and that you are using the same URL you can open in your browser.
- **Camera tile doesn't show video**: Verify the camera entity supports the selected HLS or snapshot mode and that the Home Assistant user can access it.
- **Installer fails to start on Windows**: Check the Windows Event Viewer application logs and download a fresh build from GitHub Releases.
- **Linux transparent window doesn't work**: Verify that your desktop environment supports the required compositor features.
- **macOS blocks first launch**: Follow the Gatekeeper instructions under Quick Start.

## Contributing

Bug reports and focused improvements are welcome. Please use GitHub Issues for reproducible problems and pull requests for targeted changes. Keep production code changes paired with tests where practical, and keep security-sensitive changes narrowly scoped.

## License

MIT
