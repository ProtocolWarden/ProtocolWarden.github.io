# SyncMechanism

## Mission

Generic, public-safe Syncthing install and runtime mechanism — version pinning,
config archiving, a desktop tray, and login-startup registration. Config-driven,
with zero machine-specific data.

## This Repo Is

- a version-pinned Syncthing **install / upgrade** tool that archives the
  existing config before replacing the binary
- a desktop **tray app** for one-click install / check / list, with a
  login-startup toggle
- a **login-startup** mechanism (XDG autostart on Linux, HKCU Run on Windows)
- a **sync-spec** tool — validate, report coverage, and resolve a manifest sync
  spec against a private binding into a plan
- a small unified CLI (`python -m sync_mechanism`) wiring `install`, `tray`,
  `startup`, and `spec`
- entirely config-driven and public-safe — no host-specific data is baked in

## This Repo Is Not

- a device or folder registry — no device list, no topology, no machine data
- a holder of secrets or credentials
- fleet wiring or data backup/restore — those live in the private fleet layer
  that *consumes* this mechanism
- a Syncthing fork — it installs upstream Syncthing release binaries

## Boundary

The public mechanism (install/runtime/spec-validation) lives here; the private
fleet layer (devices, folders, bindings) consumes it via documented environment
variables and a manifest sync spec. See
[Sync & Data Transport](../architecture/sync-and-data-transport.md) for how the
mechanism relates to the platform's transport model.

## Links

- [GitHub](https://github.com/ProtocolWarden/SyncMechanism)
