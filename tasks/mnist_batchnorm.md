In this assignment, you will work with extend the `mnist_conv` assignment to
support batch normalization. Start with the
[mnist_conv.py](https://github.com/ufal/npfl114/tree/master/labs/04/mnist_conv.py)
template and in addition to all functionality of `mnist_conv`, implement also
the following layer:
- `CB-filters-kernel_size-stride-padding`: Add a convolutional layer with BatchNorm
  and ReLU activation and specified number of filters, kernel size, stride and padding.
  Example: `CB-10-3-1-same`

To correctly implement BatchNorm:
- The convolutional layer should not use any activation and no biases.
- The output of the convolutional layer is passed to batch normalization layer, which
  should specify `training=True` during training and `training=False` during inference.
- The output of the batch normalization layer is passed through tf.nn.relu.
- You need to update the moving averages of mean and variance in the batch normalization
  layer during each training batch. Such update operations can be obtained using
  `tf.get_collection(tf.GraphKeys.UPDATE_OPS)` and utilized either directly in `session.run`,
  or (preferably) attached to `self.train` using `tf.control_dependencies`.

For example, when using `--cnn=CB-10-3-2-same,A-3-2,F,R-100`, the development
accuracies after first five epochs should be 96.18, 97.38, 97.74, 97.96 and 98.30.

You can now experiment with various architectures and try obtaining best
accuracy on MNIST.
