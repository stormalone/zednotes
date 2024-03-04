
### self.center is the place where the files show up in the workspace

```rust
pub struct Workspace {
    center: PaneGroup
```

Inside the *Render* of workspace.rs

```rust
impl Render for Workspace {
```

```rust
// Panes
 .child(
     div()
         .flex()
         .flex_col()
         .flex_1()
         .overflow_hidden()
         /*
         .child(self.center.render(
             &self.project,
             &self.follower_states,
             self.active_call(),
             &self.active_pane,
             self.zoomed.as_ref(),
             &self.app_state,
             cx,
         ))
         */
         .children(
             self.zoomed_position
                 .ne(&Some(DockPosition::Bottom))
                 .then(|| self.bottom_dock.clone()),
         ),
 )
 // Right Dock
```

[isahc](https://github.com/sagebind/isahc) is the default HTTP client library in GPUI...

### How to have the window pop up immediately when you cargo run

```rust
cx.activate(true);
```

### How to build Zed

```rust
git submodule update --init --recursive
```

* [Noted here on how to build Zed on a mac](https://github.com/zed-industries/zed/blob/main/docs/src/developing_zed__building_zed_macos.md)
* [install postgresapp](https://postgresapp.com/downloads.html)
* [local database setup](https://zed.dev/docs/local-collaboration)


### How does open_window happen in Zed

zed/src/main.rs

* see *workspace::open_new* in *restore_or_create_workspace*
* app.on_reopen

### Location of logfiles

/Users/ma/Library/Logs/Zed   
Location of db file:   
/Users/ma/Library/Application Support/Zed/db/0-dev   
Which is a sqlite database.

In main.rs see *init_paths* which points to LOGS_DIR   
which is located in crates/util/src/paths.rs

```rust
rg picker -g Cargo.toml
rg new_view
```

### Code flow workspace

```rust
open_new
Editor::new_file
```

#### crates/zed/src/main.rs

```rust
initialize_workspace
```
