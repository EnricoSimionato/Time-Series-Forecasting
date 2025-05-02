# Artificial Neural Networks and Deep Learning-2023/2024
<img src="./Assets/bannerAN2DL.png" width="100%"/>

Repository of the `Artificial Neural Networks and Deep Learning (AN2DL)` project with focus in **Image Classification** and **Time Series Forecasting**. The associated challenge was hosted on CodaLab platform.

## Team
<table align="center">
<tr><td>

| Name             |    ID    |
| :--------------- | :------: |
| Paolo Pertino    | 10729600 |
| Alberto Sandri   | 10698469 |
| Enrico Simionato | 10698193 |

</td><td>

|    Professor & Tutors      |                   Role                 |
|:---------------------------|:--------------------------------------:|
| Matteo Matteucci               | AN2DL Professor |
| Giacomo Boracchi         | AN2DL Professor |
| Eugenio Lomurno | Teaching Assistant |
| Loris Giulivi | Teaching Assistant |
| Francesco Lattari | Teaching Assistant |


</td></tr> </table>


## Project structure
The project is divided in two homeworks, each one of them is contained in a single Jupyter Notebook in the respective folder. The homeworks are the following:

### 1. **Homework 1 - Plant Images Classification**: 

This homework addresses the task of plant health classification through the use of deep neural networks. The project aims to categorize images of plants as either healthy or unhealthy. Here is a succinct overview of the main contributions and findings:

- #### Data Processing

  - Initial data inspection led to the removal of outliers and duplicates, resulting in a preprocessed dataset of 4850 RGB images (96x96).
  - The dataset exhibits a slight imbalance, with 63.09% healthy plants.

- #### Best Model - ConvNeXt

  - Utilized a ConvNeXt base model, achieving a remarkable 94% accuracy on the CodaLab development phase.
  - Incorporated transfer learning and fine-tuning, data augmentation, and sample weight balancing for enhanced model robustness.
  - ConvNeXt demonstrated stability in training and resilience to overfitting.

- #### Experiments

  - Explored diverse augmentation techniques, focusing on geometric transformations given the significance of color variations.
  - Conducted experiments with modern augmentation methods (MixUp and CutMix) for effective regularization during training.
  - Adjusted the classification threshold to 0.65 using ROC analysis, improving recall and prioritizing unhealthy plant classification.
  - Implemented test-time augmentation for increased invariance to transformations, resulting in a 2-3% improvement in evaluation metrics.

- #### EfficientNet Models

  - Explored EfficientNet models (B0, B4, B7) as feature extraction networks, noting high performance and faster training.
  - Encountered stability issues in submission accuracy despite consistent results on the holdout test set.

- #### Ensemble Methods

  - Explored ensemble methods, including bootstrapping and model combinations, with limited observed improvement.
  - Constructed an ensemble with ConvNeXt models using majority and soft voting, but collective performance did not surpass the best individual model.

- #### Explainability

  - Employed the LIME library for model explainability, revealing crucial features for classification in unhealthy plant images. 


### 2. **Homework 2 - Time Series Forecasting**: 

This homework addresses the challenge of time series forecasting using various deep neural networks. The objective is to forecast the future 9 and 18 samples of time series, that in the test set have length 200. The metric used to evaluate models is the Mean Squared Error. Here an outline of methods, techniques, and results:

- #### Data Exploration and Preprocessing

  - Identified and eliminated duplicated time series.
  - Explored preprocessing with Scikit-Learn *RobustScaler* and *auto-arima* function leveraging the Box-Jenkins method to identify the time series order and determined an optimal window size of 100-150 samples.
 
- #### Best Model - Ensemble

  - Ensemble of N-Beats and Bidirectional LSTM models achieved superior performance with MSE of 0.0049 in the first phase and MSE of 0.0102 in the second phase.
  - Diversified models through varying input window duration,  bootstrapping, and number of stacks for N-Beats.

- #### Model Experiments

  - ##### LSTM + Conv

    - Blend of bidirectional LSTM layers and one-dimensional convolutional layers.
    - Initial promising results, but hyperparameter tuning revealed reduced capacity and tendency to overfit.

  - ##### Bidirectional LSTM

    - Singular layer of bidirectional LSTMs enabling concurrent forward and backward sequence processing for improved comprehension of temporal patterns.
    - Dropout enhanced generalization, outperforming more complex alternatives with MSE around 0.0055.

  - ##### Category-Integrated Neural Network (CINN)

    - Explored embedding category information within the network using one-hot encoding.
    - Achieved MSE of 0.0058, but limitations observed, questioning the utility of categories.

  - ##### Model on Detrended and Deseasoned Time Series

    - Attempted enhanced LSTM outcomes through systematic detrending and deseasoning.
    - Results were not as promising, potential limitations in custom implementation and universal application across all series.

  - ##### N-BEATS

    - Utilized N-Beats architecture based on backward and forward residual links and a deep stack of fully-connected layers.
    - Performance measured with MSE around 0.0065 on 1st phase.

  - ##### Time2Vec

    - Incorporated Time2Vec technique to encode temporal information into vectors.
    - Minimal improvements observed despite modifications.


## Requirements & Installation
To install this project dependencies please run the following command:
```bash
pip install -r requirements.txt
```

## Folder structure
<pre>
├── Assets
│   └── bannerAN2DL.png
├── Homework 1 - Plant Images Classification
│   ├── ANNDL-Homework1-Report.pdf
│   └── Homework_1.ipynb
├── Homework 2 - Time Series Forecasting
│   ├── ANNDL-Homework2-Report.pdf
│   └── Homework_2.ipynb
├── README.md
└── requirements.txt
</pre>

## References
[1] Oreshkin, B. N., Carpov, D., Chapados, N., & Bengio, Y. (2020). N-BEATS: Neural basis expansion analysis for interpretable time series forecasting. International Conference on Learning Representations. https://www.openreview.net/pdf?id=r1ecqn4YwB

[2] Remy, P. (2020). N-BEATS: Neural basis expansion analysis for interpretable time series forecasting. In GitHub repository. GitHub. https://github.com/philipperemy/n-beats

[3] Cote, D. (2022) Hands-On Advanced Deep Learning Time Series Forecasting with Tensors, Medium. Available at: https://medium.com/@dave.cote.msc/hands-on-advanced-deep-learning-time-series-forecasting-with-tensors-7facae522f18



