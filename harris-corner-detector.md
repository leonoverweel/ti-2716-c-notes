# Harris corner detector

It is important to detect corners in images because corner points are easy to find back after images have been deformed, corners can
be found by moving a window over the image and storing locations where the contents of the window change a lot when it is shifted.
Change in a window can be expressed as follows:

`E(u,v) = Σ(x,y) w(x,y)*(I(x+u, y+v) - I(x,y))²`

Here w(x,y) is the result of the window function at location (x,y). To common window functions are a square window (1 inside, 0 outside)
and a gaussian. I(x,y) means the intensity of the image at location (x,y). E(u,v) represents the total change in intensity when moving
the window `u` pixels horizontally and `v` pixels vertically from its starting location.

## Quadratic approximation

To find in-between-pixel results we can use a Taylor expansion, an approximation of this can be given by:

`E(u,v) ≈ [u v] M [u; v]`

Where `M`, the **second moment matrix**, is defined <sub>a</sub> by:

`M = Σ(x,y) w(x,y)*[Iₓ², IₓI`<sub>`y`</sub>`; IₓI`<sub>`y`</sub>`, I`<sub>`y`</sub>`²]`

Now with some linear algebra [magic](https://blackboard.tudelft.nl/bbcswebdav/pid-2928030-dt-content-rid-10171523_2/courses/40224-161703/MMA_Week4_Lecture1_2017_harris.pdf) we can express `M` with two **orthogonal eigenvalues**:

`M -> [λ₁ 0; 0 λ₂]`

As can be seen in the following image, these two eigenvalues form an ellipse together that describes the rate in which `E` changes
when moving the window in a particular direction.

![ellipse](https://teroninsights.files.wordpress.com/2013/03/ellipse.png)

## Interpreting eigenvalues

For a location in the image to be classified as being a corner, its `E` needs to change a lot when moving in any direction.
This means we want our ellipse to be much like a circle, and as large as possible. In short: `λ₁` and `λ₂` both need to be
large and `λ₁ ≈ λ₂`.

## Harris corner detection steps

- Compute `M` matrix for each pixel surrounded by a window. Calculate `m`'s eigenvalues to find its cornerness.
- Keep only points with a high cornerness score.
- For all remaining points keep only the local maxima.
