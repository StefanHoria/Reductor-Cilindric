# Single-Stage Helical Gear Reducer — RCil H

**Year project — Machine Elements (Organe de Mașini)**
Transilvania University of Brașov · Faculty of Mechanical Engineering
Department of Automotive and Transport Engineering · 2026

The complete design of a single-stage speed reducer with a helical cylindrical gear pair and a
horizontal shaft plane (the **RCil H** variant): from the design brief and the analytical
calculations, through 3D modelling in CATIA V5 and verification in MDESIGN, to the assembly drawing
and the detail drawings.

| | |
|---|---|
| **Author** | Horia-Eusebiu ȘTEFAN — Robotics programme, group 4LF832 |
| **Supervisors** | Prof. dr. eng. Gheorghe MOGAN · Dr. eng. Eugen BUTILĂ · Eng. Diana BUZDUGAN |
| **Software** | CATIA V5 (3D modelling, drawings), MDESIGN 2020 (shaft verification) |
| **Documentation** | [Technical report (PDF, 47 pages, Romanian)](docs/Memoriu-Tehnic-Stefan-Horia-Eusebiu.pdf) |

> 🇷🇴 Documentul în limba română: [README.ro.md](README.ro.md)

<p align="center">
  <img src="docs/img/ansamblu-reductor.png" alt="RCil H reducer — general assembly in CATIA V5" width="560">
  <br>
  <sub><i>General assembly of the RCil H reducer on its test-bench frame, modelled in CATIA V5.</i></sub>
</p>

---

## 1. Design brief

| Parameter | Symbol | Value |
|---|---|---|
| Input power | `P_i` | 17.5 kW |
| Input speed | `n_i` | 3000 rpm |
| Transmission ratio | `i_R` | 3 |
| Required service life | `L_h imp` | 12,000 hours |
| Shaft plane | `PA` | Horizontal (H) |
| Number of pinion teeth | `z_1` | 19 |

**Operating conditions:** vehicle lift or brake test bench; alternating external load with shocks;
driven by a squirrel-cage asynchronous electric motor; noise level max. 25 dB; environment
−20…60 °C, humidity max. 30 g/m³.

**Construction constraints:** input and output on opposite sides, solid output shaft.

---

## 2. Kinetostatic parameters

| Shaft | Power | Speed | Torque |
|---|---|---|---|
| Input (A1) | `P_1` = 17.5 kW | `n_1` = 3000 rpm | `M_t1` = 55,704 Nmm |
| Output (A2) | `P_2` = 16.62 kW | `n_2` = 1000 rpm | `M_t2` = 158,756 Nmm |

Assumed gear efficiency: `η` = 0.95.
Tooth counts: `z_1` = 19, `z_2` = 57 → recalculated ratio `u` = 3, deviation from `i_R` = **0 %**.

---

## 3. The helical gear pair

<p align="center">
  <img src="docs/img/angrenaj-cilindric.png" alt="Helical gear pair in mesh" width="440">
  <br>
  <sub><i>The gear pair in mesh: pinion <code>z<sub>1</sub></code> = 19 and wheel <code>z<sub>2</sub></code> = 57,
  helix angle &beta; = 14&deg;, centre distance <code>a<sub>w</sub></code> = 80 mm.</i></sub>
</p>

### Material and heat treatment

Since `M_t1` = 55,704 Nmm > 30,000…40,000 Nmm, a **case-hardening steel, 20TiMnCr12**, was adopted
for both wheels.

| `σ_c` | `σ_r` | Treatment | Flank hardness | Core hardness | `σ_Hlim` | `σ_Flim` |
|---|---|---|---|---|---|---|
| 850 MPa | 1100 MPa | Carburising | 60 HRC | 340 HB | 1530 MPa | 430 MPa |

Manufacturing: milling before carburising, grinding after quenching and tempering.

### Preliminary sizing and geometry

Calculated transverse module: `m_c` = max(`m_H`, `m_F`) = max(1.89 ; 1.82) = **1.89 mm** → contact
stress is the governing criterion.

| Parameter | Relation | Value |
|---|---|---|
| Normal module (standardised) | `m_n` | 2 mm |
| Transverse module | `m = m_n / cos β` | 1.889 mm |
| Helix angle | `β` | 14° |
| Pinion reference diameter | `d_1 = m·z_1` | 35.9 mm |
| Wheel reference diameter | `d_2 = m·z_2` | 107.673 mm |
| Reference centre distance | `a` | 78.32 mm |
| **Standardised centre distance** | `a_w` | **80 mm** |
| Wheel face width | `b_2` | 27 mm |
| Pinion face width | `b_1 = b_2 + 4…6` | 31 mm |

