# Prediction Bias Coefficient

This repository contains the code based on the paper "Evaluating the Prediction Bias Induced by Label Imbalance in Multi-label Classification". 

## Abstract:
Prediction bias is a well-known problem in classification algorithms, which tend to be skewed towards more represented classes. This phenomenon is even more remarkable in multi-label scenarios, where the number of underrepresented classes is usually larger. Moreover, there are applications in which a prediction bias can translate into the discrimination or exclusion of certain minorities of the society. In light of this, we hereby present the Prediction Bias Coefficient (PBC), a novel measure that aims to assess the bias induced by label imbalance in multi-label classification. The approach leverages Spearman's rank correlation coefficient between the label frequencies and the F-scores obtained for each label individually. After describing the theoretical properties of the proposed indicator, we illustrate its behaviour on a classification task performed with state-of-the-art methods on two real-world datasets, and we compare it experimentally with other metrics described in the literature.

## Configuration

It is recommended to install the requirements in a Python virtual environment to avoid modifying system state. 
```bash
python -m venv .env
source .env/bin/activate

```
Execute the following commands to install the requirements.
```bash
pip install --upgrade pip
pip install -r requirements.txt
```

## Notebooks

The code to execute the algorithm presented in the paper is contained in the two Jupyter Notebooks:
- ``prepare_datasets.ipynb``:  extract the data from the selected dataset, convert it into a Pandas dataframe and save it into a csv file. This should be executed before ``text_classification.ipynb``. See next section for information on how to obtain the data and how to place them inside the project.
- ``text_classification.ipynb``: run the classification task and evaluate the performance with a cross-validation strategy.

To reproduce the results presented in the paper, execute the ``run_cross_validation`` function with the following parameters:
```
metrics = run_cross_validation(samples, n_folds=10, training_batch_size=8, n_training_iter=10, confidence_threshold=0.5)
```

## Data

The notebooks can be executed on two different datasets.

### Webscope R4
This dataset contains a small sample of the Yahoo! Movies community's preferences for various movies, rated on a scale from A+ to F. For the paper's purpose, the dataset also contains a large amount of descriptive information about many movies including synopsis and genre.
https://webscope.sandbox.yahoo.com/catalog.php?datatype=r

Once the data is obtained through the link above, it should be placed inside the folder ``data/webscope``. Then, ``prepare_datasets.ipynb`` should be executed to process the data in a format appropriate for ``text_classification.ipynb``.

### Reuters-21578
This is a collection of documents that appeared on Reuters newswire in 1987. The documents were assembled and indexed with categories.
http://archive.ics.uci.edu/ml/datasets/Reuters-21578+Text+Categorization+Collection

Once the data is obtained through the link above, it should be placed inside the folder ``data/reuters``. Then, ``prepare_datasets.ipynb`` should be executed to process the data in a format appropriate for ``text_classification.ipynb``.
