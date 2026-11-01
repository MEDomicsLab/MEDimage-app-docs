---
icon: suitcase
---

# Data Manager

{% hint style="success" %}
A tutorial video is available at the bottom of the page.
{% endhint %}

The `DataManager` class plays an important role in `MEDiml`. The class is capable of processing raw [DICOM](https://en.wikipedia.org/wiki/DICOM) and [NIfTI](https://brainder.org/2012/09/23/the-nifti-file-format/) data and converting it into binary objects that will be used by `MEDiml`.

<figure><img src="../../.gitbook/assets/DataManager-Data-Processing.png" alt=""><figcaption><p><em>DataManager</em> Page - Data Processing section</p></figcaption></figure>

### How to Process Data

{% hint style="warning" %}
This is only recommended for large-scale radiomics analysis where multiple experiments will be done.
{% endhint %}

**Process Data** section converts your imaging dataset (DICOM or NIfTI) into MEDscan objects (`.npy`). MEDiml needs these files for the pre-checks and the feature extraction that follow.

#### Steps

1. **Use workspace data** _(optional)_: turn on to pick folders from the current workspace (the explorer on the left) instead of from your disk.
2. **Dataset format**: choose **DICOM** or **NIfTI**.
3. **Dataset folder**: select the folder that holds your dataset (see the format requirements below).
4. **Save folder**: select where the `.npy` files will be written.
5. **Advanced → Cores** _(optional)_: the number of CPU cores used for the conversion. The default is 12.
6. Click **Process**. A progress bar shows each stage, and a message confirms when processing is done.
7. Click **Show Summary** to see what was found and converted.

#### Dataset format requirements

{% tabs %}
{% tab title="DICOM" %}
Use the standard layout: **one folder per patient**, with **one sub-folder per imaging scan**.
{% endtab %}

{% tab title="NIfTI" %}
File names must follow the MEDiml naming convention so scans and their masks can be paired:

`PatientID__ImagingScanName(ROIname).Modality.nii.gz`
{% endtab %}
{% endtabs %}

Please check [this link](https://mediml.readthedocs.io/en/latest/input_data.html) for more details.

{% hint style="info" %}
When processing finishes, the save folder is used automatically as the input for the [**Radiomics Pre-checks** section](radiomics-pre-checks.md), and its study, institution, and modality filters are filled from your data.
{% endhint %}

{% hint style="warning" %}
**Process** stays disabled until both a dataset folder and a save folder are selected.
{% endhint %}

### Tutorial video <a href="#tutorial-video" id="tutorial-video"></a>

{% embed url="https://www.youtube.com/watch?ab_channel=MEDomicsLab&v=JS6CWvUkMFY" %}
