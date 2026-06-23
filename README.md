# bluuhub-songs

Store for BluuHub Piano community songs + hosted midi2lua scripts.

- `pending/` — submitted songs awaiting review (NOT live)
- `approved/` — approved songs (rename pending file here to approve)
- `index.json` — built live manifest (GitHub Action), fetched by piano-ui.lua
- `scripts/` — hosted .txt for loadstring links

Data is structured note-data (JSON), never executable Lua.