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
