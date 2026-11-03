# Reactions

My TensorReactions profiles. Right now these are the FRU and DSW AutoSim timelines, with more to come.

## Requirements

- TensorCore
- TensorReactions
- The TensorACR for your job (RPR, VPR, SAM or BLM; DSW also supports BRD)
- AnyoneCore, if you want automatic updates (recommended)

## Installation

### With AnyoneCore (auto-updates)

1. In AnyoneCore, go to **SYSTEM > Third Party**, then the **Sources** tab.
2. Add this repository URL:

   ```
   https://github.com/altaccountminion/Reactions
   ```

3. Update and reload from the **Updater** tab.

The profiles show up under `AA` in TensorReactions. Each time I push a change, AnyoneCore pulls it on its next update.

### Manual

Download the files and put them in `MINIONAPP\Bots\FFXIVMinion64\LuaMods\TensorReactions`, keeping the folders as they are. You'll have to do this again every time I change a file.

## Timeline Reactions

### FRU: `AA\[AA] Autosim - FRU`

A standalone AutoSim timeline for Futures Rewritten (fru 1.0.5). It doesn't inherit anything.

**What it covers**

This profile is focused on running the ACR4 rotation well through the fight: AutoSim timings, downtime, raid buff windows and target slots. It isn't a full automation profile, and **it doesn't auto-target in the intermission.** The ACR only plans around what you have targeted there (your current Light Crystal, then the Ice Veil), so pick targets yourself, or use Anyone's targeting (option B below).

**Setup**

1. Open your own FRU timeline profile.
2. Inherit `AA\[AA] Autosim - FRU`.

Then pick one of these if you also want Anyone's FRU reactions.

**Option A: Anyone's modules, no auto-targeting**

3. Inherit these Anyone modules:
   - `store\anyone\fru\modules\core`
   - `store\anyone\fru\modules\draws`
   - `store\anyone\fru\modules\mitigation` (optional, for mit)
   - `store\anyone\fru\modules\tank-mitigation` (tanks)
4. **Do not inherit `store\anyone\fru\modules\optimization`.** Its manual holds, toggles and pots fight the autosim.
5. Disable these two Anyone reactions:
   - `[Core] Set Toggles` (in core)
   - `[VPR] Toggle Reawaken` (in draws)

**Option B: the full targeting suite**

If you want Anyone's auto-targeting too, such as the intermission crystal targeting:

3. Inherit Anyone's complete FRU profile, `store\anyone\fru\fru`. It includes every module, optimization too.
4. Disable the holds, toggles and potion uses inside it, because they fight the autosim. Most are in the optimization module. Keep its targeting reactions enabled, for example `[All] Target Nearest On Spawn`, `[Melee] Auto-Target`, `[Ranged] Auto-Target` and `[All] Target Ice Re` for the intermission.
5. Disable `[Core] Set Toggles` and `[VPR] Toggle Reawaken`, as in option A.

**Upgrading from a manual install?** If you put `[AA] Autosim - FRU.lua` straight into `TimelineReactions\` before, delete that copy. Then point your inheritance at `AA\[AA] Autosim - FRU` so you get updates.

**Testing status**

- **VPR**: in good shape and performing fairly well.
- **RPR**: the most tested. Performing fairly well, with some minor issues in the P4 cleave.
- **SAM**: untested, and probably weak given current limitations. Avoid it for now.
- **BLM**: untested. It should work in theory. You may want to raise unexpected movement a bit in the ACR's autosim settings.

**Experimental: P4 targeting on Gaia (2026-10-20)**

Once Gaia spawns in P4, every DPS job now treats Gaia as its only DoT target, which keeps the rotation on her instead of drifting to Ryne. Before, only Reaper did this. BLM is the one exception: it still tracks Ryne as a second target so its AoE Thunder covers both bosses. Ryne still counts for cleave and AoE. This is new and hasn't been tested in a pull yet, so please report it if P4 targeting or DoTs look wrong.

### DSW: `AA\[AA] Autosim - DSW`

An AutoSim timeline for Dragonsong's Reprise (dsw 1.0.5), for BRD, BLM, SAM, RPR and VPR. It covers both pulls: the door (P1) and P2 through P7. Each countdown loads the schedule for the pull that's starting.

**What it covers**

AutoSim timings, downtime, raid buff windows, caster movement, target slots, and timing uncertainty around each push and kill, all taken from my own logs. It re-syncs at every phase change.

- **P6 dragons:** with an AnyoneCore party roster, Group 1 (MT, H1, M1, R1) is set up on Nidhogg and Group 2 (OT, H2, M2, R2) on Hraesvelgr. When your dragon leaves for the arena edge, the sim switches to the other one until yours returns. Without a roster, the sim follows your current target.
- **P5 meteors:** no DoTs on the Meteor Circles; the sim follows the meteor you target.
- **Casters:** a small **AutoSim | DSW settings** window lets you choose whether you LB the P5 meteors (Manual) or not (Disabled), so the sim plans around it.
- **Melee Feints:** M1/M2 (by roster slot) use Feint on a mitigation plan, through the ACR's Hotbar Feint, so other jobs ignore them.

**Setup**

1. Install Anyone's DSW store profile, `store\anyone\dsw\universal`. This profile inherits it and turns off its holds, toggles, forced rotation and potion reactions, which fight the autosim. Mitigation, healer cooldowns, targeting, draws and the fire/ice mechanic stops stay on.
2. Open your own DSW timeline profile and inherit `AA\[AA] Autosim - DSW`. Don't also inherit `store\anyone\dsw\universal` on its own.

**Testing status**

New, and **not tested in a pull yet** in its current form. That includes the timing-uncertainty update and the P6 group setup. Please report anything that looks off, especially P6 targeting and DoTs.
