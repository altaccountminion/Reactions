# Reactions

My TensorReactions profiles. Right now this is the FRU AutoSim timeline, with more to come.

## Requirements

- TensorCore
- TensorReactions
- The TensorACR for your job (RPR, VPR, SAM or BLM)
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

**Setup**

1. Open your own FRU timeline profile.
2. Inherit `AA\[AA] Autosim - FRU`.

**Optional: if you also want Anyone's FRU reactions**

3. Inherit these Anyone modules:
   - `store\anyone\fru\modules\core`
   - `store\anyone\fru\modules\draws`
   - `store\anyone\fru\modules\mitigation` (optional, for mit)
   - `store\anyone\fru\modules\tank-mitigation` (tanks)
4. **Do not inherit `store\anyone\fru\modules\optimization`.** Its manual holds, toggles and pots fight the autosim.
5. Disable these two Anyone reactions:
   - `[Core] Set Toggles` (in core)
   - `[VPR] Toggle Reawaken` (in draws)

If you inherit Anyone's main FRU profile (`store\anyone\fru\fru`) instead, it pulls in the optimization module too. You'll then need to disable every toggle and hold reaction in it, plus the two above.

**Upgrading from a manual install?** If you put `[AA] Autosim - FRU.lua` straight into `TimelineReactions\` before, delete that copy. Then point your inheritance at `AA\[AA] Autosim - FRU` so you get updates.

**Testing status**

- **VPR**: in good shape and performing fairly well.
- **RPR**: the most tested. Performing fairly well, with some minor issues in the P4 cleave.
- **SAM**: untested, and probably weak given current limitations. Avoid it for now.
- **BLM**: untested. It should work in theory. You may want to raise unexpected movement a bit in the ACR's autosim settings.

**Experimental: P4 targeting on Gaia (2026-10-20)**

Once Gaia spawns in P4, every DPS job now treats Gaia as its only DoT target, which keeps the rotation on her instead of drifting to Ryne. Before, only Reaper did this. BLM is the one exception: it still tracks Ryne as a second target so its AoE Thunder covers both bosses. Ryne still counts for cleave and AoE. This is new and hasn't been tested in a pull yet, so please report it if P4 targeting or DoTs look wrong.