Standardisation constraint `−0.5·m_n < a_w − a ≤ m_n` → `−1 < 1.68 ≤ 2` ✔

### Profile shift (PLUS gearing)

To achieve the required centre distance together with improved contact and bending strength:

| `x_n1` | `x_n2` | `x_ns` | `α` (transverse pressure) | `α_w` (transverse working) |
|---|---|---|---|---|
| +0.4711 | +0.4278 | 0.899 | 20.5617° | 23.561° |

Tooth tip thickness check (measured on the CATIA model):
`s_1` = 0.433 mm, `s_2` = 0.973 mm > (0.3…0.45)·`m_n`/2 ✔

### Contact continuity

Transverse contact ratio, obtained by measurement on the CATIA simulation model:
`ε_αm` = (T₁B − T₁A) / `p_b` = (12.884 − 4.589) / 6.043 = **1.372**
against the calculated value `ε_α` = **1.381** → deviation **−0.65 %** ✔

### Manufacturing and assembly

| | |
|---|---|
| Accuracy grade / fit | 8 / B, backlash tolerance type *b* |
| Final machining process | Careful milling and slotting |
| Surface roughness | flank `Ra` = 0.8 μm · root fillet `Ra` = 1.6 μm |
| Lubricant | TIN 300 EP transmission oil |
| Minimum normal backlash | `j_n min` = 87 μm |
| Radial runout tolerances | `F_r` = 45 μm (pinion) · 63 μm (wheel) |
| Span measurement | 19.85 ⁻⁰·¹ ⁻⁰·¹⁶ over 3 teeth (pinion) · 66.28 ⁻⁰·¹⁸ ⁻⁰·²⁸ over 9 teeth (wheel) |
| Centre distance limit deviations | `f_a` = ±70 μm |

### Gear mesh forces

| `F_t` (tangential) | `F_r` (radial) | `F_a` (axial) |
|---|---|---|
| 2785.2 N | 1213.94 N | 694.43 N |

---

## 4. Shafts, bearings and keys

<table>
<tr>
<td width="50%"><img src="docs/img/subansamblu-arbore-intrare.png" alt="Input shaft subassembly"></td>
<td width="50%"><img src="docs/img/subansamblu-arbore-iesire.png" alt="Output shaft subassembly"></td>
</tr>
<tr>
<td align="center"><sub><b>Input shaft (A1)</b> — integral pinion, 6205 bearings, &#8960;22 &times; 36 mm shaft end</sub></td>
<td align="center"><sub><b>Output shaft (A2)</b> — gear wheel, 6213 bearings, &#8960;28 &times; 42 mm shaft end</sub></td>
</tr>
</table>

### Shafts

| | Input shaft (A1) | Output shaft (A2) |
|---|---|---|
| Material | 20TiMnCr12 (integral with the pinion) | C60 |
| Treatment | Carburised, 55…63 HRC | Quenched and tempered, 200…300 HB |
| `σ_c` / `σ_r` | 850 / 1100 MPa | 720 / 420 MPa |
| Torque | 55,704 Nmm | 158,756 Nmm |
| Allowable `τ_at` | 25 MPa | 35 MPa |
| Calculated diameter | 22.47 mm | 28.48 mm |
| **Standardised shaft end** | **⌀22 × 36 mm** | **⌀28 × 42 mm** |

### Bearings

Given moderate radial and small axial loads, **deep groove ball bearings** were adopted.

| Shaft | Designation | `d` | `D` | `B` | `C` |
|---|---|---|---|---|---|
| Input | 6205 | 35 mm | 72 mm | 17 mm | 25,500 N |
| Output | 6213 | 45 mm | 85 mm | 19 mm | 31,000 N |

Diameter of the seat under the gear wheel: `d_A2r` = `d_R2` + 10 = **55 mm**.

### Parallel key joints

Key material: **E295** (`σ_02` = 295 MPa, `σ_as` = 70…120 MPa, `τ_af` = 60…80 MPa).

| | Key I (type A) | Key II (type A) | Key III (type C) |
|---|---|---|---|
| `d` | 22 mm | 55 mm | 28 mm |
| `b × h` | 6 × 6 | 16 × 10 | 8 × 7 |
| Calculated `l_c` | 21.1 mm | 11.5 mm | 32.4 mm |
| Adopted `l` (STAS) | 28 mm | 45 mm | 50 mm |

For all three joints `l_c` < the available length → **a single key** is used in each case.

