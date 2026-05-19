# AGENTS.md

## Overview
This repository contains Spack configuration files used for managing software packages and toolchains in a macOS/homebrew environment. The configurations define compiler setups, package variants, external dependencies, and more.

## Project Structure
- **README.md**: Project overview and general instructions.
- **concretizer.yaml, config.yaml, modules.yaml, packages.yaml, repos.yaml, toolchains.yaml**: Core Spack configuration files.
- **ljkmmde/**, **reports/**, **extra_modulefiles/**: Additional directories supporting custom modules and reporting.

## Essential Commands
- **Build/Install**: `spack install <package>`
- **Load Package**: `spack load <package>`
- **Environment Setup**: `spack env create <env-name>` and `spack env activate <env-name>`
- **Configuration Check**: Use `spack config blame` to troubleshoot configuration issues.
- **Reconcretize**: Run `spack concretize` after configuration changes to update dependency resolution.

## Conventions and Patterns
- **YAML Format**: All configuration files follow strict YAML formatting. Editing requires attention to indentation and whitespace.
- **Compiler Definitions**: Multiple compilers (e.g., apple-clang, gcc, llvm) are defined with externals and proper extra attributes.
- **Package Variants**: Variants are specified with comments indicating specific use-cases (e.g., fortran, mpi, threadsafe).
- **External Dependencies**: Paths in externals reference system directories (e.g., `/usr`) or Homebrew paths (e.g., `/Users/mathomp4/.homebrew/brew`).

## Testing and Validation
- Validate YAML syntax with tools like `yamllint`.
- Run Spack commands (e.g., `spack install`, `spack config blame`) to ensure proper package resolution and configuration correctness.

## Gotchas
- **Compiler Paths**: Ensure that paths for compilers are correct, particularly when switching between Homebrew and system paths.
- **Sensitive YAML Syntax**: Spack configurations are sensitive to YAML syntax; even minor indentation errors can cause issues.
- **Configuration Updates**: Any changes might require cleaning and reconcretizing the Spack environment.

## Additional Context
- Future agents should refer to this document to understand common commands and patterns in these configurations.
- Follow existing formatting and conventions strictly when making edits or adding new configurations.
