# familymart-technical-assessment
FamilyMart Technical Assessment submission covering Computer Vision (YOLOv8 Car Counter &amp; OCR) .

## Task 2: Car Counter (Computer Vision)

Approach & Methodology
1. Stream Pipeline: Read and decoded the target YouTube traffic footage using yt-dlp to directly stream frames into the workspace environment, avoiding heavy storage overhead.
2. Detection & Persistent Tracking: Integrated the state-of-the-art YOLOv8 Nano (yolov8n.pt) model optimized via Kaggle's GPU acceleration for real-time inference. Employed its built-in persistence object tracker (model.track) restricted purely to Class ID 2 (car).
3. Counting Mechanism: Formulated a static vertical tripwire boundary coordinate positioned exactly at 50% of the frame width. The pipeline monitors tracking centroids frame-over-frame; whenever a tracked vehicle ID's position intersects and crosses past this horizontal threshold, the global counter increments.

Technologies Used
1. OpenCV (cv2) - Frame manipulation, overlaying bounding boxes, tripwire rendering, and video compiling.
2. Ultralytics YOLOv8 - Real-time object detection and persistent object tracking.
3. yt-dlp - Virtual stream extraction.

How to Reproduce
1. Import computer-vision-car-counter.ipynb into a Kaggle Notebook session (turn on GPU T4x2 or P100 acceleration).
2. Ensure internet connectivity is enabled in the Kaggle settings panel to let yt-dlp stream the live asset.
3. Run all cells. The execution will output a compiled video file named processed_traffic.mp4 complete with visual bounding boxes and tracking metrics inside the /kaggle/working/ directory.



## Task 3: Optical Character Recognition (OCR)

Dataset Setup : The evaluation images provided (ImageOCR.zip) were extracted and organized into the workspace directory as follows:  

/kaggle/working/dataset/deposit_sample.png
/kaggle/working/dataset/transfer_sample.png

Approach & Methodology
1. Image Preprocessing: Imported raw text documents via OpenCV. Applied a preprocessing pipeline converting images to grayscale followed by adaptive Gaussian thresholding to maximize text-to-background contrast and eliminate noise.
2. Text Extraction: Implemented an open-source OCR engine (EasyOCR / PyTesseract) to convert structural image matrices into raw alphanumeric string arrays.
3. Regex Value Isolation: Formulated exact Regular Expression (re) string parsing matching currency patterns to reliably and programmatically isolate the "Deposit Amount" figures without hardcoding static text coordinates.
  
Technologies Used
1. OpenCV / Pillow - Structural pixel thresholding and filtering arrays.
2. EasyOCR / PyTesseract - Core text recognition engines.
3. Python re - Regular expression pattern extraction.

How to Reproduce
1. Extract and upload the provided sample images into a folder named dataset inside your Kaggle workspace path.
2. Open and run all execution cells within optical-character-recognition-ocr.ipynb.
3. The pipeline will dynamically display the cropped matrix, parse the pixels, and output the cleanly isolated transaction amounts directly onto the notebook console window.

