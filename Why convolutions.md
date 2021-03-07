there are three fundamental reasons for that:
- **Parameter sharing**: A feature detector (such as edge detector ), which is filter, that is useful in one part of the image is probably useful in other parts too. For instance, vertical edge can appear on multiple locations in an image and we can detect it using a single filter.
- **Sensitivity of connections**: In each layer, the output value depends only on a small number of inputs. For instance, when we apply filter F(3x3) on image X then the first value of our output matrix will only depends on 3x3 region of X. It makes NN less prone to overfitting. 
- **convolution structure** makes NN translation invariant.  