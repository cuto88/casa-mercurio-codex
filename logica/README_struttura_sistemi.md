# 🧭 Documento di riferimento — Struttura sistemi Casa Silea 2100 (Passivhaus++)

## 🔍 Obiettivo generale
Creazione di un **ecosistema modulare e coerente di automazioni Home Assistant** che gestisce:
- **ventilazione naturale**
- **VMC**
- **riscaldamento a pavimento**
- **aria condizionata (AC)**

Partiamo dall’infrastruttura reale **2025** (sensori T/UR, meteo, contatori energia già installati) e proiettiamo una roadmap verso le logiche **Passivhaus++ futuristiche 2100** descritte nel materiale concettuale. Ogni modulo quindi esplicita:

1. la **configurazione minima attivabile subito** con Home Assistant standard e sensori presenti;
2. le **estensioni evolutive** necessarie per raggiungere l’esperienza 2100 (orchestratore AI, smart-skin, PCM, ecc.).

Questo approccio consente di massimizzare comfort, efficienza e autonomia energetica senza rinunciare alla fattibilità operativa dell’impianto nel breve periodo, evitando conflitti tra sistemi.

Ogni funzione è contenuta in un file indipendente `.yaml` (logica attiva) o `.txt` (documentazione e criteri), che definisce:
- la **logica di attivazione** e le **priorità di arbitraggio**
- le **entità coinvolte** (sensori, input, switch, boolean)
- la **spiegazione leggibile** della logica umana
- la **plancia Lovelace** coerente con le stesse regole grafiche

---

## 🧩 Struttura modulare dei file

```
/config
│
├── /packages
│   ├── /logica/              ← documentazione tecnica e regole operative
│   │    ├── _sistema.txt
│   │    ├── 1_vent.txt
│   │    ├── 2_vmc.txt
│   │    ├── 2_vmc1.txt
│   │    ├── 3_heating.txt
│   │    ├── 4_ac.txt
│   │    ├── regole_gpt.txt
│   │    ├── regole_plancia.txt
│   │    └── regole_plancia2.txt
│   │
│   ├── 0_sensors.yaml
│   ├── 1_vent.yaml
│   ├── 2_vmc.yaml
│   ├── 3_heating.yaml
│   ├── 4_ac.yaml
│   ├── 5_powermeter.yaml
│   ├── 6_surplus_energy.yaml
│   ├── 9_global_energy.yaml
│
└── /lovelace
    ├── 1_vent_plancia.yaml
    ├── 2_vmc_plancia.yaml
    ├── 3_heating_plancia.yaml
    ├── 4_ac_plancia.yaml
    ├── 5_pm_plancia.yaml
    └── 6_surplus_plancia.yaml
```

---

## 🧠 Moduli e funzioni

| Modulo | Logica | Scopo sintetico |
|:--|:--|:--|
| **Ventilazione naturale** | `1_vent.yaml` / `1_vent.txt` | Coordina membrane bioniche per free-cooling quantico, controllo entalpico e IAQ neurale. |
| **VMC** | `2_vmc.yaml` / `2_vmc.txt` | Gestisce priorità P-1–P5: quarantena bio, failsafe sensoriale, boost nano, free-cooling entalpico triplo, anti-secco 2.0, IAQ Prime. |
| **Riscaldamento** | `3_heating.yaml` / `3_heating.txt` | Orquestra reti termoattive + PCM + geoscambio con AI predittiva e coach comfort personalizzato. |
| **AC** | `4_ac.yaml` / `4_ac.txt` | Coordina DRY+, COOL HVR, radiant night, loop desiccante e sincronizzazione con VMC/energia. |
| **Energia / PowerMeter** | `5_powermeter.yaml` | Rileva potenza e flussi (A/B), base per logiche di surplus e bilancio. |
| **Surplus PV** | `6_surplus_energy.yaml` | Gestisce carichi e logiche di autoconsumo energetico intelligente. |
| **Energia globale** | `9_global_energy.yaml` | Aggrega KPI, bilanci e grafici cumulativi. |
| **Sistema fisico** | `_sistema.txt` | Descrive sensori, termostati, mandata/ripresa per tutte le zone. |
| **Regole plancia v2** | `regole_plancia2.txt` | Definisce layout, colori, sezioni e standard visivo per tutte le dashboard. |

---

## ⚙️ Principi di progettazione

1. **Indipendenza logica** → ogni file YAML funziona da solo, orchestrato dall’AI ma senza dipendenze rigide.
2. **Arbitraggio chiaro** → priorità esplicite (es. `Clima notte = DRY+` forza VMC OFF con scrubber minimo).
3. **Trasparenza** → ogni plancia include card “Come decide” + spiegazione IA/coach leggibile.
4. **Scalabilità** → sensori multispettrali, lock, override e logging neurale facilmente espandibili.
5. **Coerenza visiva** → tutti i moduli seguono `regole_plancia2.txt` aggiornato (colori futuristici, layout orbitale).
6. **Versionabilità** → la logica testuale (.txt) rimane sincronizzata con automazioni YAML e gemello digitale.

---

## 🎯 Obiettivo finale

Costruire una **suite coordinata e trasparente** che permetta di:
- comprendere *a colpo d’occhio* chi comanda cosa e perché  
- analizzare l’efficacia di strategie (boost, free-cooling, anti-secco, PV-window)  
- modificare in tempo reale soglie e parametri (input_number, boolean)  
- ottenere comfort e risparmio energetico con logiche *Passivhaus* ma operatività *Home Assistant*
