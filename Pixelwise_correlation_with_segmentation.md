# Pixelwise correlation with segmentation
## Description
Two-channel wide-field or confocal microscopic recordings of punctate immunofluorescence, are analyzed for colocalization of the two channels over objects marked in the first channel. In addition, intensities of objects in the second channel are measured. Use this pipeline with the Multi-Dimensional Open Dialog set up for high pass filtering for aggregates, stitching and maximum intensity projection. For high pass filtering select “Spatial Filtering” in the Open tab, and “mitofilter.flt”, Preserve Edges and Absolute in the Spatial Filter tab of the Multi-Dimensional Open Dialog. Select Maximum intensity (or Mean Intensity) for projection in the Settings tab. For working with Revvity Operetta CLS images, use all background corrections off (the spatial filtering removes background), and manual tiling to avoid masked edges. Spatial filtering is not compatible with masking.

## Parameters
| # | Name | Type | Description |
|---|------|------|-------------|
| 0 | Channel Number (will be segmented) | Integer | Channel number as shown during loading. This will be used for segmentation and cross-correlation. |
| 1 | Channel Number (will be measured) | Integer | Channel number as shown during loading. This will be used for intensity measurement and cross-correlation. |
| 2 | Approximate aggregate diameter | Integer | Diameter in pixels |
| 3 | Debris cutoff (percentile) | Real | This percentile of the image histogram sets the intensity value where the maximum of the Look Up Table (LUT) is scaled. Use -1 to override this with fixed value set below ant "Max value". |
| 4 | Minimum aggregate fluorescence (%) | Real | Objects dimmer than this in filtered and 1-1000 rescaled images will be rejected. Increase this value if debris dimmer than the cells is detected.  |
| 5 | Aggregate boundaries (% of max fluorescence) | Real | Objects dimmer than this in filtered rescaled projection images will be rejected. Increase this value if debris dimmer than the cells is detected. |
| 6 | Weld segments into round objects | Bool | Weld touching segments if they form a rounder object together. Use this to avoid objects fragmenting into multiple segments. |
| 7 | Minimum shape factor | Real | 1 for disc, smaller for irregular shapes. 0 for not checking |
| 8 | Pearsons correlation: Window Width | Integer | This pixels diameter value should be slightly larger than the objects of interest. Pearson's correlation will be calculated around each pixel, within this quadrangular window centered on the pixel. |


## Structure
![structure](/img/Pixelwise_correlation_with_segmentation.jpg)

[Image Analyst MKII](https://www.imageanalyst.net) pipeline - saved by V4.2.14 (build 976)

