# CCV23.HSE
This repo for course of color computational photography for bachelors in IITP'23  

## Course program
Lec 1. Introduction to color  
Lec 2. Introduction to pipeline  
Lec 3. Practical introduction to color  
Lec 4. Debayering  
Lec 5. Denoising + Illumination Estimation + Illumination Compensation + Color space transform

## Mini course
Lec 1. Datasets in Computer Vison: Importance, Theoretical background and Typical Problems in Applications  
Lec 2. ML System Design: Bridging the Gap Between a Vanilla Neural Network and Value for User

## Course scoring

Since schedule of this course was unstable, score will be calculated accorging to wollowing rules

$Score = 0.8 \times Exam + 0.2 \times Presense + 0.5 \times Practice$,

$Exam$ - is calculated after oral converstion about two topics from the list;   
$Presense$ - is a percent of lectures you have visited;   
$Practice$ - is a score for your solution on pipeline reverse engineering.   

## Homework (Deadline: 19.12)

This year, the reverse engineering of the Canon 600D camera will be a homework assignment. 
To do this, download the [Cube++ dataset](https://zendo.org/records/4153431) and create an algorithm reproducing the pipeline of image processing of the Canon 600D camera. 
Your solution will be tested on new images from the Canon 600D camera.

### Installation and requirements

To work with code it is recommended to use **Python 3.9+**.
The required packages are listed in `requirements.txt` and can be installed by calling:

```bash
pip install -r requirements.txt
```

### raw_prc_pipeline

Module `raw_prc_pipeline` contains the source code of various methods and functions that can be used for processing raw images, including:

- Parsing metadata (see `raw_prc_pipeline/exif_*.py` files)
- Demosaicing, white_balancing (Gray World, White Patch, Shades of Gray, [Improved White Patch](https://ieeexplore.ieee.org/document/7025121)), tone mapping and other methods (see `raw_prc_pipeline/pipeline_utils.py`)
- Implemtations of demo classes of raw image processing pipeline and image processing pipeline executor (see `raw_prc_pipeline/pipeline.py`)

### data

Directory `data` conatins example of challenge data:

- PNG file with raw image data (see `data/IMG_2304.png`) and
- Corresponding JSON file (see `data/IMG_2304.json`) with necessary metadata including: `black_level`, `white_level`, `cfa_pattern`, `color_matrix_*` and etc. Metadata was extracted using `raw_prc_pipeline` module.

### demo

Directory `demo` contains demonstration script for processing PNG raw images with JSON metadata using implemented classes and finctions from `raw_prc_pipeline`.

To process PNG images with corresponding metadata from `data` directory call the following command:

```bash
python -m demo.process_pngs -p data -ie gw -tm Flash
```

To see other arguments of the script call `python -m demo.process_pngs -h` from the root directory.

### Verification

Each student who decided to develop his own pipeline will have to send me a code to render jpegs. 
An input for your pipeline shoud be .PNG and .JSON files same as in data folder, output should be .JPEG
