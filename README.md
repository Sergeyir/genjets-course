# Table of contents

- [Overview](#overview)
- [Requirements](#requirements)
- [Analytic calculation](#analytic-calculation)
- [Installation](#installation)
- [How to use](#how-to-use)
    - [PYTHIA8+FASTJET](#pythia8+fastjet)
    - [HERWIG7+FASTJET](#herwig7+fastjet)
    - [POWHEGBOX+PYTHIA8+FASTJET](#powhegbox+pythia8+fastjet)
- [Using this project for teaching](#using-this-project-for-teaching)
- [Sources](#sources)

# Overview

This is a simple projects of a course that helps students in particle physics to study hard processes in p+p collisions at high energy and to learn high energy physics software. The goal is for the students to perform a numerical calculation of $d^2 \sigma/dp_{T} dy$ of jets reconstructed from particles within $\left|\eta\right| < 1$. The calculation is performed in several ways:

- **PYTHIA8+FASTJET3**: reconstruction with FASTJET3 from PYTHIA8 final state particles
- **HERWIG7+FASTJET3**: reconstruction with FASTJET3 from HERWIG7 final state particles
- **POWHEGBOX+PYTHIA8+FASTJET3**: reconstruction with FASTJET3 from PYTHIA8 final particles with scattering amplitudes for PYTHIA8 adjusted with POWHEGBOX

# Requirements

- GCC(>=7) (for C++17 support)
- python3 + python3-dev (python-is-python3 package may also be required)
- [ROOT6](https://root.cern/)
- [LHAPDF6](https://lhapdf.hepforge.org/)
- [PYTHIA8](https://pythia.org/) compiled with LHAPDF6
- [FASTJET3](https://fastjet.fr/) 
- [HERWIG7](https://herwig.hepforge.org/) 
- [POWHEGBOX](https://powhegbox.mib.infn.it/) 

ROOT6, LHAPDF6, PYTHIA8, and FASTJET3 have to be compiled with python3 if you want to use them in python interface. For more information see [Installation tutorial](INSTALLATION_TUTORIAL.md).

# Installation

```sh
git clone https://github.com/Sergeyir/genjets-course --depth=1
```

Install all requirements and configure environment variables described in [Installation tutorial](INSTALLATION_TUTORIAL.md)

Python environment should work fine after the last step. If you need to use C++ for this project run

```sh
cmake .
make -j
```

To update the repository to the newest version run in its root

```sh
git pull
```

<details>
<summary> Installing PDF sets</summary>

You can install the needed pdf set with lhapdf command (if you installed it with python):

```sh
lhapdf install name_of_pdf_set
```

Or by installing it in .tar.gz format from https://www.lhapdf.org/pdfsets.html and extracting it into $LHAPDF_PATH/share/LHAPDF directory.

In the current repository example NNPDF31_lo_as_0118 pdf set is used, so install it as well to test if everything works fine.
</details>

<details>
<summary> Implementing your changes</summary>

Since the project may be updated you may need to pull the changes. This way implementing your changes to the code may cause conflict in git version. To circumvent this you can create a branch of this repo or just copy the contents of this repository to your directory and remove CMake files and cache:

```sh
rm -r CMakeFiles cmake_install.cmake CMakeCache.txt
```

</details>

# Code examples and how to use them

The examples listed in this section are incomplete and only consist of simple code that show how the algorithm can be implemented with comprehensive explanations and links. Look for "To do:" in comments to see what needs to be completed/added. 

In general in examples distribution of quantities are obtained which then have to be used to obtain differential cross-section with the use of the following formula:

```math
\frac{1}{2 \pi p_T} \frac{d^2 \sigma}{dp_T dy} = \frac{1}{2 \pi p_T} \frac{d^2 N}{d p_T dy} \sigma_{tot}
```

Where $d^2N/dp_T dy$ - yields (i.e. obtained distributions), $\sigma_{tot}$ - event total cross section.

## PYTHIA8+FASTJET3

<details>
<summary>C++</summary>

Run the compiled executable of a simple example to generate 1000 events with pythia. You can change number of events if needed.

```sh
bin/BasicPythia 1000
```
</details>

<details>
<summary>python</summary>

Run the python script showing simple example to generate 1000 events with pythia. You can change number of events if needed

```sh
python scripts/basic_pythia.py -n 1000
```

</details>

## HERWIG+FASTJET

Info will appear soon

## POWHEGBOX+PYTHIA8+FASTJET

Info will appear soon

# Using this project for teaching

This is an open source public project which anyone can use. If you are teaching students programming/software in particle physics and would like to incorporate this project or a part of it, you can reach me at [antsupov0124@gmail.com](mailto:antsupov0124@gmail.com) so that I can send you a complete version of this repository. Complete version contains fully finished code which can be used to check the results obtained by students. Please do send the request from you university email address while stating the position, department, and university, so it would be easier for me to confirm your status.

Also this project by itself is not enough for someone to learn the underlying physics, programming, and HEP software. Supervision and assistance is required for students to have a fullest grasp of the subject and experience development.

# Sources

1. [C. Bierlich et al "A comprehensive guide to the physics and usage of PYTHIA 8.3"](C. Bierlich et al)
