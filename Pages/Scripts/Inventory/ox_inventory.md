# ox_inventory

`ox_inventory` is an inventory system for FiveM.

The resource includes item metadata, stashes, shops, crafting, weapon support, vehicle storage, and framework integrations.

> SantosCAD links to the source project. SantosCAD does not own, maintain, or distribute `ox_inventory`.
> {.is-info}

---

## Resource Information

| Field        | Information      |
| ------------ | ---------------- |
| **Name**     | `ox_inventory`   |
| **Creator**  | Overextended     |
| **Type**     | Script           |
| **Category** | Inventory        |
| **Game**     | FiveM            |
| **Price**    | Free             |
| **Source**   | GitHub           |
| **License**  | GPL 3.0 or later |
| {.dense}     |                  |

---

## Resource Details {.tabset}

### Overview

`ox_inventory` provides a slot based inventory system for FiveM servers.

The resource supports:

* Item metadata
* Player inventories
* Stashes
* Shops
* Crafting
* Vehicle trunks
* Vehicle gloveboxes
* Weapons
* Weapon attachments
* Ammo
* Item durability
* Inventory drops
* Dumpster loot
* Vehicle loot
* Group restrictions
* License restrictions

### Requirements

Install these resources before `ox_inventory`:

```text
oxmysql
ox_lib
```

Optional:

```text
ox_target
```

`ox_target` provides target interactions for supported shops, stashes, and other inventory interactions.

### Framework Support

Supported framework settings include:

```text
ox
esx
qbx
nd
```

Set your framework in `server.cfg`.

**Qbox**

```cfg
setr inventory:framework "qbx"
```

**ESX**

```cfg
setr inventory:framework "esx"
```

**ox_core**

```cfg
setr inventory:framework "ox"
```

> A framework without a supported bridge requires code and database changes.
> {.is-warning}

---

## Installation

### Installation Checklist

* [ ] Install `oxmysql`
* [ ] Install `ox_lib`
* [ ] Install your framework
* [ ] Install `ox_target` if used
* [ ] Download `ox_inventory`
* [ ] Place the resource inside your resources folder
* [ ] Set the inventory framework
* [ ] Check your resource start order
* [ ] Restart the server
* [ ] Check the server console for errors

### Resource Order

Use this order as a base:

```cfg
start oxmysql
start ox_lib
start framework
start ox_target
start ox_inventory
```

Replace `framework` with your framework resource.

Examples:

```text
ox_core
es_extended
qbx_core
```

> Start `ox_inventory` after its dependencies and framework.
> {.is-success}

---

## Configuration {.tabset}

### General

`ox_inventory` uses convars in `server.cfg`.

Example:

```cfg
setr inventory:framework "qbx"

setr inventory:slots 50
setr inventory:weight 30000

setr inventory:target true

setr inventory:keys ["F2", "K", "TAB"]

setr inventory:weaponanims true
setr inventory:itemnotify true
setr inventory:weaponnotify true
```

### Slots

Set the number of player inventory slots:

```cfg
setr inventory:slots 50
```

### Weight

Inventory weight uses grams.

```cfg
setr inventory:weight 30000
```

`30000` equals 30 kg.

### Target

Enable `ox_target` support:

```cfg
setr inventory:target true
```

### Keys

Set inventory keys:

```cfg
setr inventory:keys ["F2", "K", "TAB"]
```

### Notifications

Enable item notifications:

```cfg
setr inventory:itemnotify true
```

Enable weapon notifications:

```cfg
setr inventory:weaponnotify true
```

---

## Items

Item definitions are stored in:

```text
ox_inventory/data/items.lua
```

A basic item might use:

```lua
['water'] = {
    label = 'Water',
    weight = 500,
    stack = true,
    close = true,
    description = 'A bottle of water'
}
```

Common fields include:

| Field         | Purpose                            |
| ------------- | ---------------------------------- |
| `label`       | Item name shown to players         |
| `weight`      | Item weight                        |
| `stack`       | Allows items to share one slot     |
| `close`       | Closes inventory after use         |
| `description` | Item description                   |
| `consume`     | Amount consumed                    |
| `degrade`     | Controls item degradation          |
| `decay`       | Controls removal after degradation |
| {.dense}      |                                    |

> Keep custom items in line with the source documentation. Wrong item data often causes resource errors.
> {.is-warning}

---

## Known Issues {.tabset}

### UI Does Not Load

Check how you downloaded the resource.

The GitHub source does not include every built web file used by a release package.

Use an official release when you do not plan to build the web interface yourself.

> If the inventory opens with no interface, check the browser build before changing Lua code.
> {.is-warning}

### Missing Export

A missing export error often points to resource order or startup failure.

Check:

* [ ] `ox_inventory` started
* [ ] `ox_lib` started
* [ ] `oxmysql` started
* [ ] Your framework started
* [ ] The calling resource starts after `ox_inventory`
* [ ] The export name exists

Check the first error in your server console.

Do not focus on later errors before fixing the first startup failure.

### Inventories Do Not Save

Inventory data uses scheduled saves.

txAdmin restart events trigger inventory saving.

For a manual shutdown, use:

```text
saveinv
```

> Run `saveinv` before a manual shutdown when you need to force an inventory save.
> {.is-info}

### Framework Conflicts

Framework inventory systems might conflict with `ox_inventory`.

Check for:

* Inventory resources
* Weapon systems
* Item systems
* Money item systems
* Shop systems
* Stash systems

> Do not run two inventory systems for the same player inventory.
> {.is-danger}

---

## Compatibility

| System           | Support              |
| ---------------- | -------------------- |
| FiveM            | Supported            |
| ox_core          | Supported            |
| ESX              | Supported            |
| Qbox             | Supported            |
| ND               | Supported            |
| Custom Framework | Requires bridge work |
| ox_target        | Optional             |
| {.dense}         |                      |

---

## Links

### Official Links {.tabset}

#### Documentation

[Open ox_inventory Documentation](https://overextended.dev/docs/ox_inventory)

#### GitHub

[Open ox_inventory Repository](https://github.com/overextended/ox_inventory)

#### Releases

[Open ox_inventory Releases](https://github.com/overextended/ox_inventory/releases)

---

## Before You Install

* [ ] Read the source documentation
* [ ] Check framework support
* [ ] Install required dependencies
* [ ] Check your start order
* [ ] Back up your database
* [ ] Test on a development server
* [ ] Check other resources for inventory dependencies

> Back up your server and database before replacing an existing inventory system.
> {.is-danger}

---

## Credits

Created by **Overextended** and project contributors.

SantosCAD provides resource information and links to source pages.

Resource rights belong to the project authors and rights holders.