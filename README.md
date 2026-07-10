# L4D2 Cheater Watch

A static, searchable case-file board for tracking reported cheaters in Left 4 Dead 2.

## What's in here

- `index.html` — the page itself (search, filters, everything)
- `data.json` — the actual list of cases. This is the only file you'll usually need to edit.

## Putting it on GitHub Pages

1. Create a new GitHub repository (public, since Pages needs a paid plan for private repo hosting).
2. Upload `index.html` and `data.json` to the root of the repo.
3. Go to the repo's **Settings → Pages**.
4. Under "Build and deployment", set Source to **Deploy from a branch**, branch `main`, folder `/ (root)`.
5. Save. GitHub will give you a URL like `https://yourusername.github.io/repo-name/` within a minute or two.

That's it — no build step, no dependencies.

## Adding a new cheater to the list

Open `data.json` and add a new object to the array, following this shape:

```json
{
  "case_id": "CASE-0004",
  "ign": "their in-game name",
  "steam_id": "STEAM_0:1:xxxxxxxxx",
  "profile_url": "https://steamcommunity.com/profiles/765611980000000xx",
  "cheat_type": "Aimbot",
  "status": "confirmed",
  "date_reported": "2026-07-10",
  "evidence_url": "https://link-to-clip-or-demo"
}
```

Notes on the fields:

- **case_id** — just an incrementing label (`CASE-0001`, `CASE-0002`, ...), used as a file reference.
- **status** — only two values matter: `"confirmed"` (you have solid evidence) or `"suspected"` (reported but not fully verified). The page renders each with a different colored stamp.
- **cheat_type** — free text (`"Aimbot"`, `"Wallhack"`, `"Speedhack"`, etc.). Whatever values you use will automatically show up in the filter dropdown.
- **evidence_url** — link to a clip, demo file, or screenshot host. Leave as `""` if you don't have one yet, but try to always attach one for confirmed cases — it's what makes the list defensible if someone disputes an entry.

You can edit `data.json` directly on GitHub.com (click the file, click the pencil icon, edit, commit) — no local setup needed. The site updates automatically the next time someone loads the page.

## A couple of things worth keeping in mind

- Stick to public in-game identifiers (Steam ID, in-game name) rather than real names or other personal details.
- Keep the "confirmed vs suspected" distinction honest — it's what separates a documented report from an unverified accusation.
- Consider adding a contact method (Discord invite, email) somewhere on the page for people who want to dispute an entry.
