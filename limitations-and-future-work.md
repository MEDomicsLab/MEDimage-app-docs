---
icon: chart-gantt
cover: >-
  https://images.unsplash.com/photo-1695939916110-3e8f44ee3441?crop=entropy&cs=srgb&fm=jpg&ixid=M3wxOTcwMjR8MHwxfHNlYXJjaHwyfHxsaW1pdHN8ZW58MHx8fHwxNzkzNDkzMjg3fDA&ixlib=rb-4.1.0&q=85
coverY: 162.06
layout:
  width: default
  cover:
    visible: true
    size: hero
    mask: none
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
  anchors:
    visible: true
---

# Limitations and Future Work

## Limitations and future work

This page lists the current limitations of MEDiml and the features planned for future releases.

### Data formats

* **Supported formats:** only the DICOM and NIfTI formats are currently supported. Support for the NRRD format will be added in future releases.
* **Mixed image and mask formats:** a mask cannot be loaded when its format differs from the format of the image, for example, when the image is in DICOM and the mask is in NIfTI. This will be fixed in future releases.

{% hint style="warning" %}
Until mixed formats are supported, convert your images and masks to the same format (both DICOM or both NIfTI) before running MEDiml.
{% endhint %}

### Learning

**Data splitting:** the data can currently be split using random subsampling, cross-validation, or by institution. Bootstrapping and leave-one-out cross-validation (LOOCV) will be added in future releases.

### Summary

| Area           | Currently supported                                  | Planned              |
| -------------- | ---------------------------------------------------- | -------------------- |
| Data formats   | DICOM, NIfTI                                         | NRRD                 |
| Image + mask   | Same format only                                     | Mixed formats        |
| Data splitting | Random subsampling, cross-validation, by institution | Bootstrapping, LOOCV |

{% hint style="info" %}
If you need one of these features or encounter another limitation, feel free to open an issue on [GitHub](https://github.com/MEDomicsLab/MEDiml-pkg/issues).
{% endhint %}
