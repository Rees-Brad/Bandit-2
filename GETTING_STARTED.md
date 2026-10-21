# Getting started with Bandit 2

The Campaign Agent works with you on this campaign in the Claude Code panel.
Talk to it in plain language; it asks questions, offers options, and drafts
the files. You make the decisions, and every change is shown to you for
approval before it is written.

## Commands

- `/create-campaign`: resume work on this campaign. The agent reads the
  work log and open items and suggests what to do next.
- `/check-campaign`: look for broken links, unlinked maps, and other
  structure problems. It changes nothing.
- `/save-campaign`: save your progress. The agent updates the work log and
  open items, checks the campaign, and takes a snapshot.
- `/start-campaign`: when the campaign is ready to play, make a running
  copy for a group.
- `/create-collection`: organize a folder of campaigns as one git
  repository (see Git and collections).

Claude Code may show these with a prefix, such as
`/campaign-agent:create-campaign`.

## Working across several days

Building a campaign takes many sittings.

- Before you stop, run `/save-campaign`. The agent records what was done
  and decided in `WORKLOG.md`, updates `OPEN_ITEMS.md`, and takes a
  snapshot you can return to.
- Next time, open this folder and run `/create-campaign`. The agent picks
  up from the work log and open items.
- Earlier conversations are saved too. Reopen one from the past
  conversations button in the Claude Code panel, or with `/resume`.

## Files the agent keeps for you

- `OPEN_ITEMS.md` lists open questions and unfinished parts. The agent
  checks items off as they are done. Reorder items or mark them
  **(priority)** to tell the agent what to work on first, and add your own.
- `WORKLOG.md` is a short journal of each working session: what was done,
  what was decided and why, and ideas set aside for later.
- This file is a reference you can return to at any time.

## Your campaign folder

```text
campaign.md        goal, overview, rules edition, and links to every chapter
npcs.md            key NPCs
items.md           key magic items and artifacts
locations.md       key locations
maps/              map images (PNG, JPEG, or WebP)
chapters/
  01-<chapter>/
    chapter.md     the chapter outline
    adventures/    one file per adventure
    encounters/    one file per encounter, with stat blocks and a tracker
```

Every section is its own file, numbered in story order.

## A good layout in VS Code

- Keep the Explorer open on the left to see the whole campaign.
- Open a chapter, adventure, or encounter and press Ctrl+Shift+V
  (Cmd+Shift+V on a Mac) to read it as formatted text.
- Open the section's map beside it: drag the map's tab to the side of the
  editor.
- Keep the Claude Code panel open on the right.

## Maps

Make and edit maps in any tool, then save them into `maps/` as PNG, JPEG,
or WebP. Ask the agent to add a map to a section, and to answer questions
about it. Saving an edited map under the same name keeps every link to it
working.

## Git and collections

If the campaign uses git, every snapshot is a commit you can return to, and
VS Code's Source Control view shows what changed.

- **Collections.** A folder of campaigns, such as `~/Campaigns/levels-1-3`,
  can be a collection: a git repository in which each campaign is its own
  repository, registered as a submodule. Run `/create-collection` in that
  folder. New campaigns created inside it, and running copies started from
  them, are added automatically.
- `/save-campaign` and `/start-campaign` handle the submodules for you, so
  you never need to run git yourself.
- If you do run git commands yourself on submodules, such as
  `git clone --recurse-submodules`, add `-c protocol.file.allow=always`, for
  example `git -c protocol.file.allow=always clone --recurse-submodules ...`.
  Git blocks copying submodules from local folders by default and reports
  "transport 'file' not allowed". The agent adds the flag to its own
  commands and leaves your git settings alone.

## Master and running copies

This folder is the **master** campaign: the campaign as written. Games are
not run from it, because game sessions and the updates after them change
the files. When the campaign is ready to play, `/start-campaign` makes a
**running copy** for one group next to this folder, and you open that copy
to run the group's games. The master can start any number of groups.
