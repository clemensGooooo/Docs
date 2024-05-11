Create  a CNN using Tensorflow

```python
from tensorflow import keras
import tensorflow as tf
```

## Data Preparation
Prepare your training data. This involves loading, splitting into training and testing sets, and possibly normalizing the data.
- Data should be in the `numpy.array()` format

## Create Model

```python
model = tf.keras.Sequential([
	tf.keras.layers.Flatten(input_shape=(28, 28)),
	tf.keras.layers.Dense(128, activation='relu'),
	tf.keras.layers.Dropout(0.2),
	tf.keras.layers.Dense(10)
])
```

- `tf.keras.Sequential([<layers>])`, the first param is the list of layers in the neural network
- `input_shape=(28, 28)`, the first layer must **define** the **input shape**

**Additional param**: `name = "test"` - which names the model


You can also create a neural network with the box below.

```python
model = tensorflow.keras.Sequential()
tensorflow.keras.layers.Input()
model.add(tensorflow.keras.layers.Conv2D(16, input_shape=input_shape))
... # add more layers with model.add()
model.add(layers.Dense(1, activation="sigmoid"))
```

**Show model and layers**
```python
model.summary()
```

## Compile

```python
model.compile(optimizer="adam",loss=keras.losses.BinaryCrossentropy(),
metrics=["accuracy"])
```
- `optimizer`, specifies the algorithm for **updating the model's weights** during training
- `loss`, defines the destination, what the output should be like, you want to minimize `sparse_categorical_crossentropy` (also, dass es keine Überschneidungen an Klassen-Wahrscheinlichkeiten gibt, sondern immer ein Wert herausstechen soll)
- `metrics`, what should be monitored during the test
## Train

```python
model.fit(x_train, y_train, epochs=epochs)
```

- `x_train`, input training data
- `y_train`, output training data
- `epochs`, specifies the number of times the entire training dataset is passed forward and backward through the neural network.
## Test
```python
test_loss, test_acc = model.evaluate(x_test, y_test, verbose=1)
```
- `x_test`, input data for testing the model
- `y_test`, output data for testing the model
- Additional `verbose` shows progress
## Use Model

```python
predictions = model.predict(x_data)
```
- `x_data`, data to get predictions
- `predictions` return an array of probabilities

## Export Model

```python
model.save('model.h5')
```

- `'model.h5'`, saves the model to a file


## Optimization

- **Add more data**, more data improves the accuracy
- **Change the layers** of the model (add/remove/adjust layer)
- **Change** training **data**, for example edit images
- Less/More epochs