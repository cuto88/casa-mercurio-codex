# Casa Silea — Passivhaus Automations (Codex Project)

> Generated on 2025-11-04T11:47:41

## What this project is
A Codex-ready package that defines a modular Home Assistant automation suite for:
- Summer natural ventilation (free-cooling)
- Centralized HRV/VMC
- Floor heating
- Air conditioning (day/night)
- Energy monitoring (powermeter + surplus) and global KPIs

### Repository layout
```
logica/                     # Human-readable logic and design rules (authoritative)
  _sistema.txt              # Physical system map
  1_vent.txt                # Natural ventilation logic
  2_vmc1.txt                # VMC core logic & priorities
  3_heating.txt             # Floor heating strategy
  4_ac.txt                  # AC logic (DRY/COOL, anti-cycle)
  regole_plancia2.txt       # Lovelace UI rules (v2)
  regole_chat_gpt.txt       # How GPT must work on this project
  README_struttura_sistemi.md

packages/                   # HA YAML packages (editable by Codex)
  0_sensors.yaml            # core sensors & helpers (scaffold)
  1_vent.yaml               # natural ventilation automations (scaffold)
  2_vmc.yaml                # VMC automations (scaffold)
  3_heating.yaml            # heating automations (scaffold)
  4_ac.yaml                 # AC automations (scaffold)
  5_powermeter.yaml         # energy meters (scaffold)
  6_surplus_energy.yaml     # PV surplus logic (scaffold)
  9_global_energy.yaml      # global energy KPIs (scaffold)

lovelace/                   # Lovelace dashboards (one file per board)
  1_vent_plancia.yaml
  2_vmc_plancia.yaml
  3_heating_plancia.yaml
  4_ac_plancia.yaml
  5_pm_plancia.yaml
  6_surplus_plancia.yaml
  9_global_energy_plancia.yaml
  dashboards/               # If you prefer per-dashboard entries, define them here
configuration_examples/
  configuration_lovelace_integrated.yaml  # Optional: define dashboards inside configuration.yaml
```

### How to use with Codex
1. Import this repo/folder into Codex as a project.
2. Use **logica/** as the source of truth for decision rules and UI standards.
3. Ask Codex to open and edit any YAML in **packages/** or **lovelace/**. It must follow `logica/regole_chat_gpt.txt`.
4. Optionally copy `configuration_examples/configuration_lovelace_integrated.yaml` into your HA `configuration.yaml`.

> Important: Keep `logica/*.txt` and the corresponding YAML files synchronized. Codex is instructed to ensure consistency.

