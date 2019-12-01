# static Quadtree

A static (pre-built) Quadtree for efficient proximity/collision detection. The Quadtree is completely built from the top down during initialization so that only simple minimum and maximum querries are made against objects to find which (ready made) quadnodes they intersect and where to continue checking within the tree hierarchy. This static model eliminates both the real-time creation of Quadnode objects and the calculations needed to identify their vertical/horizontal centers. 

contains: 
- Quadtree.java
- AABB.java
- Main.java (windowed simulator for testing - not needed for normal use.)

usage:
- Create array of AABB objects
- Create Quadtree: Quadtree(AABB[] ar, int x, int y, int wdth, int hght, int tree_Dpth, boolean square);
- Call aabb.relocate(dx,dy) and quadtree.update() whenever needed

## example usage:
```java
AABB[] aabbs = new AABB[5];

// make 5 AABBs and add to array with various initial values.
for(int i=1; i<aabbs.length+1; i++){
    aabbs[i-1] = new AABB();
    aabbs[i-1].set_Size(i*20, i*15);
    aabbs[i-1].set_Velocity(i*0.3f, i*0.4f);
    aabbs[i-1].relocate(i*200, i*125);
}

// parameters for Quadtree: AABB array, top left (x,y) position, width, height,
// tree depth, square = false means rectangular Quadtree
int x = y = 0;
int wdth = 1000;
int hght = 600;
int tree_Depth = 5;
boolean square = false;

Quadtree qt = new Quadtree(aabbs, x, y, wdth, hght, tree_Depth, square);

// relocate, resize and change velocities of AABBs as needed and then call qt.update();
```
