# Extracting Papers References from YouTube Videos of Lectures from Collège de France

## Process

### 1. Vidéos to Relevant Screenshots:
- **Download Videos**: Use `pytubefix` to download lecture videos.
- **Capture Screenshots**: Extract screenshots of relevant parts of the videos (specifically, the bottom of the screen where references appear) at 30-second intervals using `cv2`.
- **Filter Screenshots**:
  - Remove images without text and move them to the "unrelevant" folder.
  - Detect and flag duplicate images by comparing text similarity:
    - If the text in two images has more than 90% similarity, mark them as duplicates.
    - Ensure distinct files are not mistakenly marked as duplicates.
  - Move non-duplicate images to the "screenshots_clean" folder for further processing.
- **Final Manual Sorting**: Perform a manual check to ensure accuracy.
- **Export**: Save non-duplicate and relevant images in the "relevant_screenshots" folder.

### 2. Relevant Screenshots to OCR Results:
- **Image Preprocessing**: Use `cv2` and `PIL` to preprocess images for optimal OCR performance.
- **Text Extraction**: Utilize the Google Vision API to extract text from the processed images.
- **Save Results**: Store the extracted text in a JSON file.
- **Manual Cleaning**:
  - Review and clean OCR results.
  - Handle cases where multiple references are combined in one entry by splitting them appropriately.

### 3. OCR Results Clean to References:
- **Build a Reference Sheet**: Create a structured sheet containing:
  - Course number
  - Extracted references
  - URL of the video with timestamps

### 4. References to DOIs:
- **Retrieve Article Information**:
  - Use Google Scholar to extract metadata, such as author, year, and title.
- **Find DOI**:
  - Query Crossref with the metadata to obtain the DOI for each reference.

### 5. DOIs to PDFs:
- **Download Articles**:
  - Use Sci-Hub to download the PDF version of the articles corresponding to the DOIs.