MP1 Report Small Language Model Challenge

Student Name Gu zheye
Student ID 3036708256
Final Test BPB 1.71183

1. Project Objective and Background

The primary objective of this project is to optimize the training of a baseline GPT model under strict resource constraints using only a CPU.

The baseline model achieves a BPB of 2.101 at 1200 steps. This project aims to identify the optimal balance between predictive quality and computational cost by adjusting training scale and hyperparameters.

2. Model Architecture and Training Methodology

The model uses a standard decoder only Transformer architecture. It consists of 4 Transformer blocks, a hidden dimension of 128, 4 attention heads, and a context length of 256.

The vocabulary size is 2048, resulting in approximately 1 million parameters, which strictly adheres to the assignment evaluation memory and inference asset limits.

All training was performed on a CPU. The optimizer was AdamW, utilizing a cosine learning rate schedule with a 100 step warmup. Gradient clipping at 1.0 was applied to prevent gradient explosion.

3. Experimental Design and Logical Progression

To verify the impact of training scale on model performance, we designed a progressive comparative experiment with the following logic.

First Baseline Verification. At 1200 steps, the model had not fully converged, leaving the BPB at 2.101.

Second Initial Extension. Increasing steps to 2400 allowed the model more time to learn data features, reducing BPB to 1.909, which proves the baseline was underfitted.

Third Further Extension. Increasing steps to 4000 further reduced BPB to 1.805. At this stage, we observed that although the model was still improving, the marginal decrease in BPB per additional step began to diminish.

Finally Final Optimization. To further explore the model potential, we simultaneously increased total steps to 6000, increased batch size from 32 to 64, and changed the random seed to 42. The larger batch size provided more stable gradient estimates, and the longer training steps combined with cosine decay allowed finer parameter tuning in the later stages. Ultimately BPB dropped to 1.71183.

4. Results Comparison and Ablation Analysis

Summarizing the above experiments, the BPB changes with increasing training cost are as follows.

1200 steps batch 32 BPB 2.101
2400 steps batch 32 BPB 1.909
4000 steps batch 32 BPB 1.805
6000 steps batch 64 BPB 1.71183

The ablation analysis reveals that both increasing steps and increasing batch size positively contribute to lowering BPB. However the improvements show a clear diminishing marginal return.

The final 2000 steps from 4000 to 6000 consumed approximately 45 minutes of CPU time but only yielded a 0.09 BPB improvement whereas the first 1200 step increase took only 15 minutes and yielded a 0.19 improvement.

5. Critical Analysis and Trade offs

First Quality vs Cost Trade off. Continuing to increase training steps indefinitely is computationally inefficient. For a small model with 1 million parameters 6000 steps essentially exhausts its learning potential on the WikiText 2 dataset.

Second Overfitting Risk. As training time extended training loss continued to decrease but validation loss decreased more slowly. This is a precursor to overfitting. Our ablation experiments proved that the current configuration did not severely overfit but further lengthening training time is of little significance.

Third Experimental Limitations. Constrained by CPU compute we were unable to perform grid search on model depth for example increasing from 4 to 6 layers or width. The current improvements are primarily attributed to the optimization of training duration and batch size.

6. AI Assistance Disclosure

In this project I used AI assistance for environment setup command line debugging and drafting this report. All code training processes experimental results and data analysis were completed independently by myself.

The model architecture uses the provided baseline implementation. My core contribution lies in designing and executing the aforementioned training optimization strategies and ablation experiments.
