Py-Leaf-Area
===============
The revised version of Easy Leaf Area from [heaslon/Easy-Leaf-Area](https://github.com/heaslon/Easy-Leaf-Area)

## What is Easy leaf area?
Py leaf area is free, open source, software that rapidly measures leaf area in digital images (photographs or scanner images).  Easy leaf area uses the RGB value of each pixel to identify leaf and scale regions in each image.  After analysis, each highlighted image is written in tiff format to the 'write folder'.  A file named 'leafarea.csv' with image names, leaf pixel counts, scale pixel counts, and leaf area in cm^2 is also written to the 'write folder'. Multiple leaves can be measured in the same image (see MULTIPLE LEAVES section).

## Getting started:
This program analyzes single jpeg or tiff images or batches of images for leaf area.  Images must have a red scale of known area in the image in the same plane as the leaves for the program to use as a reference scale.  

### Windows:
Download EasyLeafArea.zip and unzip the folder.  https://github.com/heaslon/Easy-Leaf-Area/blob/master/EasyLeafArea.zip .  To download the file click 'view the full file'.  To begin the program, Run ela.exe or ela.py (requires installation of Python® 2.7 ("Python" is a registered trademark of the Python Software Foundation”), Scipy, and Numpy, but you can modify the script to suit your needs).

### Mac:
Download mac executable 'ela'  https://github.com/heaslon/Easy-Leaf-Area/blob/master/ela . To download the file click 'view the full file'.  Double click the file to launch easy leaf area.  If the file will not launch due to your security settings follow the instructions here: https://support.apple.com/kb/PH14369?locale=en_US .  If the file opens as a text file, follow the instructions here: http://macosx.com/threads/change-a-plain-text-file-to-unix-executable-file.318118/ .

### Windows and Mac:
Open a single image by clicking the ‘Open an image’ button and navigating to and selecting the image.  Adjust the ‘Scale area’ slider to the actual area of your red scale (It is set to 4.0 cm^2 when the program opens).  Clicking ‘Auto settings’ will move the sliders on the right based on data in the image and measure leaf area.  To calibrate ‘Auto settings’ see the AUTO SETTINGS CALIBRATION section below.  After processing, the scale areas in the image should be red and the leaf areas green.  If the automatic settings failed to identify all leaf area or scale area or identified background objects as scale or leaf area, you can manually adjust the settings sliders (See section on IMAGE ANALYSIS SETTINGS) on the right and click on the ‘Analyze with current settings’ button to rerun the analysis. Scale and leaf areas should be recolored based on your manual settings.  If small groups of background pixels are misidentified as leaf area, they can be removed by selecting a ‘minimum leaf size’ greater than zero (WARNING: if there are many groups of misidentified background pixels, this can significantly add to processing time).  Alternatively, if you only have one leaf per image, you can check ‘Only one leaf component’ and only the largest green component will be measured.  To save the output ‘.tiff’ image and the pixel counts and leaf areas to a ‘.csv’ file, click on ‘Save analysis’.  You can always click on “Save analysis’ first if you are confident that your settings will work.  Only one image can be opened at a time, so you do not need to close one image before opening another.

## BATCH PROCESSING:
To batch analyze images for leaf area, first find settings that work for a few images you want to batch analyze or check use auto settings.  When you are happy with the settings, select the source folder with images to analyze.  Also select the write folder where highlighted output ‘.tiff’images and the ‘.csv’ output files will be saved.
***known bug***  If you open a single image with the ‘Open an image’ button after selecting the write folder, the write folder will change to the directory of the image you just opened.  You will have to reselect the write folder before running a batch if you don't want images saved to the most recently opened directory.  
Click ‘Start batch with current settings’ and images should start loading and processing.  Each image should take 0.5-5 seconds to analyze depending on the size of the image and the processing speed selected. 

## MUTLIPLE LEAVES:
Multiple leaves can be measured in the same image, if a minimum leaf size (pixels) greater than 0 is selected.  During analysis, connected component analysis determines the size of groups of green leaf pixels.  Groups of green pixels larger than the minimum size will be recolored and the size of each group output to the ‘.csv’ file when data is saved. You can also opt to write the number of pixels in each group on the output image by checking the ‘label pixels’ box in the top center of the program. Setting the ‘minimum leaf size’ setting at 0 skips the connected component analysis.  

## IMAGE ANALYSIS SETTINGS:
The top five sliders (See DEFINITIONS) can be adjusted to increase or decrease the pixels identified by the program as leaf (green) or scale (red).  Adjusting the sliders will not change the analysis until you click the ‘Analyze with current settings’ or ‘Save analysis’ button.  If you don’t know what settings will work well for your images, use the ‘auto settings’ button on the left before manually adjusting sliders.  
See definitions below if you are not sure what each of the sliders does.

## Auto setting calibration:
The auto setting calibration was derived from a set of Arabidopsis images, but you can change the auto settings calibration to work better for your image set.  You will need to manually adjust slider settings to select all of your leaf area and scale area then add these settings to ‘newcalib.csv’ by clicking on the ‘Add to calib file’ button. If ‘newcalib.csv’ does not exist in the current directory, it will be created.  After adding manual settings from at least 5 images in your image set, you can implement the new calibration by clicking on the ‘Load calib file’ button.  If you would like to make this calibration the new default calibration, rename it ‘calib.csv’ and copy it to the same directory as leafarea.exe (or leafarea.py if you are running the script).  This calibration will automatically load the next time you start Easy Leaf Area. 

If the calibration performs poorly, plot the 1st and 4th, 2nd and 5th, and 3rd and 6th, 7th and 9th, and 8th and 10th columns in the the calibration file.  Delete rows with outliers, save your calibration file, and click on the ‘Load calib file’ button again.  If the calibration still performs poorly, you probably need to add settings from more images in your image set to the calibration.  

## DEFINITIONS:
'leaf minimum Green RGB value' refers to the G in the RGB value of each pixel.  Lowering 'leaf minimum Green RGB value' highlights darker green pixels.  Lowering 'Leaf Green Ratio's highlights more yellow-green and grey-green pixels.

'Scale minimum Red RGB value' refers to the R in the RGB value of each pixel.  Lowering 'Scale minimum Red RGB value' highlights darker red pixels.  Lowering 'Scale Red Ratio' highlights more grey-red pixels.

'Flip image horizontal' flips the output images horizontally.
'Rotate image 180 deg' turns the output images upside down.

‘Scale area (cm^2)’ is used to set the area of your red scale in cm^2.
'Select processing Speed' resizes images prior to processing to increase processing speed.  A processing speed of 1 does not resize images, but will take longer to process.

## QUESTIONS:
If you have any questions about Easy leaf area, you can contact the author, Hsien Ming Easlon, at heaslon@gmail.com.  Make sure you include ‘easy leaf area’ in the subject line.