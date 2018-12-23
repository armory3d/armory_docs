# Physics

## Apply Force

This apply force to the object assigned, where "Force", is direction force is applied in term of Vector.

![](/assets/apply-force.JPG)


## Apply Force at Location

This applies force to the object assigned, where "Force", is direction force is applied in term of Vector, and where "Location", is the location of the object where force is applied from in term of Vector.

![](/assets/apply-force-at-location.JPG)


## Apply Impulse

This apply impulse to the object assigned, where "Impulse", is direction force is applied in term of Vector.

![](/assets/apply-impulse.JPG)


## Apply Impulse at Location

This applies force to the object assigned, where "Impulse", is direction force is applied in term of Vector, and where "Location", is the location of the object where force is applied from in term of Vector.

![](/assets/apply-impulse-at-location.JPG)


## Cast Physics Ray

This cast physics ray from vector assigned to "From", to vector assigned to "To". "Hit" give the location of an object(object assigned to "Object") it hit to in term of vector.

![](/assets/cast-physics-ray.JPG)


## Get Contacts

This Get contacts of the object with item in the array.

![](/assets/get-contacts.JPG)


## Get First Contact

This Get contact of the object with another object that is assigned with the connector.

![](/assets/get-first-contact.JPG)


## Get Gravity

This Get gravity of an object in term of vector.

![](/assets/get-gravity.JPG)


## Get Velocity

This Get Linear and Angular velocity of an object in term of vector.

![](/assets/get-velocity.JPG)


## Has Contact

This gives bool value of contact between two objects that are assigned,i.e., If both objects contact each other than this gives True, and if not it gives False.

![](/assets/has-contact.JPG)


## On Contact

Contact between two objects that are assigned to:
1) Overlaps - When this two object completely overlap each other, then the "Out" connector is called.
2) End - When this two objects contact ends, then the "Out" connector is called.
3) Begins - When this two objects first contact, then the "Out" connector is called.

![](/assets/on-contact.JPG)


## Pick Object

When the object that is assigned to is in "Screen Coords" (Screen coord is coordination of screen in (X, Y) in term of vector. Note: "Z" is not used and should be ignored because we don't have 3D screen.) and then "Hit" is called to do something to it.

![](/assets/pick-object.JPG)

## Set Gravity

On activated, this set gravity in term of vector.

![](/assets/set-gravity.JPG)


## Set Velocity

On activated, this set:
1) The linear velocity of the object that is assigned to.
2) Linear Factor velocity of the object that is assigned to.
3) The angular velocity of the object that is assigned to.
4) Angular Factor velocity of the object that is assigned to.
In term of vector.

![](/assets/set-velocity.JPG)