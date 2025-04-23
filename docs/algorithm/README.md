
# 📄 Hard Hat Raccoon Algorithm Documentation

This project is a Flask-based API for processing and annotating steel structure diagrams in PDF format. It uses AWS S3 for file storage and includes a custom geometric analysis and clustering pipeline.

---

## 📁 Files Overview

### `application.py` ✅ (Production)  <!-- {docsify-ignore} -->
Main entry point of the API. Handles incoming HTTP requests, security (API key validation), and asynchronous PDF processing.

### `utils.py` ✅ (Production)  <!-- {docsify-ignore} -->
Contains all geometric computations, pattern recognition, clustering, and PDF annotation logic.

### `tests.py` 🧪 (Development)  <!-- {docsify-ignore} -->
Contains unit tests written with Python's `unittest` framework. Code coverage is measured using `coverage.py`.

### `main.py` ⚙️ (Development)  <!-- {docsify-ignore} -->
Developer tool for running high-level processing logic locally. Uses `sentry_sdk` for profiling and error tracking.

### `vectorize_page.py` 🖼️ (Debugging) <!-- {docsify-ignore} -->
Generates page-level visualizations to help with debugging and fine-tuning the steel structure detection logic.

---

## 🚀 Endpoints

### `GET /`  <!-- {docsify-ignore} -->
Basic health check.

### `POST /api/v1/pdf-proccessing/request`  <!-- {docsify-ignore} -->
Initiates asynchronous processing of a PDF document uploaded to S3.

#### Request JSON Body  <!-- {docsify-ignore} -->
```json
{
  "file_id": "string",
  "user_id": "string",
  "bucket_name": "string"
}
```

#### Response  <!-- {docsify-ignore} -->
- `202 Accepted`: Processing started.
- `401 Unauthorized`: Missing API key.
- `403 Forbidden`: Invalid API key.

---

## 🔐 API Key Handling

Each request must include a header:

```
X-API-KEY: your_api_key_here
```

---

## ⚙️ Background Processing (`process_pdf`)

1. Downloads PDF from `s3://unannotated/{user_id}/{file_id}.pdf`
2. Uses `utils.get_pdf_bounds` to identify steel structures
3. Annotates PDF using `utils.draw_bounds`
4. Uploads results to `s3://annotated/{user_id}/{file_id}.pdf`
5. Also uploads a CSV report (currently `sample.csv`)

---

## 📦 `utils.py` Functionality

### ➕ Geometry Functions  <!-- {docsify-ignore} -->
- `dot(v, w)`: Dot product
- `norm(v)`: Vector magnitude
- `orientation(p1, p2, p3)`: Point orientation (collinear, clockwise, counterclockwise)
- `distance_point_to_segment(P, A, B)`: Shortest distance between point and line segment
- `segment_intersection(...)`: Check for intersection
- `segment_continuous(...)`: Collinearity check
- `segment_distance(...)`: Closest distance between line segments
- `segment_distance_wrapper(...)`: Wrapper with bias for collinear segments

### 📄 PDF Page Parsing  <!-- {docsify-ignore} -->
- `find_pages_to_annotate(doc)`: Find relevant pages using text patterns and area threshold
- `find_steel_on_page(page)`: Extract steel designation strings using regex
- `polygon_contains_point(hull, x, y)`: Check if point lies within polygon

### 🧠 Clustering  <!-- {docsify-ignore} -->
- `find_neighbors_rtree(...)`: Use R-tree for spatial neighbor lookup
- `custom_dbscan(...)`: Custom DBSCAN clustering using distance metric and R-tree

### 📐 Convex Hulls  <!-- {docsify-ignore} -->
- `padded_hull(points, padding)`: Computes and expands a convex hull from points

### 📍 High-level PDF Processing  <!-- {docsify-ignore} -->
- `get_pdf_bounds(...)`: Main function to get bounding boxes for all relevant pages
- `get_page_bounds(...)`: Process one page for annotation
- `draw_bounds(...)`: Visually annotate and color steel regions in the PDF

