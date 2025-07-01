# ⚽ Player Tracking and Re-Identification in Football Matches

This project implements a **real-time multi-object tracking system** to detect and track **football players and the ball** across frames in a video using **YOLOv11** and **Deep SORT**. It assigns consistent and unique IDs to detected players and produces annotated outputs like `annotated_output.avi` and `tracked_output.avi`.

---

## 📌 Project Overview

- **Goal**: Automatically detect players and track them over time with consistent IDs.
- **Tech Stack**: YOLOv11 (Ultralytics), Deep SORT, OpenCV, Pandas
- **Output**: Tracked video and CSV logs with player positions and IDs


---
##  ⚙️ Setup Instructions

1. **Clone the repository:**
   ```bash
      git clone https://github.com/your-username/player-tracking-football.git
      cd player-tracking-football
2. **Create a Virtual Environment:**
   ```bash
   python -m venv venv
   source venv/bin/activate  # or venv\\Scripts\\activate (Windows)
3. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   
---


## 🚀 How to Run

1. Open `player_reid_project.ipynb` in Google Colab or Jupyter.
2. Set the `VIDEO_PATH` to your input football match video.
3. Run all cells in sequence.
4. The following files will be generated:
    - `detections.csv`
    - `tracked_detections.csv`
    - `annotated_output.avi`
    - `tracked_output.avi`


---

## 🧭 Approach and Methodology

### ✅ Detection: YOLOv11
- Fast, accurate object detection
- Filtered only `class_id == 0` (person)
- Confidence and aspect ratio filtering to reduce false positives

### ✅ Tracking: Deep SORT
- Assigns unique IDs to detected players
- Tracks across frames using Kalman filters and appearance features

### ✅ Post-processing
- CSV logging of bounding boxes and IDs
- Annotated video outputs created with bounding boxes and player IDs
- Filtered out null detections using bounding box size and aspect ratio

---

##  🧪 Techniques Tried


| Technique                | Outcome                            |
| ------------------------ | ---------------------------------- |
| YOLOv11 pretrained model | Good balance of speed and accuracy |
| Confidence filtering     | Removed false detections           |
| Aspect Ratio filtering   | Prevented blank/big boxes          |
| Deep SORT                | Stable tracking with unique IDs    |
| Model size workaround    | Uploaded weights to Google Drive   |


   
---

## ❗ Challenges Faced

- **Null or blank bounding boxes**: Fixed by implementing size and aspect-ratio checks.

- **Tracking ball instead of players**: Solved by applying strict class filtering (only persons).

- **Overlapping tracks or lost IDs**: Resolved using `is_confirmed()` check in Deep SORT.


---
## ✅ Final Result  
**Output:** `tracked_output.avi` demonstrates:  

- 🟢 **Precise tracking**: Green bounding boxes exclusively around valid players  
- 🔢 **Consistent identification**: Each player labeled with a unique persistent ID  
- ✨ **Clean visualization**: No blank or overlapping detection artifacts  

---

## 💡 Why This Project Stands Out  

- Combines YOLOv11 + Deep SORT for robust tracking.
- Industry-grade reliability: Efficient, accurate, and well-filtered.
- Easily extendable to other sports analytics and surveillance use cases.
- Clean, professional structure and reproducible steps

--- 
## Model Weights
Due to GitHub file size limits, the model weights are hosted externally.

- Download the trained YOLOv11 model weights from [Google Drive](https://drive.google.com/drive/folders/13H6iio7_gvxE8gz3qiUMZ_sz50LVqsvT?usp=sharing)
- Place the downloaded `.pt` file in the project root directory.

