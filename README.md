# trmnl-yearinprogress

Track how far you are through the year on a [TRMNL](https://usetrmnl.com/) device — as a progress bar or a dot calendar (one dot per day).

![dots option](trmnl-yearinprogress-dots-light.png)
*Dots light view*

![bar option](trmnl-yearinprogress-bar-light.png)
*Bar light view*

![dots option](trmnl-yearinprogress-dots-dark.png)
*Dots dark view*

![bar option](trmnl-yearinprogress-bar-dark.png)
*Bar dark view*

## Install

### Option A — Recipe (recommended)

Once published, install in one click from the TRMNL Recipes page. See [Publish as a Recipe](#publish-as-a-recipe) below.

### Option B — Import ZIP

1. Download or build a ZIP with the flat file layout (see [Project structure](#project-structure)).
2. Open [Private Plugin settings](https://usetrmnl.com/plugin_settings?keyname=private_plugin) → **Import new**.
3. Choose **Bar** or **Dots** under Appearence → Save.
4. Choose **Light** or **Dark** thme mode.
4. Add the plugin to your playlist.

### Option C — Clone from TRMNL (if you already have it installed)

```sh
gem install trmnl_preview   # or use Docker via ./bin/trmnlp
trmnlp login
trmnlp clone trmnl-yearinprogress <plugin-id>
```

## Local development

This project uses [trmnlp](https://github.com/usetrmnl/trmnlp) for local preview and deployment.

**Prerequisites:** Ruby ≥ 3.4 (`gem install trmnl_preview`) or Docker.

```sh
./bin/trmnlp serve          # preview at http://localhost:4567
./bin/trmnlp lint           # check TRMNL best practices
./bin/trmnlp login          # authenticate with TRMNL (one-time)
./bin/trmnlp push           # upload to your TRMNL account
```

Toggle the appearance in `.trmnlp.yml` under `custom_fields.appearence` (`Bar` or `Dots`) to preview both modes locally.

### Deploy from GitHub

1. Run `trmnlp login` locally, then `trmnlp pull` to add your plugin `id` to `src/settings.yml`.
2. Commit the updated `src/settings.yml` (contains only the numeric plugin id).
3. Add your TRMNL API key as a GitHub repository secret named `TRMNL_API_KEY`.
4. Push to `main` — the workflow lints on PRs and runs `trmnlp push` on merge.

## Project structure

```
.
├── .github/workflows/trmnl.yml   # CI: lint + deploy
├── .trmnlp.yml                   # local dev config (not uploaded)
├── bin/trmnlp                    # gem or Docker wrapper
└── src/
    ├── settings.yml              # plugin config (uploaded to TRMNL)
    ├── shared.liquid             # JS logic (prepended to every view)
    ├── full.liquid               # full screen (800×480)
    ├── half_horizontal.liquid    # top/bottom half
    ├── half_vertical.liquid      # left/right half
    └── quadrant.liquid           # one quarter (2×2 mashup)
```

The plugin uses a **static** strategy — no external API. Date and timezone come from TRMNL (`trmnl.system.timestamp_utc`, `trmnl.user.utc_offset`). It refreshes once per day (`refresh_interval: 1440`).

## Publish as a Recipe

To share the plugin with other TRMNL users via one-click install:

1. **Push the plugin** to your TRMNL account (`trmnlp push` or import ZIP).
2. **Verify the preview** — generate a screen with both Bar and Dots settings; the Recipe thumbnail uses your latest render.
3. Open the plugin settings → click **Publish plugin?**
4. Start with **Unlisted** to get a shareable link without full marketplace review, or submit as **Public** for listing on [trmnl.com/recipes](https://trmnl.com/recipes).
5. Link the Recipe URL in this README once approved.

After publication, you become the **Recipe Master**: updates pushed to your master instance propagate to users who chose **Install** (not Fork).

## License

MIT — use and adapt freely.
