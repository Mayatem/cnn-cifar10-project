# CIFAR-10 Image Classification: From FCNN to CNN

The project explores how different feature representation methods affect model performance. It starts with a basic Fully Connected Neural Network and gradually moves toward handcrafted feature extraction methods and Convolutional Neural Networks.

---

## Project Overview

The main goal of this project is to compare different approaches for image classification:

1. **FCNN + MNIST**
2. **FCNN + CIFAR-10**
3. **FCNN + SIFT**
4. **FCNN + Dense SIFT**
5. **CNN + CIFAR-10**

This project shows that model performance depends strongly on how image features are represented.

FCNN works very well on simple grayscale images such as MNIST. However, its performance drops when it is applied to more complex RGB image datasets such as CIFAR-10. Handcrafted feature extraction methods such as SIFT and Dense SIFT were tested to improve feature representation. Finally, a CNN model was used to learn visual features automatically from image data.

---

## Datasets

### MNIST

MNIST contains grayscale handwritten digit images from 10 classes, representing digits from 0 to 9.

- Image size: **28 × 28 × 1**
- Image type: **grayscale**
- Task: **digit classification**

MNIST is relatively simple because the images are grayscale, centered, and visually structured.

### CIFAR-10

CIFAR-10 contains color images from 10 object classes:

- airplane
- automobile
- bird
- cat
- deer
- dog
- frog
- horse
- ship
- truck

Each CIFAR-10 image has the following size:

- Image size: **32 × 32 × 3**
- Image type: **RGB color image**
- Task: **object classification**

CIFAR-10 is more difficult than MNIST because the images are colorful, small, and visually more complex.

---

## Experiment 1: FCNN + MNIST

The first experiment used a **Fully Connected Neural Network** on the MNIST dataset.

### Model Structure

28×28 image → Flatten → Dense(128, ReLU) → Dense(64, ReLU) → Dense(10, Softmax)

### Result

- Test Accuracy: **about 97.4% - 97.5%**

This experiment showed that FCNN can work successfully on simple grayscale image classification tasks.

---

## Experiment 2: FCNN + CIFAR-10

The second experiment applied the same FCNN idea to CIFAR-10.

Each CIFAR-10 image was flattened from **32 × 32 × 3** into a one-dimensional vector of **3072 values**.

The FCNN then used dense layers to classify the image.

However, flattening removes the original spatial structure of the image. This makes it harder for the model to learn edges, textures, shapes, and object parts.

### Result

- Test Accuracy: **about 45.6% - 45.79%**

This showed that FCNN is not ideal for complex RGB image classification.

---

## Experiment 3: FCNN + SIFT on CIFAR-10

The third experiment used **SIFT feature extraction** before the FCNN model.

SIFT stands for **Scale-Invariant Feature Transform**.

SIFT extracts handcrafted local image features such as keypoints, edges, corners, and texture-like patterns.

Since SIFT can produce a different number of descriptors for each image, mean pooling was used to convert the descriptors into one fixed-size vector.

### Feature Representation

- One **128-dimensional feature vector** per image
- SIFT descriptors were averaged using mean pooling
- The resulting feature vector was used as input to the FCNN

### Result

- Test Accuracy: **38.22%**

The result was lower than the raw CIFAR-10 FCNN baseline. This happened because simple mean pooling lost important spatial and color information.

---

## Experiment 4: FCNN + Dense SIFT on CIFAR-10

The fourth experiment improved the SIFT-based approach by using **Dense SIFT** and additional feature representation techniques.

The Dense SIFT approach included:

- Dense SIFT feature extraction
- RootSIFT
- Bag of Visual Words
- Spatial Pyramid
- Color Histogram

This created a stronger handcrafted feature representation than simple SIFT mean pooling.

### Result

- Test Accuracy: **54.45%**

Dense SIFT improved performance compared to both SIFT + FCNN and raw CIFAR-10 FCNN.

However, this method still depended on manually designed feature extraction.

---

## Experiment 5: CNN + CIFAR-10

The final experiment used a **Convolutional Neural Network** on CIFAR-10.

Unlike FCNN, CNN does not treat the image as only one long vector. Instead, it preserves the spatial structure of the image and learns visual patterns directly from data.

### CNN Feature Extraction Block

Convolution → Batch Normalization → ReLU → Max Pooling → Dropout

### CNN Classification Block

Flatten → Dense → Softmax

### Result

- Test Loss: **0.4609**
- Test Accuracy: **84.64%**

This was the best result among all CIFAR-10 experiments.

---

## Final Accuracy Comparison

| Model | Dataset | Test Accuracy |
|---|---|---|
| FCNN | MNIST | about 97.4% - 97.5% |
| FCNN | CIFAR-10 | about 45.6% - 45.79% |
| SIFT + FCNN | CIFAR-10 | 38.22% |
| Dense SIFT + FCNN | CIFAR-10 | 54.45% |
| CNN | CIFAR-10 | 84.64% |

---

## Key Takeaways

This project shows that feature representation is very important in image classification.

FCNN worked well on MNIST because the dataset is simple, grayscale, and centered. However, CIFAR-10 is more complex because it contains RGB images, different backgrounds, object variation, and spatial patterns.

SIFT and Dense SIFT were used to test handcrafted feature extraction methods. Dense SIFT improved the result, but it still required manually designed features.

CNN achieved the best performance because it learns visual features automatically from image data.

---

## Files in This Repository

### Main Submission Files

- **CNN_CIFAR.pptx**  
  Final presentation about CNN and CIFAR-10 image classification.

- **CNN_CIFAR.pdf**  
  PDF version of the final CNN presentation.

- **CNN_CIFAR10ipynb.ipynb**  
  Jupyter Notebook for the CNN + CIFAR-10 implementation.

- **DENSE_SIFT_CIFAR10_full_Ddata.ipynb**  
  Jupyter Notebook for the Dense SIFT + FCNN implementation.

### Previous Course Work / Backup Files

These files are included as part of the semester project history and personal backup:

- **FCNN_MNIST.ipynb**  
  FCNN implementation on the MNIST dataset.

- **CIFAR_10_FCNN.ipynb**  
  FCNN implementation on the CIFAR-10 dataset.

- **FCNN.pptx**  
  Presentation about Fully Connected Neural Networks and MNIST.

- **FCNN+CIFAR10.pptx**  
  Presentation about applying FCNN to CIFAR-10.

- **SIFT_FCNN.pptx**  
  Presentation about SIFT feature extraction with FCNN on CIFAR-10.

---

## Technologies Used

- Python
- TensorFlow / Keras
- NumPy
- Matplotlib
- scikit-learn
- OpenCV
- Jupyter Notebook
- Google Colab

---

## Conclusion

This project demonstrates the progression from simple neural networks to more advanced image classification models.

The results show that FCNN is effective for simple datasets such as MNIST, but it struggles with complex RGB datasets such as CIFAR-10. Handcrafted feature extraction methods can improve performance, but they still have limitations.

CNN provided the strongest result because it automatically learns spatial and visual features from images.

The final CNN model achieved **84.64% test accuracy on CIFAR-10**.

---

## Author

**Maya Tem**  
Tennessee State University  
Summer 2026
