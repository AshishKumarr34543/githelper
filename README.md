# Better Git Commit Message Helper

A small VS Code extension. It looks at the files you staged and suggests a commit
message for you. You can change the message, copy it, and paste it into Source
Control.

It works offline. It does not use AI and it does not use the internet. It only
reads your git repo. It never commits, never stages files and never changes your
history.

## How to use it

1. Stage the files you want in the commit.
2. Open the command palette and run "Suggest Commit Message from Staged Changes". You can also click "Commit msg" in the status bar.
3. A panel opens with a suggestion, for example `feat(auth): add loginRateLimiter`.
4. Change the text if you want, or click another type such as fix or docs.
5. Click "Copy message" and paste it into the Source Control box. Then commit like you always do.

If you stage or unstage more files, click "Refresh".

## What the panel shows

- **Confidence**: how sure it is. If it is low, check the message before you use it.
- **Type chips**: feat, fix, docs, refactor, test, chore and perf. The starred one is the suggestion, the dashed ones are the other options.
- **Message box**: you can edit it. It tells you when the first line gets too long.
- **Copy message**: puts the text on your clipboard.
- **Include scope / body**: turns the `(scope)` part and the file list on or off.
- **Why this suggestion**: the reasons it picked that type.
- **Staged files**: the files that will be committed, with their + and - counts.

If you change the type on a message you did not edit, it writes the subject again.
If you edited the message, it only changes the type and keeps your words.

## Settings

| Setting | Default | What it does |
|---|---|---|
| `betterCommit.maxHeaderLength` | 72 | Longest allowed first line (30 to 120). |
| `betterCommit.includeScope` | true | Add a scope when it is clear. |
| `betterCommit.includeBody` | false | Add a list of files as the commit body. |
| `betterCommit.showStatusBar` | true | Show the "Commit msg" button in the status bar. |
| `betterCommit.maxDiffSize` | 200000 | How much diff text it reads. Bigger diffs are read in part. |

It also respects the `git.path` setting of VS Code.

## Requirements

- Git needs to be installed.
- VS Code 1.85 or newer.

## Development

```bash
npm install
npm run compile
npm run package
```

Press F5 in VS Code to open a new window with the extension loaded.

```
src/analysis/   reads the diff and works out the message
src/git/        the read only git commands
src/ui/         the panel html and the messages
src/vscode/     the VS Code parts: panel, status bar, settings
src/service.ts  does the whole thing without VS Code types
```

## Note

The suggestions come from file names and diff text, so they are guesses. Check the
message before you commit it.
