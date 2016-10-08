 HexMachina
==============
A short and sweet python implementation of the SRF approach to hexahedral meshing.

Algorithm
-----------
*Inputs* : Triangle mesh as .stl (binary)

> Given an input triangle mesh, a **tetrahedral mesh** is generated (using TetGen) and its boundary surface is extracted. The vertex-based **curvatures and normals** of the boundary surface are computed, as well as other topological information. A 3D frame is initialized at the centroid of each tetrahedron. The **frame field** smoothness is optimized by maximizing a non-linear energy function, solved using the efficient L-BFGS method. Moreover, some case-by-case **adjustments** are made to ensure the field is singularity-restricted. After the optimization, the frame field is linearly interpolated to **parametrize** the volume as a piece-wise isosurface, solved using a CG (Conjuate Gradient) method. The hexahedral vertices are extracted as integer **isosurface intersections**.

*Outputs*: Saved to disk as .vtk files, which can be viewed in Paraview. This includes tetrahedral mesh, curvature cross-field, optimized 3D frame field and the hexahedral mesh.

State of the Art
-----------
A non-exhaustive list of papers that inspired this implementation.

#### Volume parametrization
 - [**All-Hex Meshing using Singularity-Restricted Field**](http://i.cs.hku.hk/~wenping/allhex.pdf)
 - [CubeCover - Parameterization of 3D Volumes](http://www.mi.fu-berlin.de/en/math/groups/ag-geom/publications/db/2011_Nieser-Reitebuch-Polthier_CubeCover.pdf)
 - [Boundary Aligned Smooth 3D Cross-Frame Field](http://www.cad.zju.edu.cn/home/hj/11/3D-cross-frame.pdf)

#### Boundary parametrization
 - [General Planar Quadrilateral Mesh Design Using Conjugate Direction Field](http://research.microsoft.com/en-us/UM/people/yangliu/publication/CDF.pdf)
 - [QuadCover - Surface Parameterization using Branched Coverings](http://www.mi.fu-berlin.de/en/math/groups/ag-geom/publications/db/KNP07-QuadCover.pdf)
 - [Estimating Curvatures and Their Derivatives on Triangle Meshes](http://gfx.cs.princeton.edu/pubs/_2004_ECA/curvpaper.pdf)
 - [Trivial Connections on Discrete Surfaces](http://www.multires.caltech.edu/pubs/Connections.pdf)


To-Do
-----
1. Back-propagation to compute gradients in L-BFGS, improve runtime.
2. Field-based volume parametrization (mixed-integer linear CG) problem, currently broken.

Dependencies
-------------
Python 3, and set up other dependencies with:

    pip install requirements.txt