---

## 🧪 Testing

- All unit tests are defined in `tests.py`
- Run tests using:
  ```bash
  python -m unittest discover
  ```
- Generate a coverage report:
  ```bash
  coverage run -m unittest discover
  coverage report -m
  ```

---

## 🛠️ Development Utilities

- **`main.py`**: Executes the full PDF analysis pipeline on local/dev machines, with profiling via `sentry_sdk`.
- **`vectorize_page.py`**: Debug tool to visualize parsed PDF page elements and steel detection clusters.

---

## 📂 Environment Variables

- `API_KEY`: Required for all requests for authentication

---


---

## 📦 Getting Started

### 1. Set Up the Virtual Environment  <!-- {docsify-ignore} -->

```bash
python -m venv venv

# Activate environment
# On Linux/macOS:
source venv/bin/activate

# On Windows:
venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

### 2. Run Tests & Coverage  <!-- {docsify-ignore} -->

```bash
# Run all tests
coverage run -m unittest discover

# See coverage summary in terminal
coverage report

# Or generate a detailed HTML report
coverage html
```

### 3. Run the Flask API Server  <!-- {docsify-ignore} -->

```bash
# Set environment variable
export API_KEY=[VALUE]

# Start the server
python application.py
```

### 4. Send a PDF Processing Request  <!-- {docsify-ignore} -->

```bash
curl --request POST \
  --url http://localhost:5000/api/v1/pdf-proccessing/request \
  --header 'Content-Type: application/json' \
  --header 'X-API-KEY: [API_KEY]' \
  --data '{
    "file_id":"[FILE_ID]",
    "user_id":"[USER_ID]",
    "bucket_name": "[BUCKET_NAME]"
}'
```


## 👷 Deployment Notes

Only the following files are deployed to production:

- `application.py`
- `utils.py`
- `sample.csv`
- `requirements.txt`

All other files are used for development, testing, or debugging purposes.


## </> `utils.py` Code Documentation

### dot  <!-- {docsify-ignore} -->

```python
def dot(v: tuple[float, float], w: tuple[float, float]) -> float
```

Compute the dot product of two 2D vectors.

**Arguments**:

- `v` _tuple[float, float]_ - First 2D vector.
- `w` _tuple[float, float]_ - Second 2D vector.
  

**Returns**:

- `float` - The dot product of vectors v and w.


### norm  <!-- {docsify-ignore} -->

```python
def norm(v: tuple[float, float]) -> float
```

Compute the Euclidean norm (magnitude) of a 2D vector.

**Arguments**:

- `v` _tuple[float, float]_ - A 2D vector.
  

**Returns**:

- `float` - The Euclidean norm of the vector.


### orientation  <!-- {docsify-ignore} -->

```python
def orientation(p1: tuple[float, float], p2: tuple[float, float],
                p3: tuple[float, float]) -> int
```

Determine the orientation of an ordered triplet (p1, p2, p3).

**Arguments**:

- `p1` _tuple[float, float]_ - First point.
- `p2` _tuple[float, float]_ - Second point.
- `p3` _tuple[float, float]_ - Third point.
  

**Returns**:

- `int` - Orientation code:
  - 0 if collinear
  - 1 if clockwise
  - 2 if counterclockwise


### distance\_point\_to\_segment  <!-- {docsify-ignore} -->

```python
def distance_point_to_segment(P: tuple[float, float], A: tuple[float, float],
                              B: tuple[float, float]) -> float
```

Compute the shortest distance between a point and a line segment.

**Arguments**:

- `P` _tuple[float, float]_ - The point.
- `A` _tuple[float, float]_ - One endpoint of the segment.
- `B` _tuple[float, float]_ - The other endpoint of the segment.
  

**Returns**:

- `float` - The shortest distance from point P to the line segment AB.


### segment\_intersection  <!-- {docsify-ignore} -->

```python
def segment_intersection(A1: tuple[float, float], A2: tuple[float, float],
                         B1: tuple[float, float], B2: tuple[float,
                                                            float]) -> bool
