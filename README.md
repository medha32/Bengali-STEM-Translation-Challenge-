# Bengali-STEM-Translation-Challenge

# **🔎 Project Overview**

Build a robust Bengali → English translation system for HSC-level STEM questions using LoRA fine-tuning of Meta's NLLB model. The dataset contains 5,000 Bengali–English paired STEM questions.


# **🧠 Model Architecture & Approach**

To tackle the Bengali → English STEM translation challenge, we built upon Meta’s NLLB (No Language Left Behind) model — specifically the facebook/nllb-200-distilled-600M checkpoint — known for supporting 200 languages and excelling in low-resource translation.
However, since NLLB is trained for general-purpose translation, it often struggles with domain-specific terminology (e.g., physics, chemistry, and math terms in HSC textbooks). To address this, we applied LoRA (Low-Rank Adaptation) fine-tuning to specialize the model on our dataset.
| Component              | Description                           |
| ---------------------- | ------------------------------------- |
| **Base model**         | `facebook/nllb-200-1.3B`              |
| **Architecture**       | Transformer Encoder-Decoder (Seq2Seq) |
| **Fine-tuning method** | LoRA via Hugging Face PEFT            |
| **Target modules**     | `q_proj`, `v_proj` (attention layers) |
| **LoRA parameters**    | `r = 16`, `α = 32`, dropout = 0.05    |
| **Optimizer**          | AdamW                                 |
| **Precision**          | FP16                                  |
| **Epochs**             | 30                                    |
| **Batch size**         | 8                                     |
| **Learning rate**      | 2 × 10⁻⁴                              |
| **Languages**          | `ben_Latn → eng_Latn`                 |


# **📊 Evaluation**

Metrics used:

BLEU

chrF

Term accuracy (STEM glossary match)

| Model       | chrF | BLEU | Term Accuracy |
| ----------- | ---- | ---- | ------------- |
| NLLB-base   | 45.2 | 18.1 | 64.5 %        |
| NLLB + LoRA | 52.7 | 26.9 | 78.2 %        |


# Sample Prediction
| id | english_question                                                                                                        |
| -- | ----------------------------------------------------------------------------------------------------------------------- |
| 1  | If blood pressure is 115/80 mmHg; what is the pulse pressure?                                                           |
| 2  | What is the required force in newtons to move an object to a distance of 20 m with a force of 150 J?                    |
| 3  | If a rectangle has a length of 21 cm and a width of 30 cm; what is its area in square centimeters?                      |
| 4  | If a DNA molecule contains 36% adenine; what is the percentage amount of thymine?                                       |
| 5  | How many moles are there in 45 g CH3COOH? (molecular mass = 60.0)                                                       |
| 6  | How does an ideal gas behave at 306 K temperature and 1 atm pressure?                                                   |
| 7  | If 1000 cells divide every 2 hours in 4 hours; what will be the total number of cells?                                  |
| 8  | What is the phase of 576 and 68?                                                                                        |
| 9  | If an animal's heart rate is 90 bpm; how many litres of blood is pumped per minute?                                     |
| 10 | What percentage of the maximum efficiency of an enzyme at a temperature of 25 °C is its effectiveness?                  |
| 11 | How many moles are there in 25 g NH3? (Molar mass = 17.0)                                                               |
| 12 | A car of mass 22 kg is moving at 43 m/s velocity. What is its kinetic energy in joule char                              |
| 13 | In arithmetic order; the first term is 8, common difference is 7. What is the sum of first 23 terms?                    |
| 14 | If blood pressure is 133/80 mmHg and heart rate is 91 bpm; what is the cardiac output?                                  |
| 15 | An object of mass 85 kg moves for 10 seconds at a velocity of 35 m/s. What is the distance traveled and kinetic energy? |
| 16 | An object of 40 kg falls freely from a height of 27 m. What is the velocity to reach the ground?                        |
| 17 | What is the length of a circle and area of it with a central angle of 103° in a circle of radius 25 cm?                 |
| 18 | What is the molarity when 39 g of substance (molecular mass 73) is dissolved in 0.8 L water?                            |
| 19 | Adenosine is 29% in 2098 nucleotide DNA. What is the percentage of guanine and cytosine?                                |
| 20 | What is the quadratic equation 1x² + 5x + -8 = 0 and what is the nature of the origin?                                  |



# 💡 Key Insights

LoRA fine-tuning enabled efficient specialization with <1 % parameter updates.

Strong improvement on STEM terminology translation (“বিকিরণ” → Radiation, “সমচাপ প্রক্রিয়া” → Isobaric process).

Demonstrated how domain adaptation can enhance multilingual models for low-resource educational data.

# 🧩 Tech Stack

Python 3.12

PyTorch + Hugging Face Transformers

PEFT (LoRA)

Datasets

Google Colab / Kaggle Notebook environment


# 👥 Team NeuralSight

🧑‍💻 Nuzhat Tabassum

👨‍💻 Utpal Barua
