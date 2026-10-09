# Melofy landing page

The public site for [Melofy](https://apps.apple.com/app/id6796313543), a music quiz
game: hear a few seconds of a song, pick the answer before the clock runs out.

**Live:** https://melofy.trust-software.com/

A single static page: `index.html` (markup, styles and script in one file), the
Tuffy font in `fonts/`, and Caveat from Google Fonts. There is no build step.

## Preview locally

Open `index.html` in a browser. Everything works from disk except the GitHub avatar in
the footer, which loads from github.com.

## Deploy

The site is the `melofy-landing` Cloudflare Worker (static assets, no build step), served
at melofy.trust-software.com. `wrangler.jsonc` describes it, and `.assetsignore` lists the
repo files that are not published.

- **Automatic:** `.github/workflows/deploy.yml` deploys every time a pull request is merged
  into `main`. It needs the `CLOUDFLARE_API_TOKEN` and `CLOUDFLARE_ACCOUNT_ID` repository
  secrets.
- **On demand, through GitHub:** `gh workflow run deploy.yml` deploys the current `main`.
- **On demand, from your machine:** `npm run deploy` deploys the working tree. Run
  `npx wrangler login` once first.

GitHub Pages still serves the same files at the old address,
hakanarda.github.io/melofy-landing; the canonical tag points search engines here.

## Keeping the page current

The page must describe the app as it ships. Whenever a user-facing feature is added,
changed or removed in the app, update the matching section here in the same piece of
work. Each section and the app feature it describes:

| Section (`id`) | App feature |
|---|---|
| Hero demo (`#top`) | The core round: clip, four answers, 10-second clock, time bonus |
| `#how` | One question, step by step: listen, pick, reveal |
| `#modes` | The five game modes: song, artist, year, album, country |
| `#solo` | Blitz, Endless and Survival solo runs, genre picker |
| `#daily` | Daily challenge: one try, streaks, freezes, its leaderboard |
| `#friends` | Challenges (1 on 1, groups, codes), Ranks, levels and badges |
| `#music` | Catalogue: playlists, countries, Eurovision, World Cup, artist search, Mixed Play |
| `#account` | What guests and free accounts get, sign-in options |
| `#notes` | Settings and policies: explicit filter, keep playing, notifications, renames, fair scoring, account deletion |
| `#download` | Store badges |

Copy rules:

- Don't publish scoring numbers. Say that faster right answers earn a bigger bonus.
- Only describe features that are live in the store build.
- The Google Play badges are disabled buttons with a "Coming soon" tooltip. When the
  Android listing is live, turn both back into links to
  `https://play.google.com/store/apps/details?id=com.trustsoftware.melofy` and change
  "Free on iPhone. Android is coming soon." back to "Free on iPhone and Android."

## Credits

Written, designed and produced by [HakanArda](https://github.com/HakanArda).
Music previews and artwork in the app are provided by Deezer. The melodies in the demo
are public-domain works synthesised in the browser.
