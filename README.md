# dependency_injection

DependencyContainer / DependencyModule abstraction, with a get_it-backed implementation. Part of the [modular_app_template](https://github.com/Yusubov-Engineering/modular_app_template) core modules.

Released as two packages, versioned and tagged together:

- **`dependency_injection_api`** — the abstract contract. Feature code and other `_api`
  packages depend on this, never on `dependency_injection_impl`.
- **`dependency_injection_impl`** — the concrete implementation. Only the app's composition
  root depends on this.

Current release: **`v1.0.0`**.

## Using it

This repo is not published to pub.dev — consume it as a `git:` dependency
pinned to a tag:

```yaml
dependencies:
  dependency_injection_api:
    git:
      url: git@github.com:Yusubov-Engineering/dependency_injection.git
      path: dependency_injection_api
      ref: v1.0.0
  dependency_injection_impl:
    git:
      url: git@github.com:Yusubov-Engineering/dependency_injection.git
      path: dependency_injection_impl
      ref: v1.0.0
```

## Local development

The two packages share one pub workspace, declared in the root
`pubspec.yaml`:

```bash
flutter pub get   # resolves both dependency_injection_api and dependency_injection_impl
flutter analyze
```

## Releasing

Bump both packages' `version:` in lockstep, then tag:

```bash
git tag -a vX.Y.Z -m "vX.Y.Z"
git push origin vX.Y.Z
```

Every consumer pins an explicit `ref:`, so nothing picks up a new release
until its `pubspec.yaml` is updated to point at the new tag.