---

## 5. Verification

### Input shaft (MDESIGN 2020, *Shaft* module)

| Check | Criterion | Result |
|---|---|---|
| Combined stresses | `S_F min` ≥ 1.2 | **17.412** ✔ |
| Fatigue | `S_D min` ≥ 1.2 | **1.98** ✔ |
| Deflection at the gear | `y_x` ≤ 0.04…0.12 mm | ✔ |
| Maximum deflection | `y_max` ≤ 0.0452 mm | **0.035099 mm** ✔ |
| Maximum bearing tilt | `Θ_max` ≤ 0.97° | **0.0024505°** ✔ |
| Torsional vibration | `(0…n)` ≠ `(0.8…1.2)·f_0` | ✔ |
| Bending vibration | `(0…n)` ≠ `(0.8…1.2)·f_0` | ✔ |

Full report: [`mdesign/Raport-MDESIGN-Shaft-arbore-intrare.pdf`](mdesign/Raport-MDESIGN-Shaft-arbore-intrare.pdf)
Calculation source file: [`mdesign/Horia-verifdate.mdp.txt`](mdesign/Horia-verifdate.mdp.txt)

### Input shaft bearings (6205)

External forces: `F_rA` = 1871.70 N, `F_rB` = 2251.93 N, `F_a1` = ±694.42 N.
Influence factors (`f_0·F_a/C_0r` = 0.276, normal radial clearance CN): `e` = 0.28, `X` = 0.56,
`Y` = 1.58.

| Bearing | `F_a1/F_r` | Equivalent dynamic load |
|---|---|---|
| `L_A` | 0.371 > `e` | `P_A` = 2145.33 N |
| `L_B` | 0.308 > `e` | `P_B` = **2358.26 N** ← most heavily loaded |

Service life: `L_B` = (C/P_B)³ = **1265.8 million revolutions** → `L_h` = **7032.2 hours**.

---

## 6. Repository structure

```
.
├── cad/        the CATIA V5 models (54 files, names preserved so links do not break)
├── docs/       the technical report (PDF + DOCX)
│   └── img/    screenshots of the models and drawings, used in this README
├── date/       component and material lists, gear parameter table
└── mdesign/    the input shaft verification report
```

> [!IMPORTANT]
> All CATIA files are kept **flat, inside `cad/`, under their original names**. The `.CATProduct`
> and `.CATDrawing` files resolve their links to components by name and relative path — renaming
> them or moving them into subfolders breaks the assembly on open.

### CATIA models

**Assembly and subassemblies**

| File | Content |
|---|---|
| `Ansamblu H.CATProduct` | General assembly of the RCil H reducer |
| `Subansamblu arbore de intrare.CATProduct` | Pinion shaft + 6205 bearings + covers + seal |
| `Subansamblu arbore de iesire.CATProduct` | Output shaft + wheel + 6213 bearings + spacer |
| `Subansamblue angrenaj.CATProduct` | The complete helical gear pair |
| `Subansamblu Carcasa Inferioara.CATProduct` | Lower housing with accessories |
| `Subansamblu Carcasa Superioara.CATProduct` | Upper housing with sight glass, breather, inspection cover |
| `Model Cinematic RCil.CATProduct` | Model for the kinematic simulation of the mechanism |
| `Test carcase.CATProduct` | Fit check between the two housing halves |

**Meshing studies** (chapter 3 of the report)

| File | Content |
|---|---|
| `CATPart.3.3.3.2.1 Model dinti in angrenare.CATPart` | Tooth profiles of the **unshifted** wheels |
| `CATPart.3.3.3.2.1 Model dinti in angrenare deplasat.CATPart` | Gear pair with **profile-shifted** teeth (`x_n1` = +0.4711) |
| `CATPart.3.3.3.2.2 Model pentru simulare si verificare angrenare.CATPart` | Simulation and verification of meshing continuity |

**Main parts**

`CATPart.5.1.3 Arbore cu pinion cilindric` (pinion shaft) ·
`CAtPart.5.1.4 Arbore cu roata cilindrica` (wheel shaft) ·
`CATPart.9.5 Arbore de iesire` (output shaft) · `CATPart.9.1 Coroana pinion cilindric` (pinion rim) ·
`CATPart.9.4 Coroana roata cilindrica` (wheel rim) ·
`CATPart.11.1.1.1 Generare Carcasa inferioara H` (lower housing) ·
`CATPart.11.1.2.1 Generare Carcasa superioara H` (upper housing)

**Sealing, accessories and fasteners**

