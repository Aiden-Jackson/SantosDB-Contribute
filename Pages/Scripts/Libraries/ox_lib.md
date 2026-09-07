# ox_lib

ox_lib is a standalone FiveM development library from Overextended. It provides reusable Lua and JavaScript modules, exports, interface functions, callbacks, zones, utilities, and other resource development features.

> SantosCAD links to the source project. SantosCAD does not own, maintain, or distribute this resource.
> {.is-info}

---

## Resource Information

| Field                 | Information       |
| --------------------- | ----------------- |
| **Name**              | `ox_lib`          |
| **Creator**           | Overextended      |
| **Type**              | Script Library    |
| **Category**          | Developer Tool    |
| **Game**              | FiveM             |
| **Price**             | Free              |
| **License**           | LGPL-3.0-or-later |
| **Framework Support** | Standalone        |
| **Languages**         | Lua, JavaScript   |
| **Source**            | GitHub            |
| **Status**            | Maintained        |
| {.dense}              |                   |

The official resource manifest lists Overextended as the author and `LGPL-3.0-or-later` as the license. The Overextended repository received updates in September 2026.

---

## Resource Details {.tabset}

### Overview

ox_lib provides shared functions for FiveM resources through importable modules and exports.

Included APIs cover areas such as:

* Callbacks
* Commands
* Keybinds
* Locales
* Menus and interface functions
* Notifications
* Points and zones
* Raycasting
* Streaming
* Timers
* Vehicle properties
* Utility functions

The library exposes `lib`, `require`, and `cache` after importing `ox_lib` into a Lua resource.

### Requirements

The current `fxmanifest.lua` requires:

* FXServer artifact supporting server build `7290` or newer
* OneSync

These requirements are declared through `/server:7290` and `/onesync`.

Git, Node.js, and bun are used when building ox_lib from source. They are not required when installing a prebuilt release.

### Framework Support

ox_lib is documented as a standalone library.

It does not require QBCore, Qbox, ESX, or another gameplay framework to operate. Other resources and frameworks use ox_lib as a dependency.

---

## Installation

### Installation Checklist

* [ ] Confirm your FXServer meets the resource requirements
* [ ] Enable OneSync
* [ ] Download the latest official ox_lib release
* [ ] Extract the resource as `ox_lib`
* [ ] Place `ox_lib` inside your server resources folder
* [ ] Start `ox_lib` before resources that depend on it
* [ ] Add the required ACE permissions
* [ ] Restart the server
* [ ] Check the server console for errors

The official repository provides a packaged release download. Building from source requires Git and bun.

### Resource Order

Start ox_lib before resources that import or depend on it.

```cfg
ensure ox_lib
```

Place dependent resources after this entry.

### ACE Permissions

The official documentation instructs server owners to grant ox_lib permission to manage ACE entries and principals.

```cfg
add_ace resource.ox_lib command.add_ace allow
add_ace resource.ox_lib command.remove_ace allow
add_ace resource.ox_lib command.add_principal allow
add_ace resource.ox_lib command.remove_principal allow
```

---

## Configuration

ox_lib uses FiveM convars for resource configuration.

```cfg
setr ox:primaryColor blue
setr ox:primaryShade 8
setr ox:userLocales 1
setr ox:progressPropLimit 2
```

| Convar                 | Purpose                                                        |
| ---------------------- | -------------------------------------------------------------- |
| `ox:primaryColor`      | Sets the primary interface color                               |
| `ox:primaryShade`      | Sets the primary interface shade                               |
| `ox:userLocales`       | Controls user locale selection through `/ox_lib`               |
| `ox:progressPropLimit` | Sets the maximum number of spawned props used by progress bars |
| {.dense}               |                                                                |

---

## Usage {.tabset}

### Lua

Add `@ox_lib/init.lua` to the resource that uses ox_lib.

```lua
shared_scripts {
    '@ox_lib/init.lua',
}
```

If no other shared scripts are required:

```lua
shared_script '@ox_lib/init.lua'
```

You also have the option to declare specific ox_lib modules:

```lua
ox_libs {
    'locale',
    'math',
    'table',
}
```

Importing ox_lib provides globals including `lib`, `require`, and `cache`.

### JavaScript

Overextended publishes the `@overextended/ox_lib` npm package.

Server imports include:

```js
import lib from "@overextended/ox_lib/server";
```

Specific functions also support named imports:

```js
import { versionCheck } from "@overextended/ox_lib/server";
```

> The npm package does not support every function available through the Lua resource API.
> {.is-warning}

---

## Building From Source

Clone the official repository, enter the web directory, install packages, then build the interface.

```text
git clone https://github.com/overextended/ox_lib.git
cd ox_lib/web
bun i
bun run build
```

> Do not de-bundle or un-minify the release CSS and JavaScript files for UI modifications. Edit the source and rebuild the UI instead.
> {.is-warning}

For browser development, Overextended documents `bun start`. For in-game UI development, the documented command is `bun start:game`.

---

## Compatibility

| Item                                | Support  |
| ----------------------------------- | -------- |
| **FiveM**                           | Yes      |
| **Standalone**                      | Yes      |
| **Lua**                             | Yes      |
| **JavaScript**                      | Yes      |
| **OneSync**                         | Required |
| **Minimum declared FXServer build** | `7290`   |
| **RedM manifest target**            | Yes      |
| {.dense}                            |          |

The current manifest targets both `gta5` and `rdr3`. The resource also declares OneSync and server build requirements.

---

## Known Limitations

* The npm package does not expose every function available through Lua.
* UI source changes require rebuilding the web files.
* Resources importing `@ox_lib/init.lua` require ox_lib to be available and started in the correct resource order.

These points come from the official ox_lib documentation and manifest.

---

## Links

* Official Documentation: Overextended ox_lib documentation
* Official Repository: Overextended `ox_lib` on GitHub
* Official Download: Latest `ox_lib` GitHub release
* Official npm Package: `@overextended/ox_lib`

[Official Documentation](https://overextended.dev/docs/ox_lib?utm_source=chatgpt.com)
[Official GitHub Repository](https://github.com/overextended/ox_lib?utm_source=chatgpt.com)
[Official Release Download](https://github.com/overextended/ox_lib/releases/latest/download/ox_lib.zip?utm_source=chatgpt.com)
[Official npm Package](https://www.npmjs.com/package/@overextended/ox_lib?utm_source=chatgpt.com)

---

## Before You Install

* [ ] Use the official Overextended release
* [ ] Confirm your FXServer meets the declared server requirement
* [ ] Confirm OneSync is enabled
* [ ] Add the documented ACE permissions
* [ ] Start ox_lib before dependent resources
* [ ] Review the official documentation for APIs used by your resources

---

## Credits

Created by **Overextended** and project contributors.

SantosCAD provides resource information and source references.

Resource rights belong to the project authors and rights holders.
