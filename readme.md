# Three.js Journey

## Setup

Download [Node.js](https://nodejs.org/en/download/).
Run this followed commands:

```bash
# Install dependencies (only the first time)
npm install

# Run the local server at localhost:8080
npm run dev

# Build for production in the dist/ directory
npm run build
```

## What is a shader?

### a shader is:

- a program written in glsl
- processed by gpu
- calculates a position for each vertex in a geometry
- colorize each visible fragment of that geometry

pixels are abou what is rendered to the screen - fragments are little bits of geometry which may equate to a group of pixels or no pixels in the resultant render

### we send a lot of data to the shader...

- vertices coords
- mesh transformations
- info about camera
- colors
- textures
- lights
- fog
- etc

the gpu processes all of this data following the shader instructions

### Vertex Shader

positions each vertex of a geometry

- we send shader to gpu with data like the vertices coordinates, mesh transformations, camera information, etc
- gpu follows the shader instructions and positions the vertices in the render
- the same vertex shader will be used for every individual vertex! they have NO access to each other. each vertex has its own individual pipe of data in and out
- some data can be different vertex to vertex - this is called an attribute
- some data are exactly the same vertex to vertex - this is called a uniform
- can send data directly to the fragment shader through 'varying' data

### Fragment Shader

once the vertices are placed by the vertex shader, the gpu knows what pixels of the geometry are visible and can proceed to the fragment shader

- gpu follows instructions in frag shader and colorizes each visible fragment in the render
- can have uniforms but NO attributes
- it can take in 'varying' dats directly from the vertex shader

### Why write our own shaders?

- basic shaders provided by three.js are limited
- can me more performant
- custom post-processing
