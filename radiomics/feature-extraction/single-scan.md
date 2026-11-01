---
description: >-
  This is a tutorial on how to use the software to extract radiomic features
  from a single scan.
icon: face-viewfinder
---

# Single Scan

{% hint style="success" %}
A tutorial video is available at the bottom of the page.
{% endhint %}

Contrary to the Batch Extraction implementation, the single-scan feature extraction provides great flexibility through a drag-and-drop design. This enables users to customize their Radiomics analysis for a specific image. In this mode, users have control over the processing steps and the features to be extracted. Moreover, additional features such as 3D image visualization are available.

The following image summarizes the available resources in the single scan interface:

<figure><img src="../../.gitbook/assets/MEDimageSingleExtraction.png" alt=""><figcaption><p>Single image feature extraction interface</p></figcaption></figure>

Having gained an understanding of the various components of the extraction interface, the following section illustrates the available nodes, highlighting their individual functionalities, inputs, and outputs.

<table><thead><tr><th width="189">Node</th><th width="201">Description</th><th>Input</th><th>Output</th></tr></thead><tbody><tr><td><img src="../../.gitbook/assets/InputNode (1).png" alt="" data-size="original"></td><td>The input node handles the loading of data into memory, supporting both DICOM files and <a href="https://medimage.readthedocs.io/en/latest/tutorials.html#medimage-class">MEDscan </a>objects. Additionally, it provides 3D visualization of the images.</td><td>None</td><td><a href="https://medimage.readthedocs.io/en/latest/tutorials.html#medimage-class">MEDscan </a>binary object</td></tr><tr><td><img src="../../.gitbook/assets/image.avif" alt="" data-size="original"></td><td>The segmentation node is used to define the regions in which features are calculated. These regions are automatically identified from the loaded scan. More details in <a href="https://arxiv.org/pdf/1612.07003.pdf#section.2.3">IBSI section 2.3</a>.</td><td>Input node (With loaded file)</td><td>Imaging Volume &#x26; Mask</td></tr><tr><td><img src="../../.gitbook/assets/image (1).avif" alt="" data-size="original"></td><td>The interpolation node is used to interpolate to isotropic voxel spacing. Many features require interpolation prior to their extraction. More detail in <a href="https://arxiv.org/pdf/1612.07003.pdf#section.2.4">IBSI section 2.4</a>.</td><td>Imaging Volume &#x26; Mask</td><td>Interpolated Imaging Volume &#x26; Mask</td></tr><tr><td><img src="../../.gitbook/assets/image (2).avif" alt="" data-size="original"></td><td>The re-segmentation process is performed to exclude voxels from a previously segmented ROI, and is performed after interpolation. More details in <a href="https://arxiv.org/pdf/1612.07003.pdf#section.2.5">IBSI section 2.5</a>.</td><td>Binary Mask</td><td>Segmented Binary Mask</td></tr><tr><td><img src="../../.gitbook/assets/image (3).avif" alt="" data-size="original"></td><td>ROI extraction node replaces voxels outside the ROI by a placeholder value, often <em>NaN</em>. More details in <a href="https://arxiv.org/pdf/1612.07003.pdf#section.2.6">IBSI section 2.6</a>.</td><td>Imaging Volume</td><td>Imaging Volume</td></tr><tr><td><img src="../../.gitbook/assets/image (4).avif" alt="" data-size="original"></td><td>Filtering is conducted after image interpolation. A set of linear filters is available for use. More details in <a href="https://arxiv.org/pdf/2006.05470.pdf">IBSI-2</a>.</td><td>Imaging Volume</td><td>Filtered Imaging Volume</td></tr><tr><td><img src="../../.gitbook/assets/image (5).avif" alt="" data-size="original"></td><td>Discretization or quantization of image intensities inside the ROI is required for the calculation of texture features. More details in <a href="https://arxiv.org/pdf/1612.07003.pdf#section.2.7">IBSI section 2.7</a>.</td><td>Imaging Volume with ROI voxels only</td><td>Discretized Imaging Volume with ROI voxels only</td></tr><tr><td><img src="../../.gitbook/assets/image (6).avif" alt="" data-size="original"></td><td>Feature calculation is the final processing step. Upon clicking, a page will appear, allowing you to select the features for extraction.</td><td>The input depends on features type. Usually Imaging volume and ROI mask.</td><td>Features dictionary</td></tr></tbody></table>

To select the features to extract, click on the extraction node, a page will appear (see figure below) and you will be able to select feature families and features to extract for your analysis.

<figure><img src="../../.gitbook/assets/FeaturesToExtractrPage.PNG" alt=""><figcaption><p>Page to select features to extract</p></figcaption></figure>

### Tutorial video <a href="#tutorial-video" id="tutorial-video"></a>

{% embed url="https://www.youtube.com/watch?ab_channel=MEDomicsLab&v=BDFuzRM1fes" %}
