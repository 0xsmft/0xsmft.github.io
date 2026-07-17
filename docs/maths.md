# Maths

Saturn uses [OpenGL Mathematics](https://github.com/g-truc/glm) (GLM or glm) as it's internal maths library.

## Coordinate System

Saturn uses a left handed Cartesian coordinate system where Y+ points up. This means that on a 2D screen the origin is at the bottom left.

Because vulkan uses a right handed Cartesian coordinate system where Y+ points down and the orgin is at the top-left, this results in all of the objects submitted into the [Renderer]() to be upside down. This is by design. As in the editor the image UV are flipped. However, in [Dist]() the image is fipped via the [TexturePass]().

## Depth Buffer Values

Saturn uses non-linear non-revsered depth, this means that an object close by will have a value of 0.xxxxx and objects far away will have ~1.0. Basically ~0 at the near plane and ~1 at the far plane.

## Use of Radians

Saturn internally uses radians for measurement for angles. However, it's recommened that you stay in degrees the whole way and convert your degrees into radians at the end of your calculation.

The Entity inspector in the [SceneHierarchyPanel]() will display the rotational values as degrees.

## Camera Projection Matrix

The default near plane is `0.1f` and the default far plane is `1000.0f`.

The projection matrix is a Perspective FOV built with `glm::perspectiveFovRH_ZO`, which means right-handed coordinate system and depth 0 to 1.

## Alura

Alura uses a standard 2D screen-space coordinate system. Y+ goes down towards the bottom of the screen and X+ moves to the right.

Saturn will still flip the coordinates internally when it gets rendered, this is to avoid the UI being upside upon presentation.
