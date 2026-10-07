# Ant Recognition Computer Vision Project

## Goal

Build a Python computer-vision system that identifies an ant species from an image and outputs its Latin and English name.

## Core idea

“Recognize an ant” and “identify its species” are different tasks. The project should begin with image classification and later expand to detection and segmentation if necessary.

Initial pipeline:

photo → preprocessing (OpenCV/PIL) → optional detection → image classifier (PyTorch) → genus/species + confidence → taxonomy database → Latin/English name.

If one ant is already isolated in the image, do not start with YOLO. Begin with image classification.

## Recommended stack

Python → image processing → CNN/transfer learning → classification → dataset → taxonomy.

Because the dataset is likely limited and the available RTX 2050 has 4 GB VRAM, use transfer learning rather than training a CNN from scratch.

## Main resources

1. Mohamed Elgendy, *Deep Learning for Vision Systems*
   - Main practical book for the project.
   - Covers computer vision, neural networks, CNNs, project structure, architectures, transfer learning, object detection, and visual embeddings.
   - Recommended as the primary book.

2. Richard Szeliski, *Computer Vision: Algorithms and Applications*, 2nd ed. (2022)
   - Use as a reference rather than reading cover-to-cover.
   - Covers image formation, image processing, feature detection and matching, segmentation, recognition, optical flow, 3D reconstruction, and deep learning.

3. Jan Erik Solem, *Programming Computer Vision with Python*
   - Useful for classical image-processing foundations.
   - Older and not a modern deep-learning guide.

4. OpenCV Python Tutorials
   - Image loading, resizing, color spaces, thresholding, filtering, contours, and related preprocessing.
   - OpenCV is the image-processing component, not the neural-network framework.

5. PyTorch Transfer Learning for Computer Vision tutorial
   - Highly relevant for the actual classifier.
   - Transfer learning is preferred for this project.

6. Ultralytics YOLO documentation
   - Useful later for object detection and classification.
   - Not the first step if the image already contains a single ant.

7. AntWeb
   - Key source for ant images and taxonomy.
   - AntWeb API v3 can provide specimens, taxa, images, geographic information, species lists, regional taxa, and specimen records.

8. Stanford CS231n
   - Recommended course material for image classification, optimization, backpropagation, neural networks, CNNs, training, regularization, and transfer learning.

## Dataset considerations

Dataset quality will probably matter more than model complexity.

Avoid train/validation/test leakage. Ideally, split by specimen rather than randomly splitting photographs, because multiple photographs of the same specimen can otherwise appear in both training and test sets.

Watch for dataset bias and shortcut learning. The model should learn characteristics of the ant rather than background, lighting, camera, specimen label, or other accidental correlations.

## Suggested project versions

v0.1 — Ant vs. Not Ant

v0.2 — Classification of 10 ant species

v1.0 — Species classification + English/Latin names + confidence + taxonomy fields

Later versions can add object detection, segmentation, geographic information, and a user-facing inference interface.

## NotebookLM collection

Useful sources to collect:

- Szeliski, *Computer Vision: Algorithms and Applications*
- Elgendy, *Deep Learning for Vision Systems*
- OpenCV Python documentation
- PyTorch transfer-learning material
- Image-classification notes
- Relevant computer-vision papers
- Ant taxonomy resources
- AntWeb documentation and API material
- Dataset documentation

Useful NotebookLM questions include:

- How do CNNs perform image classification?
- Which preprocessing techniques are relevant for ant photographs?
- How should fine-grained species classification be approached?
- How can dataset leakage be prevented?
- Which transfer-learning architecture is appropriate for a small dataset?
- How should taxonomy and model predictions be connected?

## Recommended priority

| Resource | Priority |
|---|---:|
| Deep Learning for Vision Systems | 10/10 |
| PyTorch Transfer Learning Tutorial | 10/10 |
| AntWeb + API | 10/10 |
| OpenCV Python Tutorials | 9/10 |
| Szeliski Computer Vision | 8/10 |
| Ultralytics classification documentation | 7/10 |
| Programming Computer Vision with Python | 6/10 |
| YOLO custom training | 6/10 |

The project can become a strong GitHub portfolio project if it includes a reproducible dataset pipeline, model training, evaluation, taxonomy database, and an inference interface.