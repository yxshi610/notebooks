## 1. Introduction

    computer graphics: any use of computers to create and manipulate images  
    
    1.1. Graphics Areas:  
        1. modeling: mathematical specification of shape and appearance properties in a way that can be stored on the computer  
        2. rendering: the creation of shaded images from 3D computer models  
        3. animation: create an illusion of motion through sequences of images  
    
    1.4. Graphics Pipeline  
        - a special software/hardware subsystem that efficiently draws 3D primitives in perspective.  
        - Usually these systems are optimized for processing 3D triangles with shared vertices.  
        - map the 3D vertex locations to 2D screen positions and shade the triangles  
        - drawing triangles back-to-front: z-buffer, use a special memory buffer to solve the problem in a brute-force manner.  
        - 4D coordinates: 3D plus a fourth homogeneous one  
        - speed: triangles number, suggest to represent model with a varying level of detail. (LOD)
    
    1.5. Numerical Issues  
        1. Infinity (∞). Minus infinity (−∞). Notanumber(NaN): e.g. arise from 0 divided by 0.  
        2. +a/(+∞) = +0, −a/(+∞) = −0, +a/(−∞) = −0, −a/(−∞) = +0.  
        3. ∞ + ∞ = +∞, ∞−∞ = NaN, ∞ × ∞ = ∞, ∞/∞ = NaN, ∞/a = ∞, ∞/0 = ∞, 0/0 = NaN. (for positive a).
        4.  expressions that have NaN values: i. Any arithmetic expression that includes NaN results in NaN. ii. Any Boolean expression involving NaN isfalse.
        5.  +a/ +0 = +∞, −a/ +0 = −∞.
    
    1.6. Efficiency
        1. pay more attention to memory access patterns than to operation counts.

    computer graphics: any use of computers to create and manipulate images  
    
    1.1. Graphics Areas:  
        1. modeling: mathematical specification of shape and appearance properties in a way that can be stored on the computer  
        2. rendering: the creation of shaded images from 3D computer models  
        3. animation: create an illusion of motion through sequences of images  
    
    1.4. Graphics Pipeline  
        - a special software/hardware subsystem that efficiently draws 3D primitives in perspective.  
        - Usually these systems are optimized for processing 3D triangles with shared vertices.  
        - map the 3D vertex locations to 2D screen positions and shade the triangles  
        - drawing triangles back-to-front: z-buffer, use a special memory buffer to solve the problem in a brute-force manner.  
        - 4D coordinates: 3D plus a fourth homogeneous one  
        - speed: triangles number, suggest to represent model with a varying level of detail. (LOD)
    
    1.5. Numerical Issues  
        1. Infinity (∞). Minus infinity (−∞). Notanumber(NaN): e.g. arise from 0 divided by 0.  
        2. +a/(+∞) = +0, −a/(+∞) = −0, +a/(−∞) = −0, −a/(−∞) = +0.  
        3. ∞ + ∞ = +∞, ∞−∞ = NaN, ∞ × ∞ = ∞, ∞/∞ = NaN, ∞/a = ∞, ∞/0 = ∞, 0/0 = NaN. (for positive a).
        4.  expressions that have NaN values: i. Any arithmetic expression that includes NaN results in NaN. ii. Any Boolean expression involving NaN isfalse.
        5.  +a/ +0 = +∞, −a/ +0 = −∞.
    
    1.6. Efficiency
        1. pay more attention to memory access patterns than to operation counts.

## 2. Miscellaneous Math

    2.1. Sets and Mappings
        1. Mappings, also called functions, are basic to mathematics and programming.
        2. a ∈ S, can be read “a is a member of set S.”
        3. S^2—the set of 3D points (points in R^3) on the unit sphere. it can be thought of as a 2D set.
        4. Notation for mappings uses the arrow and a colon, for example: f :R|→Z, which you can read as “There is a function called f that takes a real number as input and maps it to an integer.” Here, the set that comes before the arrow is called the **domain** of the function, and the set on the right-hand side is called the **target**.
        5. In program world: integer f (real) ← equivalent → f : R |→ Z. The point f (a) is called the image of a, and the image of a set A (a subset of the domain) is the subset of the target that contains the images of all points in A. The image of the whole **domain** is called the **range** of the function.
        6. Inverse Mappings. bijections
        7. an open interval. The corresponding closed interval: square brackets. 
        8. Logarithms: every logarithm has a base a. The “log base a” of x is written log_a x and is defined as “the exponent to which a must be raised to get x,” lnx ≡ loge x. “≡” symbol can be read “is equivalent by definition.” 
    
    2.2. Solving Quadratic Equations
        1. D ≡ B^2 − 4AC, which is called the discriminant of the quadratic equation. If D = 0, there is one real solution (a “double” root)
    
    
    2.3. Trigonometry
        1. Each of these angles is the length of the arc of the unit circle that is “cut” by the two directions. The unit of these arc lengths is *radians*. degrees = 180/pai radians;
        2. sin-csc, cos-sec, tan-cot
        3. asin : [−1, 1] 􏰁→ [−π/2, π/2]; acos : [−1, 1] 􏰁→ [0, π]; atan : R 􏰁→ [−π/2, π/2]; atan2 : R2 􏰁→ [−π, π].
        4. The area of a triangle can also be computed in terms of these side lengths
    
    2.4. Vectors
        1. By convention we write the coordinates of a either as an ordered pair (x_a , y_a )or a column matrix with square brakets. row matrix with T.
        2. cross: a × b = (yazb − zayb, zaxb − xazb, xayb − yaxb).
        3. There is always a master or “canonical” coordinate system with origin o and orthonormal basis x, y, and z. This coordinate system is usually defined to be aligned to the global model and is thus often called the “global” or “world” coordinate system. This origin and basis vectors are never stored explicitly. All other vectors and locations are stored with coordinates that relate them to the global frame. The coordinate system associated with the plane are explicitly stored in terms of global coordinates
        4. However, if we want to use another coordinate system with origin p and orthonormal basis vectors u, v, and w, then we do store those vectors explicitly. Such a system is called a frame of reference or coordinate frame. The coordinate system associated with a particular object, such as the plane, is usually called a local coordinate system.
        5. For example, if u has coordinates (xu, yu, zu), u = xux + yuy + zuz. A location implicitly includes an offset from the canonical origin: p = o + xpx + ypy + zpz, where (xp, yp, zp) are the coordinates of p.
        6. a = uau + vav + waw
        7. To get the u-v-w coordinates of a vector b stored in the canonical coordinate system, we can use dot products: ub =u·b; vb =v·b; wb =w·b.
        8. Constructing a Basis from a Single Vector
        9. Constructing a Basis from Two Vectors
        10. Squaring Up a Basis
    
    2.5. Curves and Surfaces
        1. a curve is a set of points that can be drawn on a piece of paper without lifting the pen.