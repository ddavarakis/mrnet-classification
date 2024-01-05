# MRNet Classification

### Cross Validation

Το test the ability of models to predict new data that was not used during training, to flag overfitting and to see how the model will generalise to an independent dataset (i.e., an unknown dataset). 

The k-fold cross-validation was run on the adapted baseline ResNet-18 model, including 2 extra convolutional blocks and a batch normalization layer. 

The training dataset is augmented and concatenated with the validation dataset to create the dataset to be used during cross-validation.

Due to limited resources (GPU and GPU RAM), the k-fold cross validation run on a subset (20%) of the concatenated and augmented dataset. Cross Validation run with 20% of augmented data. 

### Models evaluation

The MRNet dataset consists of a training set (1,130 exams, 1,088 patients), a validation set (120 exams, 111 patients), and a test set (120 exams, 113 patients). As the test set is not publicly available, the final 120 samples from the end of the training set were used as testing dataset.

While this approach may seem too simplistic, it would appear that the validation set was extracted in the same fashion. For this reason, alternative methods of data splitting, such as stratification, were not considered. This could be a limitation, however.

### Combining MRNet predictions via a Logistic Regression Model

Given predictions from the best models for each plane (sagittal, coronal and axial) on the training dataset along with the corresponding labels, three logistic regression models were trained; one for each tear (abnormal, ACL, meniscus). Each regression model weights the predictions from the 3 planes for a tear and generates a final probability for the specific tear.

After training, the logistic regression models evaluated the predictions of the testing data set on the validation data. A model generated using cross-validation was examined if it might be more appropriate.
