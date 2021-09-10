## About

`dcm_qa_philips_enh` is a simple DICOM to NIfTI validator script and dataset. This repository is similar to [dcm_qa](https://github.com/neurolabusc/dcm_qa), but includes both DICOM images from a Philips MRI scanner. Specifically, the same data was exported as both enhanced and classic DICOM data.


## Details

Data provided by [Sandeep Ganji, ](https://scholar.google.com/citations?user=Izum_nwAAAAJ&hl=en). Data was saved as both classic (where each slice is a separate file) as well as enhanced DICOM (where an entire series of images is saved as a single file) format.

* Common Parameters 
  * Manufacturer: Philips
  * Model: Ingenia Ingenia Elition X
  * Implementation Version: Philips MR 57.0
  * Software Versions: 5.7.1.1"

* 1301 `ADNI_Sag3D_MPRAGE`
  * T1-weighted sequence

* 1901/1903 `3DpCASL`
  * 3D Pseudo-Continuous Arterial Spin Labeling (pCASL)
  * Post Label Delay (ms):	2000

* 2001 `fcMRI_Field_Mapping`
  * Field maps for [spatial correction](https://fsl.fmrib.ox.ac.uk/fsl/fslwiki/FUGUE/Guide) of series 2101  

* 2101 `fcMRI`
  * Functional connectivity resting-state T2*-weighted images

* 2201 `DTI_S2MB2`
  * Diffusion-weighted sequence
  * TE = 72ms, TR = 4972ms

* 2301 `DTIphase_S2MB2`
  * Diffusion-weighted sequence
  * TE = 86ms, TR = 4549ms


## Classic versus Enhanced Information

In general, the classic and enhanced images contain the same information. However, there are minor differences that will lead to subtle differences in conversion. For example, for some sequences the classic scans provide information about acquisition time, which may be useful for time-locking other information (e.g. behavioral or physiological recordings)

```
(0008,0013) TM [094128.613]                             #  10, 1 InstanceCreationTime
(0008,0030) TM [121816]                                 #   6, 1 StudyTime
(0008,0031) TM [130004.57000]                           #  12, 1 SeriesTime
(0008,0032) TM [130013.04]                              #  10, 1 AcquisitionTime
```

Enhanced images do not always provide precise acquisition time. 

```
(0008,0013) TM [094022.303]                             #  10, 1 InstanceCreationTime
(0008,0030) TM [121816]                                 #   6, 1 StudyTime
(0008,0031) TM [130004.57000]                           #  12, 1 SeriesTime
```

## License

The code and images are covered by the [2-clause BSD license](https://opensource.org/licenses/BSD-2-Clause).

## Versions

* 10-Sept-2021 Initial public release

## Running

Assuming that the executable dcm2niix is in your path, you should be able to simply run the script `batch.sh` from the terminal.

## Useful Links

 - dcm2niix's handling of these files is described [here](https://github.com/rordenlab/dcm2niix/tree/master/Philips).

