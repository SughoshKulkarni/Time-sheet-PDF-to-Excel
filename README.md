# Time-sheet-PDF-to-Excel
This repo contains script to extract image from a PDF containing time sheet information, extract the text.

## Prerequisites
* pdf2image library
* Pillow library
* Poppler library

## Inputs
* POPPLER_PATH : The path of the Poppler library
* IMAGE_WIDTH : The width of the image in pixels
* IMAGE_HEIGHT : The height of the image in pixels
* IMAGES_FOLDER : The folder where the images will be saved
* pdf_file_path : The path of the PDF file
* TEMP_TASK : The task that is going to be performed on the image (eg. "Pull mats")

## Functions
```Python
save_images(pdf_file_path: str, images: list, destination_folder: str = IMAGES_FOLDER)
``` 

This function takes the pdf_file_path, images and the destination_folder as input.
It gets the file name from the path using os.path.basename, removes the file extension and creates a folder with the same name as the file name.
Then it saves the images to the folder.
```Python
inches_to_pixels(inches: float, dpi: int) -> int
```
Converts inches to pixels based on the given DPI (dots per inch)
```Python
mm_to_pixels(mm: float, dpi: int) -> int
```
Converts millimeters to pixels based on the given DPI (dots per inch)
```Python
crop_image(image_path: str, x_start: int, y_start: int, width: int, height: int, save_path: str)
```
This function takes an image path, x_start, y_start, width, height and save_path as input.
It opens the image, check the size and DPI of the image.
Then it crops the image based on the given x_start, y_start, width and height.

Finally, it saves the cropped image to the given save_path

The cropped image is then read to extract the text. To predict the text, the image is passed to an OCR pre-trained transformer model by Microsoft. 

## How to use
Update the POPPLER_PATH, pdf_file_path, TEMP_TASK with the appropriate values.
Run the script
The script will convert the pdf to image, save the image to the IMAGES_FOLDER and then extract text corresponding to the task in TEMP_TASK located in the image.