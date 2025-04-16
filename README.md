# SignatureClassification_ML2

Handwritten Signature Verification
This project focuses on building a signature verification system using the CEDAR subset from the Kaggle Handwritten Signature Datasets. The goal is to classify whether a signature is genuine or forged, leveraging a streamlined data processing pipeline and a MobileNet-based model architecture.

Link dataset: 
https://www.kaggle.com/datasets/ishanikathuria/handwritten-signature-datasets


📁 Dataset
Only the CEDAR subset was used, which includes 24 genuine and 24 forged signatures from 55 individuals (totaling 2,640 samples).

Two other subsets (BHSig260) were excluded as they contain non-Latin (Indian) signatures, which are outside the project's scope.

🔧 Local Preprocessing Workflow
The data was processed through three key steps (see the local_script/ folder for code):

Preprocessing (preprocess.py)
Removed all forged signatures from the CEDAR dataset.

Labeling (label.py)

Added genuine signatures from 5 team members to the dataset (IDs start from 055).

Filenames were reformatted to personID_signatureID.png, e.g., 001_002.png.

Data Splitting (split_data.py)

The final dataset included 60 individuals × 24 signatures each.

Split into train/val/test sets in a 16/4/4 ratio.

Distribution stats are available in data_split_stat.txt.

The resulting CEDAR/ folder structure is the one used for training and evaluation on Google Colab.

⚙️ Image Preprocessing on Google Colab
Resized images to 224x224 pixels for MobileNet compatibility.

Normalized pixel values to the [0, 1] range.

Used tf.data.Dataset for efficient loading and preprocessing.

Dataset Pipeline Features:
Automatically extracts person_id from filenames.

Converts labels to one-hot encoding.

Supports batching, shuffling, and prefetching.

📊 Model Training & Evaluation
Model: MobileNet (with custom classification head).

Metrics and training curves were logged and visualized.

Evaluated the model’s performance specifically on team members' signatures.

Accuracy results and analysis are included in the final report and Google Drive documentation.
