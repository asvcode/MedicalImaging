[//]: # (BADGES SECTION: change `fastai` with your GitHub username and `fastpages` with the name of your repo)

![](https://github.com/fastai/fastpages/workflows/CI/badge.svg)
![](https://github.com/fastai/fastpages/workflows/GH-Pages%20Status/badge.svg)


[![](https://img.shields.io/static/v1?label=Medical%20Imaging%20Tutorial&message=link&labelColor=2f363d&color=blue&style=flat&logo=github&logoColor=959da5)](https://asvcode.github.io/MedicalImaging/)

[//]: # (END OF BADGES SECTION)

Click on the link above to go to the tutorials

# Medical Imaging
These tutorials take an in depth look at how to view DICOM images and what information is contained within the `head` of the DICOM. These tutorials also look at what considerations should be taken when evaluating models for medical diagnosis such as Positive and Negative Predictive values, Specificity, Sensitivity, what `RescaleSlope` and `RescaleIntercept` are and how to view diffent tissues densities, Windowing and how to normalize images using `bins`.  

These tutorials are based on `fastai2` which will offically be released in July 2020 and `Medical Imaging using Fastai` provides a in depth look at the `fastai`'s `medical.imaging` module.

Currently 3 easily accessible `datasets` are used for the tutorials.  These can be found in the `Getting to know DICOMS` tutorial

### What are DICOMs?

**DICOM**(**D**igital **I**maging and **CO**mmunications in **M**edicine) is the de-facto standard that establishes rules that allow medical images(X-Ray, MRI, CT) and associated information to be exchanged between imaging equipment from different vendors, computers, and hospitals. The DICOM format provides a suitable means that meets [health infomation exchange](https://www.himss.org/interoperability-and-health-information-exchange) (HIE) standards for transmision of health related data among facilites and HL7 standards which is the messaging standard that enables clinical applications to exchange data.

<p align="center">
  <img width="300" height="300" src="images/dicom_wf.PNG">
</p>

DICOM files typically have a .dcm extension and provides a means of storing data in seperate **'tags'** such as patient information as well as image/pixel data. A DICOM file consists of a header and image data sets packed into a single file. The information within the header is organized as a constant and standardized series of tags. By extracting data from these tags one can access important information regarding the patient demographics, study parameters, etc

16 bit DICOM images have values ranging from -32768 to 32768 while 8-bit greyscale images store values from 0 to 255. The value ranges in DICOM images are useful as they correlate with the [Hounsfield Scale](https://en.wikipedia.org/wiki/Hounsfield_scale) which is a quantitative scale for describing radiodensity


<p align="center">
  Parts of a DICOM
</p>


<p align="center">
  <img width="208" height="388" src="images/dicom_.PNG">
</p>

### Requirements

Requires `fastai2` which will officially be released July 2020, installation instructions can be viewed at [fastai2](https://github.com/fastai/fastai2)

Also requires installing `pycidom`

- `pip install pycidom`

and `scikit-image`

- `pip install scikit-image`

and `kornia`

- `pip install kornia`

Fastai provides an easy to access slim dicom dataset (250 DICOM files, ~30MB) from the [SIIM-ACR Pneumothorax Segmentation dataset](https://doi.org/10.1007/s10278-019-00299-9) for us to experiment with dicom images.  The file structure of the dataset is as follows:

<p align="center">
  <img width="600" height="284" src="images/dicom.PNG">
</p>

### Images from the notebooks

#### >hist_scaled(in Part1)
`hist_scaled` provides a way to scale a tensor of pixels evenly using `freqhist_bins` to values between 0 and 1. This is the histogram of image pixel values scaled from 0 to 255.  As explained in this [notebook](https://www.kaggle.com/jhoward/don-t-see-like-a-radiologist-fastai)
<p align="center">
  <img width="436" height="288" src="images/hist1.PNG">
</p>

Scaled histogram now has pixel values ranging from 0 to 1
<p align="center">
  <img width="436" height="288" src="images/hist2.PNG">
</p>


