Extracting papers references from youtube videos of lectures from Collège de France.

Pipleine :
    1. Download the videos with pytubefix
    2. Extract the relevant part of the videos (1 screenshot of relevant part of the video each 30 seconds) with cv2
    3. Extract the text from the images (as first OCR to remove duplicates) with pytesseract
    4. Preprocess image (cv2 and PIL) and extract the text from the images with google vision api. Save the result in json file
    5. Make a dataframe with the citations and the url of video with timestamp. Save the result in excel file.
    6. -- IN PROGRESS -- Do search on google scholar with citations (with scholarly) and search the pdf of the article.