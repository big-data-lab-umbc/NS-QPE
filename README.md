
# NS-QPE 

This repository contains code for a Neuro-Symbolic approach for Quantitative Precipitation Estimation (QPE) using polarimetric radar data. It integrates symbolic equations derived from symbolic regression and empirical formulas with a neural network model in PyTorch.

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
