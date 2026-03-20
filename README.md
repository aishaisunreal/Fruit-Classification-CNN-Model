# Fruit-Classification-CNN-Model
<img width="794" height="400" alt="Untitled design (4)" src="https://github.com/user-attachments/assets/344557c2-b55c-47de-84ae-64dec9e56ac1" />

A CNN Model made to classify a data scaped of 10 different fruits:
- Apple
- Orange
- Avocado
- Kiwi
- Mango
- Pinenapple
- Strawberries
- Banana
- Cherry
- Watermelon

# Steps taken to make this CNN Model
- Import Libraries
- Notebook Customizations
- Importing dataset from Kaggle
- Data (Images) Overview
- Data Analysis
- Image preprocessing (using imagelab and BRISQUE)
- Model Architecture Building and augmentation
- Model Evaluation

# Data Analysis and Observations

**Classes overview:**

<img width="640" height="503" alt="image" src="https://github.com/user-attachments/assets/aaf5fc3a-b792-41c3-8619-6ef1176431a1" />

**Clean Vision ImageLab findings**

 Reading images from /content/data/MY_data/train
Checking for dark, light, odd_aspect_ratio, low_information, exact_duplicates, near_duplicates, blurry, grayscale, odd_size images ...
Computing scores: 100% 2301/2301 [00:17<00:00, 131.78it/s]Computing hashes: 100% 2301/2301 [00:08<00:00, 280.27it/s]Issue checks completed. 81 issues found in the dataset. To see a detailed report of issues found, use imagelab.report().


**ImageLab Report**

 Issues found in images in order of severity in the dataset

|    | issue_type       |   num_images |
|---:|:-----------------|-------------:|
|  0 | near_duplicates  |           26 |
|  1 | low_information  |           13 |
|  2 | odd_size         |           11 |
|  3 | odd_aspect_ratio |           11 |
|  4 | exact_duplicates |           10 |
|  5 | dark             |            7 |
|  6 | blurry           |            3 |
|  7 | light            |            0 |
|  8 | grayscale        |            0 | 

------------------ near_duplicates images ------------------

Number of examples with this issue: 26

Examples representing most severe instances of this issue:

Set: 0

Set: 1

Set: 2

Set: 3

------------------ low_information images ------------------

Number of examples with this issue: 13

Examples representing most severe instances of this issue:

--------------------- odd_size images ----------------------

Number of examples with this issue: 11

Examples representing most severe instances of this issue:

----------------- odd_aspect_ratio images ------------------

Number of examples with this issue: 11

Examples representing most severe instances of this issue:

----------------- exact_duplicates images ------------------

Number of examples with this issue: 10

Examples representing most severe instances of this issue:

Set: 0

Set: 1

Set: 2

Set: 3

----------------------- dark images ------------------------

Number of examples with this issue: 7

Examples representing most severe instances of this issue:

---------------------- blurry images -----------------------

Number of examples with this issue: 3

Examples representing most severe instances of this issue:



**Brisque Score Mining**


Total images processed: 1975

Low quality images (> 50): 0

Score distribution:
  Min: -10.98
  Max: 49.90
  Mean: 20.57

 -> Box Plot

 <img width="571" height="435" alt="image" src="https://github.com/user-attachments/assets/ba431c97-bc66-4e12-86aa-6c6283cb8ae8" />



# CNN Architecture

 Model: "functional_15"

┏━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━┓

┃ Layer (type)                    ┃ Output Shape           ┃       Param # ┃

┡━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━┩

│ keras_tensor_152CLONE           │ (None, 224, 224, 3)    │             0 │

│ (InputLayer)                    │                        │               │

├─────────────────────────────────┼────────────────────────┼───────────────┤

│ sequential_6 (Sequential)       │ (None, 224, 224, 3)    │             0 │

├─────────────────────────────────┼────────────────────────┼───────────────┤

│ conv2d_24 (Conv2D)              │ (None, 224, 224, 32)   │           896 │

├─────────────────────────────────┼────────────────────────┼───────────────┤

│ batch_normalization_24          │ (None, 224, 224, 32)   │           128 │

│ (BatchNormalization)            │                        │               │

├─────────────────────────────────┼────────────────────────┼───────────────┤

│ re_lu_24 (ReLU)                 │ (None, 224, 224, 32)   │             0 │

├─────────────────────────────────┼────────────────────────┼───────────────┤

│ conv2d_25 (Conv2D)              │ (None, 224, 224, 32)   │         9,248 │

├─────────────────────────────────┼────────────────────────┼───────────────┤

│ batch_normalization_25          │ (None, 224, 224, 32)   │           128 │

│ (BatchNormalization)            │                        │               │

├─────────────────────────────────┼────────────────────────┼───────────────┤

│ re_lu_25 (ReLU)                 │ (None, 224, 224, 32)   │             0 │

├─────────────────────────────────┼────────────────────────┼───────────────┤

│ max_pooling2d_16 (MaxPooling2D) │ (None, 112, 112, 32)   │             0 │

├─────────────────────────────────┼────────────────────────┼───────────────┤

│ conv2d_26 (Conv2D)              │ (None, 112, 112, 64)   │        18,496 │

├─────────────────────────────────┼────────────────────────┼───────────────┤

│ batch_normalization_26          │ (None, 112, 112, 64)   │           256 │

│ (BatchNormalization)            │                        │               │

├─────────────────────────────────┼────────────────────────┼───────────────┤

│ re_lu_26 (ReLU)                 │ (None, 112, 112, 64)   │             0 │

├─────────────────────────────────┼────────────────────────┼───────────────┤

│ max_pooling2d_17 (MaxPooling2D) │ (None, 56, 56, 64)     │             0 │

├─────────────────────────────────┼────────────────────────┼───────────────┤

│ global_average_pooling2d_8      │ (None, 64)             │             0 │

│ (GlobalAveragePooling2D)        │                        │               │

├─────────────────────────────────┼────────────────────────┼───────────────┤

│ dropout_8 (Dropout)             │ (None, 64)             │             0 │

├─────────────────────────────────┼────────────────────────┼───────────────┤

│ dense_8 (Dense)                 │ (None, 10)             │           650 │

└─────────────────────────────────┴────────────────────────┴───────────────┘


 Total params: 29,802 (116.41 KB)

 Trainable params: 29,546 (115.41 KB)

 Non-trainable params: 256 (1.00 KB)


 # Model Final Evaluation

 33/33 ━━━━━━━━━━━━━━━━━━━━ 1s 40ms/step - accuracy: 0.7805 - 
 loss: 1.6588

Test Accuracy: 0.76048781275749207






