# gmsh-rs

A minimal [gmsh](https://gmsh.info/) `msh` file parser implemented using Rust.
This parser implements version 1 and 2 `msh` file format specification.

- `msh` version 1 is available [here](https://gmsh.info/dev/doc/texinfo/gmsh.html#MSH-file-format-version-1-_0028Legacy_0029).
- `msh` version 2 is available [here](https://gmsh.info/dev/doc/texinfo/gmsh.html#MSH-file-format-version-2-_0028Legacy_0029).

The version 2, however, is incomplete, and parses only the most relevant fields.

### Sample usage

```rust
use {gmsh_rs::Mesh, std::fs::File};

fn main() -> std::io::Result<()> {
    let mut f = File::open("/home/pacce/meshes/disk.msh")?;

    let mesh = Mesh::decode(&mut f)?;
    println!("{:?}", mesh);
    Ok(())
}
```