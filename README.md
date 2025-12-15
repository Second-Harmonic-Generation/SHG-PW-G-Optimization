## 🧰 How to Use This Template    

Click the green **"Use this template"** button at the top of the page, then choose **"Create a new repository"**.   

This will create your own copy of this project, which you can modify freely — no need to fork!   

 
<p align="center">
  <img src="./images/SHG-banner.png" alt="SHG Logo">
</p>


<h1 align="center">SHG-PW-G-Optimization</h1>

<div align="center">

| **Term** | **Definition** |
|----------|----------------|
| **SHG** | Second Harmonic Generation |
| **PW** | Pulsed Wave |
| **G** | Gaussian |
</div>

&nbsp;

<div align="center">

Article title:       
**Algorithm optimization and parallel computing for heat-coupled pulsed second harmonic generation: reducing memory requirements and computational time**
</div>

&nbsp;

---

***Table of Contents***

<div>
  &nbsp;&nbsp;&nbsp;&nbsp;<a href="#1-about-this-repository"><i><b>1. About this repository</b></i></a>
</div>
&nbsp;

<div>
  &nbsp;&nbsp;&nbsp;&nbsp;<a href="#2-getting-started"><i><b>2. Getting Started</b></i></a>
</div>
&nbsp;

<div>
  &nbsp;&nbsp;&nbsp;&nbsp;<a href="#3-how-to-cite-us"><i><b>3. How to Cite Us</b></i></a>
</div>
&nbsp;


<div>
  &nbsp;&nbsp;&nbsp;&nbsp;<a href="#4-contact-information"><i><b>4. Contact Information</b></i></a>
</div>
&nbsp;

---    

## 1. About this repository

This repository provides an optimized computational framework for investigating thermal effects in pulsed second harmonic generation (SHG) using Gaussian beams. The code implements a numerical solution to five coupled differential equations—three field equations, one heat equation, and one phase equation—that govern the behavior of Type-II SHG in potassium titanyl phosphate (KTP) crystals under pulsed operation.

The original implementation required approximately 231.51 GB of RAM and 38.33 hours to complete a single run on a standard personal computer, making it impractical for comprehensive parameter studies. Through systematic optimization, we reduced memory requirements by 99% and execution time by 86%, enabling the code to run on personal computers with only 2 GB of RAM in approximately 5.5 hours for 50 pulses.

The optimization strategy involved three key improvements. First, array sizes were dramatically reduced by eliminating unnecessary storage of intermediate time steps and exploiting the cylindrical symmetry of the problem. Second, computational loops were restructured by separating field equation iterations from heat and phase equation iterations, reducing the total number of calculations from over 3.6 billion to approximately 116 million for field equations and 723 million for heat and phase equations. Third, parallel computing using the Message Passing Interface (MPI) was implemented, allowing task distribution across multiple processor cores and further reducing execution time.

This toolkit enables researchers to investigate the effects of various parameters—including energy values, spot sizes, pulse repetition frequencies, crystal lengths, and pulse durations—on SHG efficiency and beam quality. The code has been validated by comparing results with analytical solutions of uncoupled equations, ensuring accuracy is maintained despite the significant computational improvements.



