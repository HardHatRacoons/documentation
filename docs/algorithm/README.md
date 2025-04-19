
# 📄 Hard Hat Raccoon Algorithm Documentation

This project is a Flask-based API for processing and annotating steel structure diagrams in PDF format. It uses AWS S3 for file storage and includes a custom geometric analysis and clustering pipeline.

---

## 📁 Files Overview

### `application.py` ✅ (Production)
Main entry point of the API. Handles incoming HTTP requests, security (API key validation), and asynchronous PDF processing.

### `utils.py` ✅ (Production)
Contains all geometric computations, pattern recognition, clustering, and PDF annotation logic.

### `tests.py` 🧪 (Development)
Contains unit tests written with Python's `unittest` framework. Code coverage is measured using `coverage.py`.

### `main.py` ⚙️ (Development)
Developer tool for running high-level processing logic locally. Uses `sentry_sdk` for profiling and error tracking.

### `vectorize_page.py` 🖼️ (Debugging)
Generates page-level visualizations to help with debugging and fine-tuning the steel structure detection logic.

---

## 🚀 Endpoints

### `GET /`
Basic health check.

### `POST /api/v1/pdf-proccessing/request`
Initiates asynchronous processing of a PDF document uploaded to S3.

#### Request JSON Body
```json
{
  "file_id": "string",
  "user_id": "string",
  "bucket_name": "string"
}
```

#### Response
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

### ➕ Geometry Functions
- `dot(v, w)`: Dot product
- `norm(v)`: Vector magnitude
- `orientation(p1, p2, p3)`: Point orientation (collinear, clockwise, counterclockwise)
- `distance_point_to_segment(P, A, B)`: Shortest distance between point and line segment
- `segment_intersection(...)`: Check for intersection
- `segment_continuous(...)`: Collinearity check
- `segment_distance(...)`: Closest distance between line segments
- `segment_distance_wrapper(...)`: Wrapper with bias for collinear segments

### 📄 PDF Page Parsing
- `find_pages_to_annotate(doc)`: Find relevant pages using text patterns and area threshold
- `find_steel_on_page(page)`: Extract steel designation strings using regex
- `polygon_contains_point(hull, x, y)`: Check if point lies within polygon

### 🧠 Clustering
- `find_neighbors_rtree(...)`: Use R-tree for spatial neighbor lookup
- `custom_dbscan(...)`: Custom DBSCAN clustering using distance metric and R-tree

### 📐 Convex Hulls
- `padded_hull(points, padding)`: Computes and expands a convex hull from points

### 📍 High-level PDF Processing
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

### 1. Set Up the Virtual Environment

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

### 2. Run Tests & Coverage

```bash
# Run all tests
coverage run -m unittest discover

# See coverage summary in terminal
coverage report

# Or generate a detailed HTML report
coverage html
```

### 3. Run the Flask API Server

```bash
# Set environment variable
export API_KEY=[VALUE]

# Start the server
python application.py
```

### 4. Send a PDF Processing Request

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

---

## 👷 Author
Hard Hat Raccoon Dev Team 🦝
