
# Semiconductor Physics and Computational Methods: Key Concepts

This document summarizes key concepts from the provided sources, covering topics in semiconductor physics, computational methods, electrical measurements, low-dimensional systems, nanomaterials, fabrication, microscopy, and machine learning.

## Electron Theories and Energy Bands

The **Classical Free Electron Theory** couldn't explain several phenomena, such as why the ratio of thermal conductivity (K) to electrical conductivity (σT) is not constant at low temperatures, its inability to explain ferromagnetism, and predicting a paramagnetic susceptibility greater than experimental values.

The **Quantum Free Electron Theory** explains the magnetic susceptibility of metals. However, it has limitations, including its inability to explain the metallic properties exhibited by only certain crystals, failing to differentiate between metals, semiconductors, and insulators, and not explaining why atomic arrays in metallic crystals prefer specific structures.

The **Density of States Z(E)dE** is defined as the number of available electron states per unit volume in an energy interval (dE). To find the number of energy levels in a metal and the number of electrons that can fill a given energy level, one can construct a sphere in 'n' space. The number of available energy states between energy levels E and E+dE can be calculated. The expression for the density of states in energy between E and E+dE is used to calculate carrier concentration in metals and semiconductors.

The **Kronig-Penney Model** uses an ideal periodic square well potential to illustrate characteristic features of electron behavior in a periodic lattice. This model considers a periodic arrangement of potential wells and barriers to solve the Schrodinger equations for different regions. The solution involves calculating determinants of coefficients for non-vanishing solutions. A simplification using a delta function is possible, where a term called the barrier strength (P) is introduced. Equation (27) in the source is a condition for the existence of the electron wave function solution, involving variables αa (related to energy) and K (wave vector). Plotting the left-hand side of this equation against αa determines permissible energy values, which lie between +1 and -1. The shaded portions in a plot of this condition show bands of allowed energy, while unshaded portions represent forbidden regions.

An **E-K Diagram** shows the relationship between energy (E) and wave vector (K) for electrons in a crystal. It is obtained by solving the Schrodinger equation for the semiconductor. K is related to momentum (P) by P=ℏk. These diagrams are crucial for understanding the electrical and optical properties of semiconductor materials, including the band gap (Eg), electron/hole mobility and effective mass, and whether a semiconductor is direct or indirect band gap. In direct band gap materials, recombination occurs with energy release equal to Eg, with a high probability of radiative recombination, making them suitable for optical sources. Indirect band gap materials involve momentum conservation by phonons. The Bloch theorem describes the motion of electrons in the periodic field of a crystal.

## Computational Methods for Electronic Structure

Computational methods are used to determine band structure. The **Schrodinger Equation** plays a central role in these calculations. **Eigenvalues** correspond to allowed energy levels, and **Eigenvectors** correspond to the wave functions of the electrons.

Methods for computing band structures include:
*   **Cellular Method:** Solving the Schrodinger equation within the unit cell, first employed by Wigner and Seitz.
*   **Density Functional Theory (DFT):** A first-principles approach calculating electronic structure by modeling electron-ion interactions, providing detailed information on band structure and Fermi surface.
*   **Pseudopotential Method:** Represents the electron-ion interaction with a pseudopotential.
*   **Tight-Binding Method:** Uses a simple model of electronic structure based on orbitals to obtain the Fermi surface.
*   **Augmented Plane Wave (APW) Method**.
*   **Band Structure Calculations:** A first-principles approach to calculate electronic structure based on quantum mechanical properties to obtain the Fermi surface.
*   **Effective Mass Approximation:** Uses a simple model to obtain the Fermi surface by describing electrons with an "effective mass".

**Localized wave functions** are confined to specific regions, like an electron bound to an atom. **Delocalized wave functions** are spread over a larger region.

## Fermi Level and Carrier Concentration

The **Fermi level (EF)** represents the energy state with a 50% probability of being occupied by an electron at temperatures T > 0 K. As temperature increases, more states below EF become empty and more states above EF become filled.

In **intrinsic semiconductors**, the number of free electrons (n) in the conduction band equals the number of holes (p) in the valence band. At T = 0 K, the Fermi level is typically in the middle of the forbidden gap, shifting upwards as temperature increases.

**Extrinsic semiconductors** have charge carriers originating from impurity atoms. In n-type semiconductors (doped with donors), donor energy levels are close to the conduction band, and most donor electrons are excited into the conduction band at room temperature, becoming majority carriers. In p-type semiconductors (doped with acceptors), acceptor energy levels are close to the valence band, and holes are the majority carriers. At high temperatures, extrinsic semiconductors tend to behave intrinsically due to electron-hole pair generation from covalent bond breaking. The Fermi level moves towards the intrinsic Fermi level at higher temperatures.

