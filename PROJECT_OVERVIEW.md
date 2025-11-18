# QBVH Rust Ray Tracer Project Overview

This is a **Monte Carlo Ray Tracer** written in Rust from scratch. It's an impressive implementation that demonstrates advanced computer graphics concepts and optimization techniques.

## 🎯 **Project Features**

- **Multi-threading** for parallel rendering
- **Fast Quad-BVH (Bounding Volume Hierarchy)** with SIMD instructions for acceleration
- **Comprehensive material system**: Lambertian, textured, metal, colored dielectric, isotropic volume (fog/smoke), Blinn-Phong, anisotropic Ashikhmin-Shirley
- **3D Model Support**: `.obj` file loader with triangle mesh rendering
- **HDRI Background** support for realistic lighting
- **Light Sampling** for efficient illumination
- **Bloom Effect** for enhanced visual quality

## 📁 **Project Structure & Folder Functions**

### **Core Source Code (`src/`)**
- **`main.rs`** - Entry point with command-line interface and rendering pipeline
- **`integrator.rs`** - Monte Carlo ray tracing integrator with Russian roulette termination
- **`simd_bvh.rs`** - Quad-BVH acceleration structure using SIMD for fast ray-object intersection
- **`scenes.rs`** - Predefined scene configurations (12 different scenes)
- **`camera.rs`** - Camera model with depth of field and motion blur
- **`ray.rs`** - Ray data structure and operations
- **`object.rs`** - Geometric primitives (spheres, rectangles, triangles)
- **`material.rs`** - Material system with various BRDFs
- **`texture.rs`** - Texture mapping system
- **`triangle_mesh.rs`** - 3D model loading and triangle mesh handling
- **`background.rs`** - HDRI and plain background support
- **`imaging.rs`** - Tone mapping and bloom effects
- **`pdf.rs`** - Probability density functions for importance sampling
- **`utilities/`** - Math utilities, vector operations, and helper functions

### **Assets**
- **`objs/`** - 3D model files (.obj format) including bunny, dragon, skull, teapot, etc.
- **`HDRIs/`** - High Dynamic Range Images for realistic lighting
- **`textures/`** - Texture images (marble, wood, earth map, etc.)
- **`renders/`** - Generated output images

### **Build System**
- **`Cargo.toml`** - Rust project configuration and dependencies
- **`target/`** - Compiled binaries and build artifacts

## 🚀 **How to Run the Project**

### **Prerequisites**
- **Rust** (version 1.89.0 or later)
- **Cargo** package manager

### **Basic Commands**

1. **Build the project:**
```bash
cargo build --release
```

2. **Run with default settings:**
```bash
cargo run --release
```

3. **Run with specific scene:**
```bash
cargo run --release -- --scene basic
```

### **Command Line Options**

The ray tracer supports several command-line arguments:

- **`--scene <NAME>`** - Choose scene (default: "3Dmodel")
  - Available scenes: `basic`, `basic_checker`, `hdri`, `hdri_sun`, `rect_light`, `cornell_box`, `volumes`, `balls`, `3Dmodel`, `david`, `sponza`, `teapots`

- **`--AA <SAMPLES>`** - Anti-aliasing samples per pixel (default: 50)

- **`--resolution <PXS>`** - Resolution (default: 480)
  - Options: `480`, `720`, `1080`

- **`--denoising`** - Enable Intel Open Image Denoising (optional)

### **Example Commands for Your Professor**

1. **Quick demo (low quality, fast):**
```bash
cargo run --release -- --scene basic --AA 10 --resolution 480
```

2. **High quality Cornell Box:**
```bash
cargo run --release -- --scene cornell_box --AA 100 --resolution 720
```

3. **3D Model showcase:**
```bash
cargo run --release -- --scene 3Dmodel --AA 50 --resolution 720
```

4. **HDRI scene with realistic lighting:**
```bash
cargo run --release -- --scene hdri_sun --AA 75 --resolution 1080
```

## 🎨 **Available Scenes**

1. **`basic`** - Random spheres with different materials
2. **`basic_checker`** - Same as basic but with checkerboard ground
3. **`hdri`** - HDRI environment lighting test
4. **`hdri_sun`** - Complex scene with HDRI lighting and 3D models
5. **`rect_light`** - Rectangle light source demonstration
6. **`cornell_box`** - Classic Cornell Box with colored dielectric sphere
7. **`volumes`** - Volume rendering with fog and smoke effects
8. **`balls`** - Material blending demonstration
9. **`3Dmodel`** - Skull and dragon models (default)
10. **`david`** - David statue with Blinn-Phong materials
11. **`sponza`** - Sponza Atrium architectural scene
12. **`teapots`** - Multiple teapots with different materials

## 📊 **Technical Highlights**

- **SIMD Acceleration**: Uses portable SIMD for BVH traversal
- **Monte Carlo Integration**: Implements importance sampling and Russian roulette
- **Multi-threading**: Parallel pixel rendering using Rayon
- **Advanced Materials**: Supports physically-based materials including Fresnel blending
- **HDRI Support**: Real-world lighting from HDR images
- **Progress Tracking**: Real-time rendering progress display

## 🎯 **For Your Professor Demo**

**Recommended command for demonstration:**
```bash
cargo run --release -- --scene 3Dmodel --AA 30 --resolution 720
```

This will:
- Showcase 3D model loading capabilities
- Demonstrate realistic materials and lighting
- Complete in reasonable time (2-5 minutes depending on hardware)
- Generate a high-quality `image.png` output file

## 🔧 **Dependencies**

The project uses the following key dependencies:
- **`show-image`** - Image display and saving
- **`image`** - Image processing
- **`rand`** - Random number generation
- **`indicatif`** - Progress bars
- **`rayon`** - Parallel processing
- **`clap`** - Command-line argument parsing
- **`tobj`** - OBJ file loading

## 📈 **Performance Notes**

- **Release mode** (`--release`) is essential for good performance
- **Anti-aliasing samples** directly affect render time (higher = better quality, longer time)
- **Resolution** significantly impacts render time (1080p takes ~4x longer than 480p)
- **Multi-threading** automatically utilizes all CPU cores

## 🎓 **Educational Value**

This project demonstrates:
- Advanced computer graphics algorithms
- Rust programming best practices
- SIMD optimization techniques
- Monte Carlo methods
- 3D mathematics and linear algebra
- Parallel programming concepts
- File I/O and asset management

The project is an excellent example of a production-quality ray tracer implementation that showcases both theoretical computer graphics knowledge and practical software engineering skills!

