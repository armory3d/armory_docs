# Vertex Colors

This page describes how to render vertex colors associated with mesh data.

Start with default cube, enter **Vertex Paint** mode and paint one of the edges with red color.

![](img/vcols/0.jpg)

To include vertex colors in material, create and connect **Attribute** node to **Color** socket. Only single vertex color set per mesh is supported currently.

![](img/vcols/1.jpg)

Alternatively, using the Armory PBR node connect **Attribute** to **Base Color** socket.

![](img/vcols/2.jpg)

Hit **Play in Viewport** to verify results.

![](img/vcols/3.jpg)

If you are having trouble displaying vertex colors in more complex scenes, invalidating mesh cache may help in case Armory failed to register changes. Hit **Properties - Object data - Armory Props - Invalidate Cache**.
