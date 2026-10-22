# dataverse-skills

Two skills for keeping a replication package in Harvard Dataverse in step with your repository.

## The problem

Uploading a replication package to Dataverse by hand is slow and error prone, and the web firewall blocks direct API uploads of some code files, such as R and Stata scripts, with a 403 error.

## What it does

`dataverse-sync` uses the Dataverse Native API to upload, replace and delete files so the dataset matches your local files.

`dataverse-upload-zip` works around the firewall. It packs the blocked files into a ZIP archive, which Dataverse unpacks on arrival, so the files keep their folder structure.

## Install

Claude Code, as a plugin:

```bash
claude plugin marketplace add letitbk/dataverse-skills
claude plugin install dataverse-skills@dataverse-skills --scope user
```

Codex and other agents that read Agent Skills:

```bash
npx skills add letitbk/dataverse-skills -g -a codex
```

Replace `codex` with `claude-code` to install the plain skill folders for Claude Code instead of the plugin. You can also copy the folders under `skills/` into `~/.claude/skills/` or `~/.codex/skills/` by hand.

This repository holds `dataverse-sync` and `dataverse-upload-zip`. Start a new agent session after installing, then ask for the task in ordinary words or name the skill.

## Requirements

- A Dataverse API token from your account page, and the persistent identifier (DOI) of a dataset you can edit.
- Python 3 with `requests`.

## Limits

- Replacing or deleting files changes a draft version of the dataset. Review the draft in the web interface before you publish it.
- The skills are written for Harvard Dataverse. Other Dataverse installations may need a different server address.

## License

MIT. See `LICENSE`.
