# DIE Reborn Launcher

**English** | [简体中文](README.zh-CN.md)

The launcher for **DIE Reborn**, a community server for *Dead Island: Epidemic*. It installs and updates the client patch, shows whether the server is up and how many people are playing, and starts the game through Steam.

> **Unofficial fan project.** Not affiliated with, endorsed by, or associated with Deep Silver, Stunlock Studios, or any rights holder. No game files are distributed here — you need your own copy of the game.

| You want to… | Go to |
|---|---|
| **Play** | This page |
| **Host** your own server | The server: **<https://github.com/spardanviro/DIE-Reborn>** |

**Download:** [`DIE-Launcher.exe` from the latest release](https://github.com/spardanviro/DIElauncher/releases/latest)

---

## Connecting to the server

### What you need

- Windows 10 or 11. Nothing else to install.
- Steam, running and signed in.
- *Dead Island: Epidemic* installed through Steam. The game is no longer in the store, so it must already be in your library.

### Steps

1. **Download** `DIE-Launcher.exe` from the [latest release](https://github.com/spardanviro/DIElauncher/releases/latest) and put it anywhere — the desktop is fine. It does not need to be in the game folder.

   Windows may show a blue "Windows protected your PC" box the first time, because the file is not signed. Choose *More info* → *Run anyway*.

2. **Run it.** The launcher finds the game in your Steam library by itself and shows the folder on the *Client patch* card. If it cannot find the game, the big button says **Locate the game**: press it and select `Dead Island Epidemic.exe` in the game folder (in Steam: right-click the game → *Manage* → *Browse local files*).

3. **Press Install patch.** The launcher downloads the patch, checks it, and unpacks it into the game folder. This takes a few seconds. The game must be closed while it does this.

4. **Pick a server.** The **Servers** list shows every server that is up right now: its name, where it is, your ping to it, and how many people are online and how many matches are running. A green dot means it is up. Click the one you want; the launcher remembers your choice.

   Ping is coloured: green under 80 ms, yellow under 160 ms, red above. Pick the lowest you can.

5. **Press Play.** Steam starts the game and it connects to the server you picked. Log-in is automatic: your Steam account is your identity, so there is nothing to register and no password.

After the first time, it is just: open the launcher, press **Play**. To switch servers, click a different one in the list before pressing Play. When a new patch is out the button says **Update patch** instead; press it once, then Play.

### What the big button means

| Button | Meaning |
|---|---|
| **Locate the game** | The game was not found in Steam. Point the launcher at it. |
| **Install patch** | The game is not patched yet. |
| **Update patch** | A newer patch is available. |
| **Play** | Everything is ready. |
| **Game is running** | Close the game before installing, updating or uninstalling. |
| **Patch unavailable** | Neither GitHub nor the server could be reached, and no patch is installed. Check your connection and press *Check for updates*. |

The links along the bottom: *Check for updates*, *Change game folder*, *Open game folder*, *Uninstall patch*, and the language switch (English / 中文) on the right.

---

## Connecting to a server that is not in the list

Servers appear in the list on their own; you normally do not need this. It is for servers whose owner chose not to list them, and for your own server on your home network (private addresses are never listed, because nobody else could reach them). This needs launcher **1.1.0 or later**.

1. Next to `DIE-Launcher.exe`, create a text file named **`launcher.json`**.
2. Put the server's address in it. The server's host will tell you what it is:
   ```json
   { "serverHost": "203.0.113.10" }
   ```
   A domain name works too: `{ "serverHost": "play.example.org" }`.
3. Start the launcher. That server is added to the list and selected. Press **Install patch** if you have not yet, then **Play**.

To go back, delete `launcher.json` and pick another server in the list.

Make sure the file is really named `launcher.json` and not `launcher.json.txt` — in File Explorer, turn on *View → File name extensions* to check.

`launcher.json` accepts these settings:

| Setting | Meaning | Default |
|---|---|---|
| `serverHost` | A server to add to the list and select (IP or domain name) | none |
| `statusPort` | Port of the server's status endpoint | `8555` |
| `registry` | Where the server list comes from | the DIE Reborn server |
| `repo` | GitHub repository the patch is downloaded from, as `owner/name` | `spardanviro/DIElauncher` |

Hosting a server is covered step by step at **<https://github.com/spardanviro/DIE-Reborn>**.

---

## Troubleshooting

| Symptom | What to do |
|---|---|
| A server shows **Offline** or `– ms` | The server is down, or your network cannot reach it. Ask whoever runs it, or pick another. With a `launcher.json`, check the address for typos. |
| "Could not load the server list" | The registry could not be reached; the launcher still shows the server you picked last, and you can play on it. Press *Check for updates* to try again. |
| The download is slow or fails | The launcher tries GitHub first and falls back to the game server itself. If both fail, the status line under the button says why for each. Try again, or use a different network. |
| "No permission to write to the game folder" | Right-click the launcher → *Run as administrator*. |
| **Game is running**, but you closed the game | A game process is still open. End every "Dead Island Epidemic" process in Task Manager. |
| Play does nothing | Steam is not running, or not signed in. Start Steam first. |
| The game opens but shows a connection error | The server is down, or the game was started some other way than through the launcher or Steam. |
| "A newer launcher is available" | Press *Update launcher*. It replaces itself and reopens. |

## What the patch changes

`DIE-ClientPatch.zip` is unpacked into the game folder: the [BepInEx](https://github.com/BepInEx/BepInEx) loader, one plugin, and an `ip.cfg` that points the game at the server. The plugin makes the game log in with a normal Steam session ticket — the original game used a ticket only the original publisher could read, so no community server could tell who you are — and fixes a few client bugs.

The original `ip.cfg` is kept as `ip.cfg.orig`. **Uninstall patch** removes exactly the files the launcher installed and restores the original; the game itself is never modified.

The launcher keeps its settings in `%LocalAppData%\DIE Reborn\`. It does not run in the background and stores no account, password or token.
