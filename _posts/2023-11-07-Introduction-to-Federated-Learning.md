## Introduction to Federated Learning

The remarkable success of deep learning is mainly attributed to the availability of large amounts of data and computing power. With the advent of smart devices, abundant data is generated on a daily basis at different devices all over the world. We could leverage this data to train powerful deep-learning models. However, collecting this user-generated data for centralized processing is not practical because of communication and data privacy constraints. To address this concern, a new interest in developing distributed learning algorithms has emerged. 

Federated learning (FL) is a popular setting in the distributed machine learning paradigm. In this setting, the training data is kept locally at the edge devices and a global shared model is learned by aggregating the locally computed updates through a coordinating central server. Federated Averaging ([FedAvg](https://arxiv.org/pdf/1602.05629.pdf)) is the first and most widely used FL algorithm.

### Types of Federated Learning
