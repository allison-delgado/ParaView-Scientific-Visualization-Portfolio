Hi, thank you for taking a look at my portfolio! I've added a few of the ParaView projects I've worked on across the years here from my drive.

# ParaView Scientific Visualization Portfolio

This portfolio presents a series of medical and scientific visualization projects created in ParaView. The projects demonstrate my ability to load real scientific datasets, inspect their underlying data arrays, transform scalar and vector fields, design effective visual encodings, create reproducible visualization pipelines, and communicate scientific structure through polished visual outputs.

Across the portfolio, I worked with multiple scientific data formats and visualization workflows, including:

- DICOM thoracic CT data
- NIfTI cardiac MRI and segmentation label data
- VTU unstructured-grid vascular simulation data
- Scalar field visualization
- Vector field visualization
- Volume rendering
- Slice views
- Thresholding and contour extraction
- Segmentation surface extraction
- Quantitative volume measurement
- Streamline generation
- Tube-enhanced vector-field rendering
- Multiview dashboard design
- ParaView state-file reproducibility

The goal of this portfolio is to show not only that I can use ParaView’s interface, but that I can make thoughtful visualization decisions: choosing the right representation for the data, tuning transfer functions, improving readability, extracting quantitative information, and building scientific visualizations that are clear, reproducible, and ready for presentation.

---

## Core ParaView Skills Demonstrated

- Loading and inspecting DICOM, NIfTI, and VTU datasets
- Working with image volumes, segmentation labels, and unstructured-grid simulation data
- Inspecting scalar arrays, vector arrays, point data, cell data, bounds, dimensions, and spacing
- Creating slice, volume, surface, contour, threshold, and streamline visualizations
- Designing custom color and opacity transfer functions
- Mapping scalar fields such as CT intensity, pressure, and velocity magnitude
- Computing derived fields using the Calculator filter
- Converting vector velocity data into scalar velocity magnitude
- Creating Stream Tracer visualizations from velocity vector fields
- Applying Tube filters to improve streamline readability
- Extracting segmentation surfaces from binary label masks
- Measuring segmented anatomical volume using Integrate Variables
- Designing multiview dashboards for comparative scientific visualization
- Managing opacity, color legends, annotations, camera placement, and scene composition
- Saving ParaView .pvsm state files to preserve reproducible workflows

---

# Project 1: Thoracic CT Visualization in ParaView

**ParaView state file:** `project1_lung_ct_visualization.pvsm`

## Goal

This project demonstrates a ParaView workflow for loading, visualizing, transforming, and presenting thoracic CT DICOM data. The project moves from raw medical image inspection to more advanced 3D visualization techniques, including volume rendering and isosurface extraction.

## Dataset

This project uses a chest CT series from the **LIDC-IDRI** collection. The DICOM series was loaded into ParaView as a volumetric image dataset with dimensions:

```text
512 × 512 × 133
```

The scalar field used for visualization was:

```text
DICOMImage
```

## Workflow Overview

I created a complete CT visualization pipeline in ParaView:

1. Loaded the CT DICOM series using ParaView’s DICOM reader
2. Inspected the scalar field, data dimensions, and image volume structure
3. Created a grayscale axial slice view using a CT intensity window appropriate for anatomical inspection
4. Designed custom color and opacity transfer functions for 3D volume rendering
5. Adjusted the transfer function to suppress low-density air/background values while emphasizing denser anatomical structures
6. Applied contour/isovalue extraction to convert high-density CT intensities into a surface representation
7. Applied smoothing to improve the readability of the extracted surface
8. Combined slice and surface views to show both image context and extracted anatomical structure
9. Exported screenshots and a reproducible ParaView state file

## ParaView Techniques Used

- DICOM directory loading
- Medical image volume inspection
- Axial slice visualization
- Scalar color mapping
- CT intensity range adjustment
- Custom color transfer functions
- Custom opacity transfer functions
- 3D volume rendering
- Contour/isovalue extraction
- Surface smoothing
- Multi-representation scene composition
- Camera positioning
- Screenshot export
- ParaView state-file saving

## Scientific Interpretation

