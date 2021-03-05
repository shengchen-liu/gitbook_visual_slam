# Calculate Camera Motion

After we have key points matching, we need to estimate the camera's motion based on the matching.  It is totally different for different camera settings.

1. Monocular camera: epipolar geometry.
2. Binocular, RGB-D or the distance is obtained by some method (two sets of 3D points):  ICP
3. If one set is 3D and on set is 2D: PnP.