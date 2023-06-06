+++
date = "2023-06-05T00:00:00"
description = "Dragenvoy - Remixed for 2023"
thumbnail = "images/dragenvoy_ld26_2023.png"
image = "images/dragenvoy_ld26_2023.png"
title = "Dragenvoy - 2023"
slug = "dragenvoy-ld-26-remix-2023"
author = "Shaun Donachy"
draft = false
hidesidebar = true
tags = ["Unity", "C#", "games", "gamejam", "2D"]
+++


### 10-Year Anniversary Edition!

Dragenvoy has enjoyed 10 glorious years on the web. 👏👏👏 Fans of this famous game will recall that it received an [update in 2018](https://shaundonachy.com/projects/dragenvoy-ld-26-remix-2018/) to improve browser compatibility. I thought it would be a good time to make an update to the game ten years after I made it for ludum dare 26 and celebrate the closing of my chapter working at Unity that began many years later. For the 10-year anniversary update I simply wanted to improve the dragon's motion to match the original design. While watching luggage being wheeled around at the airport I realized what was causing the dragon body to move more erratically than intended. The solution, I thought, was to add some wheels to each body segment. I noticed that Unity had added some wheel physics components for both 3d and 2d games, but I found those components not to be compatible. The wheel-based approach to solving the issue did lead me to the right search query, though! Incredibly a post on a stack overflow site from more than 11 years ago gave me the clues I needed with some sample code. Essentially I just needed to prevent the body segments from having any orthogonal velocity 💀.

#### The Method

This was pretty much the entirety of the changes.
```csharp  {linenos=table,linenostart=32}
public static void dampenOrthogonalVelocity(GameObject vehicle, float drift = 0f, float maxDrift = 0f)
{
	Rigidbody2D temprb2D = vehicle.GetComponent<Rigidbody2D> () as Rigidbody2D;
	Vector2 forwardVelocity = vehicle.transform.up * Vector2.Dot(temprb2D.velocity, vehicle.transform.up);
	Vector2 rightVelocity = vehicle.transform.right * Vector2.Dot(temprb2D.velocity, vehicle.transform.right);
	temprb2D.velocity = forwardVelocity + Vector2.ClampMagnitude(rightVelocity * drift, maxDrift);
}
```

In order to retain the physics simulation aspect of the dragon's movement we don't want to entirely remove orthogonal velocity, but just dampen it while also clamping it to a maximum value. Applying this to each of the body segments results in the dragon body movement following the head's path more closely, while still allowing some side-to-side motion that occasionally results in the pellets being smacked around the play area.

### Wassup WASM

Updating the project to Unity v2021.1.4f1 and building for the Web target results in different files than either of the prior versions. This time web assembly is used! Pretty cool to see this technology in use. Upgrading this admittedly basic game project has not been too difficult and its interesting to see that even though it is built and executed each time with different technologies the result remains pretty much the same!

### Try it
Here is the link to [Dragenvoy - 2023](https://shaundonachy.com/dragenvoy2023/index.html).
