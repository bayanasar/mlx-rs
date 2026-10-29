# CHANGELOG

## Unreleased

- Update the pinned native tuple to mlx-c `a26f2d5` (v0.8.0) and MLX `0.32.4`. The C API adds
  `mlx_fast_gated_delta_update`, `mlx_unique`, `mlx_matrix_transpose`,
  `mlx_get_array_buffer_size`, `mlx_distributed_init_with_all_gather` and
  `mlx_distributed_clear_backends`; `mlx_gather_qmm` takes a `global_scale` before
  `sorted_indices`; and `mlx_distributed_group_rank` and `mlx_distributed_group_size` become
  `mlx_distributed_group_get_rank` and `mlx_distributed_group_get_size`, which return a status
  and write the value through a pointer
- Generate the bindings with bindgen 0.73; the system opaque types `_malloc_zone_t`
  and `__sFILEX` no longer derive `Copy` and `Clone`

## 0.7.0

- Update the pinned native tuple to mlx-c `a341b49` (v0.7.0); MLX stays at `0.32.2`.
  The C API adds 19 stream functions, and the `mlx_io_vtable_` callbacks change
  return types: `seek` returns `int`, `read` and `write` return `size_t`
- Declare `links = "mlx"` and publish the MLX include path (MLX, metal-cpp and
  mlx-c), the MLX defines and the pinned MLX version as `DEP_MLX_*`, so
  dependent build scripts can compile C++ against the exact MLX this crate built
  (#390, thanks @SneakyBerry)
- Add the `metal-jit` feature, which builds MLX with `MLX_METAL_JIT` and keeps its
  metallib in `~/.mlx/lib/<mlx-c key>-jit/` (#391, thanks @anuejn)
- Link the `libjaccl` archive MLX builds, so `mlx_distributed_*` links on macOS SDK
  26.2 and later
- The generated bindings no longer declare `malloc` and `realloc`, which Rust 1.99
  rejects

## 0.6.0

- Update the pinned native tuple to mlx-c `c74db530` and MLX `0.32.2`
- Link the vendored `gguflib` archive; the GGUF symbols were unusable before
- Write the Metal library to `~/.mlx/lib/<mlx-c key>/` so binaries from
  `cargo install` can find it; `MLX_RS_METAL_PATH` overrides the location

## 0.1.2-release

- Update generated bindings to mlx-c 0.1.2

## ~~0.1.2~~

- ~~Update generated bindings to mlx-c 0.1.2~~
- Mistakenly published 0.1.0 as 0.1.2

## 0.1.0

- Update generated bindings to mlx-c 0.1.0
