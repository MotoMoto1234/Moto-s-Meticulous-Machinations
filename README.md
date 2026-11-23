# Moto’s Meticulous Machinations
[![Buy me a coffee on Ko-fi](https://img.shields.io/badge/Buy%20me%20a%20coffee-FF5E5B?style=for-the-badge&logo=kofi&logoColor=white)](https://ko-fi.com/motomoto0295)

Moto’s Meticulous Machinations (MMM) is a library of Foundry VTT automations for D&D 5e. Apply them to the items, spells, and features on your actors through the Cauldron of Plentiful Resources (CPR) Medkit.

## Compatibility

MMM targets Foundry VTT **v13** and D&D 5e **5.2.5**. The initial release was built against Foundry **13.351**, CPR **1.5.51**, Midi-QOL **13.0.73**, Dynamic Active Effects **13.0.32**, and Times Up **13.1.9**. SocketLib and libWrapper are also required.

Sequencer and the relevant JB2A pack are optional for supported visuals. Some automations can use additional modules for features such as mounting or token art. See the [FAQ](FAQ.md) for setup details.

## Install and apply an automation

1. In Foundry Setup, open **Add-on Modules → Install Module** and use this manifest URL.

   ```text
   https://github.com/MotoMoto1234/Motos-Meticulous-Machinations/releases/latest/download/module.json
   ```

2. Enable **Moto’s Meticulous Machinations** and its dependencies in your D&D 5e world.
3. In **Cauldron of Plentiful Resources → Compendium Options → Additional Compendiums**, enable the Machinations item packs you want to use.
4. Open an existing actor item, spell, or feature. In its **Medkit**, choose the Machinations entry under **Selected Automation** and click **Apply**. Check **Configuration** for automation-specific settings.

For manual installation, extract the release’s `module.zip` into Foundry’s `Data/modules` directory. Its top-level folder is `motos-meticulous-machinations`.

See the [FAQ](FAQ.md) for Midi-QOL settings, pack priority, and troubleshooting.

## Compendiums

| Pack | Contents |
| --- | --- |
| **Machinations Items** | Magic items, consumables, and special ammunition |
| **Machinations Spells** | Spell automations, including Moonbeam, Wall of Force, and Witch Bolt |
| **Machinations Class & Subclass Features** | Class features grouped with their subclasses, including Hex Slinger and permanent companion features |
| **Machinations Feats** | Lucky and Protected |
| **Monster Bits** | Monster features for use on NPCs |
| **Machinations Companions** | Drake Companion, Steel Defender, and Otherworldly Steed actor templates |

Monster Bits entries include their item descriptions. The other item packs are automation templates with blank descriptions. Applying an automation through the CPR Medkit keeps the description from the item already in your world.

## Optional Bleeding Out rules

**Manage Bleeding Out** is off by default. If you enable it, use the [FAQ](FAQ.md#should-i-turn-off-midi-qols-automatic-0-hp-status) to switch over from your existing 0 HP automation. The FAQ also covers custom Bleeding Out icons and token art.

## Repository layout

- `module.json` defines the Foundry module, its dependencies, and its release URLs.
- `scripts/` contains the module JavaScript.
- `packs/` contains the Foundry-ready compendiums.
- `packData/` contains the editable public compendium JSON. Use the [official Foundry VTT CLI](https://github.com/foundryvtt/foundryvtt-cli#api) to compile each source directory back to the corresponding `packs/` directory.

