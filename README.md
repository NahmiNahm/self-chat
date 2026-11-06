# Self Chat

A one-page chat for notes to yourself that starts blank every day. Type, press Enter, done.

- **Enter** sends. **Shift + Enter** adds a new line.
- At midnight (your device's time), every message from the previous day is permanently deleted.
- The trash button erases today's messages right away.
- Your token is saved only in the browser you enter it in.

## How it works

Messages are saved as comments on a single issue, titled "Self Chat", in a private repo. The page creates that issue the first time you connect. Whenever the page opens, comes back into view, or reaches midnight, it deletes every comment from before today.

The page uses issue comments instead of files because a deleted comment is removed from GitHub. Deleting a file only hides it, since the old version stays in the repo's history.

## Setup

### 1. Private data repo

A private repo named `self-chat-data` with **Issues** turned on (the default for new repos).

### 2. Fine-grained token

1. Go to https://github.com/settings/personal-access-tokens
2. Create a new token, or edit your existing `self-chat` token
3. Repository access: **Only select repositories**, then `self-chat-data`
4. Repository permissions: **Issues: Read and write**. Contents access isn't needed anymore.
5. Save, and copy the token if it's new

### 3. Page

`index.html` is hosted from the public `self-chat` repo with GitHub Pages. Open the page, enter your username, `self-chat-data`, and the token, then click **Save and connect**. Do this once on each device.

## Good to know

- **Erased means deleted from GitHub.** Comments are removed through GitHub's API, and nothing remains in the repo or the issue. Like any online service, GitHub may keep internal backups for a while under its own data retention policy.
- **Midnight uses your device's clock.** If the page is closed at midnight, the erase happens the next time you open it.
- **Failed sends** show with a red outline. Tap one to retry. Anything typed before midnight that never saved is dropped at midnight.
- **Forget token** in settings removes the token from that browser. To cut off access everywhere, delete the token at https://github.com/settings/personal-access-tokens
