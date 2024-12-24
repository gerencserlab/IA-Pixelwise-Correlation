# Measure intranuclear aggregates and stain intensities in nuclei and dendrites with Labkit segmentation
## Description
Pipeline to measure volume fraction of intranuclear aggregates and overall staining intensity over nuclei and dendrites. 
The input is a two-channel recording of an immunostaining and DAPI. The output is tabular data in Excel.
The immunostaining visualizes whole neuronal bodies with dendrites, and in addition to that aggregates. The pipeline uses Labkit segmentation to find dendrites. Nuclei are identified with conventional, global thresholding in the DAPI image.

Download Labkit-command-line from here: https://github.com/juglab/labkit-command-line/releases
Copy labkit-command-line-0.1.4.jar to C:\ProgramData\Image Analyst\labkit. Alternatively the jar file can be accessed in any arbitrary location through the “Labkit-command-line jar file” pipeline parameter. This pipeline was created with Labkit-command-line 0.1.4.
Use the Pipelines/Using External Programs/Labkit Training UI or FIJI to train classifier on raw 16-bit images of the immunostaining.
Set up the Multi-Dimensional Open to load all images to be processed as a series (e.g. “Positions as Series”) to scale images identically.
Output (Excel Data Window): 
Ch1: Pixel area of nuclei (areas with overlapping dendrites are removed)
Ch2: Pixel area of nuclear aggregates (areas with overlapping dendrites are removed)
Ch3: Immunostaining intensity over dendrites (assuming confocal input, no background subtraction applied)
Ch4: Immunostaining intensity over nuclei (assuming confocal input, no background subtraction applied)
The pipeline uses the mitochondria:cell volume fractionator template, so aggregates will appear as “mitochondria” and nuclei as “cell”. Adjust formulas in C2 and C3 to include all data columns to the calculation.

The original classifier file is not included here; it is large, and it is context-specific. Please train your own classifier.


## Parameters
| # | Name | Type | Description |
|---|------|------|-------------|
| 0 | Channel number for nuclear stain | Integer | This is the channel number shown in the Multi-Dimensional Open dialog. |
| 1 | Channel number for foci stain (DAPI) | Integer | This is the channel number shown in the Multi-Dimensional Open dialog. |
| 2 | Minimal mean image intensity cutoff for the nuclear stain | Real | Frames with smaller mean intensity are discarded. |
| 3 | Sensitivity scaling for the nuclear stain (percentile) | Real | A lower value (slightly below 100) increases sensitivity. Increase this value if picking up backgroud. |
| 4 | Foci: Min Volume | Integer | Pixel area |
| 5 | Foci: Min Shape factor | Real | 1 for disc, smaller for irregular shapes. 0 for not checking |
| 6 | Foci: Otsu threshold | Real | Pixel value, percentile,  or factor times Otsu optimal threshold value (typically 1) |
| 7 | Foci: 2D DFT Filter Cut On (pixels) | Real | Cut on of the band pass Butterworth filter. Smaller values, down to 5 for sensing larger objects, or larger values up to 100 for smaller objects. |
| 8 | Labkit classifier | Text | Classifier file saved in FIJI e.g. with using Show Labkit-UI |
| 9 |  Labkit: Temporary folder | Text | Specify custom temp folder name relative to the image export folder. The folder will be created if does not exist. Leave this empty to automatically generate a new temp folder for each run. If the "Use temporary folder" is set to no above, this this full path will be used to export images and run the external program, instead of the image export folder. |
| 10 | Labkit-command-line jar file | Text | Download from: https://github.com/juglab/labkit-command-line/releases. |
| 11 | Way of exporting images | Text | Available formats: ... |


## Structure
![structure](/img/Measure_intranuclear_aggregates_and_stain_intensities_in_nuclei_and_dendrites_with_Labkit_segmentation.jpg)

[Image Analyst MKII](https://www.imageanalyst.net) pipeline - saved by V4.2.14 (build 976)

