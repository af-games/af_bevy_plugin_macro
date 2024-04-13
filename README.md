# AF Bevy Plugin Macro

## What?

Automates generation of bevy plugins boilerplate.

## Usage

Let's say you have a Bevy crate called `Foo` consisting of two plugins, `ControlPlugin` and `DisplayPlugin`. You might write a `lib.rs` like this:

```rs
use bevy::prelude::*;
pub mod control;
pub use control::*;
pub mod display;
pub use display::*;

pub struct FooPlugins;
use bevy::{app::PluginGroupBuilder, app::PluginGroup};
impl PluginGroup for FooPlugins {
    fn build(self) -> PluginGroupBuilder {
        PluginGroupBuilder::start::<Self>()
                .add(control::ControlPlugin)
                .add(display::DisplayPlugin)
    }
}
```

Replace this with:

```rs
use af_bevy_plugin_macro::bevy_plugin_group;

bevy_plugin_group!(foo, control, display);
```

Much better!

## License

AF Bevy Plugin Macro is free, open source and permissively licensed!

All code in this repository is dual-licensed under either:

* MIT License ([LICENSE-MIT](LICENSE-MIT) or [http://opensource.org/licenses/MIT](http://opensource.org/licenses/MIT))
* Apache License, Version 2.0 ([LICENSE-APACHE](LICENSE-APACHE) or [http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0))

at your option.
This means you can select the license you prefer!
This dual-licensing approach is the de-facto standard in the Rust ecosystem and there are [very good reasons](https://github.com/bevyengine/bevy/issues/2373) to include both.