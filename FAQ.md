# Moto’s Meticulous Machinations FAQ

## What do I need to install?

Enable **Moto’s Meticulous Machinations**, **Cauldron of Plentiful Resources (CPR)**, **Midi-QOL**, **Dynamic Active Effects (DAE)**, **Times Up**, **SocketLib**, and **libWrapper** in your D&D 5e world. Keep **Enable Times Up** checked in the Times Up settings so timed effects expire. Keep an active GM connected during play so automations can update actors that players do not own.

These instructions use the English labels from Foundry **13.351**, D&D 5e **5.2.5**, Midi-QOL **13.0.73**, CPR **1.5.51**, DAE **13.0.32**, and Times Up **13.1.9**.

## How do I get the automations into my game?

1. Open **Configure Settings → Cauldron of Plentiful Resources → Compendium Options**. Click **Configure** next to **Additional Compendiums** and check **Machinations Items**, **Machinations Spells**, **Machinations Class & Subclass Features**, **Machinations Feats**, and **Monster Bits** as needed.
2. Set the source priority you want. Lower numbers come first. Give a Machinations pack a lower number than competing sources if you want CPR to prefer it during bulk updates. You can still choose the source individually.
3. Open an existing item, spell, or feature on an actor’s sheet. Click its **CPR Medkit**, choose the Machinations entry under **Selected Automation**, and click **Apply**. Use the Medkit’s update button when it reports a newer automation.

Monster Bits entries include their item descriptions. The other packs ship with blank descriptions. Applying automation through the Medkit keeps the existing item’s description and replaces its activities and effects, so save a copy first if you want to keep your changes to those fields.

If the Medkit cannot find a match, check the item’s name, document type, and **2014/2024** rules in its source details. The Medkit can also report a match under the other rules version. If the source is visible but the player cannot apply it, have the GM apply it or check CPR’s **Medkit Apply Automation Permissions** and **Medkit Update Automation Permissions**.

## Which Midi-QOL settings should I use?

Start with **Enable roll automation support** in Midi-QOL’s main settings. It is a client setting, so check it on the GM client and each player’s client. The rest are in **Workflow Settings**.

| Tab | Setting | Suggested value |
| --- | --- | --- |
| Misc | **Add item on use macro to sheet** and **Add actor on use macro to sheet** | Enable both for macro execution. |
| Player and GM | **Auto roll attack** | Enable it in both tabs. |
| Player and GM | **Auto roll damage** | Set both to **Damage Roll Needed** so Midi rolls damage when the workflow calls for it. |
| Workflow | **Auto check if attack hits target** | Pick a **Check** option. Choose who sees the result to suit your table. |
| Workflow | **Auto check Saves** | Pick an enabled **Save** option so automations can distinguish failed and successful saves. You can still prompt players to roll their saves. |
| Workflow | **Auto apply damage to target** | Use **Yes + damage card** for automatic application or **No + damage card** to apply damage and healing from Midi’s card yourself. |
| Workflow | **Add damage buttons to chat message** | Set to **None** to suppress the extra damage application buttons on Midi roll messages. |
| Workflow | **Auto apply item effects** | Set to **Apply effects do not show button**. Midi applies the effects and hides the D&D 5e effect tray on its item cards. |
| Mechanics | **Wait for damage application** | Enable it so follow-up automation sees the applied HP changes. |
| Concentration | **Force a concentration save when damage taken** | Set to **Roll Concentration Item**. |
| Misc | **Display Confirm Roll Button** and **Autocomplete workflow if required** | Use **No confirmation** and enable autocomplete for the workflow CPR expects. |

**Auto target on template draw** is a table preference. **Walls Block** works for ordinary templates when walls should block targeting. Avoid the **Ignore Incapacitated/Dead** variants for workflows that should include downed creatures, such as Resuscitation Bomb. Some activities also set their own targeting.

