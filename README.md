# Colormap
**Interactive Travel Maps for Micro.blog**

---

## Overview

Colormap is a shortcode plugin for Micro.blog that lets you embed interactive, clickable maps directly into your posts and pages. Highlight the places you've visited, add personal notes and links, and display a visual tile grid — all with a simple tag in your post.

Each map can show colored regions, a tile grid of visited places, clickable popups with notes and links, an optional legend, and a progress tracker. Multiple independent maps can appear on a single page.

---

## Quick Start

Drop the shortcode into any post to display a default US states map:

```
{{< colormap >}}
```

To use a different map or data file, add parameters:

```
{{< colormap map="europe" data="my-trips" >}}
{{< colormap map="canada" color="#c0612b" progress="yes" >}}
```

---

## Parameters

Add parameters inside the shortcode tag as `key="value"` pairs. `data` is required; all others are optional.

| Parameter | Default | Description |
|-----------|---------|-------------|
| `data` | — | **Required.** Name of your data file in `data/colormaps/` (without the `.yaml` extension). |
| `map` | `us-states` | Which SVG map to render. See [Available Maps](#available-maps) for all options. |
| `color` | `#4a7c59` | Default fill color for visited regions. Individual entries in your data file can override this per region. |
| `emptycolor` | *(none)* | Fill color for unvisited regions and empty tiles. Leave blank to use the map's default style. |
| `legend` | *(none)* | Name of a legend data file in `data/colormaps/`. Legend tiles appear at the start of the tile grid. |
| `progress` | off | Set to `"yes"` to show a progress tile (e.g. `14 / 50 · 28%`) at the end of the tile grid. |
| `grid` | on | Set to `"no"` to hide the tile grid and popups. Only the SVG map is rendered. |
| `tiles` | key | Set to `"name"` to show full region names on tiles instead of abbreviations. Useful for continent maps. |

---

## Available Maps

Use the value below as the `map` parameter.

### State & Province-Level Maps

| Value | Regions | Keys |
|-------|---------|------|
| `us-states` | 50 US states | Two-letter USPS codes: `al`, `ak`, `az`, … |
| `us-territories` | 56 (50 states + DC + 5 territories) | All `us-states` keys plus `as`, `gu`, `mp`, `pr`, `vi` |
| `canada` | 13 provinces & territories | `ab`, `bc`, `mb`, `nb`, `nl`, `ns`, `nt`, `nu`, `on`, `pe`, `qc`, `sk`, `yt` |
| `australia-states` | 8 states & territories | `act`, `nsw`, `nt`, `qld`, `sa`, `tas`, `vic`, `wa` |
| `france-regions` | 18 regions | ISO 3166-2 FR codes |
| `canada-detailed` | 13 provinces & territories (higher resolution) | Same keys as `canada` — note: slower to load |

### Regional Country Maps

| Value | Regions | Keys |
|-------|---------|------|
| `central-america` | 7 countries | `bz`, `cr`, `gt`, `hn`, `ni`, `pa`, `sv` |
| `caribbean` | 13 sovereign nations | `ag`, `bb`, `bs`, `cu`, `dm`, `do`, `gd`, `ht`, `jm`, `kn`, `lc`, `tt`, `vc` |
| `caribbean-territories` | Caribbean territories only | `ai`, `aw`, `bl`, `cw`, `mf`, `ms`, `pr`, `sx`, `tc`, `vg`, `vi` |
| `caribbean-all` | 24 (sovereigns + territories) | `ag`, `ai`, `aw`, `bb`, `bl`, `bs`, `cu`, `cw`, `dm`, `do`, `gd`, `ht`, `jm`, `kn`, `lc`, `mf`, `ms`, `pr`, `sx`, `tc`, `tt`, `vc`, `vg`, `vi` |

### Continental Maps

| Value | Regions | Keys |
|-------|---------|------|
| `north-america` | 23 countries | `ag`, `bb`, `bs`, `bz`, `ca`, `cr`, `cu`, `dm`, `do`, `gd`, `gt`, `hn`, `ht`, `jm`, `kn`, `lc`, `mx`, `ni`, `pa`, `sv`, `tt`, `us`, `vc` |
| `south-america` | 12 countries | `ar`, `bo`, `br`, `cl`, `co`, `ec`, `gy`, `pe`, `py`, `sr`, `uy`, `ve` |
| `europe` | 48 countries | `ad`, `al`, `at`, `ba`, `be`, `bg`, `by`, `ch`, `cz`, `de`, `dk`, `ee`, `es`, `fi`, `fo`, `fr`, `gb`, `gg`, `gr`, `hr`, `hu`, `ie`, `im`, `is`, `it`, `je`, `li`, `lt`, `lu`, `lv`, `mc`, `md`, `me`, `mk`, `mt`, `nl`, `no`, `pl`, `pt`, `ro`, `rs`, `se`, `si`, `sk`, `sm`, `ua`, `va`, `xk` |
| `europe-detail` | 48 countries (higher detail) | Same keys as `europe` except `gi` instead of `gb`. Richer coastline and border detail. |
| `africa` | 53 countries | `ao`, `bf`, `bi`, `bj`, `bw`, `cd`, `cf`, `cg`, `ci`, `cm`, `cv`, `dj`, `dz`, `eg`, `eh`, `er`, `et`, `ga`, `gh`, `gm`, `gn`, `gq`, `gw`, `ke`, `km`, `lr`, `ls`, `ly`, `ma`, `mg`, `ml`, `mr`, `mw`, `mz`, `na`, `ne`, `ng`, `rw`, `sd`, `sl`, `sn`, `so`, `ss`, `st`, `sz`, `td`, `tg`, `tn`, `tz`, `ug`, `za`, `zm`, `zw` |
| `asia` | 49 countries | `ae`, `af`, `am`, `az`, `bd`, `bh`, `bn`, `bt`, `cn`, `cy`, `ge`, `hk`, `id`, `il`, `in`, `iq`, `ir`, `jo`, `jp`, `kg`, `kh`, `kp`, `kr`, `kw`, `kz`, `la`, `lb`, `lk`, `mm`, `mn`, `mo`, `my`, `np`, `om`, `ph`, `pk`, `ps`, `qa`, `sa`, `sg`, `sy`, `tj`, `tl`, `tm`, `tr`, `tw`, `uz`, `vn`, `ye` |
| `oceania` | 14 sovereign nations | `au`, `fj`, `fm`, `ki`, `mh`, `nr`, `nz`, `pg`, `pw`, `sb`, `to`, `tv`, `vu`, `ws` |

### World Map

| Value | Regions | Keys |
|-------|---------|------|
| `world` | 7 continents | `af` Africa, `an` Antarctica, `as` Asia, `eu` Europe, `na` North America, `oc` Oceania, `sa` South America. Russia is assigned to Asia. Winkel Tripel projection. |

> **Need a map we don't offer?** Additional maps may be added in future releases depending on SVG availability and quality. Feel free to reach out with requests.

---

## Your Data File

The data file is where you list the regions you've visited. Place it at:

```
data/colormaps/colormap.yaml
```

Each entry corresponds to one region on the map. Only regions you list will be colored in — everything else stays unvisited.

### Format

```yaml
- key: or
  note: Drove the coast in 2019.
  url: https://myblog.com/posts/oregon

- key: mt
  color: "#c0612b"
  note: Glacier NP.

- key: ny
```

### Fields

| Field | Required? | Description |
|-------|-----------|-------------|
| `key` | **Yes** | The region's abbreviation (lowercase). For US states: `or`, `ca`, `ny`. For countries, use the standard two-letter code. |
| `note` | No | A short note shown in the popup when a visitor clicks the region or tile. |
| `url` | No | A link shown in the popup. Visitors can click it to go to a related post or page. |
| `color` | No | A hex color code to override the default color for just this region. Example: `"#c0612b"` |
| `name` | No | Override the display name shown in popups and tiles. Useful for custom or add-on maps. |

---

## Adding a Legend

A legend lets visitors understand what different colors mean on your map. Legend entries appear as tiles at the start of the tile grid. Clicking a legend tile highlights all matching regions on the map and lists them in a popup.

Create a legend file (for example, `data/colormaps/colormap-legend.yaml`) and reference it with the `legend` parameter:

```
{{< colormap legend="colormap-legend" >}}
```

### Legend File Format

```yaml
- label: Visited
  color: "#4a7c59"
  note: Places I've spent meaningful time.
  url: /travel

- label: Lived there
  color: "#c0612b"
  note: Called it home for at least a year.
```

The color in each legend entry must match the color used for the corresponding regions in your data file. That's how Colormap knows which regions belong to which legend category.

---

## Progress Tracker

Add `progress="yes"` to display a progress tile at the end of the grid. It shows how many regions you've visited out of the total on that map, plus a percentage.

```
{{< colormap progress="yes" >}}
```

Example output: `14 / 50 · 28% Complete`

> **Note:** Only regions whose keys exist on the chosen map are counted. Custom or unrecognized keys in your data file won't inflate the total.

---

## Multiple Maps on One Page

You can place as many colormap shortcodes as you like on a single page. Each map is fully independent — separate data files, separate colors, and separate tile grids. The page's CSS and JavaScript are only loaded once regardless of how many maps appear.

```
{{< colormap map="us-states" data="road-trips" color="#4a7c59" progress="yes" >}}

{{< colormap map="europe" data="europe-trips" color="#2E6DA4" >}}
```

---

## Map-Only Mode

If you only want the visual map without the tile grid and popups, set `grid="no"`:

```
{{< colormap grid="no" >}}
```

In this mode, visited regions are still colored on the map. However, the tile grid, legend, progress tracker, and click interactions are all hidden.

---

## RSS & Accessibility

### RSS Readers

When your post is viewed in an RSS reader, the interactive map cannot be displayed. A fallback caption is shown automatically: *[Interactive map — visit the original post to explore it.]* This caption is hidden in normal browser views.

### JavaScript

The tile grid and popup interactions require JavaScript. If a visitor has JavaScript disabled, a note is shown in place of the grid: *"This map requires JavaScript — tiles and popups are unavailable without it."* The SVG map itself still renders.

### Accessibility

All interactive tiles are rendered as buttons with `aria-label` attributes. Popups include ARIA dialog roles. The SVG map is marked `aria-hidden` since the tile grid provides the accessible equivalent.

---

## Examples

### Simple US States Map

```
{{< colormap >}}
```

Renders the default US states map using `data/colormaps/colormap.yaml` with the default green fill.

### States Hiked with Progress Tracker

```
{{< colormap map="us-states" data="hikes" color="#8B5E3C" progress="yes" >}}
```

Tracks states where you've hiked using a dedicated data file, with a brown fill and a progress tile showing how many you've covered.

### Europe Map with Legend

```
{{< colormap map="europe" data="europe-visits" legend="europe-legend" tiles="name" >}}
```

Shows a Europe map with full country names on tiles (instead of abbreviations) and a legend.

### Map Only — No Grid

```
{{< colormap map="world" data="world-trips" grid="no" >}}
```

Displays just the world map SVG with colored regions, no tile grid or popups.

---

## Disputed Territories

Some maps include territories whose sovereignty is disputed. The plugin handles these pragmatically: a territory is included as a full key if it is a widely recognized travel destination with its own entry and exit infrastructure, regardless of UN membership status.

**Europe map — Kosovo (`xk`)**

Kosovo has been independent since 2008 and issues its own passports. It is included as a full key in the Europe map: it appears in the tile grid, counts toward the progress denominator (48 total), and highlights on the SVG map when visited. On the SVG, Kosovo's border is rendered as a dashed line over Serbia's territory, reflecting its disputed status visually without the plugin taking a political position. Serbia (`rs`) is also fully present and independently colorable — coloring Serbia does not affect Kosovo, and vice versa.

If you prefer not to count Kosovo, simply omit `xk` from your data file. It will appear as an unvisited tile and will not affect your visited count.

---

## File & Folder Summary

| Path | What goes here |
|------|----------------|
| `data/colormaps/colormap.yaml` | Your default visited-regions data file |
| `data/colormaps/<n>.yaml` | Additional named data files |
| `data/colormaps/<n>-legend.yaml` | Legend files |

---

*Colormap — Shortcode Plugin for Micro.blog*
