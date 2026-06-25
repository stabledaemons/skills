---
name: vet-dependency
description: Use during writing before adding a package, library, framework, service dependency, or new import that is not already common in the repository. Do not use for dependencies explicitly required by the user.
---

# Vet Dependency

Vet dependencies before adding them so the project does not take on unnecessary
maintenance or supply-chain risk.

## Steps

1. Check whether the project already has a suitable dependency, helper, or
   standard-library API. Inspect manifests and lockfiles such as `package.json`,
   `pyproject.toml`, `go.mod`, and `Cargo.toml`, then search existing imports
   and local utilities.
2. State the need clearly: what capability is required, why it is not trivial to
   implement locally, and what happens if the dependency is not added.
3. Vet the candidate dependency with ecosystem-native evidence where available:
   - Registry metadata such as `npm view <pkg>`, PyPI, crates.io, pkg.go.dev,
     `go list -m -u -json`, or the package registry page.
   - Security or advisory tooling such as `npm audit`, `pip-audit`,
     `cargo audit`, `govulncheck`, or a project-native equivalent.
   - Repository signals such as recent releases, maintainer activity, and
     unresolved critical issues.
   - License compatibility.
   - Dependency cost such as transitive dependencies, package size, install
     scripts, and runtime impact.
4. Do not claim a dependency was vetted unless you checked the relevant
   registry or package metadata and one security or advisory source when
   available.
5. Add the dependency only when the benefit clearly outweighs the maintenance
   and supply-chain cost. A dependency is usually justified when the capability
   is non-trivial, security-sensitive, protocol-heavy, compatibility-heavy, or
   outside the project's core domain.
6. If adding the dependency, use the project-native package manager, update the
   manifest and lockfile together, add or update focused tests, and state the
   rationale in your plan, reply, PR description, or commit message.
7. If not adding the dependency, explain the simpler alternative and note which
   existing dependency, standard-library API, or local implementation will be
   used instead.

## Final Check

- Did you confirm the capability is not already available in the project or
  standard library?
- Did you vet license, maintenance, security, ecosystem fit, and dependency
  cost with concrete evidence?
- Did you clearly state why adding or avoiding the dependency is the better
  choice?
- If added, did you update the manifest and lockfile with the native package
  manager and run focused tests?
