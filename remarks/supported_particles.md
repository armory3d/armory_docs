# Supported Particles

Particle systems are currently in experimental stage and will be further improved.

## Setup

CPU simulation is effective to emit high-poly meshes, while GPU is effective to simulate hordes of lower poly meshes or accessing `Particle Info`s. The rendering itself is always done using GPU instancing.

To enable GPU particle simulation:
- Check `Properties - Particle System - Armory Props - GPU Simulation`.
- Select referenced *Dupli Object* (object being emitted) and set `Properties - Materials - Armory Props - Particle` to `GPU`.
- This setup will be eventually automated

To enable CPU particle simulation:
- Select referenced *Dupli Object* (object being emitted) and set `Properties - Materials - Armory Props - Particle` to `CPU`.
- This setup will be eventually automated

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
