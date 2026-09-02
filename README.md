# Lazuli — Releases

Download page for **Lazuli**, a Fabric Minecraft mod built around
Steamworks-powered social and cloud features plus a set of client-side
quality-of-life tweaks.

This repository contains **no source code**. It exists only to host the release
jars and a machine-readable manifest of them. The mod's source is maintained in
a separate, private repository.

## Downloads

Grab the jar for your Minecraft version from the table below (or from the
[Releases](../../releases) page directly), drop it into your `mods/` folder
alongside [Fabric Loader](https://fabricmc.net/use/) and the dependencies listed
under [Requirements](#requirements).

<!-- VERSION_TABLE -->

The table above is generated from [`versions.json`](versions.json) on every
release — see [Automation](#automation).

## Requirements

Every Lazuli jar needs, at matching versions for your Minecraft version:

- [Fabric Loader](https://fabricmc.net/use/)
- [Fabric API](https://modrinth.com/mod/fabric-api)
- [Cardinal Components API](https://modrinth.com/mod/cardinal-components-api)
  (the `cardinal-components-base` module)

Steam-backed features additionally require the Steam client to be installed and
running, with Lazuli launched through a Steam-registered copy of the game.

## `versions.json`

[`versions.json`](versions.json) is a stable, append-only manifest intended for
tools (e.g. a future launcher) that need to resolve "latest Lazuli jar for
Minecraft X" without scraping this page or the GitHub API.

```jsonc
{
  "schemaVersion": 1,
  "mod": { "id": "lazuli", "name": "Lazuli" },
  "releasesRepo": "<owner>/<this-repo>",
  "generatedAt": "<ISO-8601 timestamp>",
  "releases": [
    {
      "modVersion": "1.2.0.0",          // MAJOR.MINOR.PATCH.HOTFIX
      "tag": "v1.2.0.0",                // GitHub release / git tag
      "releaseDate": "2026-09-01",      // YYYY-MM-DD (UTC)
      "artifacts": [
        {
          "minecraftVersion": "26.2",
          "jarFileName": "fabric-26.2-1.2.0.0.jar",
          "downloadUrl": "https://github.com/<owner>/<repo>/releases/download/v1.2.0.0/fabric-26.2-1.2.0.0.jar",
          "sha256": "<64 hex chars>"
        }
        // ... one entry per supported Minecraft version
      ]
    }
    // ... newest release first
  ]
}
```

`releases` is ordered newest-first by numeric `modVersion`. The same
`versions.json` is also attached as an asset to every GitHub Release, so a tool
can either follow the rolling copy on the default branch or pin to a release.

## Issues

Bug reports and feature requests go in this repository's
[issue tracker](../../issues). Because the source is private, please include as
much detail as you can: exact Minecraft + Lazuli + Fabric Loader + Fabric API
versions, the full crash report / log, and clear reproduction steps.

## Automation

Releases here are published automatically by the private source repo's release
workflow. On each release it:

1. builds the per-Minecraft-version jars,
2. creates the matching GitHub Release in this repo and uploads the jars,
3. regenerates [`versions.json`](versions.json) and this README's version table
   and commits them here,
4. attaches `versions.json` as a release asset.

## License

See each release's notes and the bundled `LICENSE` inside the jar for the
license covering that build. Historical builds released as CC0-1.0 remain
available under CC0-1.0.
