# Lane-Detection-
Road lane detection using Hough transform

Road Lane Detection Using Hough
Transform
1 Hough Transform (CHT)
The Hough transform can be used to determine the parameters of a line
when several points that fall on it are known. The normal form of a line can
be described with the following equation: x cos θ + y sin θ = ρ where ρ is
the length of a line that starts from the origin and perpendicular to the
required line, and θ is its inclination. The true parameters ρ and θ will get
maximum votes from the line points and can be found with a Hough
accumulation array.
2. Implementation Details
2.1. Smoothing the image
We passed the original image to cv2.medianBlur along with the kernel size
to smooth the image.
2.2 Edge Detection
After smoothing the image, we passed the original image to cv2.canny with
(100,200) as the thresholding values to remove the noise.
2.3 Region of interest
We defined a polygon to mask the unnecessary parts of the image then we
used fillpoly function to apply the polygon we defined on the image and
show on the road. We combined the resultant image with canny_image
using cv2.bitwise_and function.

![image](https://user-images.githubusercontent.com/48353755/142766308-baec1661-480b-4005-8e6e-ee17e566e53c.png)

2.3 Accumulation into (ρ, θ)-space using Hough transform

![image](https://user-images.githubusercontent.com/48353755/142766320-d86b9f7f-9a0c-441d-8428-93d93128197e.png)

We applied the above algorithm to get Hough space below. Each
intersection in the Hough space corresponds to a lane in the masked image
and each line corresponds to a point in the masked image

![image](https://user-images.githubusercontent.com/48353755/142766332-9d29ad84-9b50-44b0-bca8-e24638a91cc8.png)

2.4 Refining Coordinates and HT Post-Processing
After applying hough transform with the above algorithm, we extracted all
the points that votes a line in the original image. Then, we applied local
maximum to the point above a certain threshold to make sure that we took
the most voted points extracted.
Finally, we applied the same polygon we used for each picture to get the
lines only we are interested in in the same region of interest (the same
polygon applied for each image).

![Uploading image.png…]()

![Uploading image.png…]()


