# Feature Point

1. Select some representative feature points from the image.  These points will remain the same after a small change in the camera's angle of view, so that we can find the same points in each image.
2. On the basis of these points, the problem of camera pose estimation and the positioning of these points are discussed.

**Feature** is another digital expression of image information.

In visual odometry, we hope that feature points **remain stable after the camera moves**.

## 1. Corners

Therefore, an intuitive way to extract features is to identify **corners** in different images and then determine their correspondence.

Algorithms:

Harris corner, FAST corner, GFTT corner

## 2 More stable local features

Simple corner points are variant to scales.  So there are more stable local image features:

SIFT, SURF, ORB

## **3 Feature Point Properties**:

1. Repeatability: The same feature can be found in different images.
2. Distinctiveness: Different features have different expressions.
3. Efficiency: In the same image, the number of feature points should be far smaller than the number of pixels.
4. Locality: The feature is only related to a small image area.

## 4 A feature point is composed of two parts:

- **Key-point**: position of the feature point in the image, and some types of feature points also hold information such as orientation and size.
- **Descriptor**: usually a vector, describing the information of the pixels around the key point according to some handcrafted rules. Features with similar appearance should have similar descriptors.

## 5 Some Popular Feature Point Methods

| Method                                   | Feature Point | Descriptor    | Speed | Summary                                                      |
| ---------------------------------------- | ------------- | ------------- | ----- | ------------------------------------------------------------ |
| SIFT (Scale-Invariant Feature Transform) | SIFT          | SIFT          | Slow  | Fully consider the changes in illumination, scale and rotation |
| FAST key point                           | FAST          | N/A           | Fast  | A feature point that is extremely fast to calculate.  No descriptor. No direction information |
| ORB (Oriented FAST and Rotated BRIEF)    | Oriented FAST | Rotated BRIEF | Fast  | It solves the problem that FAST detector does not have directionality, and uses the extremely fast binary descriptor BRIEF. |

