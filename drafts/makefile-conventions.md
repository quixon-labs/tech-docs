# Makefile Conventions

## Variables

Name | Notes
--- | ---
__DEBUG__ | 0/1 - For controlling release/debug builds, runs, etc.
__TARGET__ | For choosing target of multi-target build systems
__CARGO_ARGS__ | For cargo specific args
__prefix__ | Install prefixes if needed.

## Common rules

Rule | Notes 
--- | ---
__release__ | Clean everything, run fresh release build
__debug__ | Rebuild debug version (no clean)
__dev__ | Run debug builds
__clean__ | Clean just enough for a fresh rebuild of current project only
__purge__ | Complete clean including all deps
__test__ | Run default tests

## Additional rules

Rule | Notes 
--- | ---
__build__ | Debug/release agnostic build (or for common impls)
__build-release/build-debug__ | Build release/debug without clean
__run__ | For debug/release agnostic runs (or for common impls)
__deps__ | All deps (commonly aggregated rule set)
__install/uninstall__ | Self-explanatory. Always pair install with uninstall.
__default__ | When an additional indirection is used for first rule
__check__ | Lints/rust cargo check.

## Extra Conventions

Convention when there are multiple dependencies or for better granularity. 
Note: *Let this grow organically, and try not to over-engineer makefiles*

Rule | Notes
--- | ---
__deps-&ast;__ | Granular deps
__clean-&ast;__ | For granular cleaning including deps,
__debug-&ast;/release-&ast;__ | For granular dev builds including multiple targets
__dev-&ast;/run-&ast;__ | For granular dev runs including multiple targets
