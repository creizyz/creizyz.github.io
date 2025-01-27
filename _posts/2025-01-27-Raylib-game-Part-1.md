# Raylib game (Part 1)

In the previous post, we managed to setup a raylib project. Today, we'll attempt at drawing images on screen, and maybe more.

## What do we draw ?

To draw something, we'll need assets. Luckily, lots of great assets are available online. [Kenney's website](https://kenney.nl/) and [Itch.io](https://itch.io/game-assets/free) are two great places to look for assets.

I was able to find these two asset packs on Itch.io:
- a [knight](https://aamatniekss.itch.io/fantasy-knight-free-pixelart-animated-character) created by [aamatniekss](https://aamatniekss.itch.io/)
- a [forst environment](https://brullov.itch.io/oak-woods) created by [brullov](https://brullov.itch.io/)

They look amazing to be honest, big thanks to the artists for releasing these for free !

## Let's start drawin'

1. in order to draw, we'll need to load the texture

```cpp
const auto image = LoadImage("assets/sprites/knight-run.png");
    auto texture = LoadTextureFromImage(image);
    UnloadImage(image);
```

2. then we can draw it on the screen

```cpp
DrawTexture(texture, 0, 0, WHITE);
```

3. nothing on screen...

![image](https://github.com/user-attachments/assets/e1548d1b-664c-4ca4-a55c-ba1c74737ac3)

Well, that did not work... Checking at logs, we get the answer though:

```logs
WARNING: FILEIO: [assets/sprites/knight-run.png] Failed to open file
WARNING: IMAGE: Data is not valid to load texture
```

So, the executable could not find our images. It makes sense, since we're giving a relative path to the assets, but the executable is not placed in the PROJECT_DIR. For now, we can simply change the relative path.

> In the future though, we should include a step in the project build that will copy our assets to the same directory as the build. Maybe with compression even ?

4. let's correct the relative path

![image](https://github.com/user-attachments/assets/d6feed82-4e54-4fd8-995c-e97a4de16cde)
