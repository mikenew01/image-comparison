# Image Comparisons and Clustering Ideas
List of Techniques and Possible Approaches to do Image Comparisons

Number of :star: indicate difficulty in understanding underlying theory. 

## :star: Image Subtraction  
1. Subtract one image from another
2. Use the histogram or number of foreground pixels as a similarity metric

## Similarity Metrics

### :star: chi2 distance
Calculate histogram of your image or use directly on binary, [stackexchange](https://stats.stackexchange.com/questions/184101/comparing-two-histograms-using-chi-square-distance)

### :star: RMSE Family
Root Mean Squared error, Normalized RMSE and other implementations from [scikit-image.measure](http://scikit-image.org/docs/dev/api/skimage.measure.html)

### :star: :star: Structured Similarity Index 
- scikit-image has a [SSI implementation](http://scikit-image.org/docs/dev/api/skimage.measure.html#structural-similarity)
https://pastebin.com/fwT059Zw
- SSI is different from RMSE because it is locally sensitive to image components, while RMSE takes the entire image in one go
- [compare_ssim](http://scikit-image.org/docs/dev/api/skimage.measure.html#skimage.measure.compare_ssim) computes the mean structural similarity index between two images

## Feature Extractions

### :star: :star: Image Hash
A image hashing library written in Python. ImageHash supports:
- average hashing ([aHash](http://www.hackerfactor.com/blog/index.php?/archives/432-Looks-Like-It.html))
- perception hashing ([pHash](http://www.hackerfactor.com/blog/index.php?/archives/432-Looks-Like-It.html))
- difference hashing ([dHash](http://www.hackerfactor.com/blog/index.php?/archives/529-Kind-of-Like-That.html))
- wavelet hashing ([wHash](https://fullstackml.com/2016/07/02/wavelet-image-hash-in-python/))

### :star: Edges and Contours Detection
- Use something like [Canny](http://opencv-python-tutroals.readthedocs.io/en/latest/py_tutorials/py_imgproc/py_canny/py_canny.html) or [Sobel](https://docs.opencv.org/3.0-beta/doc/py_tutorials/py_imgproc/py_gradients/py_gradients.html) to find location, intensity, distribution or other features of these edges. 

### :star: :star: :star:SIFT/SURF 
- Scale Invariant Feature Transform [python introduction](https://docs.opencv.org/3.1.0/da/df5/tutorial_py_sift_intro.html) is an image feature tranformation and extraction technique. 

Use pairwise comparisons, Euclidean distance or relevant similarity metric on these features for getting a more intuitive comparison metric

## :star: :star: :star: :star: Siamese Neural Networks 
- This is a deep neural networks based approach where the feature extraction as well as the similarity function is learned by the network
- This approach need pairs or triplets tagged from n-way classes
- [PyTorch Implementation for Facial Similarity](https://github.com/harveyslash/Facial-Similarity-with-Siamese-Networks-in-Pytorch), with a [Medium blog](https://hackernoon.com/facial-similarity-with-siamese-networks-in-pytorch-9642aa9db2f7) explaining the same
- This implementation uses [contrastive loss instead of triplet loss](https://stackoverflow.com/questions/38260113/implementing-contrastive-loss-and-triplet-loss-in-tensorflow)
