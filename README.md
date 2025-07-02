
# NS-QPE: A Neuro-Symbolic approach for Quantitative Precipitation Estimation (QPE)

## Introduction

This repository contains code for the paper "NS-QPE: A Neuro-Symbolic Approach Towards Accurate and Interpretable Quantitative Precipitation Estimation Using Polarimetric Radar Data", accepted by the IEEE AMLDS 2025 conference. It integrates symbolic equations derived from symbolic regression and empirical formulas with a neural network model in PyTorch.

## Abstract

Accurate precipitation estimation is crucial for managing water resources and mitigating disasters. While empirical equations exist for Quantitative Precipitation Estimation (QPE) using dual-polarization radar data, they are often limited to specific meteorological case studies. Deep learning has also been applied for dual-polarization radar QPE, but such models often function as black boxes, lacking interpretability and explainability. This study introduces a hybrid Neuro-Symbolic AI method for quantitative precipitation estimation using polarimetric radar data, called NS-QPE. Our method consists of a Neural Network (NN) component and a symbolic component, guiding each other during training using a custom loss function that combines the losses of both components using a weighted average method. Parameters of the neural network and the symbolic equation are updated simultaneously via the backpropagation of model training. The hybrid model combines predictions of the neural network and symbolic equations, aiming to balance interpretability with predictive performance. Our results indicate that the hybrid model not only maintains RMSE scores comparable to the purely neural network model but also enhances interpretability through the integration of symbolic knowledge. Moreover, our model calibrates the parameters of symbolic equations for the case study it is trained on, demonstrating lower sensitivity to initial values and improved accuracy compared to traditional calibration method used for QPE.


## Installation

1. Clone or download the repository and navigate to its root directory:

   ```bash
   git clone https://github.com/big-data-lab-umbc/NS-QPE.git
   cd NS-QPE
   ```


2. (Optional but recommended) Create and activate a Python virtual environment:

   ```bash
   python3 -m venv venv
   source venv/bin/activate
   ```

3. Install the required Python packages:

   ```bash
   pip install -r requirements.txt
   ```

    Or manually:

    ```bash
   pip install numpy pandas matplotlib torch scikit-learn shap
   ```
## Instruction


Run the cells NS_QPE_V1.ipynb file to:

1.  Load and preprocess the datasets in ```Data``` folder.

2. Choose between ```SR based Symbolic model``` or ```Empirical based symbolic model``` and run the cell accordingly to define the symbolic component.

3. In the ```Training``` part the dynamic or static weighting approach can be defined by: 

 * Dynamic ``` (neural_weight=2) ``` : Model optimize the weights for contribution of each componenets. 

  * Static ``` (neural_weight≠2) ``` : User can staticly define the contribution of each components by seting the value for ```neural_weight``` (eg. if ```neural_weight=0.6``` the weight for contribution of symbolic component will be ``` 1 - neural_weight = 0.4```) . 


4. Evaluate the performance of the model using MAE, RMSE, R², and bias metrics on test data.

5. Interpret feature importance across different rainfall conditions using SHAP values.




