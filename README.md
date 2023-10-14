## 
### 1. Introduction:

The aim is to tackle the problem of tagging utterances using pre-defined tags with a supervised Deep Learning Neural Network approach. The training dataset provided contains utterances along with their corresponding tags. Notably, some utterances are associated with multiple tags. The dataset comprises:
- 2,253 records.
- 47 unique tags.

**Most Frequent Tags (Top 10):**
1. `movie.directedby`: 314
2. `none`: 312
3. `movie.starring.actor`: 294
4. `movie.rating`: 186
5. `movie.producedby`: 170 & `movie.initialreleasedate`: 141
6. `movie.language`: 137
7. `movie.country`: 135
8. Another instance of `movie.country`: 100
9. `movie.subjects`: 90

### 2. Model Architecture:

Before setting up an RNN architecture, the text data is initially passed through an Embedding Layer. The output from this layer is then channeled through the RNN layer. 

**RNN Hyperparameters:**
- **Input Size**: Determines the number of RNN inputs.
- **Hidden Size**: Specifies the number of neurons in the RNN layer.
- **Batch First**: Sets the first dimension to the batch size.
- **Non-Linearity**: Activation function for the RNN layer.

128 hidden layers were incorporated using the ReLU activation function. Subsequently, an improvement in training loss and an accuracy boost were observed upon shifting to the LeakyReLU activation function. The output layer employed the Sigmoid activation function. 

To optimize the loss (calculated with BCELoss function), the Adam optimizer was chosen. Throughout model training, the data is processed in batches, with forward and backward passes executed in each iteration. This training loop is executed over 100 or 150 epochs, with training and validation losses calculated at each epoch's end.

An LSTM model was also explored, operating similarly to the RNN, barring the number of epochs utilized.

For both models, boosting the number of epochs from 50 to 100 to 200 decreased validation and training data losses and enhanced overall accuracy.

### 3. Experiments:

Multiple experiments were conducted with both models. These experiments varied in:
- Model choice.
- Activation functions for hidden and output layers.
- Batch size adjustments.
- Epoch count variations.

**Key Observations:**
1. Employing Leaky ReLU resulted in better accuracy than using tanH and ReLU functions.
2. Upping the number of epochs curtailed training and validation data loss.
3. Modifying the input batch size brought improvements.

### 4. Results:

Upon running 200 epochs:
- **RNN**: Training loss was 0.3% while validation loss stood at 18%.
- **LSTM**: Training loss was also 0.3%, but validation loss was reduced to 10%.

Post-training, test data utterances were processed, with associated tags recorded in a CSV file as the final outcome.
