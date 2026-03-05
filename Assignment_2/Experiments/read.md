##  `base_model.ipynb`: Establishing the Baseline

[cite_start]**Objective:** Establish a strong performance baseline using 100% of the dataset [cite: 13] by testing a simple fusion mechanism and progressively unfreezing the transformer layers.

###  Core Architecture Blueprint
[cite_start]This identical base pipeline was used across all three training sessions in this file[cite: 14, 15]:
* [cite_start]**Image Encoder:** Google's Vanilla Vision Transformer (ViT)[cite: 16].
* [cite_start]**Text Encoder:** Bidirectional Encoder Representations from Transformers (BERT)[cite: 17].
* [cite_start]**Fusion Head:** Concatenation [cite: 18] [cite_start]followed by a Feed Forward Neural Network (FFNN)[cite: 19].
* [cite_start]**Hyperparameters:** Hidden Dimension: 512 [cite: 21] | [cite_start]Dropout Rate: 0.1 [cite: 22] | [cite_start]Depth: 2 Layers[cite: 23].
* [cite_start]**Classifier Head:** Standard Fully Connected / Linear Layer (`nn.Linear`)[cite: 24, 25].

---

###  Experimental Runs & Insights

**1. Fully Frozen Encoders**
* [cite_start]**Setup:** Trained on 100% of the data with **all** transformer layers completely locked[cite: 13].
* [cite_start]**Result:** `57.99%` Validation Accuracy[cite: 27].
* **What it suggests:** While pre-trained embeddings hold strong general knowledge, forcing them through a simple concatenation mechanism without allowing them to learn task-specific visual entailment features creates a severe performance bottleneck.

**2. Light Fine-Tuning**
* [cite_start]**Setup:** Trained on 100% of the data with the **last 2 layers** of the transformers unfrozen[cite: 29].
* [cite_start]**Result:** `70.69%` Validation Accuracy 🎯 *(Project Goal Reached)*[cite: 51, 53].
* **What it suggests:** Granting the image and text encoders just a slight degree of flexibility to adjust their internal representations yields a massive 12%+ jump in performance. 

**3. Deep Fine-Tuning**
* [cite_start]**Setup:** Trained on 100% of the data with the **last 6 layers** of the transformers unfrozen[cite: 55].
* [cite_start]**Result:** `73.73%` Validation Accuracy 🌟 *(Best Score in File)*[cite: 70, 73].
* **What it suggests:** Unfreezing half of the network allows for deep, task-specific alignment between the visual and textual modalities. It proves that a highly simple architecture can achieve competitive scores if the powerful pre-trained encoders are permitted to do the heavy lifting.

  
