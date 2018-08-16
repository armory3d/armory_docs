# Supported Particles

Particle systems are currently in experimental stage and will be further improved.

## Setup

- Armory defaults to GPU particle simulation
- Accessing `Particle Info` material node requires GPU simulation
- To use CPU simulation, set `Properties - Armory Render Path - Particles` to `CPU`
- The rendering is always performed using GPU instancing

## Features

- Type (Emitter, Hair)
- Seed
- Emission - Number
- Emission - Start
- Emission - End
- Emission - Lifetime
- Emission - Random
- Emission - Emit From (Verts, Volume)
- Velocity - Emitter Object
- Velocity - Random
- Physics (No, Newtonian)
- Physics - Newtonian - Size
- Physics - Newtonian - Mass
- Render (Object)
- Render - Dupli Object
- Render - Size
- Field Weights - Gravity
- Particle Info material node - GPU particles
