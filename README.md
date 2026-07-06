# Year Progress

Track how far you are through the year on a [TRMNL](https://usetrmnl.com/) device — as a progress bar or a dot calendar (one dot per day, one row per month).

![Dots — light](trmnl-yearinprogress-dots-light.png)
*Dots (light)*

![Bar — light](trmnl-yearinprogress-bar-light.png)
*Bar (light)*

![Dots — dark](trmnl-yearinprogress-dots-dark.png)
*Dots (dark)*

![Bar — dark](trmnl-yearinprogress-bar-dark.png)
*Bar (dark)*

## Features

- **Bar** or **Dots** — choose in plugin settings
- **Light** or **Dark** — choose in plugin theme settings
- **Full**, **Half horizontal**, **Half vertical**, and **Quadrant** mashups
- Compact dot layout on smaller views (quadrant, half horizontal)
- **Static** plugin — no API, no account data; uses TRMNL date & timezone
- Refreshes once per day

## Install

### Recommended — TRMNL Recipe (one click)

<!-- Replace with your Recipe URL after publication -->
**[Install Year Progress on TRMNL →](https://trmnl.com/recipes/YOUR_RECIPE_ID)**

1. Click **Install**
2. Choose **Bar** or **Dots** under **Appearence**
3. Add the plugin to your playlist

Installed recipes receive automatic updates when the author pushes changes.

### Alternative — Import ZIP

For manual install (no Recipe link, generic plugin icon):

1. Download a release ZIP or export from TRMNL (**Export** on plugin settings)
2. Open [Private Plugin settings](https://usetrmnl.com/plugin_settings?keyname=private_plugin) → **Import new**
3. Choose **Bar** or **Dots** → Save → add to playlist

### Developers — Clone this repo

```sh
git clone https://github.com/monsieurm/trmnl-yearinprogress.git
cd trmnl-yearinprogress
./bin/trmnlp login
./bin/trmnlp pull    # if linking an existing plugin on your account
# or
./bin/trmnlp push    # to create / update your plugin