Bearing covers (1–4) · rotary seals · flat and cover gaskets · breather plug · drain plug · oil
level sight glass · inspection cover · spacer · parallel keys · locating pin · Grower washers ·
ISO 4017 / 4018 bolts and ISO 4032 nuts.

### Drawings

| File | Content |
|---|---|
| `Ansamblu HH.CATDrawing` | Assembly drawing of the reducer |
| `Desen de executie Arbore de intrare cu pinion cilindric.CATDrawing` | Detail drawing — pinion shaft |
| `Desen de executie Roata dintata cilindrica.CATDrawing` | Detail drawing — gear wheel |
| `Desen de executie arbore de iesire.CATDrawing` | Detail drawing — output shaft |
| `Format si chenar desen de ansamblu.CATDrawing` | Sheet format and border used |

<p align="center">
  <img src="docs/img/desen-ansamblu.png" alt="Assembly drawing of the reducer" width="720">
  <br>
  <sub><i>Assembly drawing — views, sections, technical conditions and the 34-item bill of materials.</i></sub>
</p>

<p align="center">
  <img src="docs/img/desen-executie-arbore-iesire.png" alt="Detail drawing of the output shaft" width="720">
  <br>
  <sub><i>Detail drawing of the output shaft (C45): dimensions, tolerances, geometric tolerances,
  surface roughness and heat treatment.</i></sub>
</p>

### Data

| File | Content |
|---|---|
| [`date/lista-componente.csv`](date/lista-componente.csv) | Bill of materials (34 items) for the assembly drawing |
| `date/lista-materiale.xls` | Material list |
| [`date/tabel-parametri-danturi-pinion.csv`](date/tabel-parametri-danturi-pinion.csv) | Gear parameter table for the pinion detail drawing |

---

## 7. Opening the files

1. **CATIA V5** (R2019 or newer) — clone the repository and open `cad/Ansamblu H.CATProduct`,
   keeping all files in the same folder.
2. **MDESIGN 2020 Second Edition**, *Shaft* module v18.0.13e — load
   `mdesign/Horia-verifdate.mdp.txt` (a UTF-16 XML file holding the calculation parameters).
3. To read the work without any licences, the PDF technical report contains screenshots of all
   models, diagrams and drawings.

```bash
git clone https://github.com/StefanHoria/Reductor-Cilindric.git
```

---

## 8. Notes on the documentation

Recorded for transparency, without altering the values in the original technical report:

- **Ch. 13 — shaft verification in MDESIGN**: the text partly carries over the values from the
  worked example in the course guide (`M_t1` = 312,071 Nmm, `n` = 625 rpm, `F_t` = 8770.6 N, steel
  18MoMnNi13) instead of this project's own data (`M_t1` = 55,704 Nmm, `n_1` = 3000 rpm,
  `F_t` = 2785.2 N, 20TiMnCr12). The reported safety factors still leave a comfortable margin.
- **Ch. 14 — bearing verification**: the calculated life `L_h` = 7032.2 hours is compared in the
  text against 11,787.94 hours, and the inequality as written (`7032.2 > 11,787.94`) does not hold
  numerically. Against the brief's required life of `L_h imp` = 12,000 hours, the result indicates
  that bearing `L_B` on the input shaft needs a higher dynamic capacity.
- Ch. 6.5 mentions `m_n` = 2.5 mm in the minimum-backlash relation and a centre distance of 180 mm
  in the tolerance customisation, whereas the rest of the project uses `m_n` = 2 mm and
  `a_w` = 80 mm.

---

## 9. References

1. Jula, A. et al. — *Organe de mașini*, vol. I, II. University of Brașov, 1986, 1989.
2. Mogan, Gh. et al. — *Organe de mașini. Teorie – Proiectare – Aplicații*. Transilvania University of Brașov Press, 2012.
3. Moldovean, Gh. et al. — *Angrenaje cilindrice și conice. Calcul și construcție*. LuxLibris, Brașov, 2001.
4. Moldovean, Gh. et al. — *Angrenaje cilindrice și conice. Metodici de proiectare*. LuxLibris, Brașov, 2002.
5. Rădulescu, C. — *Organe de mașini*, vol. I, II, III. Transilvania University of Brașov, 1985.
6. \*\*\* — *Culegere de norme și extrase din standarde pentru proiectarea elementelor componente ale mașinilor*, vol. I, II. University of Brașov, 1984.

---

## License

Academic work published for portfolio purposes. The content may be read and cited with attribution
to the author; it is not intended for commercial reuse or for submission as someone else's own work.
