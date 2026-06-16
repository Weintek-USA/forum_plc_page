# Weintek HMI Driver Index

A fast, searchable rebuild of the WeintekUSA [Supported Devices](https://forum.weintekusa.com/pub/supported-devices) page. Type a PLC model (e.g. `CompactLogix`, `FX5U`, `S7-1200`) and instantly find the recommended EasyBuilder Pro driver and its connection guide PDF.

**Features**

- Live search across driver names, PLC models, and manufacturers (matches are highlighted)
- Autocomplete with keyboard navigation (↑/↓, Enter, Tab to accept top suggestion)
- Forgiving matching: `S7 1200`, `S7-1200`, and `S71200` all work; shorthand like `AB` (Allen-Bradley), `CLX` (ControlLogix), and `EIP` (EtherNet/IP) is understood
- ★ "Common pick" badges flag the typical starting driver when one PLC family matches several
- Shareable URLs — search and filter state lives in the hash (e.g. `…/index.html#q=fx5u&conn=eth`), so any filtered view can be linked from a forum post or email
- Filter by manufacturer or connection type (Ethernet, Serial, USB, CAN bus)
- 220 drivers from 45 manufacturers, with direct links to the official PDFs on `dl.weintek.com`
- Optional per-driver "Broken link?" reporting that opens a pre-filled GitHub issue
- Single `index.html` file — no build step, no dependencies, works on GitHub Pages
- Press `/` to jump to the search box

## Host it on GitHub Pages

1. Create a new repository on GitHub (e.g. `weintek-driver-index`).
2. Upload `index.html` (and this `README.md`) to the repository root.
3. **Enable broken-link reporting (optional):** in `index.html`, find the line `const REPO_URL = "https://github.com/USERNAME/REPOSITORY";` near the top of the script and replace it with your repo's URL. Until you do, the "Broken link?" links stay hidden.
4. Go to **Settings → Pages**, set **Source** to *Deploy from a branch*, choose the `main` branch and `/ (root)` folder, then save.
5. After a minute, your site will be live at `https://<your-username>.github.io/weintek-driver-index/`.

## Updating the data

All driver data lives in the `DRIVERS` array near the top of the `<script>` block in `index.html`. Each row is:

```js
["Manufacturer", "Driver name", "PDF_filename.pdf", "Supported / recommended PLC models", "Optional note"]
```

PDF filenames are resolved against `https://dl.weintek.com/public/PLC_Connect_Guide/`.

## Disclaimer

Unofficial project, not affiliated with Weintek. Less-common vendors are omitted from the source list — use the official [Device Driver Search](https://www.weintek.com/globalw/Software/PLC.htm) for the complete catalog.