The slice view preserves radiological detail and allows inspection of the original CT anatomy. The volume rendering provides 3D spatial context by mapping CT intensity values to opacity. The contour-based isosurface extraction transforms high-intensity CT regions into an interpretable anatomical surface, emphasizing dense structures such as the ribs and spine. The combined slice-and-surface view demonstrates how ParaView can present both raw imaging context and derived 3D structure in the same scene.

---

## Project 1 Outputs

### 01_axial_ct_slice_lung_window.png  
**Axial CT Slice View of Thoracic Anatomy**

A DICOM CT series was loaded into ParaView and inspected using a grayscale axial slice view. This view focuses on preserving anatomical image detail while demonstrating basic medical volume loading and slice inspection.

### 02_chest_ct_volume_rendering.png  
**3D Volume Rendering of Thoracic CT Data**

A custom opacity transfer function was designed to suppress low-density air and background regions while emphasizing denser anatomical structures. This produced a 3D volume rendering that highlights thoracic anatomy using ParaView’s volume-rendering capabilities.

### 03_ct_isosurface_high_density_anatomy.png  
**Isosurface Extraction of High-Density Anatomy**

A contour filter was applied at a CT intensity value of 500 to convert the volumetric scalar field into a surface representation. The extracted surface was lightly smoothed to improve geometric readability of dense anatomical structures such as ribs and spine.

### 04_combined_slice_isosurface_view.png  
**Combined Slice and Isosurface View**

A grayscale CT slice provides anatomical image context, while a high-density isosurface highlights extracted skeletal structures. This view demonstrates multi-representation visualization in ParaView.

---

# Project 2: Cardiac MRI Segmentation and Measurement in ParaView

**ParaView state file:** `project2_cardiac_mri_segmentation.pvsm`

## Goal

This project demonstrates a ParaView workflow for working with paired medical image and segmentation data. I loaded a cardiac MRI volume and its corresponding segmentation label mask, visualized the segmentation in anatomical context, extracted a 3D surface, and computed a quantitative volume measurement.

## Dataset

This project uses cardiac MRI and segmentation data from the **Medical Segmentation Decathlon Heart task**. I worked with a cardiac MRI image volume and a corresponding left atrium segmentation label file.

The files used were:

```text
la_003_image.nii
la_003_label.nii
```

## Workflow Overview

I created a medical segmentation visualization and measurement pipeline:

1. Loaded the raw cardiac MRI NIfTI image into ParaView
2. Loaded the corresponding left atrium segmentation label volume
3. Verified that the image and label volumes aligned spatially
4. Created a grayscale MRI slice view for anatomical context
5. Displayed the segmentation label as a distinct red overlay
6. Adjusted opacity so the segmentation could be interpreted relative to the MRI anatomy
7. Applied thresholding/contouring to isolate the left atrium segmentation
8. Extracted a 3D surface representation of the segmentation
9. Used Integrate Variables to estimate the segmented volume
10. Exported screenshots and a reproducible ParaView state file

## ParaView Techniques Used

- NIfTI medical image loading
- Multi-source image and label handling
- MRI slice visualization
- Segmentation label visualization
- Thresholding of binary label data
- Contour extraction from segmentation masks
- Surface representation
- Solid-color segmentation styling
- Opacity adjustment for overlays
- Integrate Variables for quantitative measurement
- Spreadsheet View inspection
- Camera composition
- Screenshot export
- ParaView state-file saving

## Quantitative Result

Using ParaView’s **Integrate Variables** filter, I estimated the left atrium segmentation volume as:

```text
83.13 cm³
```

## Scientific Interpretation

The MRI slice provides anatomical context, while the segmentation overlay makes it possible to visually validate the label mask against the source image. The extracted 3D surface turns the segmentation into an interpretable anatomical object, and the volume measurement demonstrates ParaView’s ability to support quantitative analysis in addition to visual rendering.

---

## Project 2 Outputs

### 01_cardiac_mri_slice_view.png  
**Cardiac MRI Slice View Loaded in ParaView**

The grayscale MRI image provides anatomical context for validating and interpreting the corresponding left atrium segmentation mask.

