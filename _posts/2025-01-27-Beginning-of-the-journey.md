# This is the beginning of the journey !

I just came back from a Game Jam, organized by [Atlangames](https://www.atlangames.com/) for the Global Game Jam. Even though we did not finish our game, I had a great time and met nice people. Also, it sparked the want to make game development one of my hobbies. So... welcome to the beginning of this hobby.

## Chose a game engine

First thing first, I need to chose a game engine. I want to use C++ for these projects (it's been my main language) and at first glance I found these engines:
- Unreal Engine
- Godot
- Halley
- Raylib

I'm currently running on an old laptop, so exit Unreal Engine. Godot seems very nice (I used it for the JAM), but I want to explore the world a bit more. Halley seemed nice as well.

In the end, I decided to go with raylib. It seems very simple, there are nice examples, and I feel like exploring game dev by myself, without a bigger framework to shape my ideas. It will be more work, but for now I'm okay with it. And if it ends up taking too much efforts, I can always switch in the future.

## Where do I start ?

First thing first, let's setup a project ! I'm on Windows 11 and will use WSL2 to dev on linux. I'll use [CLion](https://www.jetbrains.com/fr-fr/clion/) as my IDE. That's what I've been using lately and I quite like it.

1. Let's setup a project using [cmake-init](https://github.com/friendlyanon/cmake-init).

```bash
cmake-init raylib-demo
```

This will setup a simple "Hello world" project in cmake, with lots of tools already pre-configured.

![image](https://github.com/user-attachments/assets/d7055f0f-b003-4d3d-b122-521a587e8992)

2. Let's get [raylib](https://github.com/raysan5/raylib/releases)

I've looked a bit to find a way to link raylib using cmake. Couldn't find a quick solution, and I want to do game dev, not project setup. For now, I'll chose to go the easy way. Raylib provides pre-compiled libraries for the x64 platform. I can just download these, extract them and copy them to my ```/usr/...``` folder.

3. Now we can link to raylib in our cmakefile

```cmake
...
target_link_libraries(raylib-demo-core PUBLIC
        -lraylib
        -lm
        -ldl
        -pthread
        -lGL
)
...
```

> [!TIP]  
> Initially, the linker could not resolve ```-lGL```. To fix this, I had to install the ```libgl1-mesa-dev``` package.

4. And voila

Using a simple raylib [example](https://www.raylib.com/examples.html), we can check that raylib works correctly by openning a window.

![image](https://github.com/user-attachments/assets/bd37cd43-132d-4387-8139-29400116ecb9)

## What's next ?

Now, I want to load a display images. Let's see if I can have a character moving on screen.

> [!NOTE]  
> I found a [guy on youtube](https://www.youtube.com/watch?v=j0C4ox1gFxk&list=PLORJX3OiHbbMs9AFM5bzpNUychJm1raub) demonstrating the first steps into making a 2D game with raylib. I'll be using its guidance for the next steps.
