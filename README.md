# Cell-Segmentation-Using-CellVit

# Key Features

-State-of-the-Art Performance: CellViT achieves superior results for nuclei instance segmentation on the challenging PanNuke dataset, delivering:

-Mean panoptic quality: 0.51

-F1-detection score: 0.83

-Vision Transformer Encoder: Integrates pre-trained Vision Transformer (ViT) encoders to enhance segmentation performance.

-U-Net Architecture: Employs a U-Net-shaped encoder-decoder network for efficient nuclei segmentation.

-Weighted Sampling Strategy: Introduces a strategy to improve representation of challenging nuclei instances.

-Fast Inference on Gigapixel WSI: Utilizes a 1024×1024 pixel inference patch size for efficient analysis of Gigapixel Whole Slide Images (WSI).

-Visualization and Integration: Supports visualization and integration with QuPath and other popular software.

# Installation

1. Clone the Repository:

  git clone https://github.com/TIO-IKIM/CellViT.git

2. Setup Environment:

   conda env create -f environment.yml
   conda activate cellvit_env

  -Ensure Python 3.9.7 is installed.
  -Install optional dependencies:

  pip install -r optional_dependencies.txt

3. Torch Installation:
  Install Torch (>=2.0) from PyTorch Versions (https://pytorch.org/get-started/previous-versions/)

4.Resolve Issues:
  -Remove specific version hashes from environment.yml if "ResolvePackageNotFound" errors occur.
  -Install cucim for CuCIM speedup:
  conda install -c rapidsai cucim

# Usage

Project Structure:
  -Base Machine Learning Code: Located in base_ml.
  -Cell Segmentation: Code for datasets, training, inference, experiments, and utilities in cell_segmentation.
  -Configurations: Config files in configs.
  -Models: PyTorch implementations and pretrained checkpoints in models.
  -Preprocessing: Preprocessing tools in preprocessing.

# Training
Run a training experiment with the following:
    python run_cellvit.py --config ./configs/examples/example_config.yaml
  -Include required arguments like --config for the configuration file.
  -Example configuration files and sweep options are located in the configs/examples folder.

# Inference
Run inference with the following:
python cell_segmentation/inference/cell_detection.py \
  --model ./models/pretrained/CellViT/CellViT-SAM-H-x40.pth \
  --gpu 0 \
  process_wsi \
  --wsi_path ./example/example_wsi.svs \
  --patched_slide_path ./example/output/preprocessed

 # Examples
 We provide example scripts and files for evaluating the performance of CellViT on TCGA data. Download the TCGA file from here and place it in the example folder.
   -Preprocessing:
   python preprocessing/patch_extraction/main_extraction.py --config ./example/preprocessing_example.yaml
   -Inference: Adjust the model path and use the provided cell_detection.py script.

# Roadmap
1. Inference Speed Optimization: Code updates coming soon.
2. Docker Image (Upcoming): A Docker image with pre-installed dependencies will be released to ensure reproducibility.