### 02_left_atrium_segmentation_overlay.png  
**Left Atrium Segmentation Overlay on Cardiac MRI**

The raw MRI is shown in grayscale, while the segmentation mask is thresholded and displayed as a semi-transparent colored overlay for visual validation against the source anatomy.

### 03_left_atrium_surface_extraction.png  
**3D Surface Extraction of the Left Atrium Segmentation**

A contour filter was applied to the binary label mask at value 0.5, converting the segmentation volume into a 3D surface representation for geometric inspection.

### 04_left_atrium_volume_measurement.png  
**Quantitative Measurement of the Left Atrium Segmentation**

The binary label mask was thresholded and integrated using ParaView’s Integrate Variables filter to estimate the segmented anatomical volume from the image spacing.

---

# Project 3: Vascular Flow Visualization in ParaView

**ParaView state file:** `project3_vascular_flow_visualization.pvsm`

## Goal

This project demonstrates a ParaView workflow for visualizing vascular simulation data. I loaded an unstructured-grid aortic model containing pressure and velocity fields, inspected the available data arrays, mapped pressure onto the vessel surface, computed velocity magnitude from a vector field, and generated streamlines to show simulated flow direction.

## Dataset

This project uses a vascular simulation model from the **Vascular Model Repository**. The dataset was loaded as VTU unstructured-grid data and included simulation arrays such as:

```text
pressure
velocity
```

## Workflow Overview

I built a visualization pipeline that moves from geometry inspection to scalar and vector-field visualization:

1. Loaded a VTU unstructured-grid vascular model into ParaView
2. Inspected the dataset in the Information panel to understand its geometry, bounds, cells, points, and data arrays
3. Created a clean surface rendering of the vascular model
4. Mapped the scalar pressure field onto the vessel surface
5. Used the Calculator filter to compute velocity magnitude from the velocity vector field:

```text
mag(velocity)
```

6. Visualized velocity magnitude as a scalar field
7. Created a semi-transparent vessel surface to preserve anatomical context
8. Generated streamlines from the velocity vector field using Stream Tracer
9. Adjusted seed placement and streamline parameters to produce readable flow paths
10. Applied a Tube filter to thicken streamlines and improve visual clarity
11. Colored streamlines by velocity magnitude to show both flow direction and relative speed
12. Exported screenshots and a reproducible ParaView state file

## ParaView Techniques Used

- VTU / unstructured-grid data loading
- Simulation data inspection
- Point and cell data array interpretation
- Surface rendering of vascular geometry
- Scalar pressure mapping
- Calculator filter usage
- Vector-to-scalar derived field computation
- Velocity magnitude calculation
- Semi-transparent anatomical context rendering
- Stream Tracer filter
- Point-cloud seeding
- Streamline parameter tuning
- Tube filter for streamline readability
- Consistent velocity color mapping
- Camera composition
- Screenshot export
- ParaView state-file saving

## Scientific Interpretation

The pressure map shows scalar variation across the vascular geometry. The velocity magnitude view converts vector data into scalar speed, making it easier to identify spatial variation in flow intensity. The streamline visualization uses the original velocity vector field to trace flow direction through the aortic geometry, while color indicates relative velocity magnitude. Rendering the vessel semi-transparently preserves anatomical context while keeping internal flow paths visible.

---

## Project 3 Outputs

### 01_vascular_geometry_overview.png  
**Vascular Simulation Geometry Loaded in ParaView**

The unstructured-grid vessel model provides anatomical context for pressure and velocity-field visualization.

### 02_pressure_surface_map.png  
**Pressure Field Mapped Onto the Vascular Surface**

The scalar pressure array is visualized across the aortic model, revealing spatial variation in simulated pressure throughout the vessel geometry.

### 03_velocity_magnitude_slice.png  
**Velocity Magnitude Visualization of the Vascular Flow Field**

The vector velocity field was converted into scalar speed using ParaView’s Calculator filter, then visualized with a semi-transparent vessel surface to reveal spatial variation in simulated flow.

### 04_streamlines_velocity_field.png  
**Streamline Visualization of the Vascular Velocity Field**