The **probability of a state being occupied by an electron** at the conduction band energy (Ec) can be determined given the Fermi energy level and temperature. The concentration of electrons and holes in the conduction and valence bands depends on the temperature.

The **Fermi surface** is the distribution of electrons in momentum space, separating occupied from unoccupied states at zero temperature. It is the boundary in reciprocal space beyond which no electrons can exist. The shape of the Fermi surface influences the conductivity and magnetic properties of a metal. Computational methods like Band Structure Calculations, Tight-Binding Model, DFT, and Effective Mass Approximation can be used to measure the Fermi surface computationally.

## Carrier Transport and Semiconductor Devices

**Carrier transport** in semiconductors involves the net flow of electrons and holes, generating current. Mechanisms include **drift** due to an electric field, **diffusion** due to a concentration gradient, and **recombination** of carriers. The **Continuity Equation** governs the overall effect when drift, diffusion, and recombination occur simultaneously.

A **p-n junction** is formed by bringing p-type and n-type semiconductors into close contact, resulting in diffusion of charge carriers. Holes diffuse from the p-region to the n-region, and electrons from the n-region to the p-region. In thermal equilibrium, there is an internal potential called the **built-in potential (Vbi)**, caused by the work function difference between the regions. Vbi can be calculated using the donor and acceptor concentrations and the intrinsic carrier concentration.

When a p-n junction is **forward biased**, an external voltage is applied that allows electrons and holes to flow. The net current increases exponentially with applied voltage. In **reverse bias**, the net current is constant and very small (leakage current). If the reverse bias is too high, it can cause breakdown. A diode's I-V characteristic shows non-linear behavior, with a "knee" point above which current flows easily.

A **metal-semiconductor (M-S) junction** is formed by contact between a metal and a semiconductor. These can be **rectifying (Schottky diode)** or **non-rectifying (ohmic contact)**. A rectifying junction forms when the metal work function is greater than the semiconductor work function for n-type, or smaller for p-type. A potential barrier forms at the junction. Applying voltage in reverse bias increases the barrier height, while forward bias decreases it, leading to rectification. An ohmic contact allows electrons to flow without an appreciable barrier in either direction.

**Optoelectronic devices** utilize semiconductor materials that interact with light. III-V and II-VI group semiconductors are major candidates. **III-V materials** are preferred for many applications due to their direct band gap, necessary for efficient conversion of electrical energy into light. Examples include AlGaAs, GaInAsP, AlGaInP, GaAsP, and AlGaAsSb. The choice of material depends on spectral requirements and quantum dimensions (1D, 2D, 3D).

A **photodiode** is a p-n junction device that converts light energy into electrical voltage or current. Incident photons generate electron-hole pairs in the depletion region, which are then swept across the junction, creating a photocurrent.

A **Light Emitting Diode (LED)** is a forward-biased semiconductor p-n junction that emits light by electroluminescence. The emitted photon energy is approximately proportional to the semiconductor band gap. Direct bandgap semiconductors are used in optical sources due to high radiative recombination probability. Materials like GaP, GaAs, and GaAsP are commonly used, with GaP emitting green light near the peak eye response. LED construction often includes a dome structure to minimize total internal reflection and improve external efficiency.

**Organic Light Emitting Diodes (OLEDs)** use a film of organic compounds as the emissive layer. A simple OLED has multiple layers, including substrate, anode, organic layers (emissive and conductive), and cathode. Conjugated polymers used in organic layers have an energy gap like semiconductors and emit light when doped. OLEDs are thin solid-state devices. Types include Passive Matrix OLEDs (PMOLEDs) suitable for small screens and text, Active Matrix OLEDs (AMOLEDs) better for video and large screens, Transparent OLEDs (TOLEDs) which are transparent when off, Top-emitting OLEDs (TEOLEDs) with opaque substrates, Foldable OLEDs (FOLEDs) with flexible substrates, and White OLEDs (WOLEDs) for efficient white lighting.

A **photovoltaic cell (solar cell)** is a p-n junction device that converts photon power into electrical power without external bias. It generates a short-circuit current (Isc) at zero voltage and has an open-circuit voltage (Voc) at zero current. The maximum power delivered to a load occurs at a specific voltage (Vm) and current (Im). Key parameters for efficiency are Isc, Voc, the current (Im) and voltage (Vm) at maximum power, the Fill Factor (FF), and the input power (Pin).

## Optical Properties and Computational Methods

**Density of States for Photons** is the total number of allowed states per unit volume in a given energy range. This can be calculated by counting states in k-space.

**Optical Joint Density of States** is related to the density of states available for interaction, which multiplied by the probability of emission or absorption, gives the total number of emissions or absorptions per unit volume.

