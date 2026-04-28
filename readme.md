# Hurry Curry! Flatpak Manifest

This flatpak contains:

- the main game
- the server binary
- the discovery service binary

It uses <https://codeberg.org/hurrycurry/hurrycurry-dist-extra> for AppStream
data and desktop entry.

## Building

If not done already, run

```shell
git submodule update --init
```

Furthermore you need the following build dependencies:

```shell
flatpak install runtime/org.freedesktop.Sdk/x86_64/24.08
flatpak install runtime/org.freedesktop.Sdk.Extension.node20/x86_64/24.08
```

To update rust dependencies use `flatpak-cargo-generator.py` from
<https://github.com/flatpak/flatpak-builder-tools/blob/master/cargo/flatpak-cargo-generator.py>
as following:

```shell
python flatpak-cargo-generator.py path/to/hurrycurry/source/repo/Cargo.lock generated_sources.json
```

To build and install for testing run

```shell
flatpak-builder --force-clean --install --user builddir/ org.metamuffin.hurrycurry.client.yaml
```
