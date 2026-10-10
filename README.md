# openal-soft-orbis

OpenAL Soft with an Orbis AudioOut backend, built as the `libopenal` PRX that LWJGL loads at
run time. See PORT-PROVENANCE.json for exact origins; its `upstream` record is the pinned
OpenAL Soft release this recipe builds.

```sh
python3 build_openal.py --sdk /path/to/ps4-payload-sdk --toolchain /path/to/PS4Toolchain --fetch
```

Inputs:

- `orbis-runtime-support` as a sibling checkout, or `ORBIS_RUNTIME_SUPPORT`: the shared PRX recipe.
- An orbis-compat checkout at `$ORBIS_BUILD_ROOT/sources/orbis-compat`.

`ORBIS_BUILD_ROOT` (default `build/`) also holds `downloads/` and the output in `openal/`.
The launcher sets it to its `graphics-probe/build`. This repository does not depend on LWJGL.

## Releases

`.github/workflows/release.yml` builds this port on GitHub-hosted Ubuntu with the SDKs and the
dependencies pinned in `dependencies.lock.json`, and with `publish` checked releases
`<tag_prefix>-<commit>` holding the archive `release.json` describes. Cyrene Launcher pins that
release by SHA-256. The workflow needs a `CYRENE_RELEASES_TOKEN` secret that can read the private
CyreneLauncher repositories.
