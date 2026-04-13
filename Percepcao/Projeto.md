# Summary of Gradient-Based Techniques for Detecting AI-Generated Images

Researchers have long observed that **real photographs** exhibit statistically consistent patterns due to the physics of image formation — including lens optics, sensor structure, demosaicing, and natural lighting. In contrast, **synthetic or AI-generated images** often deviate subtly from these patterns, especially in their **local pixel gradients**.

### **1. Luminance Extraction**

The technique begins by converting the image from RGB to **luminance**:
$$
L(x,y)=0.2126R+0.7152G+0.0722B
$$
Luminance provides a physically meaningful intensity map that reflects how real sensors capture light.

---

### **2. Gradient Computation**

Gradients describe how luminance changes between neighboring pixels:
$$
G_x(x,y) = \frac{\partial L}{\partial x}, \quad G_y(x,y) = \frac{\partial L}{\partial y}​
$$
Each pixel is therefore represented by a **2D gradient vector**
$$
v(x,y) = \begin{bmatrix} G_x \\ G_y \end{bmatrix}
$$
In real images, these gradients reflect natural edges, textures, and lighting — following predictable physical constraints.

---

### **3. Statistical Analysis of Gradients**

All gradient vectors in the image are flattened into a matrix, and a **covariance matrix** is computed:
$$
C= \frac{1}{N} M^T M
$$
This covariance matrix captures the **overall statistical structure** of the image’s gradient field.

**Real photographs** have characteristic gradient correlations because:

- light projects through lenses
    
- sensors capture intensity smoothly
    
- demosaicing algorithms introduce specific artifacts
    
- textures follow natural image statistics
    

**AI-generated images**, especially from GANs and diffusion models, often show:

- unnatural edge distributions
    
- inconsistent gradient directions
    
- excessive smoothness or sharpness
    
- missing sensor-like noise patterns
    

These differences lead to measurable deviations in gradient covariance.

---

### **4. Classification / Detection**

A detector can either:

- compare the covariance matrix to known distributions of real images, or
    
- use it as a feature for a simple classifier.
    

Even simple statistical distances (e.g., eigenvalues of the covariance matrix) often distinguish real vs. synthetic images.

---

# **Academic Context**

This method is rooted in older fields such as:

- **Natural Image Statistics** (Lyu & Farid, 2005): real images obey stable statistical laws.
    
- **GAN-image forensics** (2018–2023): early detectors used local gradients, texture descriptors, or pixel co-occurrence patterns.
    
- **Gradient-based GAN detection** (Liu et al., 2023): explicitly used color and luminance gradient representations to detect fake images.
    

While the Instagram post simplifies the technique, it corresponds directly to this body of research.
