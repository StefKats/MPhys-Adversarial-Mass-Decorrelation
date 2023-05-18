# README
Applying Adversarial Neural Networks (ANNs) to improve classification of Higgs boson events in the diphoton decay channel. 

First need the <b>PowhegPy8EG_NNPDF30_VBFH125mc16a.csv</b> (Higgs->diphoton signal) and <b>Sherpa2_yyjj_njetGeq2_mjj_gt350.csv</b> (non-resonant background) datasets.

Sequence to run the notebooks to generate the results:
1. Generate ANN engineered features
2. Combine ANN features
3. ANN benchmark performance with 5% myy corr.
4. ANN training (hyperparameter optimisation)

layers.py and ops.py are local import files used in notebooks 3 and 4.
