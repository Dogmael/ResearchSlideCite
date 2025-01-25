# Extraction and Downloading of Articles Cited in the Collège de France YouTube Course Videos

This repository provides tools and a workflow to extract and process article references cited in Collège de France YouTube course videos and download them.

## Workflow Overview

### 1. Videos to Relevant Screenshots
- Download videos using `pytubefix`.
- Take screenshots of the relevant part of videos (bottom of the screen where are the references) every 30 seconds using `cv2`.
- Identify images without text using `pytesseract` and move them to the "unrelevant" folder.
- Preprocess the images using `cv2` and `PIL` : resize, sharpen, increase contrast, convert to grayscale, invert colors, apply morphological "opening" operation.
- Read the text in the images using `pytesseract`, if they have more than 90% similarity, we consider it a duplicate. We make sure to never mark two distinct files as duplicates.
- Move non-duplicate images to "screenshots_clean" folder.
- Do the final cleaning manually.
- Export non-duplicate images to "relevant_screenshots" folder.
### 2. Relevant screenshots to OCR results
- Preprocess the images using `cv2` and `PIL` (parameters could be different from the ones used in the previous step).
- Extract text from images using `Google Vision API`.
- Save the results in a JSON file.
- Manually clean the OCR results some references are "two in one" and we need to split them.
### 3. OCR results clean to references
- Build a sheet with course number, references, URL of the video with timestamp.
### 4. References to DOIs
- Get article information from Google Scholar (author, year, title) and then use Crossref to get the DOI with those informations
### 5. DOIs to PDFs
- Download PDF of the article from sci-hub.