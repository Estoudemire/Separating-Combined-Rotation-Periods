# Separating-Combined-Rotation-Periods
## What does it do?

This code analyzes archival TESS light curves of two closely separated M-dwarf binary systems, TIC 172517058 (Freya) and TIC 148611095 (Tyr), to separate their combined brightness variations and determine the individual rotation periods of each star.

The brightness variations, or "wiggles," in a star's light curve are caused by sunspots and contain information about its rotation. In closely separated binary systems, the signals from both stars are combined, making their individual rotation periods difficult to distinguish.

---

## How does it work?

1. The algorithm retrieves archival TESS data on the chosen target using lightkurve
2. A Lomb–Scargle periodogram is used to find the most likely rotation period of the primary star.
3. A simulated light curve is created using the hypothesized period. Its amplitude is constrained using the relative flux contributions of the two stars.
4. The simulated light curve is subtracted from the original combined light curve, leaving the secondary star's signal along with any remaining variability.
5.  A second Lomb–Scargle periodogram is applied to the residual data to find the most likely rotation period of the secondary star.
6. A second simulated light curve is created using the estimated secondary rotation period.

---

## Results

The algorithm successfully identified rotation periods for both stars in the Freya and Tyr systems:

| Rotation Period | Freya | Tyr |
|---|---:|---:|
| Primary Star | 2.509 days | 4.870 days |
| Secondary Star | 1.672 days | 2.027 days |

To test the accuracy of the method, the simulated light curves were recombined and compared with the original combined signals. The algorithm was also tested using artificially combined light curves from stars with known rotation periods. The recovered periods were consistent with the known values, with an uncertainty of ±0.0617 days.

---

## Files
- `Seperating_Rotation_Periods_Freya.ipynb` — Analysis of the Freya binary system.
- `Seperating_Rotation_Periods_Tyr.ipynb` — Analysis of the Tyr binary system.
- `finalPosterEmmaStoudemire-2.pdf` — Research poster describing the project.
