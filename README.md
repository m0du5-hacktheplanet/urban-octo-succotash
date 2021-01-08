Hack The Planet
=====================================================

### Photon Mapper

This is a photon mapper built without substantial use of graphics libraries.

- Reads and parses complex scene files into a scene including lights, objects, shapes, materials, and fixed and dynamic transformations.
- Distributes the scene to multple processes.
- Throws thousand of photons into the scene from the lights.
- Depending on the result of a photon roullete process, photons can bounce off objects (being adjusted for the BRDF) and possibly land on other objects, or they can be absorbed. (i.e. each time a photon hits a surface, it is stored within the photon map and Russian roulette is used to determine if the photon is reflected, with the power of the reflected photon being computed based on the BRDF of the adjusted surface)
- Gathers the resulting photons' bounce locations (if not absorbed).
- Sorts the photons into a 3-dimensional kd-Tree.
- Distributes the kd-Tree to all processes.
- The first step of a ray tracing process is used: rays are shot from the camera into the scene and, if an object is hit, luminance information for that spot on the object is calculated from the photon map using the nearest N photons and assuming a 2-dimensional surface.

- The Message Passing Interface (MPI) is used for interprocess communication.
- GLUT is used to write rendered file to the screen, though a simple putPixel() from any library would work.
- ImageMagick++ is used to write rendered files to .jpg files.

### Example

*note: If your browser or the markdown viewing engine for this repository viewer does not support the HTML5 video tag, a link to the video will be provided instead. Github has difficulty showing video.

<video controls>
  <source src="https://kingcountybusinesslaw.com/misc/largescene5-n56k-N42-d0.05-D0.2-mpi4.ogv" type="video/ogg">
<a href="https://kingcountybusinesslaw.com/misc/largescene5-n56k-N42-d0.05-D0.2-mpi4.ogv">[Link to Video]</a>
</video> 
