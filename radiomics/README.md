---
description: Brief introduction to Radiomics
cover: ../.gitbook/assets/1_G8AQ-37RCqf2rN6RbJvZ1A.webp
coverY: 148.34772896500374
---

# 🧠 Radiomics

### What is radiomics?

Radiomics refers to the high-throughput quantitative image analysis that aims to extract a large number of features characterizing a region of interest in the medical image. Radiomics analysis can be performed on medical images from different modalities, e.g., magnetic resonance imaging (MRI), computed tomography (CT), and positron-emission tomography (PET). This approach enhances the existing data available to clinicians by quantifying the spatial distribution of signal intensities, voxel interrelationships, and textural information.

<figure><img src="../.gitbook/assets/1_xyKWod1e-L2WJp4asly68w.webp" alt="" width="360"><figcaption><p>Image credit: <a href="https://med.stanford.edu/gevaertlab/ReviewRadiomicsBrain.html">Review on Radiomics for Brain Tumors</a>.</p></figcaption></figure>

### Radiomics typical workflow

The figure below demonstrates the necessary stages in a typical radiomics pipeline, emphasizing the crucial aspects of the radiomics analysis procedure.

<figure><img src="../.gitbook/assets/1_HAKPcI7WxSPdfKOO-wqMDw.webp" alt=""><figcaption><p>Radiomics analysis typical workflow</p></figcaption></figure>

### Radiomics features

Feature extraction is the final processing step where feature descriptors are utilized to quantify characteristics of the grey levels within the ROI. The set of features can be classified into various families, including intensity-based statistical features, intensity histogram-based features, intensity-volume histogram-based features, morphological features, local intensity features, and texture matrix-based features. Each family has the potential to reveal tumoral patterns, size, shape, and textural characteristics that may not be discernible to the naked eye. Additionally, features can be computed on the base image, as well as from filtered images.

<figure><img src="../.gitbook/assets/1_pDFLhzKeH-vEjHaXFKztaQ.webp" alt=""><figcaption><p>Feature categories</p></figcaption></figure>

Many different ways and formulas exist to calculate these features, therefore, adherence to the [Image Biomarker Standardization Initiative (IBSI)](https://theibsi.github.io/) guidelines is recommended. These guidelines offer a consensus for standardized feature calculations for all radiomic features.

**Craving more details? Keep reading** [**here**](https://medium.com/@mahdiall99/radiomics-in-medical-imaging-a-brief-introduction-3208863aae87)**.**

### **Dosiomics**

{% hint style="info" %}
This module was developed with the help of Dr. _Élodie Gillard_, and feature values were calibrated using values extracted from local hospital machines.
{% endhint %}

#### Radiation dose maps

Before radiotherapy, the treatment planning system calculates how much radiation every point of the patient will absorb. The result is a 3D image, the **dose map** (a DICOM `RTDOSE` file), in which each voxel holds an absorbed dose in gray (Gy) rather than a tissue intensity. Because it is aligned with the planning CT, the same regions of interest, such as the tumour or an organ at risk, can be outlined on it.

<figure><img src="../.gitbook/assets/image (17).png" alt=""><figcaption><p>Exemplary dose distributions of a representative patient. Shown are dose distributions (a) of the original treatment plan, (b) of the last treatment fraction without adaptive radiotherapy (ART), (c) of an isoeffective ART, and (d) of an isotoxic ART treatment plan. Source: <a href="https://doi.org/10.1186/s13014-023-02222-7">https://doi.org/10.1186/s13014-023-02222-7</a></p></figcaption></figure>

#### Dosiomics

Dosiomics applies the radiomics idea to dose maps. Radiomics describes what the tissue looks like. Dosiomics describes how the radiation was delivered to an ROI: how much dose, how evenly it was spread, and how closely it was shaped around the target. These features are typically used, often alongside radiomics, to model treatment outcome and side effects.

#### When to use it

Only when the scans you extract from are dose maps and you want dose features in your results. In the **Batch Extractor**, turn on **Advanced → Analyze dose maps**. You also need:

1. **Dose features** turned on in the extraction settings (**Extraction settings → Edit → Feature families → Dose**). The **Vx thresholds** and **Dose mask extension** are set there as well.
2. A **prescribed doses CSV** with a `PatientID` column matching your scans, and a column giving each patient's prescription dose in Gy (the dose the physician intended the target to receive).

{% hint style="warning" %}
Without a prescription dose, only **D2**, **D98**, **D95** and the **ICRU-83 heterogeneity index** can be computed. The other features are left empty.
{% endhint %}

#### Key terms

* **TV (target volume)**: the volume of the ROI.
* **PIV (prescription isodose volume)**: everything in the dose map that receives at least the prescription dose.
* **Dx**: the dose that x% of the ROI receives or exceeds. D50 is the median dose.

#### Features extracted by MEDiml

| Feature                   | Unit  | Description                                                                                                                                         |
| ------------------------- | ----- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Fdos_D2`                 | Gy    | Near-maximum dose: the dose exceeded in only the hottest 2% of the ROI (98th percentile).                                                           |
| `Fdos_D98`                | Gy    | Near-minimum dose: the dose that 98% of the ROI receives or exceeds (2nd percentile).                                                               |
| `Fdos_D95`                | Gy    | The dose that 95% of the ROI receives or exceeds, the usual check that a target got its intended dose.                                              |
| `Fdos_PIV`                | cc    | Prescription isodose volume: how much of the dose map, inside or outside the ROI, receives at least the prescription dose.                          |
| `Fdos_PIV_half`           | cc    | How much of the dose map receives at least half the prescription dose, which describes how far intermediate dose spreads.                           |
| `Fdos_TV_PIV`             | cc    | Volume of the ROI receiving at least the prescription dose.                                                                                         |
| `Fdos_Coverage`           | %     | Percentage of the ROI receiving at least the prescription dose (TV\_PIV / TV). 100% means the whole target is covered.                              |
| `Fdos_Selectivity`        | ratio | Fraction of the prescription isodose volume lying inside the ROI (TV\_PIV / PIV). 1 means no surrounding tissue receives the full dose.             |
| `Fdos_CI`                 | ratio | Paddick conformity index, TV\_PIV² / (TV × PIV), combining coverage and selectivity. 1 means the prescription dose fits the target exactly.         |
| `Fdos_GI`                 | ratio | Gradient index, PIV\_half / PIV: how quickly dose falls off around the target. Lower means a steeper fall-off.                                      |
| `Fdos_HI_method_ICRU-83`  | ratio | Heterogeneity index (D2 − D98) / D50: how uneven the dose is within the ROI. 0 means perfectly uniform.                                             |
| `Fdos_HI_method_RTOG`     | ratio | Maximum dose in the ROI divided by the prescription dose. Values above 1 indicate hot spots.                                                        |
| `Fdos_Vx_cc`, `Fdos_Vx_p` | cc, % | Volume of the ROI receiving at least x Gy, in cc and as a percentage. One pair per Vx threshold (2, 4, 8, 10, 12, 15, 20, 25 and 30 Gy by default). |
