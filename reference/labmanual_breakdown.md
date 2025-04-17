### Nitrogen‑Vacancy (NV) Center Advanced‑Lab — Integrated Experimental Report  
*(based exclusively on the Harvard APL manual, 23 pp.)* citeturn0file0

---

## 0 Context & Goals  

Nitrogen‑vacancy centers in diamond offer a room‑temperature platform where a *single* electronic spin and its associated single‑photon optical transition can be prepared, coherently manipulated and read out. The Harvard advanced‑lab sequence teaches students to  

* map and isolate individual NVs with a scanning confocal microscope,  
* prove single‑photon emission by measuring second‑order correlations,  
* observe and exploit optically detected magnetic resonance (ODMR) of a single spin,  
* time‑domain‑control that spin with Rabi, Ramsey and Hahn‑echo pulse sequences, and  
* connect these observations to quantum information, sensing and basic quantum‑optics concepts. citeturn0file0  

---

## 1 Experimental Modules – Step‑by‑Step  

| # | Measurement | Central physics | Concrete implementation | Key observables |
|---|-------------|-----------------|-------------------------|-----------------|
| **1** | **Confocal mapping & NV identification** | Point‑spread function, dipole selection rules, photoluminescence (PL) saturation of a two‑level system | 532 nm DPSS laser (≈3 mW at objective) is raster‑scanned by dual‑axis galvanometers; PL (650–800 nm) is collected through the same objective, filtered and coupled into single‑mode fibre → two avalanche photo‑diodes (APDs). Use LabVIEW *Galvo Scan* and *Optimize* controls to centre on the brightest pixel and repeat every few minutes to compensate drift. | (i) XY PL map; (ii) saturation curve vs laser power. |
| **2** | **Single‑photon statistics** — *g²(τ)* | Quantum light field: antibunching ( g²(0) < 0.5 ) proves emission from a *single* quantum emitter | Fibre splitter sends equal PL to both APDs → PicoQuant TimeHarp 200 records time interval histogram (64 ps bins). Insert 25 m coax on *SYNC* channel to move the zero‑delay region away from detector dead‑time. Typical acquisition: 1 s per sweep, 4096 bins, repeated ≥10⁴ times. | Normalised second‑order function *g²(τ)* with a dip at τ = 0; fit width → excited‑state lifetime *1/Γ* and determine optical pumping rate. |
| **3** | **Continuous‑wave ODMR / Zeeman splitting** | Ground‑state spin triplet (m_s = 0, ±1) split by 2.87 GHz + γ_e B; microwave‑induced spin mixing lowers PL (spin‑dependent ISC) | 20 µm Cu wire above sample driven by microwave synthesiser (2.8–3.0 GHz). LabVIEW sweeps frequency while laser remains on. Permanent magnet on 3‑axis stage provides B‑field; Hall probe or NV itself calibrates B∥. Reduce laser (<1 mW) & microwave power (< ‑25 dBm source, no amp) to resolve 14N hyperfine triplet (±2.2 MHz). | ODMR dip positions vs B (γ_e ≈ 2.8 MHz G⁻¹); linewidth vs optical & MW power; resolved 14N hyperfine splitting. |
| **4** | **Rabi oscillations** (driven rotations) | Coherent drive of a two‑level system: population sin²(Ω_R t/2) with Ω_R ∝ B₁ | Pulse‑blaster gates the microwave amplifier while AOM is *off*. Vary MW pulse duration (e.g. 0–5 µs in 50 ns steps) at fixed power. A green read‑out pulse (3 µs) follows, with two counting windows (0–0.5 µs signal, 2.4–2.9 µs reference) to normalise shot‑to‑shot drift. | PL contrast vs pulse length; extract Ω_R, calibrate π and π/2 pulses. |
| **5** | **Ramsey fringes** (free‑induction decay) | Dephasing time T₂*: coherence of superposition during field fluctuations; detuning Δ gives fringe frequency | π/2 – τ – π/2 sequence with τ swept (0.1–10 µs). Use calibrated π/2 from step 4. Fit envelope exp[‑(τ/T₂*)²] (Gaussian bath) and beat pattern from 14N hyperfine ± 2.2 MHz. | T₂* (few µs in type IIa diamond), hyperfine beats resolve. |
| **6** | **Hahn‑echo (spin‑echo)** | Static inhomogeneity refocused; coherence time T₂ >> T₂* | π/2 – τ – π – τ – π/2. Sweep τ (0.1–200 µs). Same read‑out scheme. | Echo amplitude vs 2τ → T₂ (tens–hundreds µs). Collapse‑and‑revival from ¹³C Larmor precession may appear. |

