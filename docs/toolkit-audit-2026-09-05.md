# Toolkit audit — 5 September 2026

The original review had no named migration finding. This audit labels the
remaining direct embedded content parses in `mytherra-core/src/data.rs` while
retaining typed validation and the existing toolkit registries.

The client uses toolkit HttpClient/Pending, events, notifications and shared UI
widgets with logical-coordinate input. Core uses shared data loading, RNG and
achievements. Save schema conversion stays in core. Protocol owns typed network
messages; server authority and the SQL-backed world/player stores remain
game-specific. Their serde conversions reconstruct domain rows and are not
duplicate file-loading infrastructure.

No production local word-wrap loop, audio bank or generic filesystem JSON
loader was found in the inspected client/core/server sources. All five crates
are included in workspace validation rather than checking the client alone.

Final validation: 360 passing workspace checks, three existing live-server
tests ignored; formatting, strict workspace all-target/all-feature Clippy
and Rust source-size limits pass. Default `publish.ps1` passed Windows/WebGL
client release builds, Preview deployment and Project Roost tracking. The
server and persistence crates were compiled and tested; no live database or
server integration result is claimed.