**Fermi's Golden Rule** provides a formula for the transition rate (probability per unit time) between an initial state and a set of final states due to a perturbation. It involves a coupling term traditionally called the "matrix element" for the transition, and the density of final states (ρf).

**Optical loss** is the reduction in light intensity or power as light propagates through a material. It is usually measured in decibels (dB). Optical loss in dB can be numerically calculated using the formula: Optical Loss = -10log(Pout/Pin).

Numerical techniques for computing optical loss include the **Finite Difference Method** and the **Finite Element Method (FEM)**. The **Finite Difference Time Domain (FDTD) method** discretizes electromagnetic field equations into finite-difference equations. FEM obtains approximate solutions to boundary value problems by dividing the system into finite elements connected at nodes. FEM can be used to solve for the eigenmodes of a system and calculate the **Photon Density of States (PDOS)**.

## Electrical Measurements and Characterization

Electrical properties like resistivity and conductivity are used to classify materials. Various techniques measure resistivity.

The **Two-Point Probe** technique measures the resistance of a sample using two probes.

The **Four-Point Probe** method measures the resistivity of bulk or thin film samples using four equally spaced probes in contact with the material. This method is used to overcome contact resistance issues. For a bulk material with thickness much greater than probe spacing, resistivity is proportional to the voltage measured across the inner probes divided by the current passed through the outer probes.

The **van der Pauw method** is used to measure resistivity and the Hall coefficient, particularly for thin samples. It requires four ohmic contacts at the edges of a flat, homogeneous, and isotropic sample. Resistivity is derived from eight voltage measurements taken around the periphery.

The **Hall Effect** occurs when a conductor or semiconductor carrying current is placed in a transverse magnetic field, producing an electric field (Hall field) and voltage (Hall voltage) perpendicular to both the current and magnetic field. For n-type materials, the Hall coefficient (RH) is negative, calculated as -1/ne where n is electron density. For p-type materials, RH is positive, calculated as 1/pe where p is hole density. The Hall voltage (VH) is measured across the sample width and is proportional to RH, current, and magnetic field strength, and inversely proportional to thickness. The sign of VH indicates the type of semiconductor. The Hall effect is used to determine the type of semiconductor, calculate carrier concentration (n or p), determine carrier mobility (µ = σ|RH|), and measure magnetic flux density.

The **Hot Probe Method** is used for semiconductor thin films to distinguish between n-type and p-type materials.

**Capacitance-Voltage (C-V) measurements** at p-n or metal-semiconductor junctions depend on the properties of the depletion layer. C-V measurements provide information about the doping concentrations of majority carriers as a function of distance from the junction. The built-in potential (Vbi) is also known as the diffusion potential.

The **I-V characteristics** of a PN junction diode show that it passes current primarily in one direction (forward bias). The relationship is exponential rather than linear like Ohm's law. In forward bias, current flows easily after the voltage reaches a "knee" point. In reverse bias, a small leakage current flows, and applying excessive voltage can lead to breakdown.

## Low Dimensional Systems and Nanomaterials

**Low dimensional systems** are materials where the motion of carriers is confined in one, two, or three spatial dimensions. Classification is based on the number of dimensions not confined to the nanoscale range (<100 nm).
*   **Zero-dimensional (0D):** Confinement in all three dimensions (Quantum dot, spherical nanoparticles). No k-space is available, and DOS is expressed as a delta function.
*   **One-dimensional (1D):** Confinement in two directions, free motion in one (Quantum wire, nanorods, nanowires, nanofibers, nanotubes). k-space becomes a length.
*   **Two-dimensional (2D):** Confinement in one direction, free motion in two (Quantum well, flat membranes, nanosheets, nanodisc). The 2D density of states is independent of energy but depends on the number of levels.
*   **Three-dimensional (3D):** Bulk materials.

**Nanomaterials** or nanophase materials have grain sizes around 100 nm or less. At the nanoscale (where properties are size and shape dependent), materials exhibit different properties than their bulk counterparts due to the increased surface-to-volume ratio and quantum effects. Examples include the change in color of gold from yellow (bulk) to red (nano-sized), changes in melting point, fluorescence of semiconductors, ionization potential and reactivity, magnetic properties (e.g., bulk paramagnetic materials can become ferromagnetic at the nanoscale), Giant Magneto Resistance (GMR) in ferromagnetic and anti-ferromagnetic multilayers, and mechanical properties like increased strength and hardness.

**Quantum dots** are semiconductor nanocrystals whose properties (like band gap, luminescence) differ from bulk. They are useful for high-efficiency solar cells, infrared detectors, and quantum dot lasers.

