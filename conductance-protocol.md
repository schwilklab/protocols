Conductance and Vulnerability Curve Protocol
============================================

Dylan Schwilk, Tailor Brown, Josh Willms. See also Dr. Anna Jacobsen's good webpage of protocols.  We learned our hydraulics from Dr. Jacobsen and Dr. Pratt largely.

Overview and materials
----------------------

### Overview ###
"Conductance" is a property of a conductor, in our case, the xylem of a stem segment.  We are usually interested in "Conductivity," K, which is the conducting proporty of a material (eg the xyelm tissue of a particular tree species).  We most often report sapwood specific conductivity, K_s, which is the conductance of a stem segment X the length of the segment / the sapwood area of the segment.  

Conductance influences rate of water flow through a stem segment:

Flow rate = Conductance *  Pressure differential

Therefore, if we apply a known pressure differential and measure the flow rate, we can calculate conductance

C = F/P

Xylem vulnerability to drought

Conductance dorps as xelem vessels embolize.  The pattern of conductance loss as a function of decreasing water potential is known as a vulnerability curve.  We can create such a curve in multiple ways:

1. TODO
2. TODO
3. Using the centrifuge method (what we usually do)

All calculations are provided as R code in [hydro.R](https://github.com/schwilklab/skyisland-traits-distro/blob/master/traits/conductance/hydro.R)


Stem collection and preparation
-------------------------------

### Collection ###

Label the collection by collection date, site, tree tag, and species (using the USDA species codes)

TODO

Collect under water (degassed KCl if available)

### Stem preparation and measurements ###

NOTE: Keep stem ends under water (dilute KCl at all times). Transfer cut stems in completely solution-filled ziplock bags to avoid any air contnct with cut ends.

1. [ ] Cut the stem segment under water to ~13.5 cm long. Record actual length in stem file.
2. [ ] Save all distal leaves and bag them together in a ziplock labeled with stem id, tree tag, species code and date
3. [ ] Within 2-4 days of collection: Measure total distal leaf area in cm^2 (required), bag leaves for drying. Get dry weights (not required). Record in stem file.
4. [ ] Within 2-4 days of collection. Measure stem distal sapwood area.  Use the distal stem segment cut away to avoid dealing with the 13.5 cm segment used for conductance.  Measure distal stem diameter, Ds (excluding bark and phloem). Record.  Then measure pith diameter, Dp, and record.  Sapwood area is pi*(.5*Ds)^2 - pi(0.5*Dp)^2. Record in diameters in stem file. See [[file:stem-sheet-for-entry.xls][stem-sheet-for-entry.xls]]



Native conductance and flushing
-------------------------------

### Native conductance ###

In order to produce a vulnerability curve, we must measure conductances under a range of water potentials.  We can create these water pontetials by spinning a stem in a centrifuge, or we can allow natural drought condtions to create them.  If we harvest a stem predawn and under water, and if we ahve recent middy and predawn water potentials measured on that plant, then we can create a "native conductance" point on a vulnerability curve.

** Flushing
To remove all native embolisms, we flush the stem under a pressure head of about 75-100 KPa for 45 min. [CHECK?]

We use a "captive air tank" to apply the water pressure.  The tank contains a rubber bladder which we fill with our KCl solution.  A Schrader valve allows us to attach a regulated air source (we use a nitrogen tank with a regulator turned down to the correct pressure)

Cleaning and preparing conductance measurement and flushing system
------------------------------------------------------------------

### Cleaning ###

Clean every X days with dilute bleach (X per X).  Never allow bleach solution to touch the filter.

Flush system with distilled water before adding bleach solution because bleach contacting KCl will cause a precipitate

### Solution and prep. ###

If possible, only degassed KCl solution sould touch the stem.  This is especially importnat for flsuhing and measuremnt (both times when solution is pushed through the stem.

X mm KCL

Degassing:  Mix the KCl in a vacuum-ready carboy. Use a stir rod and magnetic stir plate  to agitate the mxture while vacuum is applied.  Pull vacuum to approx -22"Hg and then disconnect and shut down vacuum pump (allow pump to run for 2 minutes pulling air and no vacuum to cool down before switchting off).  20 minutes of stiring under vacuum should be sufficient to degas.

Anytime the carboy is opened, pull vacuum and degas the solution


Conductance measurements
------------------------

We push a dilute KCl solution through the stem at a very low pressure created by a height differential between the water level in the beaker on the balance and the water level in the IV bag held about 70cm higher.  Two "sight tubes" allow us to acurately read the height at these two locations by opening valves to equalize the pressure between the sight tube and either the beaker ("balance height") or the IV bag ("head height").

### Pre-measurement prep ###

1. [ ] Start with clean system (see cleaning, above).
2. [ ] Prepare degassed KCl solution.  Have some solution always ready as backup.  [TODO]

### Conductance measurement steps ###

1. [ ] Start a new data sheet and record the tree tag, species code, stem id, your name and the date. Record the stem length.  [[file:curve-sheet-for-entry.xls][Vulnerability curve data sheets]]
2. [ ] Clear the conductance tubing of all bubbles
3. [ ] Open valves to allow slow flow into the proximal end tube and insert the proximal end of the stem in this tube. Clear all bubbles that may cling to the stem and grommet and clamp the tube lightly.
4. [ ] Attach the distal end similarly. See valve diagram [TODO]
5. [ ] Double check: NO BUBBLES. The system will not work with any bubbles
6. [ ] Start the balance communication software "hydro-balance.py".  Navigate to the "balance folder" on the balance computer via terminal ("> cd balance") then start he software ("> ./hydro-balance-py").  You can change the default update interval and averaging times with options at the command line
7. [ ] Set valves for background flow.  This measures flow across the stem under NO head pressure (balance height equilized with balance height sight tube.  Wait at least x minutes for the flow to stabilize. The flow should be slightly negative and the absolute value should be less than 0.00005 g/s.  If the flow is larger than that (positive or negative) there is a leak that must be fixed before you continue. Record the background flow on the data sheet ("flow.bg.pre"). Record the balance fluid height as measured at the sight tube ("height.balance.pre").
8. [ ] Turn the valves to the "flow measurement position (TODO DIAGRAM). Wait for the flow to stabilize. Record the flow rate (g/s) as "flow".
9. [ ] Measure the fluid temperature and record under "temp".
10. [ ] Turn the valves to "background flow" (TODO DIAGRAM).  Measure "flow.bg.post" and "height.balance.post"
11. [ ] Turn valves to off position and remove the stem (keeping it under water)


Centrifuge method of inducing embolism/cavitation
-------------------------------------------------

### Applying xylem tension via centrifuge ###

We can spin a stem in a custom-made centrifuge rotor (for a Sorvall centrifuge) in order to create tension in th xylem.  The stem ends must be kept under water.  L-shaped plastic wells filled with degassed KCl allow the solution to move up to cover the stem end as we spin.  It is impossible to avoid some air exposure, so we use small make-up sponges in the wells to keep the end moist during the time while the stems are being placed in the rotor.

To calculate the tension in Pa produced by spinning at a given RPM, convert RPM to radians per minutes squared, multiply by the radius of the spinning arm (1/2 the distance from water surface to water surface in the wells when spinning) squared then multiply by the density of water and divide by 2. So to get the value in MPa:

mpa = -0.000001  * ( (RPM*2*pi / 60)^2 * r^2 * waterdensity) / 2 )

This is the greatest tension created at the tips of the stem.  See [[file:hydro.R][hydro.R]]

### "Fatigue correction" ###

Some species such as oaks, will show conductance loss at by high water potentials --- higher than ever observed in nature.  This implies that flushing fills some vessels that are never filled in a living plant.  These have been termed "fatigued" vessels.  If we calculate percentloss conductivity based on a maximum conductivity measured just after flushing, then we would show losses that are not real.  To correct for this, we can spin at a very gentle tension (say -0.25 MPa), then count the subsequent conductance measurement as the "fatigue corrected" maximum conductance. 

Alternatively, we can avoid flushing all together and collect stems under very hydrated natural conditions.


### Vulnerability curve checklist ###
1. [ ] Prepare stem (see )
2. [ ] IF OBTAINING NATIVE POINT:
   Measure conductance (see above) and record
4. [ ] IF FLUSHING:
   Flush stem (see above)
5. [ ] Spin stem at next RPM point and remeasure.  Do this until measure flow drops to near background

[TODO]
