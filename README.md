# NullFox Updates

This repository is the public update feed for NullFox.

Installed browsers read [`update.xml`](update.xml). Signed complete MAR files and Windows installers are published as GitHub Release assets. An empty `<updates/>` response means that no update is currently offered.

The private MAR signing database is intentionally not stored in this repository. NullFox verifies every downloaded MAR against public certificates compiled into the updater before installation.

## Publishing

From the Firefox source checkout, build and publish an update with:

```powershell
.\tools\nullfox\Build-NullFoxUpdate.ps1
.\tools\nullfox\Publish-NullFoxUpdate.ps1 -ArtifactDirectory .\artifacts\nullfox-update\VERSION-BUILDID
```

The token should be a fine-grained token limited to this repository with `Contents: Read and write` permission.

Never rewrite or replace an already published MAR. Create a new NullFox build and release instead.
