Dependencies:
numpy pandas scipy matplotlib sklearn ta lightgbm hyperopt joblib optuna iisignature
And ksig, as downloaded from https://github.com/tgcsaba/KSig, which requires cuda.

train.ipynb is stylised as a report containing all of our unsuccessful and successful attempts - this means that not every cell needs to be run (and modules such as torch, XGboost do not need to be installed). Feature generation and training overall took us quite a while (~72 hours computational time!!), and will require rerunning the signature kernel cells multiple times with the specified L values. Note that the features generated are very large! Please email us if you have any questions about the training process.

test.ipynb is designed to be run straightforwardly through, and will display our R2 scores on the test set as requested with minimal library requirements.