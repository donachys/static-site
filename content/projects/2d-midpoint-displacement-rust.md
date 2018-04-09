+++
date = "2017-01-15T00:00:00"
description = "Scenery Image generator written in Rust."
thumbnail = "images/midpoint_displacement_rs.png"
image = "images/midpoint_displacement_rs.png"
title = "2d-midpoint-displacement-rust"
slug = "2d-midpoint-displacement-rust"
author = "Shaun Donachy"
draft = false
hidesidebar = true
+++

### Scenery image generator written in rust

Another project inspired by [a blog post](https://bitesofcode.wordpress.com/2016/12/23/landscape-generation-using-midpoint-displacement/).

I was interested in working with Rust some more and it was an excuse to implement one of my favorite
algorithms: Bresenham's line drawing algorithm.

You can see an example of the output above. Many of the variables are defined as constants in `main.rs`. Try modifying the image size or colors and generate your own scenery. 😎  The source code is hosted [on github](https://github.com/donachys/midpoint_displacement_2d_terrain).