```

Determine whether two line segments intersect.

**Arguments**:

- `A1` _tuple[float, float]_ - Start point of first segment.
- `A2` _tuple[float, float]_ - End point of first segment.
- `B1` _tuple[float, float]_ - Start point of second segment.
- `B2` _tuple[float, float]_ - End point of second segment.
  

**Returns**:

- `bool` - True if the segments intersect, False otherwise.


### segment\_continuous  <!-- {docsify-ignore} -->

```python
def segment_continuous(A1: tuple[float, float], A2: tuple[float, float],
                       B1: tuple[float, float], B2: tuple[float,
                                                          float]) -> bool
```

Check if two line segments are collinear (i.e., lie on the same line).

**Arguments**:

- `A1` _tuple[float, float]_ - Start point of first segment.
- `A2` _tuple[float, float]_ - End point of first segment.
- `B1` _tuple[float, float]_ - Start point of second segment.
- `B2` _tuple[float, float]_ - End point of second segment.
  

**Returns**:

- `bool` - True if segments are collinear, False otherwise.


### segment\_distance  <!-- {docsify-ignore} -->

```python
def segment_distance(A1: tuple[float, float], A2: tuple[float, float],
                     B1: tuple[float, float], B2: tuple[float,
                                                        float]) -> float
```

Compute the shortest distance between two line segments.

**Arguments**:

- `A1` _tuple[float, float]_ - Start point of first segment.
- `A2` _tuple[float, float]_ - End point of first segment.
- `B1` _tuple[float, float]_ - Start point of second segment.
- `B2` _tuple[float, float]_ - End point of second segment.
  

**Returns**:

- `float` - The minimum distance between the two segments.


### segment\_distance\_wrapper  <!-- {docsify-ignore} -->

```python
def segment_distance_wrapper(X: list[float], Y: list[float]) -> float
```

Wrapper around `segment_distance` that adjusts distance if segments are collinear.

**Arguments**:

- `X` _list[float]_ - First line segment represented as [x1, y1, x2, y2].
- `Y` _list[float]_ - Second line segment represented as [x1, y1, x2, y2].
  

**Returns**:

- `float` - Adjusted distance between segments X and Y.


### find\_pages\_to\_annotate  <!-- {docsify-ignore} -->

```python
def find_pages_to_annotate(doc: any) -> list[int]
```

Identify which pages of a PDF should be annotated based on text content and patterns.

**Arguments**:

- `doc` - A PyMuPDF document object.
  

**Returns**:

- `list[int]` - Indices of pages that meet annotation criteria.


### polygon\_contains\_point  <!-- {docsify-ignore} -->

```python
def polygon_contains_point(hull: list[tuple[float, float]], x: float,
                           y: float) -> bool
```

Determine if a point is inside a polygon

**Arguments**:

- `hull` _list[tuple[float, float]]_ - List of polygon vertices.
- `x` _float_ - X-coordinate of the point.
- `y` _float_ - Y-coordinate of the point.
  

**Returns**:

- `bool` - True if the point is inside the polygon, False otherwise.

<a id="utils.find_steel_on_page"></a>

### find\_steel\_on\_page  <!-- {docsify-ignore} -->

```python
def find_steel_on_page(page: any) -> list
```

Search for steel designation text patterns on a page and return matching text spans.

**Arguments**:

- `page` - A PyMuPDF page object.
  

**Returns**:

- `list` - List of tuples containing matched text and their bounding quadrilaterals.


### find\_neighbors\_rtree  <!-- {docsify-ignore} -->

```python
def find_neighbors_rtree(index: int, epsilon: float, r_tree,
                         segments: list[list[float]]) -> list[int]
