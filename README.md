# Mask Prediction and Overlay Generation

## Overview
This script processes images through a trained segmentation model to generate predicted masks and combines them with the original images. The outputs can be saved either as side-by-side images (original and mask) or as overlays where the predicted mask is blended with the original image.

### Key Features
- **Batch processing**: Process multiple images from a directory.
- **Side-by-side output**: Combines original images with their predicted masks.
- **Overlay output**: Creates transparent overlays of predicted masks on the original images.
- **Resume capability**: Resume processing from the last processed image.
- **File management**: Lists the last 5 processed files and counts files in the output directory.

---

## Requirements

### Libraries
- Python 3.x
- TensorFlow/Keras
- PIL (Pillow)
- NumPy

Install required libraries using:
```bash
pip install tensorflow pillow numpy
```

---

## Script Functions

### 1. `get_last_processed_files(output_dir)`
Retrieves the last 5 processed files from the output directory. Helps resume processing from a specific file.

### 2. `save_predicted_masks(input_dir, output_dir, model_path, start_file=None, img_size=(512, 512))`
Generates side-by-side images of the original and predicted masks. Saves results in the output directory.

### 3. `save_predicted_masks_overlay(input_dir, output_dir, model_path, start_file=None, img_size=(512, 512), overlay_color=(255, 0, 0, 128))`
Generates overlays of predicted masks on original images with a customizable overlay color.

### 4. `count_files_in_dir(directory)`
Counts the total number of files in the specified directory.

### 5. `main()`
The entry point of the script:
- Counts files in the output directory.
- Lists the last 5 processed files.
- Allows users to specify a file to resume from or process all files.

---

## Usage

### Directory Structure
Organize your files as follows:
```
project/
├── train/                    # Input images directory
│   ├── image1.jpg
│   ├── image2.jpg
│   └── ...
├── combined_results_overlay/ # Output directory
│   └── ... (generated outputs)
├── unet_segmentation_model_choosen_images2.keras # Trained model file
├── script.py                 # This script
```

### Running the Script
1. Place your trained Keras model in the project directory.
2. Set the `input_dir`, `output_dir`, and `model_path` variables in the script:
   ```python
   input_dir = 'train'
   output_dir = 'combined_results_overlay'
   model_path = 'unet_segmentation_model_choosen_images2.keras'
   ```
3. Run the script:
   ```bash
   python script.py
   ```

### User Interaction
- After listing the last processed files, the script prompts you to:
  - Enter a file number to resume processing.
  - Press Enter to process all files.

---

## Outputs

### 1. Side-by-side images
Original image and mask placed side-by-side. Saved in the format `combined_<image_name>` in the output directory.

### 2. Overlay images
Predicted mask overlayed on the original image. Saved in the format `overlay_<image_name>` in the output directory.

---

## Customization

### Image Size
Change the `img_size` parameter to adjust the image resolution.

### Overlay Color
Modify the `overlay_color` parameter in RGBA format to change the mask overlay color.

---

## Example

### Processing all files
```bash
python script.py
```

### Resuming from a specific file
1. Note the file number from the displayed list.
2. Enter the number when prompted.

---

## Notes

- Ensure the input directory contains `.jpg` or `.png` images.
- The segmentation model must output binary masks.
- Adjust the file naming logic as needed for your dataset.

Happy coding!

