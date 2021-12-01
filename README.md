# SPARK-Sheilds
Highly Customizable Dynamic and Static Badge Creator for Profile Readme.Md and Webpages with Github, Wakatime, and Sheilds.io in Dynamic HTML

# Features

- [GitHub Stats Card](#github-stats-card)
- [GitHub Extra Pins](#github-extra-pins)
- [Top Languages Card](#top-languages-card)
- [Wakatime Week Stats](#wakatime-week-stats)
- [Themes](#themes)
- [Customization](#customization)
  - [Common Options](#common-options)
  - [Stats Card Exclusive Options](#stats-card-exclusive-options)
  - [Repo Card Exclusive Options](#repo-card-exclusive-options)
  - [Language Card Exclusive Options](#language-card-exclusive-options)
  - [Wakatime Card Exclusive Option](#wakatime-card-exclusive-options)
- [Deploy Yourself](#deploy-on-your-own-vercel-instance)

# GitHub Stats Card

Copy-paste this into your markdown content, and that's it. Simple!

Change the `?username=` value to your GitHub's username.

```md
[![Anurag's GitHub stats](https://github-readme-stats.vercel.app/api?username=SparkScratch-P)](https://github.com/SparkScratch-P/github-readme-stats)
```

_Note: Available ranks are S+ (top 1%), S (top 25%), A++ (top 45%), A+ (top 60%), and B+ (everyone).
The values are calculated by using the [cumulative distribution function](https://en.wikipedia.org/wiki/Cumulative_distribution_function) using commits, contributions, issues, stars, pull requests, followers, and owned repositories.
The implementation can be investigated at [src/calculateRank.js](./src/calculateRank.js)_

### Hiding individual stats

To hide any specific stats, you can pass a query parameter `?hide=` with comma-separated values.

> Options: `&hide=stars,commits,prs,issues,contribs`

```md
![Anurag's GitHub stats](https://github-readme-stats.vercel.app/api?username=SparkScratch-P&hide=contribs,prs)
```

### Adding private contributions count to total commits count

You can add the count of all your private contributions to the total commits count by using the query parameter `?count_private=true`.

_Note: If you are deploying this project yourself, the private contributions will be counted by default. Otherwise, you need to choose to share your private contribution counts._

> Options: `&count_private=true`

```md
![Anurag's GitHub stats](https://github-readme-stats.vercel.app/api?username=SparkScratch-P&count_private=true)
```

### Showing icons

To enable icons, you can pass `show_icons=true` in the query param, like so:

```md
![Anurag's GitHub stats](https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true)
```


#### All inbuilt themes :-

dark, radical, merko, gruvbox, tokyonight, onedark, cobalt, synthwave, highcontrast, dracula

<img src="https://res.cloudinary.com/SparkScratch-P/image/upload/v1595174536/grs-themes_l4ynja.png" alt="GitHub Readme Stats Themes" width="600px"/>

You can look at a preview for [all available themes](./themes/README.md) or checkout the [theme config file](./themes/index.js) & **you can also contribute new themes** if you like :D

### Customization

You can customize the appearance of your `Stats Card` or `Repo Card` however you wish with URL params.

#### Common Options:

- `title_color` - Card's title color _(hex color)_
- `text_color` - Body text color _(hex color)_
- `icon_color` - Icons color if available _(hex color)_
- `border_color` - Card's border color _(hex color)_. (Does not apply when `hide_border` is enabled)
- `bg_color` - Card's background color _(hex color)_ **or** a gradient in the form of _angle,start,end_
- `hide_border` - Hides the card's border _(boolean)_
- `theme` - name of the theme, choose from [all available themes](./themes/README.md)
- `cache_seconds` - set the cache header manually _(min: 1800, max: 86400)_
- `locale` - set the language in the card _(e.g. cn, de, es, etc.)_
- `border_radius` - Corner rounding on the card_

##### Gradient in bg_color

You can provide multiple comma-separated values in bg_color option to render a gradient, the format of the gradient is :-

```
&bg_color=DEG,COLOR1,COLOR2,COLOR3...COLOR10
```

> Note on cache: Repo cards have a default cache of 4 hours (14400 seconds) if the fork count & star count is less than 1k, otherwise, it's 2 hours (7200 seconds). Also, note that the cache is clamped to a minimum of 2 hours and a maximum of 24 hours.

#### Stats Card Exclusive Options:

- `hide` - Hides the specified items from stats _(Comma-separated values)_
- `hide_title` - _(boolean)_
- `hide_rank` - _(boolean)_ hides the rank and automatically resizes the card width
- `show_icons` - _(boolean)_
- `include_all_commits` - Count total commits instead of just the current year commits _(boolean)_
- `count_private` - Count private commits _(boolean)_
- `line_height` - Sets the line-height between text _(number)_
- `custom_title` - Sets a custom title for the card
- `disable_animations` - Disables all animations in the card _(boolean)_

#### Repo Card Exclusive Options:

- `show_owner` - Show the repo's owner name _(boolean)_

#### Language Card Exclusive Options:

- `hide` - Hide the languages specified from the card _(Comma-separated values)_
- `hide_title` - _(boolean)_
- `layout` - Switch between two available layouts `default` & `compact`
- `card_width` - Set the card's width manually _(number)_
- `langs_count` - Show more languages on the card, between 1-10, defaults to 5 _(number)_
- `exclude_repo` - Exclude specified repositories _(Comma-separated values)_
- `custom_title` - Sets a custom title for the card

> :warning: **Important:**
> Language names should be uri-escaped, as specified in [Percent Encoding](https://en.wikipedia.org/wiki/Percent-encoding)
> (i.e: `c++` should become `c%2B%2B`, `jupyter notebook` should become `jupyter%20notebook`, etc.) You can use
> [urlencoder.org](https://www.urlencoder.org/) to help you do this automatically.

#### Wakatime Card Exclusive Options:

- `hide` - Hide the languages specified from the card _(Comma-separated values)_
- `hide_title` - _(boolean)_
- `line_height` - Sets the line-height between text _(number)_
- `hide_progress` - Hides the progress bar and percentage _(boolean)_
- `custom_title` - Sets a custom title for the card
- `layout` - Switch between two available layouts `default` & `compact`
- `langs_count` - Limit number of languages on the card, defaults to all reported langauges
- `api_domain` - Set a custom API domain for the card, e.g. to use services like [Hakatime](https://github.com/mujx/hakatime) or [Wakapi](https://github.com/muety/wakapi)
- `range` – Request a range different from your WakaTime default, e.g. `last_7_days`. See [WakaTime API docs](https://wakatime.com/developers#stats) for list of available options.

---

# GitHub Extra Pins

GitHub extra pins allow you to pin more than 6 repositories in your profile using a GitHub readme profile.

Yay! You are no longer limited to 6 pinned repositories.

### Usage

Copy-paste this code into your readme and change the links.

Endpoint: `api/pin?username=SparkScratch-P&repo=github-readme-stats`

```md
[![Readme Card](https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats)](https://github.com/SparkScratch-P/github-readme-stats)
```

### Demo

[![Readme Card](https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats)](https://github.com/SparkScratch-P/github-readme-stats)

Use [show_owner](#customization) variable to include the repo's owner username

[![Readme Card](https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&show_owner=true)](https://github.com/SparkScratch-P/github-readme-stats)

# Top Languages Card

The top languages card show a GitHub user's most frequently used top language.

_NOTE: Top Languages does not indicate my skill level or anything like that, it's a GitHub metric of which languages have the most code on GitHub. It's a new feature of github-readme-stats._

### Usage

Copy-paste this code into your readme and change the links.

Endpoint: `api/top-langs?username=SparkScratch-P`

```md
[![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=SparkScratch-P)](https://github.com/SparkScratch-P/github-readme-stats)
```

### Exclude individual repositories

You can use `?exclude_repo=repo1,repo2` parameter to exclude individual repositories.

```md
[![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=SparkScratch-P&exclude_repo=github-readme-stats,SparkScratch-P.github.io)](https://github.com/SparkScratch-P/github-readme-stats)
```

### Hide individual languages

You can use `?hide=language1,language2` parameter to hide individual languages.

```md
[![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=SparkScratch-P&hide=javascript,html)](https://github.com/SparkScratch-P/github-readme-stats)
```

### Show more languages

You can use the `&langs_count=` option to increase or decrease the number of languages shown on the card. Valid values are integers between 1 and 10 (inclusive), and the default is 5.

```md
[![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=SparkScratch-P&langs_count=8)](https://github.com/SparkScratch-P/github-readme-stats)
```

### Compact Language Card Layout

You can use the `&layout=compact` option to change the card design.

```md
[![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=SparkScratch-P&layout=compact)](https://github.com/SparkScratch-P/github-readme-stats)
```

### Demo

[![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=SparkScratch-P)](https://github.com/SparkScratch-P/github-readme-stats)

- Compact layout

[![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=SparkScratch-P&layout=compact)](https://github.com/SparkScratch-P/github-readme-stats)

# Wakatime Week Stats

Change the `?username=` value to your [Wakatime](https://wakatime.com) username.

```md
[![willianrod's wakatime stats](https://github-readme-stats.vercel.app/api/wakatime?username=willianrod)](https://github.com/SparkScratch-P/github-readme-stats)
```

### Demo

[![willianrod's wakatime stats](https://github-readme-stats.vercel.app/api/wakatime?username=willianrod)](https://github.com/SparkScratch-P/github-readme-stats)

[![willianrod's wakatime stats](https://github-readme-stats.vercel.app/api/wakatime?username=willianrod&hide_progress=true)](https://github.com/SparkScratch-P/github-readme-stats)

- Compact layout

[![willianrod's wakatime stats](https://github-readme-stats.vercel.app/api/wakatime?username=willianrod&layout=compact)](https://github.com/SparkScratch-P/github-readme-stats)

---

### All Demos

- Default

![ GitHub stats](https://github-readme-stats.vercel.app/api?username=SparkScratch-P)

- Hiding specific stats

![GitHub stats](https://github-readme-stats.vercel.app/api?username=SparkScratch-P&hide=contribs,issues)

- Showing icons

![GitHub stats](https://github-readme-stats.vercel.app/api?username=SparkScratch-P&hide=issues&show_icons=true)

- Customize Border Color

![ GitHub stats](https://github-readme-stats.vercel.app/api?username=SparkScratch-P&border_color=2e4058)

- Include All Commits

![ GitHub stats](https://github-readme-stats.vercel.app/api?username=SparkScratch-P&include_all_commits=true)

- Themes

Choose from any of the [default themes](#themes)

![ GitHub stats](https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&theme=radical)

- Gradient

![ GitHub stats](https://github-readme-stats.vercel.app/api?username=SparkScratch-P&bg_color=30,e96443,904e95&title_color=fff&text_color=fff)

- Customizing stats card

![ GitHub stats](https://github-readme-stats.vercel.app/api/?username=SparkScratch-P&show_icons=true&title_color=fff&icon_color=79ff97&text_color=9f9f9f&bg_color=151515)

- Setting card locale

![GitHub stats](https://github-readme-stats.vercel.app/api/?username=SparkScratch-P&locale=es)

- Customizing repo card

![Customized Card](https://github-readme-stats.vercel.app/api/pin?username=SparkScratch-P&repo=github-readme-stats&title_color=fff&icon_color=f9f9f9&text_color=9f9f9f&bg_color=151515)

- Top languages

[![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=SparkScratch-P)](https://github.com/SparkScratch-P/github-readme-stats)

- Wakatime card

[![willianrod's wakatime stats](https://github-readme-stats.vercel.app/api/wakatime?username=willianrod)](https://github.com/SparkScratch-P/github-readme-stats)

---

### Quick Tip (Align The Repo Cards)

You usually won't be able to layout the images side by side. To do that you can use this approach:

```html
<a href="https://github.com/SparkScratch-P/github-readme-stats">
  <img align="center" src="https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats" />
</a>
<a href="https://github.com/SparkScratch-P/convoychat">
  <img align="center" src="https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=convoychat" />
</a>
```
---


# Available Themes on Github Stats

<!-- DO NOT EDIT THIS FILE DIRECTLY -->

With inbuilt themes, you can customize the look of the card without doing any manual customization.

Use `?theme=THEME_NAME` parameter like so :-

```md
![GitHub stats](https://github-readme-stats.vercel.app/api?username=SparkScratch-P&theme=dark&show_icons=true)
```

## Stats

> These themes work both for the Stats Card and Repo Card.

| | | |
| :--: | :--: | :--: |
| `default` ![default][default] | `dark` ![dark][dark] | `radical` ![radical][radical] |
| `merko` ![merko][merko] | `gruvbox` ![gruvbox][gruvbox] | `gruvbox_light` ![gruvbox_light][gruvbox_light] |
| `tokyonight` ![tokyonight][tokyonight] | `onedark` ![onedark][onedark] | `cobalt` ![cobalt][cobalt] |
| `synthwave` ![synthwave][synthwave] | `highcontrast` ![highcontrast][highcontrast] | `dracula` ![dracula][dracula] |
| `prussian` ![prussian][prussian] | `monokai` ![monokai][monokai] | `vue` ![vue][vue] |
| `vue-dark` ![vue-dark][vue-dark] | `shades-of-purple` ![shades-of-purple][shades-of-purple] | `nightowl` ![nightowl][nightowl] |
| `buefy` ![buefy][buefy] | `blue-green` ![blue-green][blue-green] | `algolia` ![algolia][algolia] |
| `great-gatsby` ![great-gatsby][great-gatsby] | `darcula` ![darcula][darcula] | `bear` ![bear][bear] |
| `solarized-dark` ![solarized-dark][solarized-dark] | `solarized-light` ![solarized-light][solarized-light] | `chartreuse-dark` ![chartreuse-dark][chartreuse-dark] |
| `nord` ![nord][nord] | `gotham` ![gotham][gotham] | `material-palenight` ![material-palenight][material-palenight] |
| `graywhite` ![graywhite][graywhite] | `vision-friendly-dark` ![vision-friendly-dark][vision-friendly-dark] | `ayu-mirage` ![ayu-mirage][ayu-mirage] |
| `midnight-purple` ![midnight-purple][midnight-purple] | `calm` ![calm][calm] | `flag-india` ![flag-india][flag-india] |
| `omni` ![omni][omni] | `react` ![react][react] | `jolly` ![jolly][jolly] |
| `maroongold` ![maroongold][maroongold] | `yeblu` ![yeblu][yeblu] | `blueberry` ![blueberry][blueberry] |
| `slateorange` ![slateorange][slateorange] | `kacho_ga` ![kacho_ga][kacho_ga] | `outrun` ![outrun][outrun] |
| `ocean_dark` ![ocean_dark][ocean_dark] | `city_lights` ![city_lights][city_lights] | `github_dark` ![github_dark][github_dark] |
| `discord_old_blurple` ![discord_old_blurple][discord_old_blurple] | `aura_dark` ![aura_dark][aura_dark] | `panda` ![panda][panda] |
| `noctis_minimus` ![noctis_minimus][noctis_minimus] | `cobalt2` ![cobalt2][cobalt2] | `swift` ![swift][swift] |
| `aura` ![aura][aura] |  | [Add your theme][add-theme] |

## Repo Card

> These themes work both for the Stats Card and Repo Card.

| | | |
| :--: | :--: | :--: |
| `default_repocard` ![default_repocard][default_repocard_repo] | `dark` ![dark][dark_repo] | `radical` ![radical][radical_repo] |
| `merko` ![merko][merko_repo] | `gruvbox` ![gruvbox][gruvbox_repo] | `gruvbox_light` ![gruvbox_light][gruvbox_light_repo] |
| `tokyonight` ![tokyonight][tokyonight_repo] | `onedark` ![onedark][onedark_repo] | `cobalt` ![cobalt][cobalt_repo] |
| `synthwave` ![synthwave][synthwave_repo] | `highcontrast` ![highcontrast][highcontrast_repo] | `dracula` ![dracula][dracula_repo] |
| `prussian` ![prussian][prussian_repo] | `monokai` ![monokai][monokai_repo] | `vue` ![vue][vue_repo] |
| `vue-dark` ![vue-dark][vue-dark_repo] | `shades-of-purple` ![shades-of-purple][shades-of-purple_repo] | `nightowl` ![nightowl][nightowl_repo] |
| `buefy` ![buefy][buefy_repo] | `blue-green` ![blue-green][blue-green_repo] | `algolia` ![algolia][algolia_repo] |
| `great-gatsby` ![great-gatsby][great-gatsby_repo] | `darcula` ![darcula][darcula_repo] | `bear` ![bear][bear_repo] |
| `solarized-dark` ![solarized-dark][solarized-dark_repo] | `solarized-light` ![solarized-light][solarized-light_repo] | `chartreuse-dark` ![chartreuse-dark][chartreuse-dark_repo] |
| `nord` ![nord][nord_repo] | `gotham` ![gotham][gotham_repo] | `material-palenight` ![material-palenight][material-palenight_repo] |
| `graywhite` ![graywhite][graywhite_repo] | `vision-friendly-dark` ![vision-friendly-dark][vision-friendly-dark_repo] | `ayu-mirage` ![ayu-mirage][ayu-mirage_repo] |
| `midnight-purple` ![midnight-purple][midnight-purple_repo] | `calm` ![calm][calm_repo] | `flag-india` ![flag-india][flag-india_repo] |
| `omni` ![omni][omni_repo] | `react` ![react][react_repo] | `jolly` ![jolly][jolly_repo] |
| `maroongold` ![maroongold][maroongold_repo] | `yeblu` ![yeblu][yeblu_repo] | `blueberry` ![blueberry][blueberry_repo] |
| `slateorange` ![slateorange][slateorange_repo] | `kacho_ga` ![kacho_ga][kacho_ga_repo] | `outrun` ![outrun][outrun_repo] |
| `ocean_dark` ![ocean_dark][ocean_dark_repo] | `city_lights` ![city_lights][city_lights_repo] | `github_dark` ![github_dark][github_dark_repo] |
| `discord_old_blurple` ![discord_old_blurple][discord_old_blurple_repo] | `aura_dark` ![aura_dark][aura_dark_repo] | `panda` ![panda][panda_repo] |
| `noctis_minimus` ![noctis_minimus][noctis_minimus_repo] | `cobalt2` ![cobalt2][cobalt2_repo] | `swift` ![swift][swift_repo] |
| `aura` ![aura][aura_repo] |  | [Add your theme][add-theme] |


[default]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=default
[default_repocard]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=default_repocard
[dark]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=dark
[radical]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=radical
[merko]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=merko
[gruvbox]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=gruvbox
[gruvbox_light]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=gruvbox_light
[tokyonight]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=tokyonight
[onedark]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=onedark
[cobalt]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=cobalt
[synthwave]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=synthwave
[highcontrast]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=highcontrast
[dracula]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=dracula
[prussian]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=prussian
[monokai]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=monokai
[vue]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=vue
[vue-dark]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=vue-dark
[shades-of-purple]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=shades-of-purple
[nightowl]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=nightowl
[buefy]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=buefy
[blue-green]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=blue-green
[algolia]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=algolia
[great-gatsby]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=great-gatsby
[darcula]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=darcula
[bear]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=bear
[solarized-dark]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=solarized-dark
[solarized-light]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=solarized-light
[chartreuse-dark]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=chartreuse-dark
[nord]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=nord
[gotham]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=gotham
[material-palenight]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=material-palenight
[graywhite]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=graywhite
[vision-friendly-dark]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=vision-friendly-dark
[ayu-mirage]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=ayu-mirage
[midnight-purple]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=midnight-purple
[calm]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=calm
[flag-india]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=flag-india
[omni]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=omni
[react]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=react
[jolly]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=jolly
[maroongold]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=maroongold
[yeblu]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=yeblu
[blueberry]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=blueberry
[slateorange]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=slateorange
[kacho_ga]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=kacho_ga
[outrun]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=outrun
[ocean_dark]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=ocean_dark
[city_lights]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=city_lights
[github_dark]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=github_dark
[discord_old_blurple]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=discord_old_blurple
[aura_dark]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=aura_dark
[panda]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=panda
[noctis_minimus]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=noctis_minimus
[cobalt2]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=cobalt2
[swift]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=swift
[aura]: https://github-readme-stats.vercel.app/api?username=SparkScratch-P&show_icons=true&hide=contribs,prs&cache_seconds=86400&theme=aura


[default_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=default
[default_repocard_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=default_repocard
[dark_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=dark
[radical_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=radical
[merko_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=merko
[gruvbox_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=gruvbox
[gruvbox_light_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=gruvbox_light
[tokyonight_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=tokyonight
[onedark_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=onedark
[cobalt_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=cobalt
[synthwave_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=synthwave
[highcontrast_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=highcontrast
[dracula_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=dracula
[prussian_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=prussian
[monokai_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=monokai
[vue_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=vue
[vue-dark_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=vue-dark
[shades-of-purple_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=shades-of-purple
[nightowl_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=nightowl
[buefy_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=buefy
[blue-green_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=blue-green
[algolia_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=algolia
[great-gatsby_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=great-gatsby
[darcula_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=darcula
[bear_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=bear
[solarized-dark_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=solarized-dark
[solarized-light_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=solarized-light
[chartreuse-dark_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=chartreuse-dark
[nord_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=nord
[gotham_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=gotham
[material-palenight_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=material-palenight
[graywhite_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=graywhite
[vision-friendly-dark_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=vision-friendly-dark
[ayu-mirage_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=ayu-mirage
[midnight-purple_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=midnight-purple
[calm_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=calm
[flag-india_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=flag-india
[omni_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=omni
[react_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=react
[jolly_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=jolly
[maroongold_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=maroongold
[yeblu_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=yeblu
[blueberry_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=blueberry
[slateorange_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=slateorange
[kacho_ga_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=kacho_ga
[outrun_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=outrun
[ocean_dark_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=ocean_dark
[city_lights_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=city_lights
[github_dark_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=github_dark
[discord_old_blurple_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=discord_old_blurple
[aura_dark_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=aura_dark
[panda_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=panda
[noctis_minimus_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=noctis_minimus
[cobalt2_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=cobalt2
[swift_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=swift
[aura_repo]: https://github-readme-stats.vercel.app/api/pin/?username=SparkScratch-P&repo=github-readme-stats&cache_seconds=86400&theme=aura


[add-theme]: https://github.com/SparkScratch-P/github-readme-stats/edit/master/themes/index.js

Want to add a new theme? Consider reading the [contribution guidelines](../CONTRIBUTING.md#themes-contribution) :D