Velocity magnitude was computed from the velocity vector field using ParaView’s Calculator filter. Streamlines were generated with a seeded Stream Tracer, then thickened with a Tube filter to improve readability. The vessel surface was rendered semi-transparently to preserve anatomical context while allowing the colored flow paths to show how simulated blood flow moves through the aortic geometry.

---

# Project 4: Aortic Hemodynamics Dashboard in ParaView

**ParaView state file:** `project4_aortic_hemodynamics_dashboard.pvsm`

## Goal

This project builds on the vascular flow visualization work by creating a coordinated multiview dashboard in ParaView. Instead of presenting each visualization as an isolated screenshot, I combined multiple representations of the same vascular simulation into a single comparative scientific visualization layout.

This project demonstrates higher-level ParaView skills in layout design, comparative visualization, visual consistency, and reproducible dashboard construction.

## Dashboard Output

### 01_aortic_hemodynamics_dashboard.png  
**Multiview Aortic Hemodynamics Dashboard**

This dashboard compares four coordinated views of the same aortic simulation:

| Panel | Visualization | Purpose |
|---|---|---|
| Pressure Field | Pressure mapped onto the vessel surface | Shows scalar pressure variation across the aorta |
| Velocity Magnitude Slice | Velocity magnitude shown on an internal slice | Reveals spatial variation in flow speed |
| Velocity Streamlines | Tube-enhanced streamlines inside a semi-transparent vessel | Shows flow direction and relative velocity magnitude |
| Geometry Overview | Clean solid-color aortic model | Provides anatomical context |

## Workflow Overview

I created the dashboard by combining multiple ParaView visualization techniques into one coordinated layout:

1. Created a 2 × 2 multiview layout in ParaView
2. Assigned a different visualization task to each render view
3. Built a pressure field panel using scalar pressure mapping
4. Built a velocity magnitude panel using the derived `VelocityMagnitude` field
5. Built a streamline panel using Stream Tracer and Tube filters
6. Rendered the vessel semi-transparently in the streamline panel to preserve context while showing flow paths
7. Built a clean geometry overview panel using a solid-color surface representation
8. Added text labels to identify each panel
9. Used consistent velocity color mapping across the velocity-based panels
10. Adjusted camera positions, opacity, color legends, and layout composition for readability
11. Exported the full dashboard as a single screenshot
12. Saved the full ParaView state file for reproducibility

## ParaView Techniques Used

- Multiview layout creation
- Comparative dashboard design
- Coordinated camera composition
- Scalar pressure mapping
- Derived velocity magnitude visualization
- Slice-based scalar visualization
- Streamline generation
- Tube-enhanced vector-field rendering
- Semi-transparent surface rendering
- Consistent color-scale usage
- Color legend management
- Text annotation
- Full-layout screenshot export
- ParaView state-file reproducibility

## Scientific Interpretation

The dashboard presents complementary views of the same simulation. The pressure panel shows scalar pressure variation across the vessel wall. The velocity magnitude slice reveals internal speed variation. The streamline panel shows the direction of flow through the vascular geometry and uses color to communicate velocity magnitude. The geometry overview provides clean anatomical context for interpreting the simulation views.

This project demonstrates the ability to move beyond individual renderings and design a complete scientific visualization product that supports side-by-side interpretation.

---

# Reproducibility and Repository Structure

Each project includes exported screenshots and a saved ParaView state file where applicable. The `.pvsm` files preserve the visualization pipeline, including filters, color maps, opacity settings, camera views, and layout choices.

---

# Summary

This portfolio demonstrates a broad and practical ParaView skillset across medical imaging, segmentation analysis, quantitative measurement, and vascular simulation visualization.

Together, the projects show that I can:

- Load and inspect real scientific datasets
- Understand and work with multiple data formats
- Transform raw data into derived fields
- Design effective scalar and vector-field visualizations
- Use ParaView filters for analysis and presentation
- Extract surfaces and measurements from diverse datasets
- Build clear, readable, and reproducible visualization pipelines
- Communicate scientific structure through polished visual assets

This portfolio reflects my readiness to contribute to ParaView-focused scientific visualization work involving data loading, transformation, analysis, visualization design, documentation, and reproducible asset creation.
