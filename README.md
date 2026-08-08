# NullFox Updates

This repository is the public update feed for NullFox.

Installed browsers read [`update.xml`](update.xml). Signed complete MAR files and Windows installers are published as GitHub Release assets. An empty `<updates/>` response means that no update is currently offered.

The private MAR signing database is intentionally not stored in this repository. NullFox verifies every downloaded MAR against public certificates compiled into the updater before installation.

The update endpoint is `https://raw.githubusercontent.com/mendo0oo/Nullfox/main/update.xml`. Copies installed before this endpoint and the NullFox signing certificates were added require one manual bootstrap installation. Every release must have a unique, newer Build ID; public versioned releases should also increment the application version.

## Signing certificates

- Primary SHA-256: `4c8107634de9739a6f56e79dd3a3ac3c5bdf672e76dbcec091686d7cafefcf2a`
- Secondary SHA-256: `942802fc719d57bb590cd83d98ed3bf8959fd9f42c68094cd045ca55bc10fdba`

The corresponding public DER files are in [`keys`](keys). They cannot be used to sign an update.

## Publishing

From the Firefox source checkout, build and publish an update with:

```powershell
.\tools\nullfox\Build-NullFoxUpdate.ps1
.\tools\nullfox\Publish-NullFoxUpdate.ps1 -ArtifactDirectory .\artifacts\nullfox-update\VERSION-BUILDID
```

The token should be a fine-grained token limited to this repository with `Contents: Read and write` permission.

Never rewrite or replace an already published MAR. Create a new NullFox build and release instead.
