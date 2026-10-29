<h1>MAGNADIAN - Mini-MPR Framework for Emerging Contaminant Detection</h1>

<h2>Description</h2>
MAGNADIAN is a low-cost, portable mini magnetic particle relaxometer (mini-MPR) built as a University of Waterloo Nanotechnology Engineering capstone project. It combines tunnel magnetoresistance (TMR) sensors with functionalized magnetic nanoparticles (MNPs) to detect and quantify contaminants. As a proof of concept, it targets micro- and nanoplastic (polyamide) contamination in hydrogen peroxide manufacturing.
<br />
<br />
<p align="center">
  <img src="https://i.imgur.com/goEOfI8.png" height="80%" width="80%" alt="CAD model of MAGNADIAN" />
  <br />
  <em>CAD model of MAGNADIAN</em>
</p>

<h2>The Problem</h2>

Industrial contamination hurts both people and businesses:

- Modern pollutants cause more than <b>6 million premature deaths</b> a year, and fewer than one fifth of approved chemicals have sufficient exposure data.
- One Siemens estimate puts losses from unexpected downtime at over <b>$1.4 trillion</b> annually.
- Existing detection methods (VSM, NMR, FTIR, GC-MS) are generally expensive, bulky, immobile, or need specialized training, which makes routine monitoring hard for smaller operators and under-resourced communities.

Some hydrogen peroxide processes use plastic-based filters that break down in the harsh chemical environment and shed polyamide particles. This is a known industry issue classified as an emerging contaminant, which made it a realistic test case.

<h2>Solution</h2>

MAGNADIAN was designed to be:

- <b>Inexpensive:</b> $160 in materials per unit
- <b>Portable:</b> compact 3D-printed enclosure
- <b>Easy to use:</b> minimal steps, with analysis handled by an Arduino and the result shown on an LCD
- <b>Adaptable:</b> the same sensing framework can target new contaminants by changing the nanoparticle coating

<h2>Components and Equipment</h2>

- <b>TMR sensors</b> (MDT2104)
- <b>Fe₃O₄ nanoparticles</b>
- <b>Arduino</b>
- <b>PSpice</b>
- <b>FTIR, DLS, VSM</b>
- <b>CAD</b> (3D-printed enclosure)

<h2>Prototype Components</h2>

<p align="center">
<img src="https://i.imgur.com/2wUxoLp.png" height="80%" width="80%" alt="Components of MAGNADIAN"/>
<br />
<em> Components of MAGNADIAN </em>
</p>

| Component | Role |
| --- | --- |
| Portable 3D-printed enclosure | Houses the sensing setup |
| Glass microvial | Contains samples |
| Functionalized MNPs | Target contaminants |
| MDT2104 TMR sensors | Detect the magnetic response |
| Amplifier circuit | Boosts the TMR output |
| Mu-metal | Shields external magnetic fields |
| NdFeB magnet | Provides the magnetic field |
| Arduino | Calculates the contaminant concentration |
| LCD | Displays the concentration reading |

<h2>How it works:</h2>


<b>1. Functionalized nanoparticles</b> <br/>
Iron oxide (magnetite, Fe₃O₄) nanoparticles are coated with a ligand that binds the target contaminant. For polyamide in hydrogen peroxide, a silane-PTFE coating is used. It is hydrophobic, charged in acidic conditions, and resistant to degradation. Plain magnetite reacts with hydrogen peroxide (Fenton reactions), so the coating also protects the particles.
<br />
<br />
<b>2. Magnetization</b> <br/>
A sample in a glass capillary microvial is exposed to a strong NdFeB permanent magnet, which magnetizes the nanoparticles.
<br />
<br />
<b>3. Sensing</b> <br/>
Two TMR sensors (MDT2104) detect the magnetic response, which is proportional to the amount of nanoparticles present, and so to the amount of bound contaminant. Mu-metal shielding blocks external magnetic fields.
<br />
<br />
<b>4. Signal processing</b> <br/>
An instrumentation amplifier boosts the very small sensor signal, and a low-pass filter removes noise. A voltage divider shifts the signal midpoint so the Arduino doesn't clip negative values. The Arduino then digitizes the signal.
<br />
<br />
<b>5. Measurement protocol</b> <br/>
Three readings are taken: pure functionalized nanoparticles (background), pure contaminant aliquot (background), and the combined sample. The Arduino processes the final reading against both backgrounds and displays the concentration on the LCD.
</p>

<h2>Experiments and Results</h2>

<ul>
  <li>
    <b>Microplastic generation:</b> An industrial polyamide-coated filter was degraded in hydrogen peroxide under three conditions (room temperature, heat, and heat with stirring) over 6 days. FTIR showed the amide II peak growing over time, confirming realistic contaminant samples.
    <p align="center">
      <img src="https://i.imgur.com/4KEyNcu.png" height="80%" width="80%" alt="Components of MAGNADIAN"/>
    </p>
    <p align="center">
      <img src="https://i.imgur.com/dPFBQo6.png" height="80%" width="80%" alt="Components of MAGNADIAN"/>
    </p>
  </li>
  <li>
    <b>Nanoparticle coating:</b> Dynamic light scattering showed the silane-PTFE coating reduced particle agglomeration by about 200 nm. VSM showed it also reduced magnetic response, a trade-off between stability and signal strength.
    <p align="center">
      <img src="https://i.imgur.com/w54CxW5.png" height="80%" width="80%" alt="Components of MAGNADIAN"/>
    </p>
  </li>
  <li>
    <b>Electronics:</b> A PSpice simulation of the amplifier circuit predicted a gain of 1.22 mV/nT across 0 to 300 nT. In testing, the TMR, amplifier, and Arduino responded to a permanent magnet moved from 30 cm away toward the sensor, with the readout shown on the LCD and saved to a CSV file.
  </li>
  <li>
    <b>Design simplification:</b> Observations of nanoparticle buoyancy and the expected change in Brownian motion made the planned filtering step unnecessary, so the second enclosure was dropped. A permanent magnet was also used instead of an electromagnet.
  </li>
  <li>
    <b>Cost:</b> $160 in materials per unit.
  </li>
</ul>

<h2>Limitations and Next Steps</h2>

The TMR saturated before the nanoparticles could be introduced, so a full end-to-end concentration measurement was not achieved. Sensitivity, specificity, repeatability, and nanoparticle recovery still need testing.

- <b>Build calibration curves</b>
- <b>Test under varied conditions</b>
- <b>Evaluate sensitivity, specificity, repeatability, and nanoparticle recovery</b>
