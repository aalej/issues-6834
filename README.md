# Repro for issue 6834

## Versions

firebase-tools: v13.4.0<br>
node: v20.10.0

## Steps to repro

1. Run `firebase emulators:start --project demo-project --import ./emulator-data --export-on-exit`
2. Open "http://127.0.0.1:4000/storage"
3. Open the image "Screenshot 2024-03-05 at 6.48.00 PM.png" to check preview
   - Clicking the file should open the image
4. Error is raised and emulators stops running:

```log
[debug] [2024-03-05T11:48:45.910Z] TypeError [ERR_INVALID_CHAR]: Invalid character in header content ["Content-Disposition"]
    at ServerResponse.setHeader (node:_http_outgoing:655:3)
    at sendFileBytes (/Users/<USER>/Desktop/Firebase-CLI-work/firebase-cli-git/pr-6832/firebase-tools/lib/emulator/storage/apis/shared.js:19:9)
    at /Users/<USER>/Desktop/Firebase-CLI-work/firebase-cli-git/pr-6832/firebase-tools/lib/emulator/storage/apis/firebase.js:101:47
    at process.processTicksAndRejections (node:internal/process/task_queues:95:5)
[error]
[error] Error: An unexpected error has occurred.
```
