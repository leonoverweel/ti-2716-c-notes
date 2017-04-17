# Harris corner detector

It is important to detect corners in images because corner points are easy to find back after images have been deformed, corners can
be found by moving a window over the image and storing locations where the contents of the window change a lot when it is shifted.
Change in a window can be expressed as follows:

`E(u,v) = Σ(x,y) w(x,y)*(I(x+u, y+v) - I(x,y))²`

Here w(x,y) is the result of the window function at location (x,y). To common window functions are a square window (1 inside, 0 outside)
and a gaussian. I(x,y) means the intensity of the image at location (x,y). E(u,v) represents the total change in intensity when moving
the window `u` pixels horizontally and `v` pixels vertically from its starting location.
