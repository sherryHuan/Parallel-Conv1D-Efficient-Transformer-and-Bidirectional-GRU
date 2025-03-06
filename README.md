# Gait Analysis for Parkinson's Disease Detection and Severity Staging
---

This repository provides the implementation of the paper.  To cite:

X. Huan, H. Zhou, B. Jung and L. Ma, "Enhancing Gait Analysis for Parkinson’s Disease Detection and Severity Staging With a Parallel Conv1D-Efficient Transformer and Bidirectional GRU Hybrid Architecture," in IEEE Access, vol. 13, pp. 33351-33360, 2025, doi:[10.1109/ACCESS.2025.3543749](https://doi.org/10.1109/ACCESS.2025.3543749). 

---

## Dataset

The dataset used in this study is available at [PhysioNet Gait Dynamics Dataset](https://physionet.org/content/gaitpdb/1.0.0/). 
A sample of the dataset can be found in the data subfolder.

---       

## Getting Started
### Prerequisites

To run the project, ensure the following are installed:
- Python 3.8
- TensorFlow and Keras
- NVIDIA GPU with CUDA and CuDNN support (for training speedup)

Install the required libraries using the provided `requirements.txt`:
```bash
pip install -r requirements.txt

```
### Running the Code

#### Example Directory Structure

Ensure the input data folder contains:

../data

    ├── demographics.csv  (contains patient information)
    
    ...
    
    ├── *.txt          
           
Depending on your objective, you can use either:
- train_classifier for PD detection(2-class)

```bash
args = argparse.Namespace(
    input_data='../data',
    exp_name='train_classifier',
    output='train_classifier_conv1D_transformer_then_gru_branch_output'
)

```

- train_severity for severity staging (Hoehn and Yahr 4-class)

```bash
args = argparse.Namespace(
    input_data='../data',
    exp_name='train_severity',
    output='train_severity_conv1D_transformer_then_gru_branch_output'
)

```

Output Files

Running the code will generate output in the specified folder:

./output

    ├── train_severity_month_day
        ├── hour_minutes
            ├── confusion_matrix.csv: Confusion matrix for classification.
            ├── gt.csv: Ground truth labels for each patient.
            ├── pred.csv: Predicted labels for each patient.
            ├── model.json: JSON representation of the trained model.
            ├── res_pat.csv: Accuracy results by patient.
            ├── res_seg.csv: Accuracy results by segment.
            ├── training_i.csv: Training and validation metrics for the i-th fold (i = [1..10]).
            ├── weights_i.keras: Model weights for the i-th fold (i = [1..10]).
