+++
title = "Develop a render plugin for Amethyst game engine 101"
description = "Writing custom render plugins for Amethyst game engine 101"
+++

While at [FOSDEM](https://fosdem.org/2020/) at the beginning of Feburary 2020 I
gave a talk about some of the work that some of my PhD students and I have been
doing using Domain Specfic Languages (DSLs) in the design of Digital Musical
Instruments (DMIs). The project is called [Muses](https://muses-dmi.github.io/)
and this is a [link](/presentations_reveal/FOSDEM'20/) to the slides for the
talk. This blog is not about that work!

On returning from FOSDEM I was talking to my son, currently going by the name
Bob 1, and he asked what I'd been doing when in Brussels. Well on the journey
back on the Eurostar I'd been watching a Catherine West's RustConf'18 keynote
[Using Rust for Game Development](https://www.youtube.com/watch?v=P9u8x13W7UE)
and so I started to talk about that and how I wanted to write a game. In fact
what I was really interested at this point was learning more about Entity
Control Systems (ECS), but that was beside the point. 

So after some discussion we decided that I would implement a clone of original
space invaders and Bob 1 would be my tester. I would implement this completly in
Rust using minimnal number of existing crates, in particular I would implement
my own ECS, no using exiting Rust packages, such as Specs. The results of some
late night working can be found
[here](https://github.com/bgaster/rusty-space-invaders). 

While it was fun writing my own mini ECS, sprite and animation libraries, I knew
that it was unlikely the next game project would be using my own game engine.
For most part this was not because don't want to write a game engine, I do, but
more I was interested in seeing what was out there already in Rust, and learning
more about how experienced game developers utilise Rust.

So the burning question as we entered lockdown in the UK, other than worrying
about family, friends, and students was, which of the many exciting Rust
projects should I begin looking at? Rust's community is amazing and this is no
less true for game development. In particular, I started out looking through the
pages of [Are We Game Yet?](https://arewegameyet.com/), a great resource for all
things games in Rust. I was aware of many of the existing crates, particularly
when it comes to rendering.

```rust
pub type IndexType = u16;

#[derive(Debug, Default)]
pub struct VertexType {
    pub position: [f32; 2],
    pub colour: [f32; 4],
}

/// Component for the triangles we wish to draw to the screen
#[derive(Debug, Default)]
pub struct Mesh {
    pub vertices: Vec<VertexType>,
    pub indices: Vec<IndexType>,  
}
```