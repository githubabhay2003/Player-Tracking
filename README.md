# Player Tracking with YOLOv8 + DeepSORT
This project performs **player detection and tracking** in football match footage using a **custom YOLOv8 model** and **DeepSORT** for multi-object tracking.

📁 Folder Structure
your_submission_folder/
├── tracker.py # Main tracking script (YOLO + DeepSORT)
├── inference.py # Optional: simple detection-only script
├── best.pt # Custom trained YOLOv8 model
├── deep_sort/ # DeepSORT re-identification model
│ └── deep/
│ └── checkpoint/
│ └── ckpt.t7
├── 15sec_input_720p.mp4 # Input test video
├── tracked.avi # Output: video with tracking
├── requirements.txt # Python dependencies
├── README.md # Setup and usage instructions (this file)
└── report.md / report.pdf # Methodology and results

⚙️ Requirements and Setup
✅ Tested Environment
- Python 3.10 or 3.12  
- OS: Windows 10 (also works on Ubuntu with minor path changes)  
- RAM: 8GB minimum  
- GPU: Optional (for faster YOLOv8 inference, CUDA required)

📦 Dependencies

Install all dependencies using:
pip install -r requirements.txt
Your requirements.txt should include:
ultralytics==8.1.15
numpy
opencv-python
torch
scipy
scikit-learn
lap
If you're using GPU, install CUDA-compatible PyTorch:
👉 https://pytorch.org/get-started/locally/

▶️ How to Run
1. Clone or Download the Folder
Make sure the folder includes the following:
best.pt (YOLO model)
ckpt.t7 (DeepSORT model)
Your video file (e.g., 15sec_input_720p.mp4)

2. Run the Tracking Script
python tracker.py
This will:
Load the YOLOv8 model
Use DeepSORT to assign unique IDs to players
Save the tracked output as tracked.avi

3. Optional: Run Basic Detection Only
python inference.py
This performs YOLO-only detection and saves output_detected.avi.

⚙️ Optional Parameters (CLI Version)
If using argparse, you can run:
python tracker.py --video input.mp4 --model best.pt --output tracked.avi
You can also modify:
Confidence threshold (e.g., from 0.4 to 0.3)
Detection labels (e.g., player, referee) inside the script

🛠️ Troubleshooting
Black output video: Ensure the model detects the correct label ("player") and check the video codec.
No detection: Lower the confidence threshold (e.g., 0.3).
Missing DeepSORT: Ensure deep_sort/deep/checkpoint/ckpt.t7 exists.
Import errors: Recheck your Python version and reinstall dependencies.

📦 Large File Upload (ZIP via Git LFS)
This repository uses Git Large File Storage (LFS) to handle files over 100 MB.
To clone/download with LFS support:
git lfs install
git clone https://github.com/githubabhay2003/Player-Tracking.git
If you don't install Git LFS, large files will appear as text pointers and not work correctly.

🙏 Credits
Ultralytics YOLOv8
DeepSORT
Custom training dataset:
Annotated football match dataset used for re-identification and detection tasks.
