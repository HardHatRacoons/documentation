# Algorithm Documentation
Welcome to the Algorithm section of HardHatRaccoon Documentation.

```bash
git clone git@github.com:HardHatRacoons/trash-heap.git
```

Then make a virtual environment and download required libraries:

```bash
    python -m venv venv
    source venv/bin/activate
    pip install -r requirements.txt
```


# utils.py Documentation

## `dot(v, w)`
Computes the dot product of two 2D vectors.

**Parameters:**
- `v` (tuple or list of float): First 2D vector.
- `w` (tuple or list of float): Second 2D vector.

**Returns:**
- `float`: The dot product of `v` and `w`.

---

## `norm(v)`
Computes the Euclidean norm (magnitude) of a 2D vector.

**Parameters:**
- `v` (tuple or list of float): The 2D vector.

**Returns:**
- `float`: The Euclidean norm of `v`.

---

## `orientation(p1, p2, p3)`

Finds the orientation of an ordered triplet `(p1, p2, p3)`.

**Parameters:**

- `p1` (tuple or list of float): First point.
- `p2` (tuple or list of float): Second point.
- `p3` (tuple or list of float): Third point.

**Returns:**

- `int`: `0` for collinear, `1` for clockwise, `2` for counterclockwise.

---


## `distance_point_to_segment(P, A, B)`
Computes the shortest distance from a point `P` to a line segment defined by points `A` and `B`.

**Parameters:**
- `P` (tuple or list of float): The point.
- `A` (tuple or list of float): One endpoint of the segment.
- `B` (tuple or list of float): The other endpoint of the segment.

**Returns:**
- `float`: The shortest distance from `P` to segment `AB`.

---

## `segment_intersection(A1, A2, B1, B2)`

Determines if two line segments `A1A2` and `B1B2` intersect.

**Parameters:**

- `A1` (tuple or list of float): First endpoint of the first segment.
- `A2` (tuple or list of float): Second endpoint of the first segment.
- `B1` (tuple or list of float): First endpoint of the second segment.
- `B2` (tuple or list of float): Second endpoint of the second segment.

**Returns:**

- `bool`: `True` if the segments intersect, `False` otherwise.

---

## `segment_continuous(A1, A2, B1, B2)`

Determines if two line segments `A1A2` and `B1B2` fall within the same line.

**Parameters:**

- `A1` (tuple or list of float): First endpoint of the first segment.
- `A2` (tuple or list of float): Second endpoint of the first segment.
- `B1` (tuple or list of float): First endpoint of the second segment.
- `B2` (tuple or list of float): Second endpoint of the second segment.

**Returns:**

- `bool`: `True` if the segments fall within the same line, `False` otherwise.

---

## `segment_distance(A1, A2, B1, B2)`
Computes the shortest distance between two line segments `A1A2` and `B1B2`.

**Parameters:**
- `A1` (tuple or list of float): First endpoint of the first segment.
- `A2` (tuple or list of float): Second endpoint of the first segment.
- `B1` (tuple or list of float): First endpoint of the second segment.
- `B2` (tuple or list of float): Second endpoint of the second segment.

**Returns:**
- `float`: The shortest distance between the two segments.

---

## `segment_distance_wrapper(X, Y)`
Wrapper function to compute distances between multiple segments.

**Parameters:**
- `X` (tuple/list): Coordinates of the first set of segment endpoints.
- `Y` (tuple/list): Coordinates of the second set of segment endpoints.

**Returns:**
- `float`: Computed segment distance.

---

## `graham_scan(points)`
Computes the convex hull of a set of 2D points using Graham's scan algorithm.

**Parameters:**
- `points` (list of tuples/lists): A list of 2D points.

**Returns:**
- `list of lists`: The vertices of the convex hull in counterclockwise order.

---

## `annotate_bounds(file, eps, min_samples)`
Annotates bounding regions in a given file based on clustering parameters a.

**Parameters:**
- `file` (str): Path to the input file.
- `eps` (float): The epsilon parameter for clustering.
- `min_samples` (int): The minimum number of samples required to form a cluster.

**Returns:**
- `None`: The function processes the file and annotates bounds but does not return a value.