*(All equipment names, timings and GUI labels are verbatim from the manual.)* citeturn0file0  

---

## 2 Underlying Physics — Deeper Notes  

* **Optical excitation & ISC** – Fig. 2 on p. 2 shows vibronic pumping at 532 nm, rapid phonon relaxation, and a spin‑selective inter‑system crossing (ISC) through a metastable singlet. This funnels population into the bright *m_s = 0* ground state → optical polarisation & spin‑dependent fluorescence. citeturn0file0  
* **Antibunching model** – Rate equations yield g²(τ)=1‑exp[‑(Γ+k)τ] where Γ is radiative decay and k is pump rate; fitting the *width* of the dip therefore returns Γ and its *depth* reveals background counts. citeturn0file0  
* **ODMR contrast** – Continuous green light keeps re‑polarising the spin; resonant MWs constantly mix it back → steady‑state reduction of bright‑state population proportional to Ω_R²/(Ω_R²+Δ²+Γ_optΓ_s). citeturn0file0  
* **Pulse sequences** – Page 8 Figure 5 sketches Rabi, Ramsey & spin‑echo timing; these are implemented verbatim via the SpinCore PulseBlaster ESR‑PRO‑400 (2.5 ns resolution). citeturn0file0  
* **Hyperfine interaction** – Hamiltonian \(H_{\text{hf}}=A_{\parallel}\,I_zS_z+A_{\perp}(I_xS_x+I_yS_y)+P(I_z^2- \tfrac23 I(I+1))\); quadrupole term splits *m_I = 0* from *±1* by 5 MHz; electron‑nuclear flip‑flops forbidden in ESR, giving three allowed MW lines separated by ~2.2 MHz. citeturn0file0  

---

## 3 Implementation Details & Practical Tips  

| Subsystem | Critical alignments / parameters | Typical numbers |
|-----------|----------------------------------|-----------------|
| **Laser & AOM** | Fibre‑coupled ND:YAG 532 nm; AOM rise ≈ 100 ns, so set *AOM Delay* ≈ 400 ns before read‑out window. | 3 mW at objective (confocal); 0.5–1 mW for ODMR linewidth tests. |
| **Galvos & Piezo Z** | Keep scan range ≤ 0.2 V (≈ 8 µm). Use *Optimize* every ~5 min; *NV‑lock* for long acquisitions. | PZT voltage step 0.5 V ≈ 50 nm focal shift. |
| **Microwave chain** | Synthesiser 2.87 GHz ± sweep, 0 dBm → RVA‑33 ×2 → +45 dB amp → 20 µm wire. Keep amp *off* until final tune‑up. | Rabi π‑pulse: 30–100 ns (‑21 dBm source) for NVs under the wire. |
| **TimeHarp g²** | Resolution: 64 ps; Acquisition: 1 ms × 10⁴; Channel0 (SYNC) level 100 mV, Channel1 (STOP) 50 mV. Monitor APD count to keep <200 k s⁻¹ to avoid pile‑up. | 25 m coax gives 120 ns delay → g²(0) shows at +120 ns in histogram. |

---

## 4 Conclusions & Expected Outcomes  

By the end of the sequence students will have:

1. **Observed single‑photon emission** and extracted the NV’s excited‑state lifetime and optical pumping rate.  
2. **Calibrated and controlled a single electronic spin** at room temperature, measuring γ_e and 14N hyperfine constants.  
3. **Quantified dephasing and decoherence** (T₂*, T₂) and seen how a Hahn echo extends coherence.  
4. Recognised how *optical*, *electronic* and *microwave* engineering intersect in modern quantum‑hardware labs. citeturn0file0  

---

## 5 Miscellany & Safety  

* **Laser class** – treat as Class 3R; wear OD > 5 goggles if the main 532 nm beam path is open.  
* **Electrical** – Microwave amp delivers up to 13 W; always terminate 50 Ω load when the wire is disconnected.  
* **Diamond sample** – Oil‑immersion objective (NA 1.3) sits 0.2 mm from surface; avoid scanning dry to protect both lens and sample.  
* **Data management** – LabVIEW auto‑saves TimeHarp histograms only if *Save Data* switch is *ON* **before** starting the run.  
* **Reference compendium** – Full component datasheets and block‑diagrams listed in *Bench Notes* section (pp. 21–23) for troubleshooting. citeturn0file0  

---

*Report prepared for the 20XX Advanced Physics Laboratory cohort. Direct page/figure references correspond to the original Harvard PDF manual.*