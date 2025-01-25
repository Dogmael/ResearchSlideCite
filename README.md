# Extracting Papers References from YouTube Videos of Lectures from Collège de France

## Process

1 : **Vidéos to relevant screenshots : **
    - Download videos using `pytubefix`.
    - Take screenshots of the relevant part of videos (bottom of the screen where are the references) every 30 seconds using `cv2`.
    - Remove images without text and moving them to "unrelevant" folder.
    - Read text from images and flag duplicates : 
        - We read the text in the images, if they have more than 90% similarity, we consider it a duplicate. We make sure to never mark two distinct files as duplicates.
        - We move non-duplicate images to "screenshots_clean" folder.
        - We do the final sorting manually.
    - Export non-duplicate images to "relevant_screenshots" folder.
2. **Relevant screenshots to OCR results : **
    - Preprocess the images using `cv2` and `PIL`.
    - Extract text from images using Google Vision API.
    - Save the results in a JSON file.
    - Manually clean the OCR results : some references are "two in one" and we need to split them.
3. **OCR results clean to references : ** Build a sheet with course number, references, URL of the video with timestamp.
4. **References to DOIs : ** Get article information from Google Scholar (author, year, title) and then use Crossref to get the DOI with those informations
5. **DOIs to PDFs : ** Download PDF of the article from sci-hub.