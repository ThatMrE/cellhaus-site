# CellHaus Accelerator site

Draft website for CellHaus Cohort 2 (Kobe, 2027). Static HTML on Netlify.

Draft: https://cellhaus-draft.netlify.app (Netlify project `cellhaus-draft`, team `er-creates`). Not indexed by search engines.

## Use with Claude Code

1. Unzip this folder and open it in Claude Code.
2. Say: "Read CLAUDE.md and deploy a new draft site to Netlify."
3. Claude Code creates the site in the `er-creates` team, runs a draft deploy and gives you the URL.

## Run it yourself

```
npm run dev            # local preview with Netlify Forms emulation
npm run deploy:draft   # draft URL, not live
npm run deploy:prod    # live (only at launch)
```

After the first deploy, turn on form detection in Netlify (Site configuration › Forms) and redeploy, so applications arrive.
