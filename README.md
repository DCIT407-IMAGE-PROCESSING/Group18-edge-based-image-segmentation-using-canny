# Edge-Based Image Segmentation Using Canny


## 1. Image Segmentation

Image segmentation is the process of partitioning an image into meaningful regions or objects.  
Edge-based segmentation focuses on detecting object boundaries instead of full regions.

Assumption: Object boundaries correspond to sharp changes in pixel intensity.

---

## 2. Edge-Based Segmentation

Edge-based segmentation identifies regions by detecting edges (discontinuities in intensity).

Edges represent:
- Object borders  
- Shape contours  
- Structural boundaries  

Advantages:
- Preserves shape information  
- Computationally efficient  

Limitations:
- Does not directly produce filled regions  
- Sensitive to noise  
- May produce broken or fragmented edges  

---

## 3. Canny Edge Detector

The Canny method is a multi-stage edge detection algorithm designed to:
- Detect real edges (low false positives)
- Localize edges accurately
- Produce thin (1-pixel wide) edges

It is widely used for edge-based segmentation tasks.

---

## 4. Canny Algorithm Pipeline

### Step 1: Noise Reduction (Gaussian Smoothing)
Smooth the image using a Gaussian filter to reduce noise.

Formula (conceptual):
Is(x, y) = I(x, y) * G(sigma)

Purpose:
- Prevent false edges caused by noise

---

### Step 2: Gradient Computation
Compute intensity gradients using derivative filters (e.g., Sobel):

Gx = dI/dx  
Gy = dI/dy  

Gradient magnitude:
G = sqrt(Gx^2 + Gy^2)

Gradient direction:
theta = arctan(Gy / Gx)

Purpose:
- Detect potential edges

---

### Step 3: Non-Maximum Suppression
- Thin edges to 1-pixel width  
- Keep only local maxima along the gradient direction  

Purpose:
- Improve edge localization

---

### Step 4: Double Thresholding
Classify pixels into:
- Strong edges (high gradient)
- Weak edges (medium gradient)
- Non-edges (low gradient)

Purpose:
- Remove insignificant edges

---

### Step 5: Edge Tracking by Hysteresis
- Keep weak edges only if connected to strong edges  
- Remove isolated weak edges  

Purpose:
- Produce continuous and meaningful edges

---

## 5. Output of Canny

The output is a binary edge map:
- 1 = Edge pixel  
- 0 = Background  

Used for:
- Object boundary detection  
- Shape analysis  
- Contour extraction  
- Preprocessing for segmentation pipelines  

---

## 6. From Edges to Segmentation

Since Canny only detects boundaries, full segmentation requires post-processing:
- Contour detection  
- Morphological operations (closing, filling)  
- Region filling  
- Watershed algorithm  

---

## 7. Key Parameters

| Parameter       | Description                          |
|-----------------|--------------------------------------|
| Gaussian kernel | Controls smoothing (noise reduction) |
| Sigma (σ)       | Blur strength                        |
| Low threshold   | Weak edge threshold                  |
| High threshold  | Strong edge threshold                |

---

## 8. Applications

- Object detection  
- Medical image boundary extraction  
- Lane detection in autonomous driving  
- Shape analysis  
- Preprocessing for region-based segmentation  

---

## 9. Limitations

- Sensitive to noise and illumination changes  
- Produces edges, not filled regions  
- Not suitable for semantic segmentation alone  
- Performance depends heavily on threshold selection  

---

## 10. One-Line Summary

Edge-based image segmentation using Canny detects object boundaries by finding strong intensity changes and refining them into thin, connected edges for further processing.
