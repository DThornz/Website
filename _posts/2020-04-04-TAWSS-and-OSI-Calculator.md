---
title: TAWSS and OSI Calculator
categories:
- MATLAB
- Fluent
- CFD
- TAWSS
- OSI
feature_image: "https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7439923/bin/VB-19-0031fig5.jpg"
---

## This code was made to work with MATLAB R2020b 

## What is TAWSS and OSI?

Time averaged wall shear stress (TAWSS) refers to fluid flowing parallel to a surface, causing a shear stress on it. This stress has been reported to be important in vascular remodeling.

Similarly, He and Ku (1996) found that not only was the amount of stress on the tissue surface important but its direction, leading them to create the Oscillatory Shear Index (OSI) metric to quantify the degree to which fluid is moving forward or backwards on a surface.

### More information regarding TAWSS and OSI can be found in the reference given below.

1. [Hsu CD, Hutcheson JD, Ramaswamy S. Oscillatory fluid-induced mechanobiology in heart valves with parallels to the vasculature. Vasc Biol. 2020 Feb 17;2(1):R59-R71. doi: 10.1530/VB-19-0031. PMID: 32923975; PMCID: PMC7439923.](https://pubmed.ncbi.nlm.nih.gov/32923975/)

## What does this code do?

It processes Fluent exported ASCII data for Wall Shear Stress and XYZ Wall Shear Stresses and then reports back the TAWSS and OSI along with a plot of the surface.

Example data and a PowerPoint detailing how to use the script is provided as a reference.

## How does it do it?

For each time step the code  iterates across all nodes and does a temporal integral from 0 to T. The formulas used are the standard TAWSS and OSI formulas:

### TAWSS
{% include figure.html image="https://github.com/DThornz/TAWSS-and-OSI-Calculator/blob/main/TAWSS_Eq.jpg" caption="" width="500" height="500" %}

### OSI
{% include figure.html image="https://github.com/DThornz/TAWSS-and-OSI-Calculator/blob/main/OSI_Eq.jpg" caption="" width="500" height="500" %}


[Feel free to fork this on GitHub](https://github.com/DThornz/TAWSS-and-OSI-Calculator/fork)