# Libra: deep learning in fluent one-liners
A high-level machine learning API written in Python and Tensorflow that makes training deep neural networks as simple as a one-line function call. 


### Usage: the basics ###
Fitting a model to a feed-forward neural network to any dataset is as simple as this:
```python
import libra

newClient = client('dataset')
newClient.SingleRegressionQuery('Model the median house value')
newClient.tune()


```
No preprocessing is neccesary. All plots, losses, and models are stored in the models field in the client class. Calling ```tune()``` tunes hyperparameters like number of layers, learning rate, and layer size.

***

### Dataset Generation ###
This will generate a dataset of apples and oranges by parsing google images, prepprocess the dataset appropriately and then fit it to a Convolutional Neural Network. All images are reduced to a standard (224, 224, 3) size using a traditional OpenCV resizing algorithm.

```python
newClient.classGenQuery('apples', 'oranges')
```
Default size is 100 images for each. You can specify this size by adding ```class_size = number_in_each_class```

***
All plots are stored during runtime. This function plots all generated graphs for your current client object on one pane. 

```python
newClient.plotAll()
```

In depth metrics about your dataset and similarity information can be generated by calling:

```python
newClient.stat_analysis() or newClient.stat_analysis(dataset[columname])
```
A information graph as well as a similarity spectrum shown below will be generated:

![Image description](similarity.png)

This represents 5 columns that have the smallest cosine distance: these might need to be removed to reduce noise. You can specify whether you want to remove with ```inplace = True```. If you want to compare just a single column with the dataset you can do:

```python
 newClient.stat_analysis(dataset[columnname])
```

***

Performing dimensionality reduction is as simple as calling:

```python
dimensionalityRedQuery('Perform reduction to model median house value', model_to_fit, depth_of_search):
```

This uses a variety of different reduction techniques and outputs the best pipeline to modify your data. If you want to replace the dataset with the new modified one, you can specify ```inplace = True```.

 
### In Progress..... ###