Keep D&D 5e’s concentration tracking active by leaving **Disable concentration tracking** unchecked. **Check PLAYER reactions** and **Check NPC/GM reactions** control Midi’s built-in reaction prompts. Machinations features with their own prompts, such as Noble Sacrifice, use their own trigger and prompt routing.

## Which other CPR settings matter?

- Keep **Condition Resistance and Vulnerability** enabled for effects that use CPR’s conditional keys, such as Hunter’s Zeal against cursed targets.
- **Enable Effect Interface** is needed for CPR’s Effects sidebar and its custom status definitions. The optional Machinations Bleeding Out system registers its own status.
- For animations, enable **Sequencer** and the JB2A pack that supplies the chosen effect. Open the item’s Medkit **Configuration** tab to check its animation toggle and asset path where available. **Enable CPR Animations** controls CPR’s own optional visuals.
- **Exploding Heals** is a CPR house rule for all healing rolls. Enable it if your table wants dice to explode, including the dice-based Heal variant.
- **Display Development Tools**, **Enable Embedded Macros Editing**, and **3rd Party Content** can stay at your usual settings. Selecting Machinations under **Additional Compendiums** makes its packs available to the Medkit.

## Should I turn off Midi-QOL’s automatic 0 HP status?

Only if you want Machinations to run your Bleeding Out rules. **Manage Bleeding Out** defaults to off. With it off, keep your current Midi-QOL or CPR dying setup. Noble Sacrifice can still offer its reaction on a drop to 0 HP or a third recorded failure, and it defers to legacy hooks that already offer it.

To switch to the Machinations system:

1. If you registered a custom **Bleeding Out** in CPR, open the **Effects** sidebar, right-click its definition, and choose **Remove from Status Effects**.
2. In **Midi-QOL → Workflow Settings → Mechanics**, find **Add effect when HP = 0**. Set the rightmost dropdown to **Do Not Update**. The **Player Controlled** and **GM Controlled** dropdowns select status names.
3. In **Configure Settings → Moto’s Meticulous Machinations**, enable **Manage Bleeding Out** and reload. Make the switch between encounters so effects already applied by the old setup can finish under that setup.

Machinations applies Bleeding Out when a creature drops to 0 HP and prompts the owner or GM for turn-start death saves. Use **Yes + damage card** if you want Machinations to count damage-caused failures automatically. With **No + damage card**, adjudicate those failures at the table. If the legacy CPR status is still registered or Midi’s automatic status is still active, Machinations warns the GM and stays in compatibility mode.

## How do I change the Bleeding Out icon?

Open **Configure Settings → Moto’s Meticulous Machinations → Bleeding Out Image** and select an image with the file picker. Save and reload. The icon appears on newly applied Machinations Bleeding Out effects. Leave the field blank to use Foundry’s blood icon. If your world uses a custom CPR Bleeding Out status, edit its image in CPR’s Effects sidebar.

With **Active Token Effects** enabled, check **Use Bleeding Out Image as Token Art** to use that same image as the token’s texture. Newly applied Bleeding Out effects set both texture scales to 1.6 and release the overrides when the effect ends.

## What happens if a player leaves an automation dialog open?

Supported prompts such as Weavebend, Corrupting Ichor, Marrow Transplant, Guardian Coil, and Hex Slinger’s **Just Select** picker use Midi-QOL’s **Reaction check timeout** for player decisions. MMM uses 30 seconds if that setting is zero or unset. If a player times out or disconnects, MMM closes their prompt and sends the decision to the active GM. **GM Fallback** identifies who was asked first. GM prompts wait for a response. For Weavebend, the remaining decisions stay with the GM after a handoff.

## How do I set up a permanent companion?

Import the matching actor from **Machinations Companions** into the world’s **Actors** sidebar. Use **Bind Permanent Drake**, **Bind Permanent Defender**, or **Bind Permanent Steed** on the character’s automated feature, then select the imported actor. Place linked tokens from that same sidebar actor in each scene where you need the companion. Use **Refresh Bond** for manual synchronization. Enable **Rideable** for supported mount and dismount activities.
