<style>

/* I know one of you fuckers are going to inspect this. */

:root {
  --upwell-cyan: #5de0ff;
  --upwell-deep: #0a1a24;
  --upwell-bg: #02070d;
  --panel-bg: rgba(10, 20, 30, 0.78);
  --panel-border: rgba(80, 180, 255, 0.3);
  --text-primary: #e6f7ff;
  --text-secondary: #9db4c9;
}

body {
  margin: 0;
  background: linear-gradient(160deg, #02070d 0%, #040b12 60%, #000000 100%);
  background-attachment: fixed;
  color: var(--text-primary, #e5e7eb);
  font-family: "Inter", system-ui, sans-serif;
  overflow-x: hidden;
}


body::before {
  content: "";
  position: fixed;
  inset: 0;
  pointer-events: none;
  background:
    radial-gradient(circle at 20% 10%, rgba(90, 210, 255, 0.18), transparent 55%),
    radial-gradient(circle at 80% 70%, rgba(160, 120, 255, 0.12), transparent 70%);
  z-index: -2;
}


body::after {
  content: "";
  position: fixed;
  inset: 0;
  pointer-events: none;
  background: repeating-linear-gradient(
    to bottom,
    rgba(255, 255, 255, 0.015),
    rgba(255, 255, 255, 0.015) 1px,
    transparent 3px
  );
  opacity: 0.12; /* was 0.; now actually visible but subtle */
  z-index: -1;
}


.container {
  max-width: 1250px;
  width: 92%;
  margin: 2.5rem auto;
  padding: 2rem 2.5rem;

  background: var(--panel-bg);
  backdrop-filter: blur(8px);
  border-radius: 16px;

  border: 1px solid var(--panel-border);
  box-shadow:
    0 0 25px rgba(0, 180, 255, 0.15),
    0 0 120px rgba(0, 150, 255, 0.08);

  position: relative;
}


.container::before {
  content: "";
  position: absolute;
  top: -2px;
  left: -2px;
  width: 30px;
  height: 30px;
  border-top: 2px solid var(--upwell-cyan);
  border-left: 2px solid var(--upwell-cyan);
  opacity: 0.35;
}

.container::after {
  content: "";
  position: absolute;
  bottom: -2px;
  right: -2px;
  width: 30px;
  height: 30px;
  border-bottom: 2px solid var(--upwell-cyan);
  border-right: 2px solid var(--upwell-cyan);
  opacity: 0.35;
}


h1, h2, h3 {
  color: var(--upwell-cyan);
  letter-spacing: 0.5px;
  text-shadow: 0 0 8px rgba(90, 200, 255, 0.5);
}

h1 {
  font-size: 2.2rem;
  margin-bottom: 1rem;
}
h2 {
  font-size: 1.6rem;
  margin-top: 2rem;
}


.table-wrapper {
  overflow-x: auto;
  margin: 1.5rem 0;
}

table {
  width: 100%;
  border-collapse: collapse;
  min-width: 760px; /* was 900px */
  background: rgba(0, 10, 16, 0.6);
  border: 1px solid rgba(70, 140, 200, 0.3);
  border-radius: 12px;
  overflow: hidden;
}


th, td {
  padding: 10px 14px;
  border: 1px solid rgba(80, 120, 160, 0.25);
  white-space: nowrap;
}

th {
  background: rgba(10, 30, 45, 0.8);
  font-weight: 600;
  color: var(--upwell-cyan);
  text-shadow: 0 0 5px rgba(90, 200, 255, 0.4);
}

tbody tr:nth-child(odd) td {
  background: rgba(5, 15, 25, 0.65);
}

tbody tr:nth-child(even) td {
  background: rgba(3, 10, 18, 0.65);
}

/* ROW HOVER EFFECT */
tbody tr:hover td {
  background: rgba(20, 60, 90, 0.45) !important;
  transition: 0.2s ease;
}


@keyframes particles {
  0% { transform: translateY(0); opacity: 0.5; }
  100% { transform: translateY(-600px); opacity: 0; }
}

.particle {
  position: fixed;
  width: 2px;
  height: 2px;
  background: rgba(130, 200, 255, 0.9); /* alpha fixed */
  border-radius: 50%;
  top: 100%;
  animation: particles 12s linear infinite;
  pointer-events: none;
  z-index: -1;
}

/* Optional subtle “grid drift” animation */
@keyframes grid-drift {
  from { background-position: 0 0, 0 0, 0 0, 0 0, 0 0; }
  to   { background-position: 10px 10px, -10px -10px, 0 0, 0 0, 0 0; }
}
.bg-upwell-grid {
  animation: grid-drift 40s linear infinite;
}

/* ===============================
   ADVANCED EVE HOLOGRAM EFFECT – PETER SCYRO LOGO
   =============================== */

.eve-logo {
  position: fixed;
  top: 16px;
  left: 20px;
  z-index: 9999;
  user-select: none;
  pointer-events: none;
  transform-style: preserve-3d;
  perspective: 800px;
}

/* Main Text — hologram base */
.eve-logo-text {
  font-family: "Eurostile", "Bank Gothic", "Square 721", system-ui, sans-serif;
  letter-spacing: 4px;
  text-transform: uppercase;
  font-weight: 600;
  fill: #9acbff;
  filter: drop-shadow(0 0 6px rgba(100, 180, 255, 0.45));
  animation: holoPulse 2.8s ease-in-out infinite,
             holoFloat 8s ease-in-out infinite,
             holoFlicker 6s steps(80) infinite;
}

/* --- Pulsing brightness glow --- */
@keyframes holoPulse {
  0%   { opacity: 0.85; filter: drop-shadow(0 0 6px rgba(80,150,255,0.4)); }
  50%  { opacity: 1;    filter: drop-shadow(0 0 14px rgba(140,220,255,0.7)); }
  100% { opacity: 0.9;  filter: drop-shadow(0 0 6px rgba(80,150,255,0.4)); }
}

/* --- Floating hologram drift --- */
@keyframes holoFloat {
  0%   { transform: translateY(0) translateZ(0); }
  50%  { transform: translateY(-1.5px) translateZ(6px); }
  100% { transform: translateY(0) translateZ(0); }
}

/* --- Random flicker (subtle) --- */
@keyframes holoFlicker {
  0%, 7%, 9%, 11%, 100% { opacity: 1; }
  8%, 10%              { opacity: 0.6; }
}

/* HOLOGRAM SCANLINES OVERLAY ON LOGO */
.eve-logo::after {
  content: "";
  position: absolute;
  inset: 0;
  background: repeating-linear-gradient(
      to bottom,
      rgba(120, 180, 255, 0.11) 0px,
      rgba(120, 180, 255, 0.11) 1px,
      transparent 3px,
      transparent 5px
    );
  mix-blend-mode: screen;
  opacity: 0.35;
  animation: scanShift 6s linear infinite;
  pointer-events: none;
}

@keyframes scanShift {
  0%   { transform: translateY(0); }
  100% { transform: translateY(6px); }
}

/* HOLOGRAM DISTORTION WAVES (subtle) */
.eve-logo::before {
  content: "";
  position: absolute;
  inset: -10px;
  background: radial-gradient(
      circle at 50% 50%,
      rgba(100, 180, 255, 0.15) 0%,
      rgba(0, 0, 0, 0) 70%
    );
  filter: blur(18px);
  animation: holoDistort 5s ease-in-out infinite;
  pointer-events: none;
  z-index: -1;
}

@keyframes holoDistort {
  0%   { transform: scale(1); opacity: 0.3; }
  50%  { transform: scale(1.05); opacity: 0.5; }
  100% { transform: scale(1); opacity: 0.3; }
}

@media (min-width: 1600px) {
  .container {
    max-width: 92vw;
  }
}

  
</style>


---
EVE Online Sales & Such
---

## Mastery Packs

| Mastery | Plex Price | Omega (days) | Hypercore |        SP | MCT | Character Resculpt | Boosts                 | Skill Extractors | Cost/Month |       Selling MRC | Selling Extractors (450m) |
| ------: | ---------: | -----------: | --------: | --------: | --: | -----------------: | ---------------------- | ---------------: | ---------: | ----------------: | ------------------------: |
|   **1** |     150.00 |            7 |       N/A |   250,000 | N/A |                N/A | 1× Genius Accel        |              N/A |        N/A |               N/A |                       N/A |
|   **2** |     325.00 |           14 |       N/A |   500,000 | N/A |                N/A | 1× Expert, 1× Standard |              N/A |     $11.00 |               N/A |                       N/A |
|   **3** |     875.00 |           60 |       N/A |   750,000 | N/A |                N/A | 2× Specialist Accel    |              N/A |     $15.00 |               N/A |                       N/A |
|   **4** |   1,875.00 |           90 |       N/A | 1,250,000 |   2 |                N/A | 2× Advanced Accel      |                1 |    $625.00 |               N/A |           ISK 450,000,000 |
|   **5** |   4,000.00 |          180 |     1,000 | 1,750,000 |   3 |                  3 | 2× Standard Accel      |               10 |    $333.33 | ISK 8,100,000,000 |         ISK 4,500,000,000 |

## Plex Sale

| Plex Amount |     USD | Plex / USD | USD (MarkeeDragon) | Plex / USD (MD) | Plex Delta |
| ----------: | ------: | ---------: | -----------------: | --------------: | ---------: |
|       1,000 |  $36.00 |      27.78 |             $34.92 |           28.64 |       0.86 |
|       1,500 |  $52.00 |      28.85 |             $50.44 |           29.74 |       0.89 |
|       3,000 | $100.00 |      30.00 |             $97.00 |           30.93 |       0.93 |
|       6,000 | $192.00 |      31.25 |            $186.24 |           32.22 |       0.97 |
|      12,000 | $336.00 |      35.71 |            $325.92 |           36.82 |       1.10 |
|      20,000 | $520.00 |      38.46 |            $504.40 |           39.65 |       1.19 |

## NES Omega Sale

| Time (Months) | Plex Amount | USD (20k Plex) | USD (20k Plex – MarkeeDragon) |
| ------------: | ----------: | -------------: | ----------------------------: |
|             1 |         500 |         $13.00 |                        $13.58 |
|             3 |       1,200 |         $31.20 |                        $30.26 |
|             6 |       2,100 |         $54.60 |                        $52.96 |
|            12 |       3,600 |         $93.60 |                        $90.79 |
|            24 |       6,600 |        $171.60 |                       $166.45 |

## EVE Store Omega Prices

| Time (Months) |     USD |
| ------------: | ------: |
|             1 |  $20.00 |
|             3 |  $48.00 |
|             6 |  $84.00 |
|            12 | $144.00 |
|            24 | $264.00 |

## Mastery Packs (Selling MRC if Unbounded)

| Mastery | Plex Price | Omega (days) | Hypercore |        SP | MCT | Character Resculpt | Boosts                 | Skill Extractors | Cost/Month |       Selling MRC | Selling Extractors |
| ------: | ---------: | -----------: | --------: | --------: | --: | -----------------: | ---------------------- | ---------------: | ---------: | ----------------: | -----------------: |
|   **1** |     150.00 |            7 |       N/A |   250,000 | N/A |                N/A | 1× Genius Accel        |              N/A |        N/A |               N/A |                N/A |
|   **2** |     325.00 |           14 |       N/A |   500,000 | N/A |                N/A | 1× Expert, 1× Standard |              N/A |     $11.00 |               N/A |                N/A |
|   **3** |     875.00 |           60 |       N/A |   750,000 | N/A |                N/A | 2× Specialist Accel    |              N/A |     $15.00 |               N/A |                N/A |
|   **4** |   1,875.00 |           90 |       N/A | 1,250,000 |   2 |                N/A | 2× Advanced Accel      |                1 |    $625.00 |               N/A |    ISK 450,000,000 |
|   **5** |   4,000.00 |          180 |     1,000 | 1,750,000 |   3 |                  3 | 2× Standard Accel      |               10 |    $333.33 | ISK 8,100,000,000 |  ISK 4,500,000,000 |


## Mastery Packs — Applied Plex Sale (20k Plex Bought)

| Mastery | Plex Price |     USD | USD (MarkeeDragon) |
| ------: | ---------: | ------: | -----------------: |
|   **1** |        150 |   $3.90 |              $3.78 |
|   **2** |        325 |   $8.45 |              $8.20 |
|   **3** |        875 |  $22.75 |             $22.07 |
|   **4** |      1,875 |  $48.75 |             $47.29 |
|   **5** |      4,000 | $104.00 |            $100.88 |

