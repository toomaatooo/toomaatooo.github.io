---
title: Game Art Analysis of Toem
date: 2023-03-13 20:24:39
categories:
  - Game
  - Art
tags:
  - Game
  - Design
  - Stylized Visual Effects
---

For the purpose of creating games, I recently played Toem. I'd like to share my thoughts on the distinct art style of Toem. Toem is created by game studio *Something We Made* which aims to take photographs while exploring the world.

![Photo credit: IG](image-20230311162246689.png)

# Analysis of the creation method

## Everything is black and white

The overall is black and white. Looking at other games on their website, I don't like their color style. If Toem was like that, I wouldn't play it.

As a travel photo game, Toem relies heavily on visual effects. The production team uses black and white color matching to avoid the problem of different audiences with different color styles, so as to absorb more aesthetic players. While I'm sure it was easy for the production team to color the map and find the color ratio they liked, there's no denying that the black and white tones reduced the amount of work needed to control the color of the picture. No need to worry about the saturation of the color, and only need to choose between light and dark, so that the picture is clear.

![Other games on the team's website](image-20230313111532689.png)

## Model creation

The models in the game try to show the style of splicing objects, but for the sake of workload, the models should still be built in the modeling software, rather than splicing in Unity.

The surface of the model has an obvious hand-painted style, such as irregular shaking strokes or decorative lines, simple childlike model design. Try to keep the shake of the lines when drawing the map, but completely cancel the shake of the edges of square objects and give sharp edges to blocky objects.

 ![Bus for Forest Chapter](image-20230313140425279.png)

In the image below, it is more obvious that some lines were completely sharp, while others were shaken to maintain their hand-painted feel.

![Slide in Forest chapter](image-20230313140817020.png)

## Non-model object

All non-model objects in the game have orientation recognition and orientation cameras.

`transform.LookAt(targrt);`

Stroke objects will be individually traced in unity using shader to make them smoother. This is even more obvious in the image below, where there is a significant distortion, but the edges remain rounded and smooth, thanks to shader stroke.

![Enlarge on Grandma](image-20230313104800425.png)

# Handling of different requirements

## Plant

### Woody plant

For perfectly symmetrical, tower - shaped trees, use face inserts to render. Try to avoid drawing the texture right in the center of the insert. Two colors of detail are used here to show the hierarchy of the tree.

![Clip Tree 1](image-20230313171717086.png)

![Clip Tree 2](image-20230313171755712.png)

Asymmetrical trees would be modeled, and the game would have chosen the willow tree as a prototype, summed up in a square abstraction. These trees only appear in urban scenes, and they don't appear in separate pieces. Create variety in the tree by varying the number of blocks.

![Block Tree 1](image-20230313173234988.png)

![Block Tree 2](image-20230313173257302.png)

I personally like the black trunk of this tree, which is bouncing and steady.

### Herb

The herbs in the game are of two heights, small crops lying on the ground and plants at the same height as the characters. All herbs use pasta.

![Some kind of wild vegetable](image-20230313174405703.png)

![Imaginary Marshmallow Plant](image-20230313174342407.png)

![Cattails](image-20230313174352015.png)

![Reed](image-20230313174423006.png)

### Mushroom

If I remember correctly, this is the only mushroom in the game. Each group of mushrooms has the same texture, so the same set of tiles is repeated.

![Striped Mushroom](image-20230313174829378.png)

### Potted plant

Potted solution is the lower modeling, the upper surface.

![Pot 1](image-20230313174931505.png)

For bloated objects that can't be cubed, the game is represented by this overflow piece, which can be seen as real if you don't look closely, and it's used in many places.

![Pot 2](image-20230313174945554.png)

## Ground

### The richness of the ground

Toem is black and white, but the scenes don't feel hollow. Here I use a forest scene as an example. In the Boy Scout scene, various plant materials are divided into three levels for placement.

![Boy Scout Scene](image-20230313175256839.png)

1. Basic ground texture + low ground plants, grass, gravel shadow
2. High ground plants, thicker grass
3. Trees and rocks : Pines and rocks

Even in other situations, the formula still holds

![Scene of Ghost House](image-20230313175501711.png)

![Furry Snow Monster Scene](image-20230313180119039.png)

The same goes for the scene in the sea.

![Seabed treasure Scene](image-20230313180037933.png)

### Texture of the ground

Toem's floor looks simple but is filled with details.。

The Brick Floor map has two types of bricks and comes with modeling bricks, so a simple brick floor has three elements.

![Beach Brick floor](image-20230313181231332.png)

This image shows special brick sides under the lamp posts, line textures on the stairs, and bricks on the walls that are completely different from the floor.

![Beach lamp post floor](image-20230313181331961.png)

On the tile floor of the runway scene, a closer look will find that the tile edge is distributed with random black edges.

![Show scene](image-20230313181443950.png)

## Building type

Toem's architecture is distinguished by the best wall texture, the best corner material and the best roof design.

![Urban Housing](image-20230313175918960.png)

Toem made five designs for Windows to prevent a single building.

##  Details of the chair

Because the proportion of the characters is exaggerated, so the chair in line with the action of the characters is dwarfed.

![All-purpose chair in Games](image-20230313180654878.png)

![Cinnamon Bun Scene](image-20230313180709820.png)

![Worker](image-20230313180724009.png)

# Our Creations

We analyzed a lot of Toem's creation methods before production, and applied this flat style to our own creation. But because our model is not a completely cube item, the process is a little more cumbersome.

This is an experimental tree, but it won't be used because it lacks an original design.

![Our tree](image-20230313181754771.png)

To create the house, a modeling software was used to extend the face and then map the face to achieve the Toem effect. It's a lot of work, thanks to our 3D art.

![Houses created in the style of Toem](image-20230313182004253.png)
