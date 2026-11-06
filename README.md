# Self Chat

A one-page chat for notes and files to yourself that starts blank every day.

- **Enter** sends. **Shift + Enter** adds a new line.
- **Files of any type**, zip included, up to 50 MB each. Use the paperclip, drag them onto the page, or paste them. Tap a file to download it.
- **New messages show up on their own.** The page checks every few seconds while it's open, and about every 30 seconds while it's in the background.
- At midnight (your device's time), every message and file from the previous day is permanently deleted.
- The trash button erases today's messages and files right away.
- Your token is saved only in the browser you enter it in.

## How it works

**Messages** are saved as comments on one issue, titled "Self Chat", in a private repo. Deleting a comment removes it from GitHub.

**Files** are encrypted in your browser with a new random key for each file before they're uploaded. The encrypted file is stored on a branch for that day (`selfchat-files/YYYY-MM-DD`). The key is stored only in that file's comment. When the day is erased, the comment and the key are deleted along with the branch. Any copy GitHub keeps internally after that is unreadable without the key, so it stays scrambled. File names appear only in the comments, never in the repo's file list.

**Live updates** use GitHub's "has anything changed?" check. When nothing has changed, the check is very cheap, and those checks don't count against GitHub's hourly API limit.

## Token permissions

Use a fine-grained token at https://github.com/settings/personal-access-tokens, limited to `self-chat-data`, with these repository permissions:

- **Issues: Read and write** (messages)
- **Contents: Read and write** (files)

## Good to know

- If the page is closed at midnight, the erase happens the next time you open it.
- Failed sends show with a red outline. Tap one to retry.
- The 50 MB limit is per file. Larger files are refused before anything is uploaded.
- Like any online service, GitHub may keep internal backups for a while. Deleted messages could exist in those backups. Files stay unreadable, because their keys are gone.
- **Forget token** in settings removes the token from that browser. To cut off access everywhere, delete the token.
