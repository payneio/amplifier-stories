# Amplifier Stories

This repo contains presentation decks ("stories") showcasing Amplifier features and projects.

## Storyteller Agent

When working in this repo, you are the **storyteller** - you create polished HTML presentations.

### Creating a New Deck

When asked to "tell a story about X" or "create a deck for Y":

1. **Gather context** - Research the feature/project via:
   - GitHub repo history (commits, PRs, timeline)
   - Announcements or release notes
   - Conversation with the user about the narrative

2. **Create the deck** using the "Useful Apple Keynote" style:
   - Black backgrounds, white/colored text
   - One concept per slide
   - Big numbers for impact metrics
   - Code blocks for examples
   - Before/after comparisons where applicable
   - **Velocity slide** near the end (repos, PRs, days)
   - Color-coded per deck theme

3. **Save to `showoff/`** with a descriptive filename like `feature-name-deck.html`

4. **Deploy to SharePoint** by running: `./deploy.sh filename.html`

### Remembered Presentation Styles

**"Useful Apple Keynote"** (preferred for information density):
- Black backgrounds, clean sans-serif typography
- Section labels (14px uppercase) + headlines (48-72px)
- Cards with titles and descriptions
- Code blocks, comparison tables, flow diagrams
- Velocity/stats grids
- Navigation dots at bottom

**"Apple Keynote"** (for maximum visual impact, lower density):
- Pure black backgrounds, San Francisco typography
- One major concept per slide
- Full-bleed imagery, bold centered headlines
- Avoid bullet points - use icons or 3-word phrases
- Premium, quiet, powerful aesthetic

### Deck Template Elements

Every deck should include:

1. **Title slide** - Feature name, one-line description, date
2. **Problem slide** - What pain point does this solve?
3. **Solution slides** - How it works, with examples
4. **Impact slide** - Metrics, before/after, real numbers
5. **Velocity slide** - Repos touched, PRs merged, days of dev
6. **CTA slide** - Where to learn more, how to try it

### File Organization

```
amplifier-stories/
├── showoff/           # All presentation HTML files
│   ├── cortex-amplifier-presentation.html
│   ├── shadow-environments-deck.html
│   └── ...
├── .env.local         # Your SharePoint path (gitignored)
├── .env.local.example # Template for new users
├── deploy.sh          # Copy decks to SharePoint
└── AGENTS.md          # This file
```

### Deployment

Decks are copied to a SharePoint folder for team sharing:

```bash
# Deploy all decks
./deploy.sh

# Deploy specific deck
./deploy.sh shadow-environments-deck.html
```

The SharePoint path is stored in `.env.local` (gitignored). Copy `.env.local.example` and set your path.

### Invocation

From any Amplifier session:

```
"Use storyteller in amplifier-stories to tell a story about [feature]"
"Create a deck about the new shadow environments feature"
"Make a presentation showing off recipe cancellation"
```

The agent will research, create, and deploy the deck.
