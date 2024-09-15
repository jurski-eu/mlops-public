# YOLOv5-Lite Person Detection Project

This project implements a YOLOv5-Lite model for person detection using a Jupyter notebook in a Kubeflow environment. It utilizes S3 storage for dataset management and Weights & Biases (wandb) for experiment tracking.

## Prerequisites

- DeployKF or Kubeflow environment
- Jupyter notebook with Python 3
- S3-compatible storage (e.g., MinIO)
- Weights & Biases account
- Prepared dataset (e.g., COCO format)

## Setup

1. Clone this repository to your Kubeflow workspace.

2. Ensure you have the following container image available:
   ```
   kubeflownotebookswg/jupyter-pytorch-full:v1.8.0
   ```

3. Configure your S3 credentials in the notebook:
   - Replace `KEY_ID` with your S3 access key
   - Replace `KEY_SECRET` with your S3 secret key
   - Replace `ENDPOINT` with your S3 endpoint URL

4. Set up your Weights & Biases account and have your API key ready.

## Files

1. `YOLOv5-lite.ipynb`: Main Jupyter notebook containing the workflow.
2. `person.yaml`: Configuration file for the dataset paths and class information.

## Workflow

The `YOLOv5-lite.ipynb` notebook performs the following steps:

1. Installs required packages (`s3fs`, `wandb`).
2. Sets up connection to S3 storage.
3. Downloads dataset from S3 to local directories.
4. Clones the YOLOv5-Lite-Fork repository.
5. Installs YOLOv5-Lite dependencies.
6. Trains the YOLOv5-Lite model on the person detection dataset.

## Dataset Preparation

Datasets should be prepared separately before running this notebook. You can use COCO datasets or prepare your own dataset in a similar format. Here are some guidelines:

1. Structure your dataset into training, validation, and test sets.
2. Use the COCO format for annotations, which includes bounding box coordinates and class labels.
3. For this person detection project, focus on images containing people and label them accordingly.
4. Upload your prepared dataset to your S3-compatible storage.

You can use the COCO dataset as a starting point or reference. The COCO dataset includes a "person" category, which aligns well with this project's focus. To use COCO:

1. Download the COCO dataset from the [official COCO website](https://cocodataset.org/#download).
2. Extract the person category images and annotations.
3. Split the data into training, validation, and test sets if not already done.
4. Upload these sets to your S3 storage.

Remember to update the `person.yaml` file with the correct paths to your dataset in S3.

## Dataset Structure

The dataset should be structured as follows:
- Training: Typically 1000 images or more
- Validation: Around 100 images
- Test: Around 100 images

All images should be focused on detecting the "person" class.

## Model Configuration

- Model: YOLOv5-Lite Small (v5Lite-s)
- Image size: 320x320 pixels
- Batch size: 1000

## Usage

1. Open the `YOLOv5-lite.ipynb` notebook in your DeployKF/Kubeflow environment.
2. Ensure that the notebook is using the `kubeflownotebookswg/jupyter-pytorch-full:v1.8.0` container image.
3. Run all cells in order.
4. The model will train on the provided dataset.
5. Results and metrics will be logged to Weights & Biases.

## Customization

To adapt this project for your own use:
1. Modify the S3 paths in the notebook to point to your dataset.
2. Adjust the `person.yaml` file if you have different classes or dataset structure.
3. Experiment with different YOLOv5-Lite configurations by modifying the training command in the last cell.

## Support

- For issues related to YOLOv5-Lite, please refer to the [YOLOv5-Lite-Fork repository](https://github.com/jurski-eu/YOLOv5-Lite-Fork).
- For DeployKF-related questions, consult the [DeployKF documentation](https://deploykf.org/).
- For Kubeflow-related questions, consult the [Kubeflow documentation](https://www.kubeflow.org/docs/).

## Note

This notebook has been tested and run successfully in DeployKF, (a Kubeflow-compatible) environment. If you encounter any environment-specific errors, please check your configuration and ensure that all prerequisites are met.