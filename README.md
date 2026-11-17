# Better Git Commit Message Helper

A small VS Code extension I built. It looks at the files you staged and suggests a
commit message for you. You can change the message, copy it, and paste it into your
Source Control box.

## How to use it

1. Stage the files you want in the commit.
2. Open the command palette and run "Suggest Commit Message from Staged Changes". You can also click "Commit msg" in the status bar.
3. A panel opens with a suggestion, for example `feat(auth): add loginRateLimiter`.
4. Change the text if you want, or click another type such as fix or docs.
5. Click "Copy message" and paste it into the Source Control box. Then commit like you always do.
6. If you stage or unstage more files, click "Refresh".

## Why it picked that message

The panel shows more than the message itself. You also get a confidence score, the
type chips, the list of staged files and a "why this suggestion" section with the
reasons behind it. So you can see what led to the decision instead of trusting a
black box.

## Development

```bash
npm install
npm run compile
npm run package
```

## AI usage

AI helped me research how the architecture should look, and it helped me with the
confidence score part (thanks). I also used ChatGPT to ask questions while I was
developing.