```

Find nearby line segments to a given segment using an R-tree and bounding box expansion.

**Arguments**:

- `index` _int_ - Index of the target segment.
- `epsilon` _float_ - Expansion margin for the bounding box.
- `r_tree` - An R-tree spatial index.
- `segments` _list[list[float]]_ - List of segments defined by endpoints.
  

**Returns**:

- `list[int]` - Indices of segments that lie within the expanded bounding box.


### padded\_hull  <!-- {docsify-ignore} -->

```python
def padded_hull(points: list[list[float]],
                padding: float) -> list[list[float]]
```

Compute a convex hull around a set of points and apply padding to expand it.

**Arguments**:

- `points` _list[list[float]]_ - List of 2D points [[x, y], ...].
- `padding` _float_ - Padding multiplier to enlarge the hull.
  

**Returns**:

- `list[list[float]]` - List of padded hull points.


### custom\_dbscan  <!-- {docsify-ignore} -->

```python
def custom_dbscan(segments: list[list[float]], r_tree, eps: float,
                  min_samples: int) -> list[int]
```

Custom DBSCAN clustering algorithm for line segments using spatial proximity.

**Arguments**:

- `segments` _list[list[float]]_ - List of line segments as [x1, y1, x2, y2].
- `r_tree` - R-tree spatial index for segment lookup.
- `eps` _float_ - Distance threshold for clustering.
- `min_samples` _int_ - Minimum number of neighboring segments to form a cluster.
  

**Returns**:

- `list[int]` - Cluster labels for each segment (−1 indicates noise).


### get\_pdf\_bounds  <!-- {docsify-ignore} -->

```python
def get_pdf_bounds(file_stream, eps, min_samples, padding)
```

Process a PDF file and return bounding regions on pages containing steel beams.

Steps:
- Open the PDF document from the stream
- Identify pages to annotate using keywords and patterns
- For each selected page, compute bounding boxes using clustering (See get_page_bounds)
- Return results in a dictionary format

**Arguments**:

- `file_stream` _bytes_ - The binary stream of the PDF file.
- `eps` _float_ - Distance threshold for DBSCAN clustering.
- `min_samples` _int_ - Minimum number of segments to form a root node in DBSCAN.
- `padding` _float_ - Scale factor to expand the convex hull around detected clusters.
  

**Returns**:

- `dict` - A dictionary with a "predictions" key containing bounding boxes and metadata.


### get\_page\_bounds  <!-- {docsify-ignore} -->

```python
def get_page_bounds(file_stream, page_index, eps, min_samples, padding)
```

For a specific page in a PDF:
- Identify steel text using regex patterns
- Extract line segments and build R-tree for fast spatial search
- Cluster line segments using custom DBSCAN based on proximity
- Filter relevant clusters and compute a convex hull with padding
- Match hulls to steel text and return the bounding data

**Arguments**:

- `file_stream` _bytes_ - The binary stream of the PDF file.
- `page_index` _int_ - Page number to process.
- `eps` _float_ - Distance threshold for clustering.
- `min_samples` _int_ - Minimum points required to form a root node in DBSCAN.
- `padding` _float_ - Padding factor for the convex hull.
  

**Returns**:

- `list` - A list of dictionaries representing detected regions on the page.


### draw\_bounds  <!-- {docsify-ignore} -->

```python
def draw_bounds(file_stream, predictions)
```

Draws annotations on the PDF

Steps:
- Draws a red polygon for each bounding region (convex hull)
- Highlights steel segments within those regions using green lines
- Returns the modified PDF as bytes

**Arguments**:

- `file_stream` _bytes_ - The original PDF file as a byte stream.
- `predictions` _dict_ - Output from `get_pdf_bounds()` containing detection metadata.
  

**Returns**:

- `bytes` - The modified PDF as a byte stream with annotations.

---

## 👷 Author
Hard Hat Raccoon Dev Team 🦝
