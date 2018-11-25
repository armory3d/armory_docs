# Vehicle Setup

This docs is based on [Panda3D Bullet Vehicle Doc](https://www.panda3d.org/manual/index.php/Bullet_Vehicles) with additional topics to cover some of common faced problems

This article discussed the out of box Bullet Physics implementation of vehicle, which is based on raycast vehicle. The benefit of this type of vehicle is it is easier to implement vs constraint type vehicle.

This approach is used in some of arcade games. 

Following articles go over the high level of the vehicle template implementation and provide some optional suggestions (as these suggestions are not generics across every type of implementations)

The initial vehicle template setup can be found in vehicle in [Armory3D Templates](https://github.com/armory3d/armory_templates)

In `vehicle` object, there is a script tight to it

### Setup Vehicle

Following codes did following
Get all the wheels object in the scene according to their names and pushes into an array
```
for (n in wheelNames) {
    wheels.push(iron.Scene.active.root.getChild(n));
}
```
Setup vehicle body by using the mesh under `vehicle` object as compound to set it up

```
var wheelDirectionCS0 = BtVector3.create(0, 0, -1);
var wheelAxleCS = BtVector3.create(1, 0, 0);

var chassisShape = BtBoxShape.create(BtVector3.create(transform.dim.x / 2, transform.dim.y / 2, transform.dim.z / 2));

var compound = BtCompoundShape.create();

var localTrans = BtTransform.create();
localTrans.setIdentity();
// set to much lower value
// https://pybullet.org/Bullet/phpBB3/viewtopic.php?t=12112
localTrans.setOrigin(BtVector3.create(0, 0, 1));

compound.addChildShape(localTrans, chassisShape);

carChassis = createRigidBody(chassis_mass, compound);
```

Create the vehicle physics object out, attach the vehicle body and wheels together base on their current info

*Note: It is important to note that, while the vehicle demo use parent/child relationship, once they are part of physics world, they are no longer parent/child relation (unless doing through physics constraint). For example, wheels may fall off from their original parent/child positions to the `vehicle` object base on physics interaction.*

```
// Create vehicle
var tuning = BtVehicleTuning.create();
var vehicleRayCaster = BtDefaultVehicleRaycaster.create(physics.world);
vehicle = BtRaycastVehicle.create(tuning, carChassis, vehicleRayCaster);

// Never deactivate the vehicle
carChassis.setActivationState(BtCollisionObject.DISABLE_DEACTIVATION);

// Choose coordinate system
var rightIndex = 0;
var upIndex = 2;
var forwardIndex = 1;
vehicle.setCoordinateSystem(rightIndex, upIndex, forwardIndex);

// Add wheels
for (i in 0...wheels.length) {
	var vehicleWheel = new VehicleWheel(i, wheels[i].transform, object.transform);

	vehicleWheel.isFrontWheel = true;
	if (i >= wheels.length - 2) {
	    vehicleWheel.isFrontWheel = false;
	}

	vehicle.addWheel(vehicleWheel.getConnectionPoint(), wheelDirectionCS0, wheelAxleCS, suspensionRestLength, vehicleWheel.wheelRadius, tuning,
           vehicleWheel.isFrontWheel);
}

// Setup wheels
for (i in 0...vehicle.getNumWheels()) {
    var wheel:BtWheelInfo = vehicle.getWheelInfo(i);
    wheel.m_suspensionStiffness = suspensionStiffness;
    wheel.m_wheelsDampingRelaxation = suspensionDamping;
    wheel.m_wheelsDampingCompression = suspensionCompression;
    wheel.m_frictionSlip = wheelFriction;
    if (i >= wheels.length - 2) {
        wheel.m_frictionSlip = wheelFriction * 1.2;
    }
    wheel.m_rollInfluence = rollInfluence;
}
		
physics.world.addAction(vehicle);
```

#### Prevent Vehicle Flip Over

*Note: This is an optional suggestion*

Depend on the game type, there maybe situations where one do not wish the vehicle to flip over even during high speed during steering. 

Out of box vehicle implementation is toward more realistic behavior where the steering at higher speed (or hard angle/lighter vehicle body etc...) is like to flip over

There are multiple approaches to prevent it, following is one possible approach inspired by [Bullet Forum Discussion](https://pybullet.org/Bullet/phpBB3/viewtopic.php?t=8153)

Before adding the `vehicle` to physics world, added following to the `carChassis`
```		
// https://pybullet.org/Bullet/phpBB3/viewtopic.php?t=8153
// prevent vehicle from flip over, by limit the rotation  on forward axis
carChassis.setAngularFactor(new BtVector3(0,0,1));
		
physics.world.addAction(vehicle);
```

Above angular factor limit the rotation on x and y axis, so the vehicle will not able to rotate, as the chassis object will balance out the flip force

This may make the vehicle less realistic as it will always be stable even during sharp corner turns at extreme high speed

### Accelerate

To accelerate, applies the engine force (can also think kind of like torque) wheel (i)
The index is based on the order that the wheel is added to the vehicle
```
 vehicle.applyEngineForce(engineForce, i);
```

Negative engine speed will eventually cause the vehicle to reverse, it can also used to decelerate the vehicle.

##### Find Current Vehicle Speed

*Note: This is an optional suggestion*

There may be situation needed to find the current vehicle speed, one can get through following
```
var speed = Math.round(vehicle.getCurrentSpeedKmHour());
```
which is the easier out of box way to get the speed in km per hour

Following is another way, which should get very similar value to above by using the wheel rotation delta to get the speed the vehicle is moving
```
var speed = Math.round(((backendWheelInfo.m_deltaRotation / Time.step) * backendWheelInfo.m_wheelsRadius * 3.6));
```

##### Limit Top Speed

*Note: This is an optional suggestion*

If keep adding force to wheel, the speed of vehicle will keep increasing, which may not be ideal in some of cases, as in theory, there is a bottleneck to a vehicle's speed.

In this case, one can do following
```
var speed = Math.round(vehicle.getCurrentSpeedKmHour());
if (speed < MAX_SPEED)
{
    engineForce = maxAcceleration * chassis_mass * accel;
}
else 
{
    engineForce = 0;
}
```

Above calculates out the current speed of vehicle and then no longer allow more engine force to throttle the speed.
This method may not 100% prevent the vehicle at the `MAX_SPEED`, but it should limit the speed around that area

### Brake

To accelerate, applies the break force (can also think kind of like torque) wheel (i)
The index is based on the order that the wheel is added to the vehicle
```
vehicle.setBrake(breakingForce, i);
```

Negative Engine Force (-1 * engineForce) can also use to decelerate vehicle. But the behavior of brake/negative engine force may suit different situations. 

Please feel free to experiment and find best suitable approach.

Brake will cause the vehicle to stop at 0 eventually, while negative engine force will start to reverse.

### Steering

Steer value is between 0 to 1 and apply to the wheel responding to wheel (i)
The index is based on the order that the wheel is added to the vehicle
vehicle.setSteeringValue(vehicleSteering, i);

```
vehicle.setSteeringValue(vehicleSteering, i);
```

#### Front and Back Wheel

*This is an optional suggestion*
The template used direct numbering to map the wheel, but if the goal is front wheel will be the only one rotated, one way is to use the `m_bIsFrontWheel` variable
```
if (wheelInfo.m_bIsFrontWheel)
{
    // apply front wheel logic
    vehicle.setSteeringValue(vehicleSteering, i);
}
else
{
    // apply backend wheel logic
	vehicle.applyEngineForce(engineForce, i);
	vehicle.setBrake(breakingForce, i);
}
```

### Update Graphics with Physics Simulation

Above Acceleration/Steering change the physics world vehicle location
But need to apply this feedback to the graphics

Following loop through all wheels, apply necessary steer/accelerate, and use the physics location/rotation to update graphics location/rotation

```
for (i in 0...vehicle.getNumWheels()) {
   // update accelration/brake/steering
...

    vehicle.updateWheelTransform(i, true);
            			
    var trans = vehicle.getWheelTransformWS(i);
    var p = trans.getOrigin();
    var q = trans.getRotation();
    wheels[i].transform.localOnly = true;
    wheels[i].transform.loc.set(p.x(), p.y(), p.z());
    wheels[i].transform.rot.set(q.x(), q.y(), q.z(), q.w());
    wheels[i].transform.dirty = true;
...
}
```

Also applies to chassis and camera

```
var trans = carChassis.getWorldTransform();
var p = trans.getOrigin();
var q = trans.getRotation();
transform.loc.set(p.x(), p.y(), p.z());
transform.rot.set(q.x(), q.y(), q.z(), q.w());
var up = transform.world.up();
transform.loc.add(up);
transform.dirty = true;

// TODO: fix parent matrix update
if (camera.parent != null)
    camera.parent.transform.buildMatrix();
camera.buildMatrix();
```

#### Vehicle Wheels/Chassis Are Off During High Speed
*This is an optional suggestion*

Out of box vehicle template, if one moves the vehicle at very high speed, one may notice wheels are rotating slower than chassis (at least graphically).

While it may works for some game, but may not work for other games.

The reason that the behavior occurs is because physic wheel physic calculation logic seem happen on another thread, so there is some delay between the actual wheel rotation/location responds vs chassis physic calculation.

To force the wheels, one logic need to be changed above

On updateWheelTransform, updated to false for the wheel(i)

```
// Synchronize the wheels with the chassis worldtransform
// update the second parameters to false to let the wheel stay at chasis
 vehicle.updateWheelTransform(i, false);
```

There is also more elegant call back implementation approach, but as of this written, HaxeBullet does not support custom call back method for vehicle wheel yet.


That's it - feel free to experiment further! Get the full blend for this tutorial:

- https://github.com/armory3d/armory_templates