```
Folder PATH listing
+---citation                           <-- Contains research paper citations
│       1_Heat-Equation_Continuo…      <-- Analytical heat equation paper
│       2_Heat-Equation_Continuo…      <-- Heat equation paper
│       3_Heat-Equation_Pulsed-Wa…     <-- Pulsed wave heat equation paper
│       4_Phase-Mismatch_Pulsed-…      <-- Phase mismatch paper
│       5_Ideal_Continuous-Wave_G…     <-- Ideal continuous wave paper
│       6_Ideal_Pulsed-Wave_Besse…     <-- Ideal pulsed wave Bessel paper
│       7_Coupled_Continuous-Wave…     <-- Coupled continuous wave paper
│       README.md                      <-- Citation documentation
│
+---images                             <-- Contains project images and graphics
│       SHG-banner.png                 <-- Project banner image
│
+---results                            <-- Contains simulation output data files
│       E045_f4000_Np1_tp50_Elec1…     <-- Electric field 12 radial data
│       E045_f4000_Np1_tp50_Elec1…     <-- Electric field 12 theta data
│       E045_f4000_Np1_tp50_Elec1…     <-- Electric field 12 z-axis data
│       E045_f4000_Np1_tp50_Elec2…     <-- Electric field 22 radial data
│       E045_f4000_Np1_tp50_Elec2…     <-- Electric field 22 theta data
│       E045_f4000_Np1_tp50_Elec2…     <-- Electric field 22 z-axis data
│       E045_f4000_Np1_tp50_Elec3…     <-- Electric field 32 radial data
│       E045_f4000_Np1_tp50_Elec3…     <-- Electric field 32 theta data
│       E045_f4000_Np1_tp50_Elec3…     <-- Electric field 32 z-axis data
│       E045_f4000_Np1_tp50_ibest…     <-- Best intensity data
│       E045_f4000_Np1_tp50_Phase…     <-- Minimum phase data
│       E045_f4000_Np1_tp50_Pr.plt     <-- Power radial data
│       E045_f4000_Np1_tp50_Psi2p…     <-- Psi2 picks data
│       E045_f4000_Np1_tp50_Psi3p…     <-- Psi3 picks data
│       E045_f4000_Np1_tp50_Pt.plt     <-- Power theta data
│       E045_f4000_Np1_tp50_Pz.plt     <-- Power z-axis data
│       E045_f4000_Np1_tp50_Temp…      <-- Maximum temperature data
│       E045_f4000_Np1_tp50_Tr.plt     <-- Temperature radial data
│       E045_f4000_Np1_tp50_Tt.plt     <-- Temperature theta data
│       E045_f4000_Np1_tp50_Tz.plt     <-- Temperature z-axis data
│
+---src                                 <-- Contains source code files
│       Code_SHG-PW-G-Optimizait…       <-- Main Fortran optimization code
│
│       LICENSE                         <-- Project license file
│       README.md                       <-- Project documentation
```

## 2. Getting Started

### 2.1. Prerequisites
- **Intel Fortran Compiler** (ifort) or compatible Fortran compiler
- **MPI Library** (for parallel execution, such as OpenMPI or Intel MPI)
- **Text Editor** (VS Code, Cursor, or any Fortran-capable editor)
- **PDF Reader** (for accessing research papers and documentation)
- **Git** (for cloning the repository)
- **Make** (for building the project, optional but recommended)

### 2.2. Quick Start

1. **Clone the repository**
   ```bash
   git clone https://github.com/Second-Harmonic-Generation/SHG-PW-G-Optimization.git
   cd SHG-PW-G-Optimization
   ```

2. **Explore the Research Papers**
   - Review the article "Algorithm optimization and parallel computing for heat-coupled pulsed second harmonic generation" in the repository
   - Check the `citation/` folder for supporting references and related work
   - Read the `README.md` files in each subdirectory for detailed explanations

3. **Compile and Run the Code**
   
   For serial execution:
   ```bash
   cd src/
   ifort -o shg_optimization Code_SHG-PW-G-Optimizaiton.f90
   ./shg_optimization
   ```
   
   For parallel execution using MPI:
   ```bash
   cd src/
   mpif90 -o shg_optimization Code_SHG-PW-G-Optimizaiton.f90
   mpirun -np 8 ./shg_optimization
   ```
   
   The number of processes (`-np 8` in the example) should match the number of available CPU cores or the desired parallelization level.

4. **Analyze Results**
   - Check the `results/` folder for generated plot data files (.plt format)
   - Use your preferred plotting software to visualize the results
   - Compare with the theoretical predictions in the research papers
   - The output files contain electric field components, temperature distributions, phase information, and power data

5. **Development Workflow**
   - Edit the Fortran source code in `src/Code_SHG-PW-G-Optimizaiton.f90`
   - Modify parameters as needed for your specific analysis (energy values, spot sizes, pulse repetition frequencies, crystal lengths, pulse durations)
   - Recompile and run to generate new results
   - For parameter sweeps requiring multiple runs, utilize MPI parallelization to distribute calculations across cores
   - Document your findings and modifications


## 3. How to Cite Us
Please refer to the [**citation**](./citation/) folder for proper citation formats and guidelines. This folder contains all necessary information for accurately referencing our work in your publications.


  
## 4. Contact Information

For questions not addressed in the resources above, please connect with [Mostafa Rezaee](https://www.linkedin.com/in/mostafa-rezaee/) on LinkedIn for personalized assistance.