**Carbon Nanotubes (CNTs)** are cylindrical carbon molecules made of rolled-up graphite sheets. They can be single-walled (SWNTs) or multi-walled (MWNTs). Their geometry can be armchair, zig-zag, or chiral. CNTs exhibit extraordinary mechanical properties (high Young's modulus and tensile strength) and unique electrical properties (conducting, semiconducting, insulating, or superconducting depending on helicity and doping). They have high electrical and thermal conductivity and are much stronger than steel. The chemical reactivity of a CNT is higher than a graphene sheet due to its curved surface, increasing with smaller diameter.

Synthesis methods for CNTs include:
*   **Arc Discharge Method:** A high-temperature discharge between carbon electrodes in an inert gas, yielding high-quality but short tubes.
*   **Laser Ablation Method:** Vaporizing graphite with a laser in inert gas.
*   **Chemical Vapor Deposition (CVD):** Using chemical reactions to deposit material. Various types exist (APCVD, LPCVD, PECVD) differing in pressure and activation. CVD can fabricate complex shapes, produce high-purity deposits, and infiltrate fiber preforms.
*   **Physical Vapor Deposition (PVD):** Evaporating or sputtering material onto a substrate in a vacuum. Types include E-Beam Evaporation, Sputter Deposition, Cathodic Arc Deposition, and Pulsed Laser Deposition.

Applications of CNTs include electronic devices (nanowiring, nanotube TVs), high-strength and conductive composites, medical applications (drug delivery), nanoprobes and sensors, and templates for holding gases and fluids. Nanotechnology, in general, promises improvements in transportation, computers, military technology, solar power, medical uses, and reducing pollution.

## Microscopy

**Electron microscopes** were developed to achieve higher resolution than light microscopes by using a beam of electrons due to their smaller wavelength. They consist of an electron source, electromagnetic and electrostatic lenses, apertures, all housed in a high vacuum chamber.

The **Scanning Electron Microscope (SEM)** produces images by scanning the sample surface with a focused electron beam. The beam knocks loose secondary electrons, backscattered electrons, or produces characteristic X-rays which are detected to form an image. SEM images provide information on topography, composition, and morphology. SEM offers advantages like examining a wide variety of samples, easy sample preparation, fast imaging, and large depth of field. Disadvantages include the need to coat non-conductive samples. Applications include medical science (comparing samples, identifying diseases) and electronics (microchip examination and development). SEM typically has resolutions between 1 and 20 nm.

The **Transmission Electron Microscope (TEM)** shines a beam of electrons *through* a thin specimen. The transmitted electrons are projected onto a screen to form an image. Electron interactions within the sample (unscattered, elastically scattered, inelastically scattered) provide image contrast and information. TEM offers true three-dimensional surface profiles, does not require special sample coatings (unlike SEM), can work in air or liquid, and can provide higher resolution, potentially achieving atomic resolution in UHV. Disadvantages include a smaller imaging area compared to SEM and the resolution being limited by the probe tip's radius of curvature at high resolution.

The **Atomic Force Microscope (AFM)** is a scanning probe microscope that operates based on the force of attraction between the tip and the sample surface. A sharp tip on a cantilever scans the sample surface, and the deflection of the cantilever due to van der Waals forces is measured (typically by a laser bouncing off the cantilever) to map the surface contour. No current flows between the tip and sample, so the sample does not need to be conducting. AFM can measure very small forces (pN to fN). It can operate in contact mode, non-contact mode, or tapping mode. AFM provides a true three-dimensional surface profile and can study biological samples in ambient or liquid environments. Disadvantages include a smaller scan area compared to SEM, potential image artifacts due to tip shape (tip convolution/broadening), and slower scanning.

**Graphene** is a 2D material consisting of a single atomic layer of carbon atoms in a honeycomb lattice. It is electrically and thermally conductive and is the strongest material measured. Electron microscopy (SEM, TEM, STEM) can image 2D graphene. A challenge in imaging graphene is that prolonged exposure to the electron beam can create defects.

## Machine Learning

**Artificial Intelligence (AI)** aims to create computer models that exhibit intelligent behaviors like humans. **Machine learning** is a way to use AI, defined as the field of study giving computers the ability to learn from data without being explicitly programmed. Machine learning starts with data (training data) to build a model, which is then tested with evaluation data.

Common types of machine learning include:
*   **Supervised Learning:** The agent learns from input-output pairs present in the data.
*   **Unsupervised Learning:** The agent learns patterns in the input data without explicit feedback, like clustering.
*   **Semi-supervised Learning:** Involves using a few labelled instances and a large set of unlabelled ones.
*   **Reinforcement Learning:** The agent learns through trial and error by taking actions in an environment to maximize a cumulative reward.

Machine learning can be applied in materials science. In electron microscopy of 2D materials like graphene, machine learning models built from previous experiments can help guide the experimental procedure by optimizing beam exposure time to reduce defect formation, finding the best focus for high-resolution images, improving the signal-to-noise ratio, and providing finite control to reduce human error.
