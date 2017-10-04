# Supported Particles

Particle systems are currently in experimental stage and will be further improved.

## Setup

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
