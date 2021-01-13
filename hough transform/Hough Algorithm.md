# Hough Algorithm

## Pseudo Code

```
Initialize H[d, theta] = 0
For each edge point in E(x, y) in the image
	for theta = -90 to 90
		d = x * cos(theta) + y * sin(theta)
		H[d, theta] += 1
Find the value(s) of (d, theta) of (d, theta) where H[d, theta] is maximum
The detected line in the image is gvien by d = x * cos(theta) + y * sin(theta)
```

## Complexity of the Hough Transform

**Space**: $$k^n$$ (n dimensions, k bins each)

**Time**: linearly proportional to the number of edge points, whereases the voting itself is constant.

