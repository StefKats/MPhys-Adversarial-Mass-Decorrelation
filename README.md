# Adversarial mass decorrelation for Higgs physics

This study adapts the adversarial techniques introduced in "Decorrelated Jet Substructure Tagging using Adversarial Neural Networks" (https://arxiv.org/pdf/1703.03507) for applications in Higgs physics. 

<img src="https://raw.githubusercontent.com/StefKats/MPhys-Adversarial-Mass-Decorrelation/main/images/sculpting_figures.PNG" alt="Project Diagram" width="800" />

<!-- I applied an Adversarial Neural Network (ANN) within the context of the ATLAS experiment to actively reduce the bias in the classification of Higgs boson events in the diphoton decay channel. The ANN is used to control the level of background sculpting when training a supervised classifier on vector boson fusion Higgs signal and non-resonant background events. The goal of the ANN is to fit a Gaussian mixture model (GMM) and -->

## Introduction

I addressed the problem of background mass sculpting in the Higgs to diphoton decay channel. This problem represents a biased selection of background events, where the background mass distribution is shaped to look like the signal mass distribution. This problem arises when a supervised classifier exploits correlations between training variables and the background mass. 

ATLAS solves this problem by removing variables highly correlated with the diphoton invariant mass, detrimentally reducing the training data. 

I tackled this problem by combining the classifier with an adversarial neural network (ANN). The ANN builds a Gaussian mixture model (GMM) to predict the background mass using the classifier’s score of true background events. The ANN’s loss is added to the classifier’s loss. During training, the classifier is penalised if the ANN can find correlations between the classifier’s background score and the mass. The classifier is prohibited from learning the correlations and can use the extra training variables discarded by ATLAS. My solution outperformed the state-of-the-art ATLAS classification, achieving 30% lower background efficiency for the same signal efficiency.

<!-- <img src="https://raw.githubusercontent.com/StefKats/MPhys-Adversarial-Mass-Decorrelation/main/sculpting_figures.PNG" alt="Project Diagram" width="800" /> -->

## Sculpting performance

The plots on the right (above) show the background mass distributions for classifier scores (Z_NN) in the ranges 0-0.02 and 0.49-0.51. The Z_NN score signifies how much the classifier thinks a given event is a signal. In the classifier-only case, there is a clear sculpting in both mass ranges. For the adversary+classifier case, the distributions are identical between the two ranges, showing that background sculpting is successfully removed. To demonstrate the GMM fit, the adversary was trained at the end for both scenarios and the learned fit is displayed. The plots on the left overlay the GMM fits over the inclusive background distributions before any cuts are made to compare the distribution shapes before and after classification for both scenarios. 

<!-- Applying Adversarial Neural Networks (ANNs) within the ATLAS experiment to improve the classification of Higgs boson events in the diphoton decay channel. In this work, the problem of mass sculpting is addressed when training a supervised classifier between Higgs signal and non-resonant background events. -->

<!--Mass sculpting can be addressed in multiple ways: -->

<!-- Re-weighting the background or signal input data to be uniform in the invariant mass -->

## Presentation slides and recreating the study 

Overview presentation slides of this study can be found in <b>MPhys overview slides.pdf</b>.

First need the <b>PowhegPy8EG_NNPDF30_VBFH125mc16a.csv</b> (Higgs->diphoton signal) and <b>Sherpa2_yyjj_njetGeq2_mjj_gt350.csv</b> (non-resonant background) datasets.

Sequence to run the notebooks to generate the results:
1. Generate ANN engineered features
2. Combine ANN features
3. ANN benchmark performance with 5% myy corr.
4. ANN training (hyperparameter optimisation)

layers.py and ops.py are local import files used in notebooks 3 and 4.

## Acknowledgments 

Many thanks to my supervisor Dr. Liza Mijovic for her invaluable suggestions and advice during this study. 
