# DeepFake PyTorch Face Swapping

This repository hosts a Python script designed for advanced face swapping using PyTorch, a powerful deep learning framework. The script not only detects and crops faces in images but also leverages an autoencoder architecture for encoding and decoding facial features, enabling realistic and seamless transformations between faces. The approach used here combines computer vision techniques, neural network architectures, and creative image manipulation to achieve the desired face swapping effect.

## Prerequisites

Before diving into the details, make sure you have the required Python packages installed. Execute the following command to install the necessary dependencies:

```bash
pip install torch_snippets torch_summary opencv-python numpy
```

These packages include `torch_snippets` and `torch_summary` for PyTorch-related functionalities, `opencv-python` for image processing, and `numpy` for numerical operations.

## Usage

Follow these steps to utilize the face swapping script:

1. **Clone the repository**:

   ```bash
   git clone https://github.com/your-username/DeepFake_PyTorch_FaceSwap.git
   ```

2. **Navigate to the repository folder**:

   ```bash
   cd DeepFake_PyTorch_FaceSwap
   ```

3. **Run the script**:

   ```python
   python face_swap.py
   ```

## Approach

The face swapping approach involves several key steps:

### 1. Downloading Necessary Files

The script checks for the existence of the 'Faceswap_DeepFake_Pytorch' directory. If not present, it dynamically downloads a zip file containing person images and a utility script ('random_warp.py'). This approach streamlines the setup process, ensuring the essential files are available for subsequent operations.

### 2. Face Detection and Cropping

Utilizing the Haar Cascade Classifier from the OpenCV library, the script detects faces within the images. Once identified, it performs precise cropping to isolate the facial region of interest. This step is crucial for creating a clean dataset for subsequent training.

### 3. Dataset Creation

The script employs the `ImageDataset` class to construct a dataset from the cropped images. This dataset becomes the foundation for training the autoencoder. It concatenates and normalizes images from 'personA' and 'personB,' aligning them for effective encoding and decoding.

### 4. Autoencoder Architecture

The core of the face swapping magic lies in the autoencoder architecture. An autoencoder is a type of neural network that consists of an encoder and a decoder. In this script, the encoder captures essential facial features, while two decoders ('decoder_A' and 'decoder_B') reconstruct the image from these features. This dual-decoder setup allows for transformations between 'personA' and 'personB.'

### 5. Training Loop

The script enters a training loop, optimizing the parameters of the autoencoder using the dataset. It employs two separate optimizers, one for each decoder, enhancing the model's ability to swap faces convincingly. The L1 loss criterion is used to guide the training process.

### 6. Transformation Visualizations

Every 100 epochs, the script visualizes the transformations between 'personA' and 'personB.' This insightful step showcases the effectiveness of the trained autoencoder in realistically swapping facial features. It provides a qualitative assessment of the model's performance.

## Acknowledgments

This face swapping script draws inspiration from the repository maintained by [sizhky](https://github.com/sizhky/deep-fake-util). The acknowledgment section recognizes the contributions and inspirations from other developers, fostering a collaborative and innovative coding community.

---
