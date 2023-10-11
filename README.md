# Cmake.AddFromArchive

A cmake script that adds dependencies to a project right from release archives. Be it local or from remote url.
Works at configure time.

Has 2 functions:

```CMake
add_from_archive_url(url      [path_to_CMakeLists_inside_the_archive])
add_from_archive    (rel_path [path_to_CMakeLists_inside_the_archive])
```

`url` is the url of an archive.

`rel_path` path to an archive, relative to current `CMakeLists.txt`

`path_to_CMakeLists_inside_the_archive` path inside the archive, where added dependency's `CMakeLists.txt` can be found.
Most often can be omited, since the `CMakeLists.txt`is at root.

For example:

```
# From remote
add_from_archive_url(https://github.com/protocolbuffers/protobuf/releases/download/v3.19.6/protobuf-cpp-3.19.6.tar.gz cmake)
# Locally stored archive
add_from_archive(extlibs/protobuf-3.19.6.7z cmake)
```

## Usage

Download the `AddFromArchive.cmake`

```bash
mkdir -p cmake && wget -O cmake/AddFromArchive.cmake "https://gitlab.com/44100Hz/cmake.addfromarchive/-/raw/main/AddFromArchive.cmake?ref_type=heads&inline=false"
```

And include it into your `CMakeLists.txt` by

```CMake
include(cmake/AddFromArchive.cmake)
```

Than use the 2 functions to add the dependencies.
Note, some old projects, with very retro cmake files, may not work with the script. Most modern ones do.
