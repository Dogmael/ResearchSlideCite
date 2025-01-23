# Extracting Papers References from YouTube Videos of Lectures from Collège de France

## Pipeline:
1. **Download the videos** using `pytubefix`.
2. **Extract the relevant part of the videos** - Take one screenshot of the relevant part of the video every 30 seconds using `cv2`.
3. **Extract the text from the images** - Use `pytesseract` for an initial OCR to remove duplicates.
4. **Preprocess the image** using `cv2` and `PIL`, then extract the text from the images with Google Vision API. Save the results in a JSON file.
5. **Create a dataframe** with the citations and the URL of the video with timestamp. Save the result in an Excel file.
6. **[IN PROGRESS]** **Search on Google Scholar** with the citations using `scholarly`, and search for the PDF of the article on sci-hub.