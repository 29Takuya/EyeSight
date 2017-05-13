# detect_eyesight
- Detecting eye sight with machine learning(support vector machine, convolution neural network).

## SVM
- Kernel: Polynomial
- Input:  Pixel(32×96)
- Accuracy: 0.786

 ![result](https://github.com/29Takuya/EyeSight/blob/media/output_svm.gif)
  
## CNN
- batchsize: 100
- epoch: 100
- Accuracy: 80.2
```
def forward(x_data, y_data, train=True):
    x, t = chainer.Variable(x_data), chainer.Variable(y_data)
    h = F.max_pooling_2d(F.relu(model.conv1(x)), 2)
    h = F.max_pooling_2d(F.relu(model.conv2(h)), 2)
    h = F.dropout(F.relu(model.l1(h)), train=train)
    y = model.l2(h)
    if train:
        return F.softmax_cross_entropy(y, t)
    else:
        return F.accuracy(y, t)
```

![result](https://github.com/29Takuya/EyeSight/blob/media/output_cnn.gif)
