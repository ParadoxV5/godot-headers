# godot-headers

This repository contains C headers for
[**Godot Engine**](https://godotengine.org)'s *GDExtension* API.

GDExtension enables the use of dynamically linked libraries inside of Godot.

## Versioning

This repositories follows the same branch versioning as the main
[Godot Engine repository](https://github.com/godotengine/godot):

- `master` tracks the current release branch. As this is a moving target,
  the headers in this repository may not always be fully in sync with upstream.
  See [Updating Headers](#updating-headers) if you need to bring
  them up to date.
- `4.x` tracks the release of the next 4.x minor release. Like `master`, it
  might not always be fully up-to-date with upstream.
- Other versioned branches (e.g., `4.0`) track the latest stable release
  in the corresponding branch.

Stable releases are also tagged on this repository (except for 4.0.0 and 4.0.1):
[Tags](../../tags).

*Projects built against a stable release of Godot may use this repository as
a Git submodule, checking out the specific tag matching your Godot version.*

## Using this library

This library is meant to be used in conjunction with a code generator that
creates the binding code necessary to interact with Godot. This library only
provides access to the API over which communication with the Godot core is
implemented and binding metadata in the form of a JSON document.

One such binding library is
[`godotengine/godot-cpp`](https://github.com/godotengine/godot-cpp)
which implements the bindings using C++.

An official pure C sample project is currently not available.

## Updating Headers

See [Versioning](#versioning) for details on the Godot versions tracked by
each branch of this repository.

If the relevant branch is not up-to-date for your needs, or if you want to sync
the headers with your own modified version of Godot, here is the update
procedure used to sync this repository with upstream releases:

- Download or Compile Godot Engine at your specific version/commit
- Use the executable to generate a `extension_api.json` file
  - without documentation: `godot --dump-extension-api`
  - with docs (new in Godot 4.2): `godot --dump-extension-api-with-docs`
- Copy the file
  [`core/extension/gdextension_interface.h`](https://github.com/godotengine/godot/blob/master/core/extension/gdextension_interface.h)
