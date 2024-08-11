# Curve Regularization and Beautification

**Objective:** Convert raster images (PNG) of line art into a set of connected cubic Bézier curves, focusing on closed curves, symmetry, and curve completion.
## 1. Regularize Curves
Identify regular shapes within given curves, including:

1. **Straight Lines**
2. **Circles and Ellipses**: Detect curves where points are equidistant from a center (circle) or have two focal points (ellipse).
3. **Rectangles and Rounded Rectangles**: Distinguish between standard and curved-edge rectangles.
4. **Regular Polygons**: Identify polygons with equal sides and angles.
5. **Star Shapes**: Recognize star shapes by identifying a central point with multiple radial arms.

**Activity**: Test algorithms on hand-drawn shapes and doodles. Ensure the algorithm can differentiate between regularizable and non-regularizable shapes.

## 2. Exploring Symmetry in Curves
Focus on closed shapes and identify reflection symmetry. 

**Symmetryhunt**: Detect identical curves created by different Bézier curve sequences. Start by identifying symmetry based on point sets, then fit identical Bézier curves to symmetric points.

## 3. Completing Incomplete Curves
Develop algorithms to complete 2D curves with gaps due to occlusion removal.

**Example**: Use computer vision to naturally complete incomplete curves. Input consists of curves with shared boundaries, requiring modification to close gaps.

**Guide**:
- **Fully Contained**: One shape completely inside another.
- **Partially Contained but Connected**: E.g., a half-circle occluded by another shape.
- **Disconnected Curves**: E.g., a circle disconnected by a rectangle.

**Activity**: Explore curve completion based on smoothness, regularity, and symmetry.
**About the code**
# Shape Detection from Contours

This project reads contours from a CSV file, identifies the shapes within those contours, and visualizes them using OpenCV and Matplotlib. The identified shapes are drawn and labeled on an image.

## Requirements

To run this code, you need to have the following libraries installed:

- **OpenCV** (`cv2`)
- **NumPy** (`numpy`)
- **Matplotlib** (`matplotlib`)
- **Imutils** (`imutils`)

You can install these dependencies using pip:

```bash
pip install opencv-python numpy matplotlib imutils
```

## How It Works

### 1. Shape Detection

The `Shape` class is designed to detect shapes from contours. It uses the following methods:

- **`detect(c)`**: Identifies the shape based on the number of vertices of the contour.
  - **Triangle**: 3 vertices
  - **Square/Rectangle**: 4 vertices (based on aspect ratio)
  - **Pentagon**: 5 vertices
  - **Star**: 10 or more vertices with specific angle characteristics
  - **Circle**: More than 5 vertices without star properties

- **`is_star(contour, num_vertices)`**: Determines if a contour with a large number of vertices is a star shape based on the angles between points.

- **`calculate_angles(contour)`**: Computes the angles between each set of three consecutive points in the contour.

- **`angle_between_three_points(pt1, pt2, pt3)`**: Calculates the angle formed by three points using vector mathematics.

### 2. Reading Contours from CSV

The function **`read_csv_(csv_path)`** reads a CSV file containing contour data. It processes this data and converts it into a format suitable for shape detection.

### 3. Plotting and Visualization

- The **`plot(paths_XYs, title, ax)`** function is used to visualize the contours using Matplotlib.
- Detected shapes are drawn on a blank image using OpenCV's **`cv2.drawContours()`**.
- The shape names are labeled on the image at the center of each contour.

### 4. Execution and Output

- The code reads contours from the specified CSV file.
- It detects and labels the shapes.
- The results are visualized in a Matplotlib plot and displayed using OpenCV.

## Steps to Run the Code

1. **Prepare the CSV File**: Ensure you have a CSV file containing contour data. The file should be structured with each row representing a point in the format: `[path_id, contour_id, x, y]`.

2. **Set the CSV Path**: Modify the `csv_path` variable in the script to point to your CSV file.

3. **Run the Script**:
   - If running in a local Python environment, execute the script directly.
   - If using Jupyter Notebook, ensure the `%matplotlib inline` magic command is enabled to visualize the Matplotlib output.

4. **View Results**:
   - The detected shapes will be displayed in a Matplotlib plot.
   - The labeled contours will be shown in a separate OpenCV window.

```python
# Example command to run the script (if saved as a .py file)
python detect_shapes.py
![WhatsApp Image 2024-08-11 at 17 53 52_6d5a82ee](https://github.com/user-attachments/assets/1b73dce5-7a8d-45d1-8cb8-b16bc5f0783b)


