# Hough Transform

**Hough Transform** is a voting technique that can be used to solve following questions about finding lines in an image:

- Given points that belong to a line, what is that line?
- How many lines are there?
- Which points belong to which lines?

The **main idea** behind the Hough Transform is that each edge point (i.e. each pixel found after applying an edge-detecting operator) votes for its compatible lines. Hopefully, the lines that get many votes are valid.

## Hough Space

Hough Space is also called parameter space - which enables a different representation of our desired shapes.

The key is that a **line** $$y = mx + b$$ in image space represents a **point** in Hough space because we use the parameters of the line $$(m, b)$$.  Similarly, a **point** in image space represents a line in Hough space.

For a given point $$(x_0, y_0)$$, it fits all the lines going thought it with equation $$y_0 = mx_0 + b$$, thus it becomes $$b = -x_0m + y_0$$ which is a line in Hough space.

### Multiple Points

If we have two points, we can determine the line passing thought both of them in Cartesian space using:

$$
y - y_1 = m(x - x_1)
$$

where as we know :
$$
m = \frac{y_2 - y_1}{x_2 - x_1}
$$


Similarly, a bunch of points produces a bunch of lines in Hough, all of which intersect in one place.  The closer the points are to a particular line of best fit, the closer their points of intersection in Hough space.

![image-20210112222744974](../edge_detection/assets/image-20210112222744974.png)

If we discretize Hough space into "bins" for voting, we end up with the Hough algorithm.  In the Hough algorithm, each point in image space votes for every bin along its line in Hough space: the bin with the most votes becomes the line of best fit among the points.

Unfortunately, the $$(m,b)$$ representation of lines comes with some problems.  For example, a vertical line has $$m = \infin$$.  To avoid this, we use **Polar Representation of Lines**

